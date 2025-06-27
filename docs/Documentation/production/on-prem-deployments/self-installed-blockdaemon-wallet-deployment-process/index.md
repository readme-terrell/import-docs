---
title: AWS Deployment Process
excerpt: 💡Find out how to set up a Production Institutional Vault on your own.
deprecated: false
hidden: false
metadata:
  title: Production - Self-installed Blockdaemon Wallet Deployment Process
  description: >-
    Learn the seamless process of deploying a self-installed Blockdaemon Wallet.
    Explore the steps and empower your blockchain asset management.
  robots: index
next:
  description: ''
---
The AWS deployment of the Self-installed Institutional Vault involves distinct, secure setup steps that leverage separate AWS KMS policies and Secret Manager instances to guard each of the MPA Nodes. During MPA Node execution, sensitive in-memory data is protected by Nitro enclaves. This ensures no single party has access to multiple master key shards.

## Roles and Responsibilities

This table represents the roles and responsibilities of all parties involved in this installation. Due to the complex installation, please be sure to assign your team member with the following roles and responsbilities. 

| Roles                | Responsibilities                               |
| :------------------- | :--------------------------------------------- |
| Infrastructure admin | The admin that manages wallet infrastructure   |
| Policy node admin    | The admin that manages one policy node KMS key |

The number of admins is equal to the number of AWS accounts being used to distribute the wallet infrastructure. For example, in the recommended configuration, the wallet partitions will be deployed such that one policy node KMS key will reside in the same AWS account as the wallet infrastructure and the other two policy nodes KMS keys will reside in two other separate AWS accounts. 

In this case, your team member actors, roles, and responsibilities would be as follows:

| Actor   | Roles                                 | Responsibilities                                                      |
| :------ | :------------------------------------ | :-------------------------------------------------------------------- |
| Actor A | Infrastructure and policy node0 admin | The admin that manages wallet infrastructure and policy node0 KMS key |
| Actor B | Policy node1 admin                    | The admin that manages policy node1 KMS key                           |
| Actor C | Policy node2 admin                    | The admin that manages policy node2 KMS key                           |

### Summary of Steps Performed Based on Roles for Installation

To make sure you follow this instruction carefully, we summarize which roles should perform which step; please refer to the table below for details.

| Roles                | Steps Performed    |
| :------------------- | :----------------- |
| Infrastructure admin | 1, 4 - 11, 13 - 16 |
| Policy nodes admins  | 1, 4 - 9, 12 - 13  |

## Prerequisite

