---
title: Create, Sign and Broadcast Transactions
excerpt: 🌨️ Find out how to do a transaction with Cold Wallet.
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

A cold (offline) wallet must go through signing and broadcasting transactions. This security process is meant to make transactions more secure and controlled. It starts by creating a transaction through the hot (online) wallet and then digitally signing it using a secure offline key. After that, the signed transaction is sent to the hot (online) wallet for verification and recording. This method focuses on security by keeping important keys offline, reducing the risk of unauthorized transactions, and ensuring compliance with rules.

> 📘 Note:
>
> Remember that Hot (online) wallet and Cold (offline) wallet are separate entities.

## Transacting with a Cold Wallet

> 📘 Note:
>
> The cold wallet is only limited to approving one asset per network. For example, If you have an account containing ETH and USDC, you can only send either ETH or USDC simultaneously within a batch of transactions. You cannot send both in a batch of transactions. If this is a concern, we recommend having assets in the same network to a different account. For example, you can have a dedicated account that holds USDC and another dedicated account for ETH.

Follow the steps below to create a transaction with the Cold wallet:

1. To create a transaction in a Cold wallet, ensure you have paired the hot and cold wallet. If not, follow the steps [here](https://wallet.docs.blockdaemon.com/docs/how-to-pair-offline-online-accounts-in-blockdaemon-institutional-wallet) to pair both wallets.
2. Navigate to the hot wallet, and click the **Accounts** tab.

<Image align="center" src="https://files.readme.io/f2bcda3-ceedaeb0-c4af-446a-ab98-809f8fc634bc.png" />

3. Click the **New Account** button.

<Image align="center" src="https://files.readme.io/54f1b22-7cec8f21-8a18-4d68-ac02-c85df32d3e55.png" />

4. Enter the **account name** and enable the **Cold Storage** feature.

<Image align="center" src="https://files.readme.io/af0c0a8-20582c06-3319-4a28-80d8-41823579cc89.png" />

5. Click the newly created cold wallet account.
6. Click the **Add Asset** button and select the asset you want to add to the account.

<Image align="center" src="https://files.readme.io/b184243-ef3093f6-2fea-48dc-94a4-e419a7ce9c88.png" />

7. Click the **Transfer Funds** button, and transfer some funds from another account to the cold wallet account.

<Image align="center" src="https://files.readme.io/add27d2-eb935e8a-884f-42f3-a6c2-193ce64290c0.png" />

8. Approve the transactions using your Institutional Vault approver app.

> 📘 Note:
>
> Due to the nature of the Solana network, cold transactions need to be approved within \~67s, or there is a high risk of failure. Blockdaemon is working on a potential enhancement to improve this network limitation.

9. After that, follow the same steps as above and transfer some funds from a cold wallet account to a hot wallet account.

<Image align="center" src="https://files.readme.io/23dfefd-b584b53d-8ac8-435f-bc9b-99856d8fc55f.png" />

10. Approve the transactions using your Institutional Vault approver app.
11. Click the **Transactions** tab, and select the **Cold Signing** tab.

<Image align="center" src="https://files.readme.io/bc68128-7ab64bf8-2d73-487c-bc58-fc69cca8e398.png" />

12. Click the **Export Batch** button.
13. Navigate to your Cold wallet app.
14. Click the **Transactions** tab, and click the **Import** button.

<Image align="center" src="https://files.readme.io/7a15e04-d3494682-35f8-4748-a375-bd1b7ce91e14.png" />

15. Upload the transaction batch **JSON** file that you have downloaded from the Hot Wallet app.

<Image align="center" src="https://files.readme.io/13dbd93-d775f12e-fb2c-41ae-b3c5-5c18d5ef5194.png" />

16. After that, click the **Sign** button and click **Sign** to confirm the signing operation.

<Image align="center" src="https://files.readme.io/45a3fe0-ce9e8ecd-d5a6-478e-918d-6252b01bba0c.png" />

<Image align="center" src="https://files.readme.io/5ad8b4f-bdf990a2-e7e8-48f4-8f7a-a4649f04039a.png" />

17. Click the **Export** button.

<Image align="center" src="https://files.readme.io/c0d0d3c-35d463c2-e421-4eb9-a482-0ba4bf10928c.png" />

18. Navigate back to your hot wallet app.
19. Under the **Cold Signing** tab, click the **Accept Batch**.

<Image align="center" src="https://files.readme.io/9bfca41-b8b27fb7-6c90-4314-8045-522bbcaa2951.png" />

20. Upload the file you downloaded from the Cold wallet app and click **Accept Batch**.

<Image align="center" src="https://files.readme.io/ddde9ad-75e4b3d9-bc83-47e0-8ed2-8bf199730221.png" />

21. Click the **History** to see the transaction details. The transaction status should be changed to **broadcasting** > **completed**.

<Image align="center" src="https://files.readme.io/23f5739-624c5173-cfad-44f7-b367-cd46dd046e2d.png" />

<Support />
