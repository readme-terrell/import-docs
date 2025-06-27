---
title: How to export logs for troubleshooting
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
To assist Blockdaemon in troubleshooting issues with your Azure wallet, perform the following steps below:

1. Navigate to the Azure Cloud Shell within your Azure Portal service page.
2. Switch to the `clouddrive` directory:
   1. Enter `cd clouddrive`
3. Set the environment:
   1. For testnet: export `CUSTOMER_MPA_ENVIRONMENT=testnet`
   2. For mainnet: enter `CUSTOMER_MPA_ENVIRONMENT=mainnet`
4. Switch to the appropriate network:
   1. For testnet: `make switch-to-testnet`
   2. For mainnet: `make switch-to-mainnet`
5. Initialize plugins:
   1. Enter `make init-plugins`
6. Generate the SAS URL:
   1. Enter `make generate-sas-url`
7. You will see the Blob Service SAS URL generated. Please provide this to Blockdaemon contact.

> 📘 Note:
>
> The Blob Service SAS URL is only valid for 6 hours.

<Support />
