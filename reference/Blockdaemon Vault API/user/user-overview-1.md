---
title: User Overview
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: User Overview
  description: >-
    Explore the user overview in Blockdaemon Wallet API reference. Learn how to
    manage user accounts, access controls, and permissions for secure digital
    asset management.
  image: https://files.readme.io/1cdc70d-image_3.png
  robots: index
next:
  description: ''
---
User endpoints allow users to manage user accounts and access permissions for their blockchain infrastructure. This helps control who has access to their blockchain nodes and networks and what actions they can perform. Users can also monitor user activity and usage logs to ensure the security and compliance of their blockchain environment.

These endpoints also enable users to create or delete system users and get the Institutional Vault API key.

# User Attributes

| Attribute       | Type   | Description                                                  |
| :-------------- | :----- | :----------------------------------------------------------- |
| SystemUsers     | Array  | The list of available system users within a wallet.          |
| CreatedAt       | String | The creation date of the system user.                        |
| Id              | String | The identifier of the user.                                  |
| MpaId           | String | The email address of the registered system user.             |
| Name            | String | The name of the system user.                                 |
| Role            | String | The role of the system user.                                 |
| State           | String | The state of the system user.                                |
| WalletPublicKey | String | The system's user wallet public key.                         |
| Users           | Array  | The list of users.                                           |
| IdpUserId       | String | The email address provided by the organization for the user. |

# Endpoints

Below is the available endpoint list for User:

| Endpoint                                                                                                                          |
| :-------------------------------------------------------------------------------------------------------------------------------- |
| [Get a List of Users](https://vault.docs.blockdaemon.com/reference/getallusers) - GET /users                                      |
| [Delete System User Endpoint](https://vault.docs.blockdaemon.com/reference/deletesystemuserendpoint) - POST /systems/\{id}/delete |
| [Get a User Details](https://vault.docs.blockdaemon.com/reference/getuserinfo) - GET /users/info                                  |
| [Create a New User](https://vault.docs.blockdaemon.com/reference/registeruserendpoint) - POST /users/register                     |
| [Reset a User](https://vault.docs.blockdaemon.com/reference/resetuserendpoint) - POST /users/\{Id}/reset                          |
| [Delete a User](https://vault.docs.blockdaemon.com/reference/deleteuserendpoint) - POST /users/\{Id}/delete                       |

# Sample Object

The example object returned by the `Get a List of Users` endpoint is shown below.

```json
{
  "SystemUsers": [
    {
      "CreatedAt": "2023-05-02T06:23:18.373Z",
      "Id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "MpaId": "johndoe@yourcompany.com",
      "Name": "JohnDoeAdmin",
      "Role": "Admin",
      "State": "Active",
      "WalletPublicKey": null
    }
  ],
  "Users": [
    {
      "CreatedAt": "2023-05-02T06:23:18.373Z",
      "Id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "IdpUserId": "johndoe@yourcompany.com",
      "Name": "John Doe",
      "Role": "Admin",
      "State": "Active"
    }
  ]
}
```

<Support />
