---
title: Audit Overview
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
The Institutional Vault's audit endpoints offer the capability to obtain audit logs in CSV format for a specified date range.

> 📘 Note:
>
> The response from this endpoint will be a downloadable zip file containing the requested audit logs in a CSV file.

# Endpoint

Below is the available endpoint list for Audit:

| Endpoint                                                                                              |
| :---------------------------------------------------------------------------------------------------- |
| [Export Audit Logs](https://vault.docs.blockdaemon.com/reference/exportaudit) - GET /audit/export.zip |

# Sample Audit Logs

The example object returned by the `Export Audit Logs`  endpoint is in zip format and contains a CSV file, as shown below.

<Image align="center" src="https://files.readme.io/01df0cb-Group_18_-_2023-11-08T102605.330.png" />

The file contains the following parameters:

### Field Parameters

| Parameter     | Description                                                                                                                                                                                         |
| :------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| UserID        | The unique identifier or email associated with the user who initiated the action or operation in the wallet.                                                                                        |
| ClientIP      | The IP address of the user or device that was used to perform the actions or operations.                                                                                                            |
| EventType     | The type of event or action that occurred. For a more detailed list of event types, please see [here](https://vault.docs.blockdaemon.com/reference/audit-overview#event-types).                     |
| EventState    | The state or outcome of the actions or operations performed. For a more detailed list of event states, please see [here](https://vault.docs.blockdaemon.com/reference/audit-overview#event-states). |
| Message       | The additional information or details about the actions or operations.                                                                                                                              |
| CreatedAt     | The timestamp where the actions or operations took place.                                                                                                                                           |
| CorrelationID | The unique identifier correlates different components within the wallet stack used for debugging.                                                                                                   |

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

<Support />
