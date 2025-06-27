---
title: Staking Overview
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
Staking endpoints allow users to perform staking operations. These endpoints enable users to stake, withdraw, and get all the staked assets from the Institutional Vault.

# Staking Attributes

| Attribute     | Type    | Description                                                                                                                                      |
| :------------ | :------ | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| AssetDetails  | Object  | This object contains asset details, including exchange rates, fees, whether the asset is an ERC-20 token, unit precision, and vault information. |
| ExchangeRate  | String  | This field represents the exchange rate of the asset.                                                                                            |
| Fee           | Object  | This field contains information about the fee associated with the asset.                                                                         |
| IsERC20       | Boolean | This field indicates whether the asset is an ERC-20 token.                                                                                       |
| UnitPrecision | Integer | This field represents the precision of the unit of the asset.                                                                                    |
| Vaults        | Array   | This field contains information about the vaults associated with the asset.                                                                      |
| Assets        | Array   | This array contains information about individual assets.                                                                                         |
| Abbreviation  | String  | This field represents the abbreviation of the asset name.                                                                                        |
| Amount        | String  | This field represents the amount of the asset.                                                                                                   |
| Name          | String  | This field represents the name of the asset.                                                                                                     |
| AssetsCount   | Integer | This field represents the total count of assets. It's currently set to 0.                                                                        |

# Endpoint

Below is the available endpoint list for Staking:

| Endpoint                                                                                                                |
| :---------------------------------------------------------------------------------------------------------------------- |
| [Get All the Staking Assets](https://vault.docs.blockdaemon.com/reference/getallstakingassets) - GET /staking/assets    |
| [Get the Staking Plans](https://vault.docs.blockdaemon.com/reference/liststakingplans) - GET /staking/plans             |
| [Stake Funds](https://vault.docs.blockdaemon.com/reference/stake) - POST /staking/stake                                 |
| [Withdraw the Staked Assets](https://vault.docs.blockdaemon.com/reference/stakingwithdrawal) - POST /staking/withdrawal |

# Sample Object

The example object returned by the `Get All the Staking Assets` is shown below.

```json
{
  "AssetDetails": {
    "ExchangeRate": "string",
    "Fee": {
      "FeeExchangeAsset": "string",
      "FeeExchangeRate": "string",
      "FlatFee": true,
      "Precision": 0,
      "Rates": {
        "High": "string",
        "Low": "string",
        "Medium": "string"
      },
      "Size": "string",
      "Unit": "string"
    },
    "IsERC20": true,
    "UnitPrecision": 0,
    "Vaults": [
      {
        "Amount": "string",
        "ColdVault": true,
        "Id": "string",
        "Name": "string"
      }
    ]
  },
  "Assets": [
    {
      "Abbreviation": "string",
      "Amount": "string",
      "Name": "string"
    }
  ],
  "AssetsCount": 0
}
```

<Support />