1. The admin must have AWS knowledge and scripting experience to be on point to execute the installation.
2. The admin must have familiarity with Docker, and have a local environment with docker, make and the AWS CLI installed. Admin users should have AWS credentials for the account where the sandbox will be installed, configured locally, or available to configure with environment variables. 
3. Never use the root user for installs, and be sure to follow AWS best practices [here](https://docs.aws.amazon.com/accounts/latest/reference/best-practices-root-user.html).
4. Create an auth0 tenant that includes single and native applications for the wallet. For details, please refer [here](https://vault.docs.blockdaemon.com/docs/configuring-auth0).
5. A DNS zone will be used for your hosted wallet. Example: [https://wallet](https://wallet)`<subdomain>`.`<companydomain.com>`. The wallet installer will create networking services within this zone. Furthermore, the authentication service will call back to this domain endpoint.
6. A new AWS Account for installation The 12-digit AWS identifiers are used to assign permissions to pull container images from the Institutional Vault AWS EC2 Container Registry repository.
7. Emergency Recovery Secret (ERS) Public Key. For details, please refer to this [step](https://vault.docs.blockdaemon.com/docs/self-installed-blockdaemon-wallet-deployment-process#step-2-generate-emergency-recovery-secret).
8. A local development environment to perform the install.
9. Have the following accounts:
   1. A Blockdaemon API key and username
   2. Chainalysis ([https://www.chainalysis.com/](https://www.chainalysis.com/)) only if you want to use the transaction risk assessment feature.

## Recommended AWS Wallet Architecture

Understanding the recommended AWS wallet architecture depicted in the image below is important before you deploy.

<Image align="center" src="https://files.readme.io/d23f41e910d0e494132c8c071ab760f6612f777a16f5095c5aaedda45f2fde7d-Asset_23300x.png" />

<br />

## Step 1: Create Local Installation Environment

To deploy the wallet, **all the infrastructure and policy nodes admins must configure a local environment for deployment**.  On the machines where the installation will be performed, the following must be configured:

* [docker](https://www.docker.com/)
* make
* AWS cli
* cosign (recommended, required for image validation) 

Each admin should have separate credentials configured for their corresponding AWS account.

If you run into issues setting up a local environment with the dependencies above, reach out to Blockdaemon Customer Success Manager. 

## Step 2: Generate Emergency Recovery Secret

In the event of a disaster you will need to restore your master wallet private key from backup. This backup is encrypted with the Emergency Recovery Secret (ERS) key-pair. You need to generate this Emergency Recovery Secret (ERS) key-pair prior to the installation and backup of the master private key. 

> 📘 Note:
>
> If you already generated this before, please skip this step and go to the next step.

This ERS private key must be generated and stored securely. Follow your company policy when performing the key ceremonies. 

For the mainnet or production environment, be sure to understand the importance of your key ceremony fully, we suggest starting with the following [document](https://d1c2gz5q23tkk0.cloudfront.net/assets/uploads/2956620/asset/CVA_Trusted_Key_Ceremony_Guidelines.pdf?1594131972) from the Crypto Valley association. 

The base64 encoded output of the public key must be supplied during the application installation of the wallet.

## Step 3: Generate customer tokens

We will generate an **Institutional Vault API key** granting access to the various Blockdaemon hosted API suite supporting services, if you did not have one when filling out your intake form. The installation software repository details and these tokens will be sent to you via a secure channel.

> 📘 Note:
>
> If you already generated this before, please skip this step and go to the next step.

## Step 4: Authenticate to the Institutional Vault and validate software authenticity

Ensure that you have the following tools and have verified the authenticity of the software:

* Docker - [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/) 
* Cosign - [https://docs.sigstore.dev/cosign/installation/](https://docs.sigstore.dev/cosign/installation/) 
* New AWS Account details:
  * AWS Account credentials
  * AWS Region

Use your new AWS Account credentials to authenticate to the Institutional Vault container registry repository:

```shell
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin \
638663786504.dkr.ecr.us-east-1.amazonaws.com
```

Use the `cosign` executable to validate the authenticity of the images against the Institutional Vault signing authority. Replace the `<version>` tag with the wallet version - **OPTIONAL**

```shell
BLOCKDAEMON_SIGNING_AUTHORITIY="-----BEGIN PUBLIC KEY-----
MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEfJLNcMpG3m8EOswCU7cqzWBsHSfY
+rt4HRvbPWAqadeYxIhhBWXjWDiRk4SAa2XXhZVi7IEO7TMaJcuFyHvoBQ==
-----END PUBLIC KEY-----" \
cosign verify --key env://BLOCKDAEMON_SIGNING_AUTHORITIY 638663786504.dkr.ecr.us-east-1.amazonaws.com/blockdaemon/wallet-deployer/aws:<version>
```

## Step 5: Pull Wallet Installer Makefile

All of the infrastructure and/or policy nodes admins should pull the Makefile for the version of the wallet software that will be installed. If you are unsure of which version to use, please reach out to Blockdaemon Customer Success Manager. 

```shell
aws s3 cp s3://638663786504-prod-mpa-deployment-customer-artifacts/customer/<customer_namespace>/Makefile
```

## Step 6: Configure Makefile Vars

The Makefile downloaded in the previous step has a default value of **CUSTOMER\_MPA\_ENVIRONMENT** that will need to be updated with environment variable overrides, or by manually modifying the Makefile. It should be updated to the environment name you will be deploying to. This is also the DNS prefix for the environment. Blockdaemon recommends using “testnet” and “mainnet” for environment names, but these can be customized to suit a specific customer's needs (Default = testnet).

> 📘 Note:
>
> All of the infrastructure and/or policy nodes admins need to perform this step.

## Step 7: Pull Configuration Files

The wallet installation configuration is defined in the`bd-wallet.yaml`, and the users and policies that will be applied are defined in `bootstrap.yaml`. Blockdaemon generates these files for **all of the infrastructure and/or policy nodes admins** to download with the information provided in the pre-engagement form. For details, please refer to the steps below:

```shell
make pull-wallet-spec
make pull-bootstrap-spec
```

1. Download your pre-generated `bd-wallet.yaml` `bootstrap.yaml`and  by executing the following:

> 📘 Note:
>
> 1. Refer to an example `bd-wallet.yaml` configuration with explanations for each value [here](https://vault.docs.blockdaemon.com/docs/mpa-self-installed-institutional-wallet-production-deployment-process-configuration-yaml#bd-walletyaml-specification).
> 2. The MPA node Administration Policies are not meant to be changed after setup and cannot be changed through the Wallet UI. These include policies for registering users, deleting users, changing transfer policies, assigning groups to a user, etc. Refer to the Administration Policies [here](https://vault.docs.blockdaemon.com/docs/all-about-policies).

## Step 8: Pull the Deployer Image

The last step prior to installation is to pull the deployer image. This can be done by executing the following:

```shell
make pull-deployer
```

> 📘 Note:
>
> Please make sure that all of the infrastructure and/or policy nodes admins perform this step.

## Step 9: Deploy the baseline infrastructure

Prior to running the installation commands, make sure that the value for the **CUSTOMER\_MPA\_ENVIRONMENT** value at the top of the Makefile matches the environment name you wish to deploy from your `bd-wallet.yaml`. Once this has been validated, you can begin installation with the deployer. 

The deployer will instantiate baseline infrastructure such as VPCs, subnets, DNS zones, IAM roles, KMS policies, SecretsManager vaults, databases and compute clusters. This infrastructure is required for the later installations of remaining compute infrastructure and applications. 

All the AWS accounts, including AWS accounts for infrastructure and policy nodes, need to have the baseline stack deployed. To deploy this, **all of the infrastructure and/or policy nodes admins** need to initiate and deploy the baseline stack with the following command:

```shell
make deploy-baseline
```

## Step 10: Deploy Service Images

The ECR repositories that will house the wallet application container images need to be populated with images that are bundled in the deployer container. To populate these container images, **the infrastructure admin** needs to run the following make command:

```shell
make deploy-service-images
```

## Step 11: Deploy the Wallet Long-Lived Resources

The **infrastructure admin** needs to deploy the wallet long-lived resources by entering the following make command:

```shell
make deploy-wallet-long-lived
```

> 📘 Note:
>
> The resources in the long lived stack should not be deleted unless you are ready to fully decommission your wallet instance.

## Step 12: Deploy the Policy Node KMS keys

Each of the policy node admin needs to deploy policy node KMS keys and run the command based on the account that they manage. 

1. The **policy node0 admin** will run the following command:

```shell
make deploy-policy-node0-long-lived
```

2. The **policy node1 admin** will run the following command:

```shell
make deploy-policy-node1-long-lived
```

3. The **policy node2 admin** will run the following command:

```shell
make deploy-policy-node2-long-lived
```

## Step 13: Generate and populate secrets

The Encryptor Master Password is highly sensitive as it encrypts the MPA node’s database containing the wallet’s master key share. For every MPA node there must be a corresponding Encryptor Master Password. Prior to application deployment, the Encryptor Master Password for each database must be generated. The tool encrypts and uploads the Encrypted Master Password to the corresponding AWS SecretManger vault. 

1. The **infrastructure admin** needs to initiate the secret generation by running the following command:

```shell
make generate-secret-file
```

2. The **infrastructure admin** fills in the secrets file `customer-secrets.yml` with
   1. **Blockdaemon Workspace name** (ubiquity\_org\_username) 
   2. **Blockdaemon API key** (ubiquity\_auth\_token)
   3. **Auth0** (AUDIENCE, ISSUER, CLIENT\_ID\_SPA, and CLIENT\_ID\_NATIVE) values. 
   4. **Chainalysis Credentials** (chainalysis-user and chainalysis-token) **OPTIONAL** 
   5. **ERS public key** (ers\_public\_key) from Step 2 above.
3. The **infrastructure admin** needs to update the secret contents in AWS Secrets Manager by running the following command:

```shell
make populate-secrets-wallet
```

> 📘 Note:
>
> The **infrastructure and policy nodes admins** need to perform different commands based on what they manage.

4. The **policy node0 admin** needs to update the secret contents in AWS Secrets Manager by running the following command:

```shell
make populate-secrets-policy-node0
```

5. The **policy node1 admin** needs to update the secret contents in AWS Secrets Manager by running the following command:

```shell
make populate-secrets-policy-node1
```

6. The **policy node2 admin** needs to update the secret contents in AWS Secrets Manager by running the following command:

```shell
make populate-secrets-policy-node2
```

<br />

## Step 14: Deploy wallet and MPA nodes

 After populating the wallet environment secrets in the secrets manager, you will deploy the wallet application. This application consists of microservices deployed on AWS Elastic Container Service (ECS). These microservices include:

* **Wallet**: The service container for the wallet itself. After this deployment, the service will be defined, but not started.
* **NATS**: The container for the messaging broker. This is the message broker used for messaging between service containers in the application

The **infrastructure admin** needs to perform the following commands:

1. To deploy the wallet application containers:

```shell
make deploy-wallet
```

2. After the wallet is deployed, you need to deploy the policy nodes and nitro enclave to communicate securely. To do that, use the following command:

```shell
make deploy-nitro-nodes
```

3. Finally, once all of the supporting infrastructure and secret values are in place, we are ready to start the wallet application! To do so, issue one final make command:

```shell
make start-wallet
```

> 🚧 Warning:
>
> 1. Once you finish this step, the URL target should never change, or the wallet will miss events. Changing the URL is not supported without manual intervention by Blockdaemon, which will involve at least a few minutes of downtime. This means you should be very careful to set up the DNS in a manner that is not expected to change in the future.
> 2. The `runtime_resource_identifier` database table should never be disturbed, or events may be missed, initialization may occur redundantly and incur additional Ubiquity fees, etc.

## Step 15: Populate Users and Policies

After the wallet container is deployed and healthy, we can populate the users and policies for the wallet using the `bootstrap.yaml` downloaded in step 8c. The administrative policies in this file are the recommended settings for new customers, but they can be modified to suite your organizations needs. We recommend using the default policy settings for your initial testnet install, then modify as needed after usage prior to installing mainnet. If you have questions regarding policy configuration, please reach out to Blockdaemon Customer Success Manager. 

The **infrastructure admin** needs to populate your wallet users and policies with the following command:

```shell
make bootstrap-policies-and-users
```

## Step 16: Backup the wallet's master private key

Upon first logging in and pairing your account with the Institutional Vault Approver App, approve backing up the wallet’s master private key from the Approver App. The **infrastructrue admin** needs to ensure this backup is stored separately from the wallet system for use in recovery during a disaster.

Refer to the backup and process here: [Back Up Master Key](https://wallet.docs.blockdaemon.com/docs/back-up-master-key)

<Support />