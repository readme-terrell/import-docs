---
title: Azure Installation Troubleshooting
excerpt: How to troubleshoot common issues for Azure Installation.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Remote Troubleshooting with Blockdaemon

To assist Blockdaemon in troubleshooting issues with your Azure wallet, we have provided a process for you to extract logs from Azure Log Analytics in the Azure Cloud Shell, save them to a file, and download them for sharing. 

Follow the steps below to complete this process.

1. Navigate to the Azure Cloud Shell within your Azure Portal service page.
2. Enable the LogAnalytics Extension within the Azure Cloud Shell:

```shell
cd clouddrive
az extension add --name log-analytics
```

3. Run the Azure LogAnalytics command to extract the logs to a local `wallet_logs_<date>.tgz` file. This process will take roughly 5 minutes to run when extracting 30 days of logs.

```shell
WORKSPACEID=$(az monitor log-analytics workspace list --query "[?name=='mainnet-mpa'].customerId" --output tsv)
QUERY="ContainerLogV2 | where (ContainerName == 'wallet' or ContainerName == 'facade' or ContainerName == 'policy-node0') | where TimeGenerated > ago(30d) | project PodName, LogMessage"
az monitor log-analytics query -w $WORKSPACEID -o tsv --analytics-query "$QUERY" > wallet_logs_$(date +"%m-%d-%Y").csv
tar -czf wallet_logs_$(date +"%m-%d-%Y").tgz wallet_logs_$(date +"%m-%d-%Y").csv && rm -f wallet_logs_$(date +"%m-%d-%Y").csv
```

4. Open the Azure Cloud Shell Managed Files file share window to download the log file:

<Image align="center" width="50% " src="https://files.readme.io/990149c-image.png" />

5. Locate the log file, download it to your desktop and share it with Blockdaemon via [support@blockdaemon.com](mailto:support@blockdaemon.com)

<Image align="center" width="50% " src="https://files.readme.io/34e1ad3-image.png" />

<Support />
