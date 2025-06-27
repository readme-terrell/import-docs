---
title: Vault Overview (COPY)
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
Vault endpoints allow users to access a secure storage location for digital assets, such as cryptocurrencies or tokens. It provides advanced security measures to ensure only authorized parties can access the assets and includes features for managing and monitoring asset transactions.

# Vault Attributes

| Attribute        | Type    | Description                                        |
| :--------------- | :------ | :------------------------------------------------- |
| HiddenVaultCount | Integer | Total number of hidden vaults.                     |
| Vaults           | Array   | List of available vaults.                          |
| Assets           | Array   | List of available assets within a vault.           |
| Amount           | String  | The total amount of the assets.                    |
| Asset            | String  | The abbreviation of the asset.                     |
| Name             | String  | The full name of the asset.                        |
| USDAmount        | String  | The total amount of the assets in dollars.         |
| CreatedAt        | String  | The creation date of the vault.                    |
| CreatedBy        | String  | The one who created the vault.                     |
| ID               | String  | The identifier of the vault.                       |
| Name             | String  | The vault's name.                                  |
| State            | String  | The state of the vault.                            |
| USDAmount        | String  | The total amount of asset in the vault in dollars. |

# Endpoints

Below is the available endpoint list for Vault:

| Endpoint                                                                                                                                       |
| :--------------------------------------------------------------------------------------------------------------------------------------------- |
| [Get a List of Unhidden Vaults and the Count of Multiple Hidden Vaults](https://wallet.docs.blockdaemon.com/reference/getvaults) - GET /vaults |
| [Get a List of Assets Not in Vault](https://wallet.docs.blockdaemon.com/reference/getallassetsnotinvault) - GET /vaults/assetsNotInVault/\{Id} |
| [Create a New Vault](https://wallet.docs.blockdaemon.com/reference/createvault) - POST /vaults/createVault                                     |
| [Search Multiple Vaults](https://wallet.docs.blockdaemon.com/reference/searchvaults) - GET /vaults/search                                      |
| [Get a Vault](https://wallet.docs.blockdaemon.com/reference/getvault) - GET /vaults/\{Id}                                                      |
| [Add an Asset to a Vault](https://wallet.docs.blockdaemon.com/reference/addasset) - POST /vaults/\{Id}/addAsset                                |
| [Get the Addresses of an Asset](https://wallet.docs.blockdaemon.com/reference/getaddressofasset) - GET /vaults/\{Id}/assets/\{Asset}           |
| [Hide a Vault ](https://wallet.docs.blockdaemon.com/reference/hidevault)- POST /vaults/\{Id}/hide                                              |
| [Unhide a Vault](https://wallet.docs.blockdaemon.com/reference/unhidevault) - POST /vaults/\{Id}/unhide                                        |

# Sample Object

The example object returned by the `Get a List of Unhidden Vaults and the Count of Multiple Hidden Vaults` endpoint is shown below.

```json
{
  "HiddenVaultCount": 0,
  "Vaults": [
    {
      "Assets": [
        {
          "Amount": "string",
          "Asset": "ETH",
          "Name": "ethereum",
          "USDAmount": "500.000"
        }
      ],
      "CreatedAt": "2023-05-02T06:23:18.373Z",
      "CreatedBy": "string",
      "ID": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "Name": "string",
      "State": "VaultCreationInProgress",
      "USDAmount": "string"
    }
  ]
}
```
