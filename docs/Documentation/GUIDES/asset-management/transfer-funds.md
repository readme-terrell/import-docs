---
title: Transfer Funds
excerpt: 📤Find out how to transfer funds to another accounts
deprecated: false
hidden: false
metadata:
  title: Transfer Funds
  description: >-
    Effortlessly transfer funds with Blockdaemon Wallet. Explore the steps to
    securely send and manage digital asset transactions with ease.
  image: https://files.readme.io/c77ce77-image_3.png
  robots: index
next:
  description: ''
---
# Overview

Within the wallet, you have the ability to perform internal transfers between different accounts and send funds to addresses external to the wallet. These internal transfers allow you to distribute funds effectively among accounts that need manual approvals and those designed to serve customers swiftly through automated approval processes.

> 📘 Note:
>
> 1. The transaction fees for all token transactions in the Institutional Vault are covered by the base token of that account (eg. ETH for ERC-20s). Ensure you have sufficient tokens before performing a transaction.
> 2. Once a transaction is broadcasted, the wallet will keep updating its status until it's included into a block, and eventually confirmed.

# Wallet Types

The Institutional Vault supports both internal and external wallets. An **internal wallet** is utilized when both addresses involved in a transaction are in the same wallet. On the other hand, an **external wallet** is utilized when incoming or outgoing transactions involve an external wallet/address. In Institutional Vault, all internal and external transfers incur the same transaction fee. The differences between Internal and External wallets are listed below.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Type
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Internal Wallet
      </td>

      <td>
        \- An internal wallet ensures the same instance controls account transfers. It is also used when the sender and receiver addresses are within the same wallet.  

        * In Institutional Vault, internal and external wallets can apply different policies depending on the nature of the transaction.
      </td>
    </tr>

    <tr>
      <td>
        External Wallet
      </td>

      <td>
        \- An external wallet is used when an external wallet/address is involved in incoming or outgoing transactions.  

        * In Institutional Vault, it will be rejected if you enter an internal address for an external transaction. This is based on the idea that the approver should know that this is an internal transfer, not an external one, so they can decide to approve or reject the transaction based on that factor.
      </td>
    </tr>
  </tbody>
</Table>

# How to Transfer Funds

To do an internal transfer in your Institutional Vault, follow the steps below:

1. Click the **Transfer Funds** button from the main navigation menu.

<Image align="center" src="https://files.readme.io/755f72f4ec6e5860c45973fa5408a2adb4c98d17c0e1986dd6cd5502fefc45b1-Group_18_-_2024-09-12T145128.869.png" />

2. Specify all the fields.

| Field        | Description                                                                                                                                                                                                                  |
| :----------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Asset        | Select the asset you want to transfer.                                                                                                                                                                                       |
| Source       | Select the source account.                                                                                                                                                                                                   |
| Destination  | Select the destination account. You can choose between Internal Account or External Address.                                                                                                                                 |
| Cypto Amount | Specify the amount of asset you want to transfer. You can choose between Net or Gross transfer.                                                                                                                              |
| Fee Rate     | Specify the fee priority to determine the fee rate.                                                                                                                                                                          |
| Reference    | The referenced field is optional, enabling users to include relevant references or notes related to the staking transaction. It can be used for personal record-keeping or to provide additional information about the stake |

<Image align="center" src="https://files.readme.io/e38a177a9617a33d598aa143c4b1243748d4ebcd5424a2f967ea0f4cf7a39081-Group_18_-_2024-09-12T152504.203.png" />

3. Click **Transfer** to submit the transfer operation.

<Image align="center" src="https://files.readme.io/0748f5fc73a4b69e338fc419e5703881a8f9b9c9f259c1d6df5899a6bf053da4-Group_18_-_2024-09-12T152451.566.png" />

4. The transfer amount and fee are subtracted from the source account. 
5. Go to the **Transaction History** menu. The operation to transfer funds is shown in the table with the Pending confirmation status.
6. Confirm the operation on your **Institutional Vault Approver** application.

> 📘 Note:
>
> Confirmation is required from the originator of the transaction (or a delegate if using an API key). Approvals are performed according to what has been set in the policy. For details of policies, please refer [here](https://vault.docs.blockdaemon.com/docs/all-about-policies).

7. When an operation has been confirmed, it is evaluated for approval requirements. The relevant users are notified through the Institutional Vault Approver application if approval is needed. 
8. The transaction is performed when the operation has cleared approval, and the actual fee is calculated. 

> 📘 Note:
>
> At this point, fee rates are recalculated to match the current market. The fee input provided by the user serves as the upper limit for the fee rate that could potentially be requested for payment.

9. The transaction is signed and pushed to the blockchain. The transaction status in the Transaction History changes to **broadcasting** > **confirming** > **completed**.
10. The transferred amount is added to the destination account after completing the transaction.

<Support />
