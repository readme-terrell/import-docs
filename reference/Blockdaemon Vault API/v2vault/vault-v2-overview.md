---
title: Vault V2 Overview
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Vault V2 endpoints allow users to get a list of the vaults with pagination.

# Vault V2 Attributes

| Attribute   | Type   | Description                                                                |
| :---------- | :----- | :------------------------------------------------------------------------- |
| Addresses   | Array  | This array contains information about addresses associated with the vault. |
| Address     | String | This field represents the address associated with the vault.               |
| AssetSymbol | String | This field represents the symbol of the asset associated with the address. |
| VaultID     | String | This field represents the ID of the vault.                                 |

# Endpoints

Below is the available endpoint list for Vault V2:

| Endpoint                                                                                    |
| :------------------------------------------------------------------------------------------ |
| [Get All Vaults](https://wallet.docs.blockdaemon.com/reference/listvaults) - GET /v2/vaults |

# Sample Object

The example object returned by the `Get a List of Users` endpoint is shown below.

```json
[
  {
    "Addresses": [
      {
        "Address": "string",
        "AssetSymbol": "string"
      }
    ],
    "VaultID": "string"
  }
]
```
