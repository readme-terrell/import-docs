---
title: Assets Overview
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: Assets Overview
  description: >-
    Explore the Assets API reference in Blockdaemon Wallet. Gain insights into
    managing digital assets programmatically with comprehensive asset-related
    endpoints.
  image: https://files.readme.io/89dd62a-image_3.png
  robots: index
next:
  description: ''
---
Asset endpoints allow users to interact with the platform's asset management APIs, which provide access to various features and functionalities related to managing and deploying blockchain assets. Some key functionalities accessed through asset endpoints include asset creation, asset management, asset integration, and asset monitoring.

# Asset Attributes

| Attribute                    | Type    | Description                                                                        |
| :--------------------------- | :------ | :--------------------------------------------------------------------------------- |
| Assets                       | Object  | List of available assets within the wallet.                                        |
| Asset                        | String  | The abbreviation of the asset                                                      |
| Name                         | String  | The full name of the asset.                                                        |
| Amount                       | String  | The amount of the asset.                                                           |
| USDAmount                    | String  | The amount of the asset in dollars.                                                |
| ExchangeRate                 | String  | The exchange rate of an asset.                                                     |
| ContractAddress              | String  | The contract address of the asset.                                                 |
| TotalCount                   | Integer | The total count of the asset.                                                      |
| ERC20                        | Object  | List of configurations for the ERC-20 asset.                                       |
| TransferRestrictionStandards | Array   | An array containing objects specifying the transfer restriction standards.         |
| Name                         | String  | Specifies the name of the transfer restriction standard, in this case, "ERC-1404". |

# Endpoints

Below is the available endpoint list for Assets:

| Endpoint                                                                                                                                           |
| :------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Get a List of Assets](https://vault.docs.blockdaemon.com/reference/getallassetssummary) - GET /assets                                             |
| [Add an Additional Address to an Asset ](https://vault.docs.blockdaemon.com/reference/addaddress)- POST /assets/addAddress                         |
| [Add Support for an Additional ERC20](https://vault.docs.blockdaemon.com/reference/adderc20asset) Asset - POST /assets/erc20                       |
| [Get a List of Assets and Their Exchange Rate](https://vault.docs.blockdaemon.com/reference/getallexchangerates) - GET /assets/getExchangeRates    |
| [Retry to Add an Address](https://vault.docs.blockdaemon.com/reference/retryaddaddress) - POST /assets/retryAddAddress                             |
| [Set Exchange Rate of an Asset ](https://vault.docs.blockdaemon.com/reference/setexchangerate)- POST /assets/setExchangeRate                       |
| [Get an Asset Icon](https://vault.docs.blockdaemon.com/reference/getasseticon) - GET /assets/\{Asset}/icon                                         |
| [Get a Single Asset](https://vault.docs.blockdaemon.com/reference/getassetdetails) - GET /assets/\{Asset}                                          |
| [Get a Validators for a Single Asset](https://vault.docs.blockdaemon.com/reference/getsummaryofassetsvalidators) - GET /assets/\{asset}/validators |

# Sample Object

The example object returned by the `Get a List of Assets` endpoint is shown below.

```json
{
  "Assets": [
    {
      "Amount": "string",
      "Asset": "string",
      "ERC20": {
        "TransferRestrictionStandards": [
          {
            "Name": "ERC-1404"
          }
        ]
      },
      "ExchangeRate": "string",
      "Name": "string",
      "USDAmount": "string"
    }
  ],
  "TotalCount": 0
}
```

<Support />
