---
title: Cold Wallet Overview
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Cold Wallet endpoints allow users to interact with the cold wallet, a type of cryptocurrency wallet not connected to the internet, enhancing its security.

# Cold Wallet Attributes

| Attribute     | Type    | Description                                                                                                                                          |
| :------------ | :------ | :--------------------------------------------------------------------------------------------------------------------------------------------------- |
| amount        | String  | Represents the quantity or value associated with a transaction or operation.                                                                         |
| asset         | String  | Refers to the specific asset or currency involved in a transaction.                                                                                  |
| batch\_id     | String  | Identifies a batch or group to which the operation or transaction belongs.                                                                           |
| created\_at   | String  | Represents the timestamp indicating when the entity was created.                                                                                     |
| dest\_type    | String  | Specifies the type or category of the destination.                                                                                                   |
| destination   | String  | Specifies the target or receiving entity involved in a transaction                                                                                   |
| id            | String  | Serves as a unique identifier for the entity.                                                                                                        |
| source        | String  | Indicates the source or origin of the transaction.                                                                                                   |
| test\_network | Boolean | A boolean flag that, when true, indicates that the transaction or operation is conducted on a test network rather than a production or main network. |
| type          | String  | Specifies the type or category of the transaction or operation.                                                                                      |

# Endpoints

Below is the available endpoint list for Cold Wallet:

| Endpoint                                                                                                                                                  |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Get Cold Wallet Config](https://wallet.docs.blockdaemon.com/reference/coldwalletconfig) - GET /api/v1/config                                             |
| [Generate Cold Pairing Messages](https://wallet.docs.blockdaemon.com/reference/generatecoldpairingmessages) - POST /api/v1/generate-cold-pairing-messages |
| [Transaction Batch Parse](https://wallet.docs.blockdaemon.com/reference/transactionbatchparse) - POST /api/v1/transaction-batch/parse                     |
| [Sign Transaction Batch](https://wallet.docs.blockdaemon.com/reference/transactionbatchsign) - POST /api/v1/transaction-batch/sign                        |

# Sample Object

The example object returned by the `Transaction Batch Parse` endpoint is shown below.

```json
{
  "amount": "string",
  "asset": "string",
  "batch_id": "string",
  "created_at": "2023-11-21T04:42:56.705Z",
  "dest_type": "string",
  "destination": "string",
  "id": "string",
  "source": "string",
  "test_network": true,
  "type": "string"
}
```
