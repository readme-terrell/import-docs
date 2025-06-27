---
title: Export Audit Logs
excerpt: ⬇️Find out how to export your wallet Audit logs!
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

Audit Logs serve as a detailed and chronological history of changes, actions, transactions, and operations performed by users and system users within the wallet. Audit Logs help to provide transparency, accountability, security, and troubleshooting capabilities.

# Export Audit Logs

To export audit logs, follow the steps below:

1. Click **Settings** on the main navigation menu.

<Image align="center" src="https://files.readme.io/278c1c1fc6bf5c349e4fc7573bbf5f205a13db6b849b159293502c0319203d24-Group_18_-_2024-09-10T140320.704.png" />

2. Select the **Audit Logs** tab.

<Image align="center" src="https://files.readme.io/0dbe2aa658538ffbb8bc3849559b0b9444cc610c987bf9c13289fb79903ed215-Group_18_-_2024-09-12T130558.896.png" />

3. Select the start date and end date range of the audit logs.

<Image align="center" src="https://files.readme.io/fd19e3bb1b5308f1fbc0f635c31976934e9d99666b18bed8a07f32ecc7f99300-Group_18_-_2024-09-12T130635.856.png" />

4. Click the **Export Aduit Logs** button.

<Image align="center" src="https://files.readme.io/e911a2224b5b0aa08deefcd18ad5554aad9d685bee79983cbd33104f453ebf76-Group_18_-_2024-09-12T130711.215.png" />

> 📘 Note:
>
> The maximum date range is three months.

5. Your browser will download the audit logs file in a **.zip** format. The file contains the following parameters:

### Field Parameters

| Parameter     | Description                                                                                                                                                                                       |
| :------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| UserID        | The unique identifier or email associated with the user who initiated the action or operation in the wallet.                                                                                      |
| ClientIP      | The IP address of the user or device that was used to perform the actions or operations.                                                                                                          |
| EventType     | The type of event or action that occurred. For a more detailed list of event types, please see [here](https://wallet.docs.blockdaemon.com/docs/export-audit-logs#event-types).                    |
| EventState    | The state or outcome of the actions or operations performed. For a more detailed list of event states, please see [here](https://vault.docs.blockdaemon.com/docs/export-audit-logs#event-states). |
| Message       | The additional information or details about the actions or operations.                                                                                                                            |
| CreatedAt     | The timestamp where the actions or operations took place.                                                                                                                                         |
| CorrelationID | The unique identifier correlates different components within the wallet stack used for debugging.                                                                                                 |

### Event Types

| Event Type                |
| :------------------------ |
| AddAddress                |
| AddAsset                  |
| AddERC20Asset             |
| AddressGeneration         |
| AddUserToGroup            |
| AssetAdded                |
| Authenticate              |
| CreateVault               |
| ERC20Asset                |
| ExchangeRatesUpdate       |
| ExportTransaction         |
| Freeze                    |
| Group                     |
| RemoveUserFromGroup       |
| SeeNotifications          |
| StakingPolicyUpdate       |
| SystemUser                |
| Transaction               |
| TransactionBalanceChanged |
| TransactionPolicyUpdate   |
| TransferFunds             |
| Unfreeze                  |
| User                      |
| UserActivation            |
| UserDeletion              |
| UserRegistration          |
| UserReset                 |
| VaultCreation             |
| VaultHidden               |

### Event States

| Event State         |
| :------------------ |
| Approved            |
| Confirmed           |
| Created             |
| Deleted             |
| Failed              |
| Initiated           |
| Pending             |
| PendingConfirmation |
| Pulled              |
| Pushed              |
| Rejected            |
| Stabilized          |
| Stabilizing         |
| Success             |
| Unauthorized        |
| Updated             |

# Sample Audit Logs

The audit log will be in zip format and contain a CSV file, as shown below.

<Image align="center" src="https://files.readme.io/9c39c4ac2dd4d9083b7eae5ca5561c817621a13a817057471c0a7e709eb932fd-Group_18_-_2024-09-12T130741.034.png" />

<Support />
