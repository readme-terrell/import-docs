---
title: System User Overview
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
System User endpoints allow users to facilitate the management and authentication of system users within the Institutional Vault.

# System User Attributes

| Attribute  | Type   | Description                                                                                                 |
| :--------- | :----- | :---------------------------------------------------------------------------------------------------------- |
| Confirmers | Array  | This array contains information about individual confirmers.                                                |
| MpaId      | String | This field represents the ID associated with the confirmer within the MPA (Multi-Party Application) system. |
| Name       | String | This field represents the name of the confirmer.                                                            |

# Endpoint

Below is the available endpoint list for System User:

| Endpoint                                                                                                                    |
| :-------------------------------------------------------------------------------------------------------------------------- |
| [Get All Confirmers](https://vault.docs.blockdaemon.com/reference/getallconfirmers-1) - GET /systems/confirmers             |
| [Create System User Endpoint ](https://vault.docs.blockdaemon.com/reference/createsystemuserendpoint)- POST /systems/create |

# Sample Object

The example object returned by the `Get All Confirmers` is shown below.

```json
{
  "Confirmers": [
    {
      "MpaId": "string",
      "Name": "string"
    }
  ]
}
```

<Support />
