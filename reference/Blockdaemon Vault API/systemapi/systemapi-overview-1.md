---
title: SystemAPI Overview
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: SystemAPI Overview
  description: >-
    Discover the System API overview in Blockdaemon Wallet API reference. Access
    system-level functionality for managing wallet configurations and
    infrastructure settings.
  image: https://files.readme.io/0e711a8-image_3.png
  robots: index
next:
  description: ''
---
> 🚧 Deprecation Notice:
>
> The `/system/api/*` APIs are deprecated and will be removed in a future release.

SystemAPI endpoints allow users to interact with the platform's system-level APIs, which provide access to various features and functionalities of the underlying blockchain infrastructure. SystemAPI endpoints provide access to essential functionalities such as adding an address, adding an asset, creating a new account, and performing synchronous fund transfers.

# SystemAPI Attributes

| Attribute | Type   | Description                    |
| :-------- | :----- | :----------------------------- |
| Address   | String | The address of the account.    |
| ID        | String | The identifier of the account. |

# Endpoints

Below is the available endpoint list for SystemAPI:

| Endpoint                                                                                                                                     |
| :------------------------------------------------------------------------------------------------------------------------------------------- |
| [Add an Address Synchronously](https://vault.docs.blockdaemon.com/reference/addaddresssynchronously) - POST /accounts/addAddress             |
| [Add an Asset to an Account Synchronously](https://vault.docs.blockdaemon.com/reference/addassetsynchronously) - POST /accounts/addAsset     |
| [Create a New Account Synchronously](https://vault.docs.blockdaemon.com/reference/createaccountsynchronously) - POST /accounts/createAccount |
| [Transfer the Funds Synchronously](https://vault.docs.blockdaemon.com/reference/transferfundssystemapi) - POST /transactions/transfer        |

# Sample Object

The example object returned by the `Add an Address Synchronously` endpoint is shown below.

```json
{
  "Address": "string"
}
```
