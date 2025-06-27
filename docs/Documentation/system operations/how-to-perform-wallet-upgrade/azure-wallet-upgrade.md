---
title: Azure Wallet Upgrade
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
> 📘 Note:
>
> The upgrade process may take up to an hour.

To upgrade your Azure Wallet, follow the steps below:

1. Navigate to your Azure portal and open the cloud shell. It is the >\_ symbol near the search bar.
2. Blockdaemon generates pre-signed URLs for both the common and package bundles. Download and extract these updated bundles by using the commands below. This will place a Makefile in the directory of the cloud shell.

```
cd clouddrive
wget "<some package url>" -O - | tar -xz
wget "<some common url>" -O - | tar -x
```

3. Set the installation process for either Testnet or Mainnet wallet environment by executing one of the following:

```
CUSTOMER_MPA_ENVIRONMENT=testnet make switch-to-testnet
# or
CUSTOMER_MPA_ENVIRONMENT=mainnet make switch-to-mainnet
```

4. Re-initialize the Terraform state, bootstrap and MPA plugins:

```
make init-plugins
```

5. Finally, run the following command to upgrade. This will perform any infrastructure updates, push the new container images to the registry, and restart the wallet services to instantiate the new version. Terraform will highlight the changes in different colors to show what is being removed (red), changed (orange), or added (green). Answer "yes" with these prompts.

```
make push-images
make deploy-wallet
```

<Support />
