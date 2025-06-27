---
title: How to export logs for troubleshooting
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
By default, the logs for your wallet application are not shared with Blockdaemon or outside of your AWS account(s). If you run into an issue with your self-hosted wallet and request troubleshooting assistance, Blockdaemon support team may request that you export logs for Blockdaemon engineering to investigate.

To make the process of exporting logs to Blockdaemon easy, we have included a lambda function that can be used to facilitate this. It can be found in the resources tab of the wallet long-lived stack with the logical ID of `ExportLogsLambda` as shown below.

![](https://files.readme.io/54c873a994315762e1df1064bc0264dda6afbcb57528ab873883f367d5abf654-image.png)

You have the option to specify which log groups get exported and the start and end times of the log messages you wish to export. 

Each time you share data with us, any previously shared data is deleted, so that we have a fresh dataset with just what the customer wants to share with us. Existing data in the S3 bucket / Lakeformation tables will be cleared automatically after 30 days.

To share your log, you need to send the event payload structure detailing the start and end times and log groups you want to share as shown below.

```json
{
    "start_time": "2024-06-21 19:48:57.694939", 
    "end_time": "2024-06-24 19:48:57.694953", 
    "log_groups": [
        "/<customer_namespace>/<customer_environment>/wallet",
        "/<customer_namespace>/<customer_environment>/nitro-enclaves/instance0,
        ...
    ]
}
```

Logs are exported for the log groups specified in `log_groups`, for timestamps between `start_time` and `end_time` (ISO format).

If `log_groups` is not specified, the payload defaults to all log groups:

* /\<customer\_namespace>/\<customer\_environment>/nitro-enclaves/instance0
* /\<customer\_namespace>/\<customer\_environment>/nitro-enclaves/instance1
* /\<customer\_namespace>/\<customer\_environment>/nitro-enclaves/instance2
* /\<customer\_namespace>/\<customer\_environment>/wallet
* /\<customer\_namespace>/\<customer\_environment>/mosquitto

If `start_time` is not specified, the value is defaulted to 72 hours prior to the current date/time. If `end_time` is not specified, the value is defaulted to the current date/time.

![](https://files.readme.io/1c92885e4a6e08ab2a56901bd530f93708a10cf208c2fb797401d8f2ec39cbe0-image.png)

<Support />
