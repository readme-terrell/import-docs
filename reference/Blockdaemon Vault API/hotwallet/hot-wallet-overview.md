---
title: Hot Wallet Overview
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
Hot wallet endpoints enable users to connect their hot and cold wallets. These endpoints facilitate the creation, acceptance, or rejection of transaction batches used for the pairing process. Additionally, the hot wallet allows users to export and import pairing messages to establish the connection between the hot and cold wallets.

# Hot Wallet Attributes

| Attribute                    | Type    | Description                                                                                                                                             |
| :--------------------------- | :------ | :------------------------------------------------------------------------------------------------------------------------------------------------------ |
| IsBatchInProcess             | Boolean | This field indicates whether a batch of transactions is currently in process. If true, it means that there are transactions being processed in a batch. |
| Transactions                 | Array   | This array contains information about individual transactions.                                                                                          |
| Amount                       | String  | This field represents the amount of the transaction.                                                                                                    |
| Asset                        | String  | This field represents the asset involved in the transaction.                                                                                            |
| AssetName                    | String  | This field represents the name of the asset involved in the transaction.                                                                                |
| CreatedAt                    | String  | This field represents the timestamp when the transaction was created.                                                                                   |
| CreatedBy                    | String  | This field represents the entity that created the transaction.                                                                                          |
| Destination                  | Object  | This field contains information about the destination of the transaction.                                                                               |
| Addresses                    | Array   | This field represents the destination addresses involved in the transaction.                                                                            |
| ColdVault                    | Boolean | This field indicates whether the destination is a cold storage vault.                                                                                   |
| VaultID                      | String  | This field represents the ID of the destination vault.                                                                                                  |
| VaultName                    | String  | This field represents the name of the destination vault.                                                                                                |
| ExternalDestinationAddresses | Array   | This field represents external destination addresses involved in the transaction.                                                                       |
| ExternalSourceAddresses      | Array   | This field represents external source addresses involved in the transaction.                                                                            |
| Id                           | String  | This field represents the unique identifier of the transaction.                                                                                         |
| InternalDestination          | Boolean | This field indicates whether the destination of the transaction is internal.                                                                            |
| InternalSource               | Boolean | This field indicates whether the source of the transaction is internal.                                                                                 |
| Source                       | Object  | This field contains information about the source of the transaction.                                                                                    |
| Addresses                    | Array   | This field represents the source addresses involved in the transaction.                                                                                 |
| ColdVault                    | Boolean | This field indicates whether the source is a cold storage vault.                                                                                        |
| VaultID                      | String  | This field represents the ID of the source vault.                                                                                                       |
| VaultName                    | String  | This field represents the name of the source vault.                                                                                                     |
| Status                       | String  | This field represents the status of the transaction.                                                                                                    |
| TransactionType              | String  | This field represents the type of the transaction.                                                                                                      |
| TxHash                       | String  | This field represents the hash of the transaction.                                                                                                      |
| UpdatedAt                    | String  | This field represents the timestamp when the transaction was last updated.                                                                              |
| WithdrawDestination          | Object  | This field contains information about the withdrawal destination of the transaction.                                                                    |
| Addresses                    | Array   | This field represents the withdrawal destination addresses involved in the transaction.                                                                 |
| ColdVault                    | Boolean | This field indicates whether the withdrawal destination is a cold storage vault.                                                                        |
| VaultID                      | String  | This field represents the ID of the withdrawal destination vault.                                                                                       |
| VaultName                    | String  | This field represents the name of the withdrawal destination vault.                                                                                     |

# Endpoints

Below is the available endpoint list for Hot wallet:

| Endpoint                                                                                                                                                |
| :------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Get the Current Batch](https://vault.docs.blockdaemon.com/reference/getcurrentbatch) - GET /hot-wallet/batch                                           |
| [Create a Batch](https://vault.docs.blockdaemon.com/reference/createbatch) - POST /hot-wallet/batch                                                     |
| [Accept a Batch](https://vault.docs.blockdaemon.com/reference/acceptbatch) - POST /hot-wallet/batch/accept                                              |
| [Reject a Batch](https://vault.docs.blockdaemon.com/reference/rejectbatch) - POST /hot-wallet/batch/reject                                              |
| [Export the Hot Pairing Message](https://vault.docs.blockdaemon.com/reference/exporthotpairingmessage) - GET /hot-wallet/export-hot-pairing-message     |
| [Import the Cold Pairing Message](https://vault.docs.blockdaemon.com/reference/importcoldpairingmessage) - POST /hot-wallet/import-cold-pairing-message |
| [List the Master Keys](https://vault.docs.blockdaemon.com/reference/listmasterkeys) - GET /hot-wallet/masterkeys                                        |

# Sample Object

The example object returned by the `Get the Current Batch` endpoint is shown below.

```json
{
  "IsBatchInProcess": true,
  "Transactions": [
    {
      "Amount": "string",
      "Asset": "string",
      "AssetName": "string",
      "CreatedAt": "string",
      "CreatedBy": "string",
      "Destination": {
        "Addresses": [
          "string"
        ],
        "ColdVault": true,
        "VaultID": "string",
        "VaultName": "string"
      },
      "ExternalDestinationAddresses": [
        "string"
      ],
      "ExternalSourceAddresses": [
        "string"
      ],
      "Id": "string",
      "InternalDestination": true,
      "InternalSource": true,
      "Source": {
        "Addresses": [
          "string"
        ],
        "ColdVault": true,
        "VaultID": "string",
        "VaultName": "string"
      },
      "Status": "string",
      "TransactionType": "string",
      "TxHash": "string",
      "UpdatedAt": "string",
      "WithdrawDestination": {
        "Addresses": [
          "string"
        ],
        "ColdVault": true,
        "VaultID": "string",
        "VaultName": "string"
      }
    }
  ]
}
```

<Support />
