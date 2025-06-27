---
title: AWS Installation Troubleshooting
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  image: https://files.readme.io/d6781ad-metadata.png
  robots: index
next:
  description: ''
---
This document provides guidance on how to troubleshoot common issues.

## Overview

During the installation process, the components for the wallet need to be deployed in the following order:

* Long-lived resources ( wallet and policy nodes)
* Secrets pushed
* Deploy Wallet and Policy Nodes
* Start Wallet

We wait to start the wallet until the policy nodes are completed because the policy nodes have to come online before the wallet can be started. The security of the policy nodes requires that they are a pre-requisite for the wallet to start. The orchestrator/facade service is the communication hub between those components. It is required to start and initiate the master key of the system before the wallet can perform commands within the system.

When the system starts, the key init process must be performed by all of the policy nodes communicating. The orchestrator will initially perform migrations, but after it starts up for the first time will look to the system to make sure that the nodes have properly generated keys. Once this key process is complete, the system can start performing operations.

## Troubleshooting

## Wallet is not starting

If the Wallet is not starting, check the following:

### Facade/Orchestrator

The facade/orchestrator is part of the system that brokers communication to the policy nodes. Part of the startup sequence is that the orchestrator must be available for the policy nodes to start. Locate the orchestrator logs in ECS and check for any errors that may happen. If the orchestrator is not starting, it may be due to the policy nodes not being available, or not being able to start.

### Policy Nodes

The policy nodes run inside of a nitro enclave. A nitro enclave is a bit different than the average container. It is a secure enclave that is isolated from the host. This isolation makes it more secure, but more difficult to troubleshoot. In order to troubleshoot the policy nodes, you will need to perform two operations. One is to enable debugging on the policy node enclave (use policy node 0 for this purpose), and the other is to log into the policy node in AWS and perform the console output to see what the error condition is.

### Enable Debug Output from Policy Node 0

*Nitro Debug Mode*\
In order to enable nitro debug mode for an enclave, you will first need to navigate to the KMS console in AWS and find the KMS key that is responsible for requiring the enclave to be in debug mode. Once you have found the key, you will need to enable the debug mode for the enclave. This is done by setting the KMS policy to have a debug value for the PCR that is set. The KMS key is in the -policy-node0-kms-key location. The policy should have a statement that looks like this:

```
{
    "Sid": "Enable decrypt from nitro enclave policy-node0",
    "Effect": "Allow",
    "Principal": {
        "AWS": "arn:aws:iam::12309900923:root"
    },
    "Action": "kms:Decrypt",
    "Resource": "*",
    "Condition": {
        "StringEqualsIgnoreCase": {
            "kms:RecipientAttestation:PCR8": "7b9eff26a37b1604c516dda3c68d7fc1bdab0ae0b5175dae2461e848ddf7b4bf8b8b094f45ec83766132b7a0f2c4888b"
        },
        "ArnLike": {
            "aws:PrincipalArn": "arn:aws:iam::12309900923:role/<namespace>nitroRole0"
        }
    }
}

```

The KMS key would need to be changed in order to access the node in debug mode to see the logs.

```
"kms:RecipientAttestation:PCR8": "000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"
```

#### Enter Debug Mode on EC2

1. Find the EC2 instance that is running the nitro enclave within AWS. The name should be -node0. Right click on the instance and click 'Connect'.
2. Connect to it with Session Manager.
3. Once you are connected, navigate to the `/home/ssm-user directory`.
4. Change the `restart-mpa.sh` file to enter into debug mode, by adding the `--debug-mode` flag to the `nitro-cli run-enclave` command.

```
#!/bin/sh
nitro-cli terminate-enclave --all
systemctl restart tacos.service
nitro-cli run-enclave --cpu-count 2 --memory 8000 --eif-path mpa-policy-nitro.eif --enclave-cid 16 --debug-mode
```

5. Restart the enclave by `systemctl restart policy-node.service`.

```
sudo su
cd /home/ssm-user
systemctl restart policy-node

# wait a few seconds for the nitro enclave to start, then run
nitro-cli console --enclave-name mpa-policy-nitro
```

5. You can query the status of the enclave runtime by executing `nitro-cli describe-enclaves`. From here, you can see all the logs for the policy node service.

<br />

## Remote Troubleshooting with Blockdaemon

To allow Blockdaemon to troubleshoot remotely, your AWS installation includes a Lambda function to export the last 72 hours of CloudWatch logs to the Blockdaemon Triage Stack. The exported logs are retained for 30 days.

Steps to Export Logs:

1. Navigate to the Lambda service page.
2. Locate the function named `ExportLogsLambda`.
3. Go to the `Test` tab.
4. Click `Test` to execute the function.
5. After completion, the function will return the message: "Logs exported successfully."

<Support />
