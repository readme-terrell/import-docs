---
title: Vault Overview
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: Vault Overview
  description: Test and get yourself familiar with Vault Endpoints.
  image: https://files.readme.io/1368981-image_3.png
  robots: index
next:
  description: ''
---
Vault endpoints allow users to access a secure storage location for digital assets, such as cryptocurrencies or tokens. It provides advanced security measures to ensure only authorized parties can access the assets and includes features for managing and monitoring asset transactions.

# Vault Attributes

| Attribute        | Type    | Description                                                      |
| :--------------- | :------ | :--------------------------------------------------------------- |
| HiddenVaultCount | Integer | Total number of hidden vaults.                                   |
| TotalCount       | Integer | Total number of vaults.                                          |
| Vaults           | Array   | List of available vaults.                                        |
| Assets           | Array   | List of available assets within a vault.                         |
| Amount           | String  | The total amount of the assets.                                  |
| Asset            | String  | The abbreviation of the asset.                                   |
| Name             | String  | The full name of the asset.                                      |
| USDAmount        | String  | The total amount of the assets in dollars.                       |
| Balance          | Object  | This object contains information about the balance of the vault. |
| AvailableUSD     | String  | The available balance of the vault in USD.                       |
| OnChainUSD       | String  | The on-chain balance of the vault in USD.                        |
| PendingUSD       | String  | The pending balance of the vault in USD.                         |
| ColdVault        | Boolean | This field indicates whether the vault is a cold storage vault.  |
| CreatedAt        | String  | The creation date of the vault.                                  |
| CreatedBy        | String  | The one who created the vault.                                   |
| Hidden           | Boolean | This field indicates whether the vault is hidden.                |
| ID               | String  | The identifier of the vault.                                     |
| Name             | String  | The vault's name.                                                |
| State            | String  | The state of the vault.                                          |

# Endpoints

Below is the available endpoint list for Vault:

| Endpoint                                                                                                                                      |
| :-------------------------------------------------------------------------------------------------------------------------------------------- |
| [Get a List of Unhidden Vaults and the Count of Multiple Hidden Vaults](https://vault.docs.blockdaemon.com/reference/getvaults) - GET /vaults |
| [Get a List of Assets Not in Vault](https://vault.docs.blockdaemon.com/reference/getallassetsnotinvault) - GET /vaults/assetsNotInVault/\{Id} |
| [Create a New Vault](https://vault.docs.blockdaemon.com/reference/createvault) - POST /vaults/createVault                                     |
| [Search Vaults](https://vault.docs.blockdaemon.com/reference/searchvaults) - GET /vaults/search                                               |
| [Get the Vault Validators](https://vault.docs.blockdaemon.com/reference/getvaultvalidators) - GET /staking/\{id}/validators                   |
| [Get a Vault](https://vault.docs.blockdaemon.com/reference/getvault) - GET /vaults/\{Id}                                                      |
| [Add an Asset to a Vault](https://vault.docs.blockdaemon.com/reference/addasset) - POST /vaults/\{Id}/addAsset                                |
| [Get the Addresses of an Asset](https://vault.docs.blockdaemon.com/reference/getaddressofasset) - GET /vaults/\{Id}/assets/\{Asset}           |
| [Hide a Vault ](https://vault.docs.blockdaemon.com/reference/hidevault)- POST /vaults/\{Id}/hide                                              |
| [Unhide a Vault](https://vault.docs.blockdaemon.com/reference/unhidevault) - POST /vaults/\{Id}/unhide                                        |

# Sample Object

The example object returned by the `Get a List of Unhidden Vaults and the Count of Multiple Hidden Vaults` endpoint is shown below.

```json
{
  "HiddenVaultCount": 0,
  "TotalCount": 0,
  "Vaults": [
    {
      "Assets": [
        {
          "Amount": "string",
          "Asset": "string",
          "Name": "string",
          "USDAmount": "string"
        }
      ],
      "Balance": {
        "AvailableUSD": "string",
        "OnChainUSD": "string",
        "PendingUSD": "string"
      },
      "ColdVault": true,
      "CreatedAt": "string",
      "CreatedBy": "string",
      "Hidden": true,
      "ID": "string",
      "Name": "string",
      "State": "VaultCreationFailure"
    }
  ]
}
```

<Support />
