---
title: Notifications Overview
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
Notification endpoints allow users to receive notifications and alerts about the state and performance of their blockchain infrastructure, such as new transactions, new users or groups, or network health. Notification endpoints in Blockdaemon enable users to stay informed and responsive to changes in their blockchain environment.

# Notification Attributes

| Attribute      | Type    | Description                                                      |
| :------------- | :------ | :--------------------------------------------------------------- |
| Notifications  | Array   | List of recent notifications.                                    |
| CreatedAt      | String  | The creation date of the notification.                           |
| CreatedBy      | String  | The one who is responsible for the notification.                 |
| ErrorMessage   | String  | The error message of the notification.                           |
| NotificationId | String  | The identifier of the notification.                              |
| Seen           | Boolean | Whether or not a user has seen the notification.                 |
| SubjectId      | String  | The identifier of the notification's subject.                    |
| Topic          | String  | Whether the user is active or not when the notification pop-ups. |

# Endpoint

Below is the available endpoint list for Notifications:

| Endpoint                                                                                                                                  |
| :---------------------------------------------------------------------------------------------------------------------------------------- |
| [Get the Recent Notifications](https://vault.docs.blockdaemon.com/reference/getnotifications) - GET /notifications                        |
| [Set the Last Seen Notifications](https://vault.docs.blockdaemon.com/reference/setlastseen) - POST /notifications/setLastSeen             |
| [Subscribe to the Async Updates](https://vault.docs.blockdaemon.com/reference/subscribetoupdates) - GET /notifications/subscribeToUpdates |

# Sample Object

The example object returned by the `Get the Recent Notifications endpoint` is shown below.

```json
{
  "Notifications": [
    {
      "CreatedAt": "string",
      "CreatedBy": "string",
      "JsonSerializedDetails": "string",
      "NotificationId": "string",
      "ProblemDetails": {
        "CorrelationId": "string",
        "Detail": "string",
        "ErrorCode": "10000",
        "Errors": [
          {
            "ErrorCode": "AddressIsInternal",
            "Index": [
              0
            ],
            "Message": "string"
          }
        ],
        "Instance": "string",
        "Status": 0,
        "Title": "string",
        "Type": "Authorization Error"
      },
      "Seen": true,
      "SubjectId": "string",
      "Topic": "AddUserToGroupFailed"
    }
  ],
  "TotalCount": 0
}
```

<Support />
