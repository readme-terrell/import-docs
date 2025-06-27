---
title: Self-Hosted Deployment
excerpt: 💡Find out how to set up a Sandbox Institutional Wallet on your own.
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
> ❗️ Important:
>
> We have deprecated Goerli testnet.

# High-level sequence

<Image align="center" src="https://files.readme.io/0b55b1f-blockdaemon_flow_v4-landscape.png" />

The AWS deployment of the Self-installed Institutional Wallet involves distinct, secure setup steps that leverage separate AWS KMS policies and Secret Manager instances to guard each of the MPA Nodes. During MPA Node execution, sensitive in-memory data is protected by Nitro enclaves. This ensures that no single party has access to multiple master key shards.

> 📘 Note:
>
> At this time, the automated deployment is packaged exclusively for AWS.

## Prerequisite

1. The admin must have AWS knowledge and scripting experience to be on point to execute the installation.
2. The admin must have familiarity with Docker and Cosign.
3. Never use the root user for installs, and be sure to follow AWS best practices [here](https://docs.aws.amazon.com/accounts/latest/reference/best-practices-root-user.html).

## Step 1: Send deployment request form

1. To obtain the request form, [Contact Us](mailto:sales@blockdaemon.com) or go to this [page](https://www.blockdaemon.com/get-started/iwtoken#cta) and enter your contact details. 
2. Our sales team will send you a deployment request form which includes more detailed information including but not limited to:
   1. A DNS zone will be used for your hosted wallet. Example: [https://wallet](https://wallet)`<subdomain>`.`<companydomain.com>`. The wallet installer will create networking services within this zone. Furthermore, the authentication service will call back to this domain endpoint.
   2. A new AWS Account ID and Region will be used for the installation. The 12-digit AWS identifiers are used to assign permissions to pull container images from the Institutional Wallet AWS EC2 Container Registry repository.
   3. At least 2 administrators and emails.
   4. Auth0 Tenant.
   5. Emergency Recovery Secret (ERS) Public Key.
   6. AWS Cloud9 Development Environment. 
3. To initiate the process, please complete the form and send it back to us.

## Step 2: Configure identity provider

The wallet relies on an external Open ID Connect (OIDC) authentication service to verify user identities and provide secure access tokens to the wallet. For details about the auth0 installation, please refer to [here](https://wallet.docs.blockdaemon.com/docs/configuring-auth0).

## Step 3: Create AWS Cloud9 Development Environment

To deploy the wallet, AWS Cloud9 Development Environment would be used to streamline the onboarding process and eliminate a process to re-specify and re-authenticate your AWS account ID and region. For details on creating the environment, please refer to [here](https://docs.aws.amazon.com/cloud9/latest/user-guide/create-environment-main.html).

> 📘 Note:
>
> Please ensure that you update the `AWS_REGION` and `DEPLOYER_REPO` within the Makefile file to use the AWS region value that you have.

## Step 4. Delegate new wallet DNS zone

1. The network administrator sets DNS Nameserver zone delegations from the company's authoritative zone to the new AWS name servers.

> 📘 Note:
>
> DNS name server zone delegations may require up to one business day for completion, depending on the authoritative zone settings.

2. To add a corresponding NS record to the Hosted Zone, please do the following steps:

   1. Go to Route 53 console in the AWS account where the wallet long-lived stack is deployed.
   2. You should see a hosted zone named `<your namespace>`.`<your hosted zone>`
   3. Click on the hosted zone.
   4. Copy the values from the NS record to create the other one in your prerequisite hosted zone.
   5. Navigate to the parent hosted zone you set up as a prerequisite.
   6. Click the **Create record** button.
   7. Select **NS - Name servers for a hosted zone** from the Record type dropdown.
   8. Paste the values you copied previously in the value text area.

> 📘 Note:
>
> We recommend a value of 1800 seconds.

## Step 5: Generate Emergency Recovery Secret

In the event of a disaster you will need to restore your master wallet private key from backup. This backup is encrypted with the Emergency Recovery Secret (ERS) key-pair. You need to generate this Emergency Recovery Secret (ERS) key-pair prior to the installation and backup of the master private key. 

This ERS private key must be generated and stored securely. Follow your company policy when performing the key ceremonies. 

For a testnet network or sandbox environment, the following command can be used to generate key pair locally:

```
$ openssl genrsa -out private-key.pem 3072  
$ openssl rsa -in private-key.pem -pubout -outform D | base64
```

The base64 encoded output of the public key must be supplied during the application installation of the wallet.

### Differences between Production and Sandbox Environment

In the context of Multi-Party Computation, separating the administrators of each MPA node is crucial for maintaining security. Each MPA node stores a key shard of the wallet's master key in its respective database. Each database instance is encrypted with an Encryptor Master Password. Before deployment, the Encryptor Master Password for each database is generated by a different privileged actor and stored in a separate vault.

However, as this is a sandbox deployment, certain security practices are relaxed in favour of a simplified installation. The differences are as follows:

<Table align={["left","left","left"]}>
  <thead>
    <tr>
      <th>
        Difference
      </th>

      <th>
        Production
      </th>

      <th>
        Sandbox
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Separation of AWS accounts and related MPA node infrastructure
      </td>

      <td>
        The MPA nodes and their respective secrets are installed into an AWS account, with separate KMS policies and SecretManager vaults.  

        This ensures no privileged actor with AWS account root permissions can compromise the wallet system.
      </td>

      <td>
        All infrastructure, secrets, and MPA nodes are installed in a single AWS account.  

        A single AWS account administrator can compromise this wallet system.
      </td>
    </tr>

    <tr>
      <td>
        Encryptor Master Password generation
      </td>

      <td>
        Each of the three privileged actors will generate their own Encryptor Master Password, which will be supplied during each Key Ceremony Seeding process.  

        This is performed in three separate steps by each respective privileged user.
      </td>

      <td>
        The Key Ceremony and Seeder tool automatically generates each MPA node’s Encryptor Master Password and stores them within a single AWS account.  

        This is performed in a single step by a single privileged user.
      </td>
    </tr>
  </tbody>
</Table>

## Step 6: Generate customer tokens

We will generate an **Institutional Wallet API key** granting access to the various Blockdaemon hosted API suite supporting services. The installation software repository details and these tokens will be sent to you via a secure channel.

## Step 7: Authenticate to the Institutional Wallet and validate software authenticity

Ensure that you have the following tools and have verified the authenticity of the software:

* Docker - [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/) 
* Cosign - [https://docs.sigstore.dev/cosign/installation/](https://docs.sigstore.dev/cosign/installation/) 
* New AWS Account details:
  * AWS Account credentials
  * AWS Region

Use your new AWS Account credentials to authenticate to the Institutional Wallet container registry repository:

```
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin \
638663786504.dkr.ecr.us-east-1.amazonaws.com
```

Use the `cosign` executable to validate the authenticity of the images against the Institutional Wallet signing authority:

```
BLOCKDAEMON_SIGNING_AUTHORITIY="-----BEGIN PUBLIC KEY-----
MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEfJLNcMpG3m8EOswCU7cqzWBsHSfY
+rt4HRvbPWAqadeYxIhhBWXjWDiRk4SAa2XXhZVi7IEO7TMaJcuFyHvoBQ==
-----END PUBLIC KEY-----" \
cosign verify --key env://BLOCKDAEMON_SIGNING_AUTHORITIY 638663786504.dkr.ecr.us-east-1.amazonaws.com/blockdaemon/wallet-deployer/aws:<tag>
```

## Step 8: Installation of infrastructure and applications

You will carry out the wallet installation by following Steps A-D of the below sequence:

<Image align="center" src="https://files.readme.io/438525a-Slide1.PNG" />

### Step 8a. Configuration generation - OPTIONAL

> 📘 Note:
>
> `customer_config.yaml` is only required if you do not provide a full environment configuration and only gives us AWS account number. If you provide the full config, we will do the following steps for you.

The wallet installation requires several input variables during set-up. The list of required inputs is itemized in the  `customer_config.yaml` template file. From this file, an installation specification file is generated containing the wallet infrastructure and application defaults. This autogenerated installation specification can be customized prior to the install and used within deployment pipelines for future updates.

1. Download the `customer_config.yaml` template file from the wallet container image to your local path:

```
aws s3 cp s3://638663786504-prod-mpa-deployment-customer-artifacts/release/[versionnumber]/Makefile
aws s3 cp s3://638663786504-prod-mpa-deployment-customer-artifacts/[customer]/customer_config.yaml
make pull-deployer
```

> 📘 Note:
>
> * \[versionnumber] is the version number.
> * \[customer] is your organization name.

2. Update the `customer_config.yaml` with your deployment-specific values using a text editor.
3. Ensure the updated `customer_config.yaml` is in the current path and executes the wallet configuration generation process, which will output the installation specification to `bd-wallet.yaml` within the local path:

```
make generate-wallet-spec
```

4. The `bd-wallet.yaml` configuration file includes autogenerated values for the below. Adjust the `bd-wallet.yaml` configuration values according to your setup needs.
   1. Default MPA Administration Policies
   2. Infrastructure values with references to the secrets created as part of the seeding process
   3. Blockchains and assets enabled within the wallet

> 📘 Note:
>
> 1. Refer to an example configuration with embedded explanations for each value [here](https://wallet.docs.blockdaemon.com/docs/mpa-self-installed-blockdaemon-wallet-sandbox-deployment-process-configuration-yaml-copy).
> 2. The MPA node Administration Policies are not meant to be changed after setup and cannot be changed through the Wallet UI. These include policies for registering users, deleting users, changing transfer policies, assigning groups to a user, etc. Refer to the Administration Policies [here](https://wallet.docs.blockdaemon.com/docs/all-about-policies).

### Step 8b. Deploy the baseline infrastructure

The deployer will instantiate baseline infrastructure such as VPCs, subnets, DNS zones, IAM roles, KMS policies, SecretsManager vaults, databases and compute clusters. This infrastructure is required for the later installations of remaining compute infrastructure and applications.

1. The first deployment stage can be done individually, or together. If you choose to deploy the first stage together with a single command with the `customer_config.yaml` and `bd-wallet.yaml` in the current path, please enter the following command. Skip to step 8c after doing so. Otherwise, run the commands in steps 2-6 below.

```
make deploy-stage-1
```

**OR**

2. Initiate the baseline infrastructure installation with the `customer_config.yaml` and `bd-wallet.yaml` in the current path.

```
make deploy-baseline
```

3. Make a note of the created DNS Nameserver addresses, which must be delegated to from the parent domain.
4. The ECR repositories that will house the wallet application container images need to be populated with images that are bundled in the deployer container. To populate these container images, run the following make command:

```
make deploy-service-images
```

5. Deploy the wallet long-lived resources by enterring the following make command:

```
make deploy-wallet-long-lived
```

6. To deploy policy node KMS keys, run the command below:

```
make deploy-policy-nodes-long-lived
```

### Step 8c. Generate and populate secrets

The Encryptor Master Password is highly sensitive as it encrypts the MPA node’s database containing the wallet’s master key share. For every MPA node there must be a corresponding Encryptor Master Password. Prior to application deployment, the Encryptor Master Password for each database must be generated. The tool encrypts and uploads the Encrypted Master Password to the corresponding AWS SecretManger vault. 

1. Initiate the secret generation using the`customer_config.yaml` and `bd-wallet.yaml` in the current path by running the following command:

```
make generate-secret-file
```

2. Populate the secret file by running the following command:

```
make populate-secrets
```

### Step 8d. Deploy wallet and MPA node applications

 After populating the wallet environment secrets in secrets manager, you will deploy the wallet application. This application consists of microservices deployed on AWS Elastic Container Service (ECS). These microservices include:

* **Wallet**: The service container for the wallet itself. After this deployment, the service will be defined, but not started.
* **Facade**: Service container used as an API between the web application and the microservice backend.
* **Approval**: The container for the approval service. This is used for transaction approvals within the wallet application.
* **Mosquitto**: The container for the MQTT messaging broker. This is the message broker used for messaging between service containers in the application

1. The final deployment stage can be done individually, or together. If you choose to deploy the final stage together with a single command with the `customer_config.yaml` and `bd-wallet.yaml` in the current path, please enter the following command. Skip to step 9 after doing so. Otherwise, run the commands in steps 2-4 below.

```
make deploy-stage-2
```

**OR**

2. To deploy the wallet application containers, use the following command:

```
make deploy-wallet
```

3. After the wallet is deployed, you need to deploy the policy nodes and nitro enclave to communicate securely. To do that, use the following command:

```
make deploy-nitro-nodes
```

4. Finally, once all of the supporting infrastructure and secret values are in place, we are ready to start the wallet application! To do so, issue one final make command:

```
make start-wallet
```

## Step 9: Backup the wallet's master private key

Upon first logging in and pairing your account with the Institutional Wallet Approver App, approve backing up the wallet’s master private key from the Approver App. Ensures this backup is stored separately from the wallet system for use in recovery during a disaster.

Refer to the backup and process here: [Back Up Master Key](https://wallet.docs.blockdaemon.com/docs/back-up-master-key)

<Support />

<br/>