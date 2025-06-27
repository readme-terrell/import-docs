---
title: Configuration Overview
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: Configuration Overview
  description: >-
    Explore the configuration overview in Blockdaemon Wallet API reference.
    Learn how to customize and optimize wallet settings for your digital asset
    management needs.
  image: https://files.readme.io/a157980-image_3.png
  robots: index
next:
  description: ''
---
Configuration endpoint allows users to see various settings and parameters for their blockchain nodes and networks, such as the wallet name, license, and version.

# Configuration Attributes

| Attribute                 | Type    | Description                                                                                                                                                                                                                            |
| :------------------------ | :------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AppConfigLink             | String  | The application configuration link.                                                                                                                                                                                                    |
| AppStoreLink              | String  | The wallet app store link.                                                                                                                                                                                                             |
| Feature                   | Object  | List of wallet's features.                                                                                                                                                                                                             |
| BlockExplorer             | Boolean | Indicates whether the application has a block explorer feature.                                                                                                                                                                        |
| ColdStorage               | Boolean | Indicates whether the application supports cold storage for cryptocurrency.                                                                                                                                                            |
| DevTools                  | Boolean | Indicates whether the application provides developer tools.                                                                                                                                                                            |
| ERC20TransferRestriction  | Boolean | Indicates whether the application supports ERC-20 token transfer restrictions.                                                                                                                                                         |
| EnhancedAudits            | Boolean | Indicates whether the application provides enhanced audit features.                                                                                                                                                                    |
| StakeEth                  | Boolean | Indicates whether the application supports staking Ethereum.                                                                                                                                                                           |
| TxnRiskAssessment         | Boolean | Indicates whether the application includes transaction risk assessment features.                                                                                                                                                       |
| Frozen                    | String  | Whether the wallet is frozen or not.                                                                                                                                                                                                   |
| InstanceName              | String  | The wallet's name.                                                                                                                                                                                                                     |
| MasterKeyBackupPerformed  | Boolean | Whether the master key backup has been executed or not.                                                                                                                                                                                |
| MuixLicenseKey            | String  | The muix license key of the wallet.                                                                                                                                                                                                    |
| OAuthAudience             | String  | A unique identifier specifies which API or service a client application can access. This helps ensure that only authorized parties can access sensitive data or resources.                                                             |
| OAuthClientId             | String  | The registered client app’s unique identifier with an OAuth provider. This ID verifies the app's identity and grants permission to access protected data. A secret code lets an app securely connect and use certain services or data. |
| OAuthDomain               | String  | The website linked to an OAuth provider, responsible for verifying client apps and securely granting access to protected resources.                                                                                                    |
| SelectableValidatorAssets | Array   | This array contains strings representing selectable validator assets for the application.                                                                                                                                              |
| TestNet                   | Boolean | Whether or not the wallet has a testnet environment.                                                                                                                                                                                   |
| Version                   | String  | The wallet's version.                                                                                                                                                                                                                  |

# Endpoint

Below is the available endpoint list for Configuration:

| Endpoint                                                                                             |
| :--------------------------------------------------------------------------------------------------- |
| [View the Config](https://vault.docs.blockdaemon.com/reference/viewconfig) - GET /config             |
| [Logout the Current User](https://vault.docs.blockdaemon.com/reference/logoutendpoint) - GET /logout |

# Sample Object

The example object returned by the `View the Config` endpoint is shown below.

```json
{
  "AppConfigLink": "string",
  "AppStoreLink": "string",
  "Feature": {
    "BlockExplorer": true,
    "ColdStorage": true,
    "DevTools": true,
    "ERC20TransferRestriction": true,
    "EnhancedAudits": true,
    "StakeEth": true,
    "TxnRiskAssessment": true
  },
  "Frozen": "AwaitingConfirmationOfFullFreeze",
  "InstanceName": "string",
  "MasterKeyBackupPerformed": true,
  "MuixLicenseKey": "string",
  "OAuthAudience": "string",
  "OAuthClientId": "string",
  "OAuthDomain": "string",
  "SelectableValidatorAssets": [
    "string"
  ],
  "TestNet": true,
  "Version": "string"
}
```

<Support />
