---
title: Emergency Recovery
excerpt: ⚠️ Discover how to retrieve Master Key in an emergency
deprecated: false
hidden: false
metadata:
  title: Back Up and Emergency Recovery
  description: >-
    Ensure the safety of your digital assets with backup and emergency recovery
    in Blockdaemon Wallet. Learn how to protect and restore your wallet in
    critical situations.
  image: https://files.readme.io/134406e-image_3.png
  robots: index
next:
  description: ''
---
In an emergency, you must recover the master key wallet to derive all other private keys within it. The Institutional Vault proposes a method for configuring the ERS in the MPC wallet, which is implemented when the wallet system is initiated.

> 📘 Note:
>
> The purpose of ERS is to recover the master private key, not to restore the wallet system. Both the backup Master Key and the restore wallet system processes use DB backups.

Recovery information is required to recover the master key. This data consists of encrypted key shares for each node that the correct share is encoded in the ciphertext. The recovery individual's public key is used to encrypt the key shares. **The private key owner** is the only person who can decrypt the ciphertext and recover the key shares. The secret key must be retained offline in a secure location and accessed only in an emergency.

# How to Create Master Key Recovery Information

Follow the steps below on how to create a master key and get the recovery information for wallet users:

1. Upon its first launch, the wallet requests MPA (nodes) to create its master key.
2. MPA nodes then:
   1. Create the master key along with a key ID.
   2. Create ERS recovery info and send it to each other. They must all agree on the material.
   3. The master key is then marked as operational, and the key ID and recovery material are sent to the wallet. Only an operational key can be used to derive new keys in the wallet.
3. Wallet users must then download the recovery info. 

> 📘 Note:
>
> It is best to start creating accounts on the wallet after validating and storing the recovery information.

# How to Recover the Master Key Shares from ERS Backup

1. Download the cold wallet CLI installation package using the link provided by your sales associate or technical representative. The cold wallet binary includes the ERS restore utility.
2. Change the directory to where you extracted the cold wallet CLI. On MacOS following these [steps](https://vault.docs.blockdaemon.com/docs/macos-system#step-3-permit-execution-of-the-installation-binary) to permit execution of the unsigned binary.
3. Run the following command to extract the private keys and chain codes from the backup file and print the JSON results.

**For macOS**

```shell
APP_MODE=docker ./coldwallet-cli-darwin ers  
   --backup-file-path={Where you store the backup file}  
   --private-key-pem-path={the prviate key path} 
   --derivation-path={the derivation path}
```

Replace `{the derivation path}` with the appropriate path. Please refer to the [Derivation Paths](https://vault.docs.blockdaemon.com/docs/derivation-paths) page.

**For Linux**

```shell
./coldwallet-cli-linux ers  
   --backup-file-path={Where you store the backup file}  
   --private-key-pem-path={the prviate key path} 
   --derivation-path={the derivation path}
```

Replace `{the derivation path}` with the appropriate path. Please refer to the [Derivation Paths](https://vault.docs.blockdaemon.com/docs/derivation-paths) page.

4. The results should be in the following format:

```json
{  
  "ED-25519": {  
    "CurveName": "ED-25519",  
    "PrivateKey": "0395cd07dc53b49d256a0d3a9272ec63777cf0e4ce1806cab43e3b296188f9bf",  
    "ChainCode": "3405953bf9ff179576ceaa76a2ccbb4fb61623f6aae2eb699b835b047b0df99f"  
  },  
  "secp256k1": {  
    "CurveName": "secp256k1",  
    "PrivateKey": "f6f7fdb69634b3f2b8b6febcf5f00a586bd949c542f36a7cd8d1a0723f46d50c",  
    "ChainCode": "91148669c79df96c705517baaa01f7c94a6441fd2f0a8e77da5e88f2d2ea3e40"  
  }  
}
```

<Support />
