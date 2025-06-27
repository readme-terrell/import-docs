---
title: Confidential Computing - Remote Attestation and Secret Injection
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Overview

This page describes the principles of remote attestation on AWS Nitro and presents a series of recommendations to protect the MPA policy node code and its associated secrets.

## Remote Attestation

Remote attestation, or cryptographic attestation in AWS Nitro, is a robust security mechanism to verify the integrity and authenticity of the software stack operating on Nitro enclaves and the associated hardware. Using cryptographic primitives, the nitro hypervisor verifies the integrity of diverse system components, such as boot loaders, kernels, and initramfs. This process generates unique measurements comprising hashes and platform configuration registers (PCRs) for each component involved in the boot process of AWS Nitro, further enhancing system security.

> 📘 Note:
>
> The comprehensive list of PCR measurements available for use can be found [here](https://docs.aws.amazon.com/enclaves/latest/user/set-up-attestation.html).

<Image align="center" src="https://files.readme.io/f83a943-Asset_2300x_5.png" />

The image above illustrates the process of creating an Attestation Document. Specifically tailored to AWS Nitro and remote attestation, the document acts as cryptographic proof, ensuring the MPA policy node within the Nitro enclave is genuine, secure, and unaltered during the boot process or while the EIF image file is at-rest. The process can be summarized as follows:

Boot-up Initiation: The MPA policy node in the Nitro enclave initiates the boot-up sequence.

1. **Asymmetric Key Generation**: During boot-up, the MPA policy node generates a unique asymmetric key pair comprising a private key and a corresponding public key.
2. **PCR Measurement Request**: The MPA policy node requests a specific set of PCR measurements from the AWS Nitro hypervisor.
3. **Attestation request**: The MPA policy node requests a cryptographic attestation consisting of a specific set of PCR measurements from the AWS Nitro hypervisor and and provides its just-generated public key.
4. **Signed cryptographic attestation document**: Upon receiving the request, the AWS Nitro hypervisor signs the requested PCR measurements as well as MPA policy node public key using its private key.\
   a. **Signed Measurement Data**: The AWS Nitro hypervisor returns the signed PCR measurements to the MPA policy node.\
   b. **Public Key Signing**: The AWS Nitro hypervisor signs the MPA policy node's public key with its private key.
5. **Attestation Document Creation**: The MPA policy node combines the signed PCR measurements and the signed public key to form the Attestation Document.

## High-Level Workflow

<Image align="center" src="https://files.readme.io/b8ca1ed-Asset_1300x_7.png" />

The following step-by-step processes illustrate the high-level workflow of the Policy Node interacting with AWS KMS for handling node code and its associated secrets:

1. **Fetch Encrypted Blob**: After generating the attestation document, the MPA policy node retrieves an encrypted blob from persistent storage. This blob can contain various items, such as the entire configuration, a set of secrets, or an encrypted EncryptorKeyFile used to derive keys for encrypting the MPA policy node shares.
2. **Submission to AWS KMS**: The MPA policy node submits the attestation document and the encrypted blob to the AWS Key Management Service (KMS) for further processing.
3. **CMK Policy Verification**: Upon receiving the data, AWS KMS verifies the Customer Master Key (CMK) policy to ensure that the policy node has the necessary permissions to access and use the specified CMK.
4. **PCR Value Verification**: AWS KMS checks whether the PCR (Platform Configuration Register) values provided by the MPA policy node in the attestation document match the defined conditions in the CMK policy. This step ensures that the attestation is based on the correct system configuration.
5. **Attestation Document Validation**: AWS KMS verifies the validity of the attestation document's signature to confirm its authenticity and integrity.
6. **Blob Decryption**: If the CMK policy conditions are met, and the attestation document's signature is valid, AWS KMS proceeds to decrypt the encrypted blob using the appropriate CMK.
7. **Re-encryption with Public Key**: The decrypted content is then re-encrypted by AWS KMS using the provided public key from the attestation document. This step ensures that only the MPA policy node, with access to the corresponding private key, can read the data.
8. **Ciphertext Return**: The resulting ciphertext, which now holds the re-encrypted blob, is sent back securely to the MPA policy node.

> 📘 Note:
>
> All communication between the MPA policy node and AWS KMS is TLS-secured, providing a secure and encrypted channel for data exchange throughout the process.

The process involves cryptographic verification through the attestation document, ensuring the integrity of the node and providing a secure way to access and handle sensitive data within the AWS Nitro environment.

## Recommendations for EIF deployment

There are two primary options available for deploying the MPA (MPC Policy Authority) policy node's Enclave Image File (EIF):

1. **Blockdaemon-Provided EIF**: If the customer chooses to use the EIF provided by Blockdaemon, they will need to securely register the PCR (Platform Configuration Register) values provided by Blockdaemon and the EIF. It is strongly recommended to rely on the PCR8 measurement for the decryption policy. This measurement remains constant even when an updated EIF is released, eliminating the need for frequent updates to the KMS (Key Management Service) policy.
2. **Customer-Built EIF**: Alternatively, customers can build their own EIF using the MPA policy node docker image. In this case, the customer can choose which PCR to use for the KMS policy. The recommended choices are either PCR0 (image file measurement) or PCR2 (application measurement). However, it is essential to note that opting for these measurements will require updating the KMS policy each time a new EIF is built, such as when a new MPA policy node image becomes available. As an alternative to frequent KMS policy updates, the customer also has the option to generate a signing certificate and a private key and to rely on PCR8 value for attestation and secret injection.

> 📘 Note:
>
> Please refer to the [PCR8](https://docs.aws.amazon.com/enclaves/latest/user/set-up-attestation.html) section of the AWS Cryptographic Attestation Guide for step-by-step instructions on how to construct and sign the EIF using a private key.

## MPA policy node EIF bootstrap technical details

The Enclave Image File (EIF) is constructed from a Nitro-specific Docker image, which executes an entry point responsible for environment setup and various tasks:

1. **Networking Stack Setup**: The entry point sets up a generic networking stack using `socat`.
2. **Environment Variable Configuration**: Environment variables, including AWS region and EC2 instance token for retrieving instance metadata, are configured.
3. **Fetching Configuration Files and Encrypted Blob(s)**: Non-sensitive configuration files and encrypted blob(s), such as `EncryptoKeyFile`, are fetched.
4. **Cryptographic Attestation and Decryption**: The cryptographic attestation with AWS KMS is implemented through the `attestor.py` Python script. This script requires the AWS region for KMS decryption, the ciphertext file to decrypt, and the destination path within the enclave's user space to write the resulting plaintext if decryption is successful. The ciphertext is assumed to be encrypted with KMS and contains the KMS CMK arn (which does not need to be specified separately). The `attestor.py` script utilizes the `aws-nitro-enclaves-nsm-api` library from AWS to interact with the `/dev/nsm` device within Nitro and retrieve the attestation document. For Python script support, the `aws-nitro-enclaves-nsm-api` library should be patched with `nsmlib_cpython_wrappers.patch`, and the compiled `libnsm.so` should be placed in the Nitro-specific Docker image.

The `attestor.py` script carries out the following steps:

1. Generates an **RSA2048 key pair**.
2. Requests an **attestation document from NSM**, which includes nitro-signed PCR values and the newly generated RSA public key.
3. Initiates a **decryption call** to AWS KMS, providing the ciphertext blob and the attestation document.
4. If AWS KMS decryption succeeds, the script decrypts the CiphertextForRecipient field using the RSA private key and the decrypted AES symmetric key.
5. Writes the cleartext to the file specified as an argument.

The EIF can be made generic by retrieving the MPA node number from the EC2 instance metadata tag. The tag must be enabled and configured to reflect the corresponding node number.

> 📘 Note:
>
> To configure and enable the metadata tag, please see [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html#work-with-tags-in-IMDS).

```
export NODE_NUM=`curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/tags/instance/mpa-node`
echo "MPA node number: ${NODE_NUM}"
```

> 📘 Note:
>
> The `http://169.254.169.254` is the baseURL for AWS metadata service.

<Support />
