---
title: Transactions Overview
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
Transaction Endpoints allow users to initiate and manage transactions on their blockchain nodes and networks. Transaction endpoints in Blockdaemon enable users to transfer cryptocurrencies or other digital assets and execute smart contracts and other blockchain-based transactions.

# Transaction Attributes

| Attribute                          | Type    | Description                                                      |
| :--------------------------------- | :------ | :--------------------------------------------------------------- |
| TotalCount                         | Integer | Total amount of transactions.                                    |
| Transactions                       | Array   | List of the transactions along with the details.                 |
| Amount                             | String  | The amount of assets in the transaction.                         |
| Asset                              | String  | The abbreviation of the asset.                                   |
| AssetName                          | String  | The name of the asset.                                           |
| CreatedAt                          | String  | The creation time of the transaction.                            |
| CreatedBy                          | String  | The one who initiates the transaction.                           |
| Destination                        | Object  | List of the destination addresses of the transactions.           |
| Address                            | Array   | List of the addresses.                                           |
| VaultId                            | String  | The identifier of the vault.                                     |
| VaultName                          | String  | The vault's name.                                                |
| ExternalDestinationAddresses       | Array   | List of external destination addresses.                          |
| ExternalSourceAddress              | Array   | List of external source addresses.                               |
| ExternalWithdrawDestinationAddress | String  | List of external destination addresses.                          |
| Id                                 | String  | The identifier of the address.                                   |
| InternalDestination                | Boolean | Whether or not the transaction uses the internal address.        |
| InternalSource                     | Boolean | Whether or not the transaction uses an internal source address.  |
| Source                             | Array   | List of the source addresses.                                    |
| StakingTransaction                 | Boolean | Whether the transaction includes the staking transaction or not. |
| Status                             | String  | The status of the transaction.                                   |
| TxHash                             | String  | The hash of the transaction.                                     |
| UpdatedAt                          | String  | The last time the transaction was updated.                       |
| WithdrawDestination                | Array   | The withdraw destination addresses.                              |

# Endpoint

| Endpoint                                                                                                                                              |
| :---------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Get All Transactions](https://vault.docs.blockdaemon.com/reference/showtransactions) - GET /transactions                                             |
| [Get the Details of a Specific Asset ](https://vault.docs.blockdaemon.com/reference/gettransferassetdetails)- GET /transactions/assetDetails/\{Asset} |
| [Get the Blockchain Progress](https://vault.docs.blockdaemon.com/reference/getblockchainprogress) - GET /transactions/blockchainProgress/\{Asset}     |
| [Export Multiple Transactions as a CSV File](https://vault.docs.blockdaemon.com/reference/exporttransactions) - GET /transactions/export.csv          |
| [Get the Filter Details](https://vault.docs.blockdaemon.com/reference/getfilterdetails) - GET /transactions/filterDetails                             |
| [Freeze the Wallet](https://vault.docs.blockdaemon.com/reference/freeze) - POST /transactions/freeze                                                  |
| [Get the Recurring Transactions](https://vault.docs.blockdaemon.com/reference/getrecurringtransactions) - GET /transactions/recurring                 |
| [Cancel the Recurring Transaction](https://vault.docs.blockdaemon.com/reference/cancelrecurringtransaction) - POST /transactions/recurring/\{id}      |
| [Transfer the Funds](https://vault.docs.blockdaemon.com/reference/transferfunds) - POST /transactions/transfer                                        |
| [Get the Transfer Details](https://vault.docs.blockdaemon.com/reference/gettransferdetails) - GET /transactions/transferDetails                       |
| [UnFreeze the Wallet](https://vault.docs.blockdaemon.com/reference/unfreeze) - POST /transactions/unfreeze                                            |
| [Get the Transactions Vault](https://vault.docs.blockdaemon.com/reference/showtransactionsforvault) - GET /transactions/vault/\{vaultId}              |
| [Get a Transaction](https://vault.docs.blockdaemon.com/reference/gettransaction) - GET /transactions/\{Id}                                            |

# Sample Object

The example object returned by the `Get a List of Transactions` endpoint is shown below.

```
{
  "TotalCount": 0,
  "Transactions": [
    {
      "Amount": "string",
      "Approvers": [
        "string"
      ],
      "Asset": "string",
      "AssetName": "string",
      "BlockExplorerUrl": "string",
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
      "ExternalWithdrawDestinationAddress": "string",
      "FeeRecipient": "string",
      "Id": "string",
      "InternalDestination": true,
      "InternalSource": true,
      "Reference": "string",
      "Source": {
        "Addresses": [
          "string"
        ],
        "ColdVault": true,
        "VaultID": "string",
        "VaultName": "string"
      },
      "Status": "Approved",
      "TransactionType": "Reward",
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
