---
title: Health Overview
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: Health Overview
  description: >-
    Explore the health overview in Blockdaemon Wallet API reference. Monitor and
    maintain the health of your wallet infrastructure for seamless digital asset
    operations.
  image: https://files.readme.io/f7ed4bc-image_3.png
  robots: index
next:
  description: ''
---
Health endpoint allows users to monitor and assess the health and performance of their blockchain infrastructure. Health endpoints in the Institutional Vault provide real-time metrics and insights into the status and usage of their blockchain nodes, networks, alerts, and notifications for potential issues or problems.

# Health Attributes

| Attribute      | Type    | Description                             |
| :------------- | :------ | :-------------------------------------- |
| DatabaseHealth | Object  | The information about database health.  |
| ErrorMessage   | String  | The error message of the response.      |
| Healthy        | Boolean | Whether the database is healthy or not. |
| Healthy        | Boolean | Whether the server is healthy or not.   |

# Endpoints

Below is the available endpoint list for Health:

| Endpoint                                                                                       |
| :--------------------------------------------------------------------------------------------- |
| [Enquire the Server System](https://vault.docs.blockdaemon.com/reference/system) - GET /health |

# Sample Object

The example object returned by the `Enquire the Server System` endpoint is shown below.

```json
{
  "DatabaseHealth": {
    "ErrorMessage": "string",
    "Healthy": true
  },
  "Healthy": true
}
```

<Support />
