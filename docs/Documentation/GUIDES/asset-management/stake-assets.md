---
title: Stake Assets
excerpt: 🪙Find out how to stake assets
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Overview

The stake assets feature in the Institutional Vault application allows users to participate in staking activities with their digital assets. Staking refers to actively participating in validating and confirming transactions on a blockchain network. By staking their assets, users contribute to the network's security and consensus mechanisms while earning rewards.

> 📘 Note:
>
> * Contact **Enterprise Customer Manager** to enable the staking feature in your wallet.
> * This feature currently support **ETH** token.
> * The transaction fees for all token transactions in the Institutional Vault are covered by ETH. Ensure you have at least **32 ETH** before performing a staking transaction.

## How to Stake Assets

To stake an asset in your Institutional Vault, follow the steps below:

> 📘 Note:
>
> **Stake feature is account level only** which means, you can only use the staking feature with the specific account where it's enabled. But within that account, you're free to use different wallets for staking your assets.

1. Click the **Accounts** button from the main navigation menu.

<Image align="center" src="https://files.readme.io/e645fc3-b4afe3b-small-Group_14_38.png" />

2. Select the **account** you want to stake.
3. Select the **Asset** you want to stake and click the **overflow** button.

<Image align="center" src="https://files.readme.io/c613121-Group_18_95.png" />

4. Click the **Stake Asset** button.

<Image align="center" src="https://files.readme.io/ea0fb62-Group_18_96.png" />

5. Specify all the required fields.

![](https://files.readme.io/19060ca-Group_18_62.png)

| Field         | Description                                                                                                                                                                                                                   |
| :------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Asset         | This field refers to the specific digital asset that the user wants to stake. It could be a cryptocurrency token that is supported by the Institutional Vault.                                                                |
| From Wallet   | This field indicates the wallet the user wants to stake the assets from. The user may have multiple wallets within their Institutional Vault's account, so they can select the appropriate one for staking.                   |
| Withdraw To   | This field allows the user to specify the destination wallet or address where they want to receive the staking rewards or any other withdrawals related to the staked assets.                                                 |
| Fee Recipient | The fee recipient field lets the user define the address or wallet that will receive these transaction fees.                                                                                                                  |
| Crypto Amount | This field is used to enter the quantity or amount of the asset that the user wants to stake. It represents the number of tokens or units of the selected asset involved in the staking process.                              |
| Fee Rate      | The fee rate field allows the user to specify the rate or percentage of the staking rewards that the Institutional Vault or the underlying blockchain network will charge as a fee.                                           |
| Referenced    | The referenced field is optional, enabling users to include relevant references or notes related to the staking transaction. It can be used for personal record-keeping or to provide additional information about the stake. |

6. Click the **Stake** button.

![](https://files.readme.io/ee1c334-Group_18_63.png)

7. Confirm the operation on your **Institutional Vault Approver** application.
8. When an operation has been confirmed, it is evaluated for approval requirements. The relevant users are notified through the Institutional Vault Approver application if approval is needed. 

<Image align="center" src="https://files.readme.io/8fa7a3c-ezgif.com-crop_10.gif" />

9. The staking is performed when the operation has cleared approval and the actual fee is calculated.
10. The transfer amount and fee are subtracted from the source account.
11. Go to the **Transaction History** menu. The operation to stake an asset is shown in the table with the pending confirmation status.

<Image align="center" src="https://files.readme.io/b4128d1-b43c64c-aa8f905-small-Group_14_33_1.png" />

<Image align="center" src="https://files.readme.io/a1989ea-Group_17_40.png" />

12. The stake is signed and pushed to the blockchain. 

> 📘 Note:
>
> The staking status in the Transaction History changes to broadcasting, confirming, and completed.

## Earning Rewards

After staking your assets, you have the opportunity to earn rewards. The rewards are earned by the validator and will be regularly sent back to the source account, which is the account that performed the staking. This ensures that the rewards are returned to the user who contributed the assets for staking. To check the rewards:

> 📘 Note:
>
> As a rule of thumb, if the validator becomes active on day X, it will start earning rewards per epoch (every 6.4 mins). The first rewards would appear for that validator on X+1 unless the staking happens right before the midnight.

1. Go to the **Account** that has been used to stake the ETH token.

<Image align="center" src="https://files.readme.io/daf5680-b4afe3b-small-Group_14_38.png" />

2. Click **Staked Assets**.

<Image align="center" src="https://files.readme.io/1dbd4cf-Group_18_97.png" />

3. You can see the Rewards and the current balance of your staked assets reflected in your account.

<Image align="center" src="https://files.readme.io/b0c33c9-Group_18_100.png" />

<Support />
