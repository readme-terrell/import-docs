---
title: Azure Deployment Process
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
<Image align="center" src="https://files.readme.io/c4268d5-Asset_64300x_1.png" />

The Azure deployment of the Self-installed Institutional Vault involves distinct, secure setup steps that leverage separate Azure Key Wallet instances to guard each of the MPA Nodes. This ensures that no single party has access to multiple master key shards.

# Prerequisite

1. To execute the installation, the admin must have basic knowledge of Azure deployment and familiarity with the command line interface.

> 📘 Note:
>
> It may be necessary to increase the usage quota for the `Standard_DC4as_v5` instance type. The guide to increase the usage quota can be found [here](https://learn.microsoft.com/en-us/azure/quotas/per-vm-quota-requests#request-an-increase-for-adjustable-quotas).

2. The admin must have Kubernetes knowledge.
3. The admin must have Owner permissions to install to the Azure Subscription.
4. Perform auth0 configuration. For details, please refer [here](https://vault.docs.blockdaemon.com/docs/configuring-auth0).

## Azure Wallet Architecture

Understanding the Azure wallet architecture depicted in the image below is important before you deploy.

<Image align="center" src="https://files.readme.io/0df5180-flow_69300x.png" />

# Step 1: Send Deployment Request Form

1. To obtain the request form, [Contact Us](emailto:sales@blockdaemon.com) or go to this [page](https://www.blockdaemon.com/get-started/iwtoken#cta) and enter your contact details.
2. Our sales team will send you a deployment request form which includes more detailed information including but not limited to:
   1. A new Azure subscription and Region will be used for the installation.
   2. A DNS zone will be used for your hosted wallet. Example: [https://wallet.](https://wallet.)\<companydomain.com>. The wallet installer will create networking services within this zone. Furthermore, the authentication service will call back to this domain endpoint.
   3. At least two administrator names and emails.
   4. An Auth0 Tenant.
   5. A token rates service
   6. Emergency Recovery Secret (ERS) Public Key.
3. To initiate the process, please complete the form and send it back to us.

# Step 2: Configure Identity Provider

The wallet relies on an external Open ID Connect (OIDC) authentication service to verify user identities and provide secure access tokens to the wallet. For details about the auth0 installation, please refer to [here](https://vault.docs.blockdaemon.com/docs/configuring-auth0).

# Step 3: Delegate New Wallet DNS Zone

1. Create a management resource group and DNS Zone. If you don't know how to create, please follow the steps [here](https://learn.microsoft.com/en-us/azure/dns/dns-getstarted-portal).
2. The network administrator sets the DNS Nameserver zone delegations from the company's authoritative zone and adds them to the site in the company's registrar.

# Step 4: Generate Emergency Recovery Secret

In the event of a disaster, you must restore your master wallet's private key from the backup. This backup is encrypted with the Emergency Recovery Secret (ERS) key pair. You need to generate this Emergency Recovery Secret (ERS) key pair before installing and backing up the master private key.

This ERS private key must be generated and stored securely. Follow your company policy when performing the key ceremonies.

For the mainnet or production environment, fully understand the importance of your key ceremony. We suggest starting with the following [document](https://d1c2gz5q23tkk0.cloudfront.net/assets/uploads/2956620/asset/CVA_Trusted_Key_Ceremony_Guidelines.pdf?1594131972) from the Crypto Valley association.

The base64 encoded output of the public key must be supplied during the wallet application installation.

# Step 5: Installation of Infrastructure and Applications

## Step 5a: Prepare the Azure Cloud Shell Environment

1. Navigate to your Azure portal and open the cloud shell. It is the `>_` symbol near the search bar.
2. If multiple subscriptions exist within the tenant, ensure the desired subscription context is set within the azure prompt:

```shell
az account list
az account set -name <name>
```

3. The installation requires more space than what is available by default within the cloud shell. Increase the cloud shell disk partition space by running the following:

```shell
SIZE_IN_GB=50
STORAGE_ACCOUNT=$(az storage account list --query '[?tags."ms-resource-usage"==`azure-cloud-shell`] | [0].name' -o tsv)
CS_SHARE=$(az storage share list --account-name $STORAGE_ACCOUNT --query '[?starts_with(name, `cs`)] | [0].name' -o tsv)
az storage share update --account-name $STORAGE_ACCOUNT -n $CS_SHARE --quota $SIZE_IN_GB
```

4. Blockdaemon generates pre-signed URLs for both the common and package bundles. Download and extract these bundles by using the commands below. This will place a Makefile in the directory of the cloud shell.

```shell
cd clouddrive
wget -O common.tar "<some url>"
tar xvf common.tar -C .
wget -O package.tar "<some url>"
tar xvf package.tar -C .
```

5. Next, to set up some paths and python updates required for the installation, run the following command:

```shell
make prep-shell
```

> 📘 Note:
>
> Due to the nature of nested shells, there may be an error at this stage. Run `source ~/.bashrc` and the `make prep-shell` again.

## Step 5b: Deploy the Baseline Infrastructure

1. Set the installation process for either Testnet or Mainnet blockchains by executing one of the following:

```shell
make switch-to-testnet
make switch-to-mainnet
```

2. If this is the first wallet installation within the Azure subscription, execute the following command to create an Azure storage account that will store the Terraform state for Mainnet and Testnet deployments. Note, if this has already been run for a previous installation, skip this step.

```shell
make deploy-state-storage
```

3. Next, proceed to deploy the bootstrap stack by executing the following command:

```shell
make deploy-bootstrap
```

4. Once the container registry is created above, push the Wallet software container images to it:

```shell
make push-images
```

## Step 5c: Populate Secrets

1. Fill in the secrets file `customer-secrets.yml` with your **Blockdaemon Workspace name**, **Blockdaemon API key**,  and **auth0 values**. Include the rates **service access key** and your **ERS public key** from the process outlined above.
2. Execute the following command to create the Azure Key Wallet secrets from the updated yml file:

```shell
make populate-secrets
```

## Step 5d: Deploy Wallet and MPA Node Applications

1. Finally deploy and start the wallet application by running the following command:

```shell
make deploy-wallet
```

# Step 6: Backup the Wallet's Master Private Key

Upon first logging in and pairing your account with the Institutional Vault Approver App, approve backing up the wallet’s master private key from the Approver App. Ensure this backup is stored separately from the wallet system for use in recovery during a disaster.

> 📘 Note:
>
> Refer to the backup and process here: [Back Up Master Key](https://vault.docs.blockdaemon.com/docs/back-up-master-key).

<Support />
