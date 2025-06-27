---
title: Policy Overview
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: Policy Overview
  description: >-
    Discover the policy overview in Blockdaemon Wallet API reference. Gain
    insights into policy management and create customized rules for secure
    digital asset operations.
  image: https://files.readme.io/2c82ee0-image_3.png
  robots: index
next:
  description: ''
---
Policy endpoints allow users to set and manage various policies and rules for their blockchain nodes and networks, such as access control policies, transaction validation rules, and other governance mechanisms. Policy endpoints in the Institutional Vault enable users to ensure the security and compliance of their blockchain infrastructure.

# Policy Attributes

| Attribute          | Type    | Description                                               |
| :----------------- | :------ | :-------------------------------------------------------- |
| ApprovalGroups     | Array   | List of the approval groups within the wallet.            |
| GroupId            | String  | The identifier of the group.                              |
| GroupName          | String  | The group's name.                                         |
| Assets             | Array   | List of available assets within the wallet.               |
| Abbreviation       | String  | The abbreviation of the asset.                            |
| Name               | String  | The full name of the asset.                               |
| Pending            | Object  | The pending policy or approval within the wallet.         |
| CreatedAt          | String  | The creation date of the pending operation.               |
| CreatedBy          | String  | The one responsible for the pending operation.            |
| Policies           | Array   | List of policies for the wallet.                          |
| ApprovalExpression | Array   | List of approvals.                                        |
| NoOfApprovals      | Integer | The number of approvals needed for the operation.         |
| DestinationType    | String  | The type of operation destination.                        |
| Destinations       | Array   | List of destination addresses.                            |
| ExternalAddress    | String  | The eternal address destination.                          |
| VaultId            | String  | The identifier of the vault.                              |
| VaultName          | String  | The name of the vault.                                    |
| MinAmount          | Integer | The minimal amount of the transaction.                    |
| TriggerGroup       | Array   | The group that is responsible for the operation.          |
| Sources            | Array   | The source vault of the operation.                        |
| TriggerGroups      | Array   | The list of groups that are responsible for the policies. |

# Endpoints

Below is the available endpoint list for Policy:

| Endpoint                                                                                                                                           |
| :------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Get a List of Groups](https://vault.docs.blockdaemon.com/reference/getallgroups) - GET /groups                                                    |
| [Create a New Group](https://vault.docs.blockdaemon.com/reference/creategroup) - POST /groups/createGroup                                          |
| [Get a List of Groupable Users ](https://vault.docs.blockdaemon.com/reference/getgroupableusers)- GET /groups/groupableUsers                       |
| [Get a Group](https://vault.docs.blockdaemon.com/reference/getgroup) - GET /groups/\{Id}                                                           |
| [Add a User(s) to a Group](https://vault.docs.blockdaemon.com/reference/adduser) - POST /groups/\{Id}/addUsers                                     |
| [Remove a User(s) from a Group](https://vault.docs.blockdaemon.com/reference/removeuser) - POST /groups/\{Id}/removeUser                           |
| [Get the Staking Policy List ](https://vault.docs.blockdaemon.com/reference/getstakingpolicylist)- GET - /policy/stakingPolicyList                 |
| [Update the Staking Policy List](https://vault.docs.blockdaemon.com/reference/updatestakingpolicylist) - PUT /policy/stakingPolicyList             |
| [Get the Transaction Policy List](https://vault.docs.blockdaemon.com/reference/gettransactionpolicylist) - GET /policy/transactionPolicyList       |
| [Update the Transaction Policy List](https://vault.docs.blockdaemon.com/reference/updatetransactionpolicylist) - PUT /policy/transactionPolicyList |
| [Get the UnStaking Policy List](https://vault.docs.blockdaemon.com/reference/get-unstaking-policies) - GET /policy/unstakingPolicyList             |
| [Update the UnStaking Policy List](https://vault.docs.blockdaemon.com/reference/update-unstaking-policies) - PUT /policy/unstakingPolicyList       |

# Sample Object

The example object returned by the `Fetch the Transaction Policy List` endpoint is shown below.

```json
{
  "ApprovalGroups": [
    {
      "GroupId": "string",
      "GroupName": "string"
    }
  ],
  "Assets": [
    {
      "Abbreviation": "string",
      "Name": "string"
    }
  ],
  "Pending": {
    "CreatedAt": "string",
    "CreatedBy": "string",
    "Policies": [
      {
        "ApprovalExpression": [
          {
            "ApprovalGroups": [
              {
                "GroupId": "string",
                "GroupName": "string"
              }
            ],
            "NoOfApprovals": 0
          }
        ],
        "ApprovalExpressionType": "Allow",
        "Assets": [
          "string"
        ],
        "DestinationType": "Any",
        "Destinations": [
          {
            "ExternalAddress": "string",
            "VaultID": "string",
            "VaultName": "string"
          }
        ],
        "MinAmount": 0,
        "Sources": [
          {
            "VaultID": "string",
            "VaultName": "string"
          }
        ],
        "TriggerGroup": {
          "GroupId": "string",
          "GroupName": "string"
        }
      }
    ],
    "Status": "PolicyUpdateAwaitingApproval",
    "UpdatedAt": "string"
  },
  "Policies": [
    {
      "ApprovalExpression": [
        {
          "ApprovalGroups": [
            {
              "GroupId": "string",
              "GroupName": "string"
            }
          ],
          "NoOfApprovals": 0
        }
      ],
      "ApprovalExpressionType": "Allow",
      "Assets": [
        "string"
      ],
      "DestinationType": "Any",
      "Destinations": [
        {
          "ExternalAddress": "string",
          "VaultID": "string",
          "VaultName": "string"
        }
      ],
      "MinAmount": 0,
      "Sources": [
        {
          "VaultID": "string",
          "VaultName": "string"
        }
      ],
      "TriggerGroup": {
        "GroupId": "string",
        "GroupName": "string"
      }
    }
  ],
  "Sources": [
    {
      "VaultID": "string",
      "VaultName": "string"
    }
  ],
  "TriggerGroups": [
    {
      "GroupId": "string",
      "GroupName": "string"
    }
  ]
}
```

<Support />
