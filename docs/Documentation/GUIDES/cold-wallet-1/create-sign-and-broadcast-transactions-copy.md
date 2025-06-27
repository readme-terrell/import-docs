---
title: Create, Sign and Broadcast Transactions (Updated)
excerpt: 🌨️ Find out how to do a transaction with Cold Wallet.
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Overview

A cold (offline) wallet follows a secure process for signing and sending transactions. A transaction is first created using the hot (online) wallet and then signed offline using a secure key. The signed transaction is sent back to the hot wallet for verification and broadcast. This keeps sensitive keys offline, lowering the risk of unauthorized access and helping meet security rules.

In this example, the cold wallet uses two separate MPC nodes, each providing part of the signature. These nodes are stored in two different air-gapped cold wallets for extra protection. The hot wallet, which is accessible on-site, works with these cold wallets. Even if one cold wallet device is compromised, a transaction still can’t be fully signed.

<Image align="center" src="https://files.readme.io/40d1e64d146cd379c025843da60a2e06f84a7d4950d3090d39eec371bc87b31e-Asset_33300x.png" />

> 📘 Note:
>
> Remember that Hot (online) wallets and Cold (offline) wallets are separate entities.

## Transacting with a Cold Wallet

<Image align="center" src="https://files.readme.io/dcf1bdc84de1310a0418dc80087c89d2c7ecdd3a28bba9d183f70f681b579b7f-Asset_3300x.png" />

Follow the steps below to create a transaction with the Cold wallet:

> 📘 Note:
>
> To create a transaction in a Cold wallet, ensure you have paired the hot and cold wallet. If not, follow the steps [here](https://wallet.docs.blockdaemon.com/docs/how-to-pair-offline-online-accounts-in-blockdaemon-institutional-wallet) to pair both wallets.

### Step 1: Create a Cold Wallet Account

1. Navigate to the Accounts page, and click New Account.
2. Enter the Account Name and click the Cold Account button switch.
3. Click Create.

### Step 2: Add an Asset to the Cold Wallet Account

1. Click the newly created cold wallet account.
2. Click Add Asset.
3. Select the Asset you want to add and click Add Crypto.

### Step 3: Create Cold Wallet Transaction

1. Click the Transfer Funds button.
2. Click the Cold Signing tab.
3. Select the asset you want to transfer and Select the Cold wallet account in the Source Account section.
4. Click Transfer.
5. Click the Export Batch button to download the Transaction batch file.
6. Save the file on a trusted USB stick.

> 📘 Note:
>
> It is possible to export multiple transactions at once.

7. The status of the transactions changed to Pending Signature.
8. Back to the air-gapped cold wallets to sign the transaction.

> 📘 Note:
>
> Signing transactions for cold wallets does not have to be performed simultaneously in both cold wallets.

9. Plug the USB into the cold wallet device.
10. Navigate to the Transactions page.
11. Click Import.
12. Select the batch file.
13. Click Upload.
14. Click Sign and Sign again to sign the transaction.
15. Once signed, click Export to download the partial signature.
16. Repeat the steps above for the second cold wallet device.
17. Save the partial signature files on a trusted USB stick.
18. Back to the hot wallet to upload the partial signature files.
19. On the cold signing tab on the Transactions page click the Accept Batch button.
20. Upload both partial signature files.

> 📘 Note:
>
> There is no order to upload which files first from the cold wallets.

21. When you navigate back to the Transactions History tab, the cold wallet transaction status changes from Pending Signature to Broadcasting to Completed.

<Support />
