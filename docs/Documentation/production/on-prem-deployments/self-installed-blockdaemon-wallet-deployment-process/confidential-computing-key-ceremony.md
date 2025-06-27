---
title: Confidential Computing - Key Ceremony Raw Process
excerpt: 🗝️ Key Ceremony Raw Process
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Overview

The Key Ceremony Raw Documentation provides a comprehensive overview of the entire process, procedures, and protocols involved in the Key Ceremony. A key ceremony is a critical event where cryptographic keys are generated, distributed, and securely stored to ensure the integrity, confidentiality, and authenticity of sensitive information and communications within the Institutional Wallet. This guide outlines the steps required for a successful ceremony.

## High - Level Workflow

![](https://files.readme.io/1023234-d9b224ab-bc06-4e59-bca6-a72ab9b1ac88.png)

The above image depicts the high-level workflow for generating and managing MPA policy nodes, configuration files, and sensitive parameters. Currently, the MPA policy node configuration file contains several types of sensitive parameters:

* **EncryptorMasterPassword/EncryptorKeyFile**

The password or key file generates the encryption and authentication keys for sensitive data in the persistent MPA DB. Specifically, it encrypts the MPA node's private key share(s).

* **PrivateKey**

MPA node’s private key for mTLS communication between MPA nodes in the cluster.

* **Blockchain Services-Related Configuration**

The blockchain configuration.

* **Message Broker and MPA Node Persistent DB Configurations**

The DB configurations that specific to the MPA node and Message Broker.

* **Callback Public Key**

A public key to verify confirmation from a callback service.

* **ERS Public Key**

A public key of an Emergency Recovery Service is used to encrypt the mpa shares and create an ERS backup bundle.

Configuration files for MPA nodes can be split into several files and loaded by specifying a comma-separated file list in the `-configFile` parameter. Furthermore, configuration values can be loaded from environment variables. Environment variables should be prefixed with MPA and use the `_` separator.

The suggested way is to load values common to 3 MPA policy nodes through `common.conf` and node-specific configuration through `node.conf`. This is also how the prebuilt Nitro EIF operates.

A provisioner helper tool (`mpagen`) can facilitate the secure generation and provisioning of sensitive values for MPA policy nodes. Even though the workflow is detailed, the AWS-specific `mpagen` tool can generate sensitive values and perform provisioning to other key-value stores such as Hashicorp Vault.

The below diagram represents a recommended workflow for the secure deployment of one MPA node.

<Image align="center" src="https://files.readme.io/5621db5-Asset_48300x.png" />

> 📘 Note:
>
> A highly recommended approach involves deploying 3 MPA nodes across 3 separate accounts and conducting the 3 key ceremonies with diverse stakeholders. This means that individuals such as Privileged User 1 and Privileged User 2 should be distinct individuals across the 3 accounts.

# Perform the Key Ceremony

![](https://files.readme.io/fdbf9fd-550cc448-43e0-47c7-b815-21262f229d78.png)

Follow the steps below to perform the key ceremony by deploying an MPA node.

## Step 1: Define Provisioning Values for AWS Secrets Manager

Define the following sensitive parameters in the MPA policy node configuration file:

* **EncryptorKeyFile/EncryptorMasterPassword** - This is the most sensitive value. This value derives keys to encrypt and authenticate sensitive data in the persistent MPA DB. There are two options here:
  * **EncryptorMasterPassword** - String directly in the configuration file.
  * **EncryptorKeyFile** - It is recommended to encrypt the EncryptorKeyFile with an AWS KMS CMK (Customer-Managed Key) and store the encrypted blob on the S3 bucket. The ACL for CMK should enable only one specific MPA policy node on an EC2 Nitro instance to access it.
* **PrivateKey** - MPA node’s private key for mTLS communication between MPA nodes in the cluster.
* **Ubiquity Authentication Token** - API key for blockchain services.
* **Message Broker Password** - Password for the Message Broker.

> 📘 Note:
>
> It is recommended to store the following value in AWS Secrets Manager:
>
> * **EncryptorMasterPassword**
> * **PrivateKey**
> * **Ubiquity Authentication Token**
> * **Message Broker Password**

## Step 2: Generate the mpagen Configuration

Generate the `mpagen` configurations from a template run by using the code below:

```
mpagen ingest -i config_template.toml -f toml
```

The result would be a `config_common.toml` and 3 `config_node<n>.toml` configuration files. `mpagen` also generates `EncryptorMasterPassword`, `PrivateKey` and  `PublicKey` for each MPA policy node.

> 📘 Note:
>
> You can generate a TOML, YAML and JSON file formats.

## Step 3: Configure the mpagen Configuration Template

<Image align="center" width="70% " src="https://files.readme.io/07851e5-Asset_49300x.png" />

The `mpagen` helps generate the cryptographic keys, builds configuration files for MPA policy nodes, and provisions sensitive values into AWS Secrets Manager. A template allows you to prefill some values, which will be integrated into the final configuration file. The template contains the following values:

| Value            | Description                                                                                 |
| :--------------- | :------------------------------------------------------------------------------------------ |
| `CommonSection`  | The value declared will be written into configuration files common to all MPA policy nodes. |
| `PerNodeSection` | The value declared will be written to the corresponding node configuration file.            |

> 📘 Note:
>
> Any value that is deemed sensitive can be changed to `{{ awsSecret "<name of AWS secret>" }}`. It can be provisioned using the `mpagen` tool in AWS Secrets Manager.

Below is an example of `mpagen` TOML template:

> 📘 Note:
>
> Please make sure you understand all of the parameters and adapt to your own environment.

<details><summary><b>`config_template.toml`</b></summary><br/></details>


```
## Common part
[[CommonSection.ConfiguredUsers]]
UserID = "confirm"
Name = "Confirm Anything"
PublicKey = "BDbEhfiD2s+zY8j2TWqC5WU9fTZkKzoQi1FVWo0zQH1caclSIU/OQ+pfgEMQu+Y+De7L8em6aV2sd1OxMby/85g="
Group = "API"
[[CommonSection.ConfiguredUsers]]
UserID = "reject"
Name = "Reject Everything"
PublicKey = "/reject/1KR7id68tzcFmC4GMWQSi26NsbilhptQ4n+GLa3zhhimPCTR1+1Yyvf0EwXYKMBuaHo364rG8dx9Yts="
Group = "API"
[[CommonSection.ERC20Tokens]]
Name = "USD Coin"
Symbol = "USDC-ERC20"
Address = "0x07865c6e87b9f70255377e024ace6630c1eaa37f"
TestNetwork = true
[CommonSection.Server]
Port = 8080
[CommonSection.Node]
Port = 9080
ERSPublicKey = "MIIBojANBgkqhkiG9w0BAQEFAAOCAY8AMIIBigKCAYEA1h0w7VEBF8OtKkel8fBluF9RgpolAwmcnH4KGtoL438MakMLM7nW6ia/1j6F1ViMrWX2a8/PqOOAoLaVnWVEP7l6dFqSpOY60TbAW2WT1KYlqkWKac5gr+F9JRsfwbsfApjAtkhKBb1tD5lG3ugf8srRJQ6VQrZUh3pPUX6QNPJLVCKrbDs6O0J1kSlZKp5OuJzP+LiQbplz47Sn+VWoxIBVGLe1QHBnpsATdLjRnv+873kn7yWgdUM6OVDIZEhrDNSGJBd2cx4kCjb+5/pTeRQyi+z43TRWrBpBfq0XfRX1WTZWho4sBNMO5nZ67/hVvXtKdg1uSrI38rA2WxJgywMJXn4I1zUiyJ/Xk9JuFKViOBbDyfsiPUjDWOG/uGjue8Xj7zKxZqNJvVOmLnviQlYWRHBM9I6PxPdQna1IgwPv0RNhP0PAo/XItrrJ/8nN3Ha/XTnjlTyYgGVw3AO4vx0cxFjSr9kDdOM1yjQ54QBtIuVKqs1uM0NO7IcLIwi5AgMBAAE="
[CommonSection.Blockchains]
[CommonSection.Blockchains.btctest]
Name = "BTC"
UTXOStrategy = "mostconfirmations"
[CommonSection.Blockchains.btctest.Service]
Name = "bitcoincore"
URL = "<https://test123.bdnodes.net">
TestNetwork = true
AuthToken = "{{ awsSecret `wallet-sandbox.test.btc_core_auth_token` }}"
[CommonSection.Blockchains.polkadot]
Name = "DOT"
[CommonSection.Blockchains.westend]
Name = "WND"
[CommonSection.Blockchains.westend.Service]
Name = "sidecar"
URL = "<https://svc.blockdaemon.com/polkadot/westend/native">
TestNetwork = true
AuthToken = "{{ awsSecret `wallet-sandbox.test.ubiquity_auth_token` }}"
[CommonSection.Blockchains.solanatest]
Name = "SOL"
[CommonSection.Blockchains.solanatest.Service]
Name = "bd_ubiquity"
TestNetwork = true
AuthToken = "{{ awsSecret `wallet-sandbox.test.ubiquity_auth_token` }}"
[CommonSection.Blockchains.ethtest]
Name = "ETH"
[CommonSection.Blockchains.ethtest.Service]
Name = "bd_ubiquity"
TestNetwork = true
AuthToken = "{{ awsSecret `wallet-sandbox.test.ubiquity_auth_token` }}"
[CommonSection.OIDCConfig.auth0]
Issuer = "<https://test-auth0-replace.us.auth0.com">
ClientID = "SaB8GG8GEUJe54sVs5nmW3UKYUxCOYhS"
[CommonSection.Policies]
transfer = "{ \"OperationType\": \"transfer\", \"Policies\": [ { \"DestinationType\": \"internal\", \"MinAmount\": \"500\", \"AmountCurrency\": \"USD\", \"ApproverExpression\": { \"Groups\": [], \"RequiredCount\": 1 }, \"TxCurrencies\": [ \"BTC\" ] }, { \"DestinationType\": \"internal\", \"MinAmount\": \"1000\", \"AmountCurrency\": \"USD\", \"ApproverExpression\": { \"Groups\": [], \"RequiredCount\": 1 }, \"TxCurrencies\": [ \"ETH\" ] }, { \"DestinationType\": \"internal\", \"ApproverExpression\": { \"Op\": \"allow\" } }, { \"DestinationType\": \"external\", \"ApproverExpression\": { \"Groups\": [], \"RequiredCount\": 1 } } ] }"
"update policy set" = "{ \"PolicyOperationType\":\"update policy set\", \"Policies\":[{\"TriggerGroup\":\"owner\",\"ApproverExpression\":{\"Op\":\"allow\"}},{\"ApproverExpression\":{\"Groups\":[\"owner\"],\"RequiredCount\":1},\"PolicyUpdateOpType\":\"transfer\"}] }"
[CommonSection.Users]
[CommonSection.Users.0]
UserID = "Someuser@mail.com"
Name = "User"
Group = "owner"
[CommonSection.OperationConfirmation]
Skip = ["get address", "create master key", "create account"]
[[CommonSection.RateService]]
ServiceName = "coinlayer"
Symbols = ["BTC", "ETH", "ADA"]
AccessKey = "5f2dd4c65f2ff4cd4ff32192fe5c01ff"
TTL = "1h13m"
Validate = true
[[CommonSection.RateService]]
ServiceName = "coincap"
Symbols = ["SOL", "NEAR", "DOT"]
TTL = "43m"
Validate = true
[[CommonSection.RateService]]
ServiceName = "constant"
Symbols = ["ERC20_cd383f6ec39de4b0b588b4d1f11b28e0cff9cd29"]
Rate = "1.0"
[[CommonSection.RateService]]
ServiceName = "constant"
Symbols = ["WND"]
Rate = "6.0"
## Per node part
[PerNodeSection.Nodes.0]
NodeAddress = "localhost:9080"
NodePort = 9080
[PerNodeSection.Nodes.0.Broker]
BrokerURL = "mqtts://brokerhost.local:8883"
BrokerPublicKey = "MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAE0NoAS1Ym0tO+kXWT5YV7Z+25NlKmWtfisDktneo+f1Q9UR+PWuSFQAjxncEODp3gPXxiOPzwhkyP8MpVD9suMA=="
Username = "node0"
Password = "node0password"
PersistenceDirectory = "db/node0mqtt"
[PerNodeSection.Nodes.0.Database]
DriverName = "sqlite"
DataSourceName = "db/node0.db"
MaxIdleConns = 1
MaxOpenConns = 1
[PerNodeSection.Nodes.1]
NodeAddress = "localhost:9081"
NodePort = 9081
[PerNodeSection.Nodes.1.Broker]
BrokerURL = "mqtts://brokerhost.local:8883"
BrokerPublicKey = "MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAE0NoAS1Ym0tO+kXWT5YV7Z+25NlKmWtfisDktneo+f1Q9UR+PWuSFQAjxncEODp3gPXxiOPzwhkyP8MpVD9suMA=="
Username = "node1"
Password = "node1password"
PersistenceDirectory = "db/node1mqtt"
[PerNodeSection.Nodes.1.Database]
DriverName = "sqlite"
DataSourceName = "db/node1.db"
MaxIdleConns = 1
MaxOpenConns = 1
[PerNodeSection.Nodes.2]
NodeAddress = "localhost:9082"
NodePort = 9082
[PerNodeSection.Nodes.2.Broker]
BrokerURL = "mqtts://brokerhost.local:8883"
BrokerPublicKey = "MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAE0NoAS1Ym0tO+kXWT5YV7Z+25NlKmWtfisDktneo+f1Q9UR+PWuSFQAjxncEODp3gPXxiOPzwhkyP8MpVD9suMA=="
Username = "node2"
Password = "node2password"
PersistenceDirectory = "db/node2mqtt"
[PerNodeSection.Nodes.2.Database]
DriverName = "sqlite"
DataSourceName = "db/node2.db"
MaxIdleConns = 1
MaxOpenConns = 1
```


## Step 4: EncryptorKeyFile Generation and Encryption

![](https://files.readme.io/70d771e-5f57cc07-80f1-44fe-aef8-605e01df45cb.png)

> 📘 Note:
>
> This step is **OPTIONAL** but strongly **RECOMMENDED** to further improve the password encryption protection of sensitive data in the DB including MPA policy node shares.

An alternative to EncryptorMasterPassword is to use a key file. The content of the key file is hashed and used as the master password. This way, the master password can be handled by an entirely separate entity (privileged user or administrator) from any other configuration values. The below steps are extremely sensitive since the EncryptorKeyFile is being handled clearly. Therefore, those steps constitute an integral part of the key ceremony process. Follow the steps below to use a key file:

1. Generate a random `EncryptorKeyFile`.

```
openssl rand 2048 > keyfile.bin
```

> 📘 Note:
>
> As an additional measure for enhanced resilience, you have the option to perform Shamir-splitting on the keyfile and create backups of the resulting Shamir shares. This would enable you to reconstruct the EncryptorKeyFile in case of an unforeseen emergency.

2. Comment out in the corresponding `config_node<n>.toml` the line and add the `EncryptorKeyFile`.

```
# EncryptorMasterPassword = "..."
EncryptorKeyFile = "/config/keyfile.bin"
```

3. Generate an **AWS CMK key**, and write down the **KeyId** of the newly generated **CMK key**.

```
aws kms create-key
```

4. For example, it will generate a`"KeyId": "73a69813-9eb7-4b4a-bc95-5642634d872c"`. Create an alias for the key. The alias has to be named `alias/mpa-cmk`.

```
aws kms create-alias \
  --alias-name 'alias/mpa-cmk' \
  --target-key-id '73a69813-9eb7-4b4a-bc95-5642634d872c'
```

5. Encrypt the `EncryptorKeyFile`.

```
aws kms encrypt \
    --key-id '73a69813-9eb7-4b4a-bc95-5642634d872c' \
    --plaintext 'fileb://keyfile.bin' \
    --output 'text' \
    --query 'CiphertextBlob' | base64 \
    --decode > keyfile.enc
```

6. Upload it to the S3 bucket `nitro-mpa`.

## Step 5: Review the mpagen Payload JSON

Create and evaluate the JSON payload for provisioning sensitive values into AWS Secrets Manager. Below is an illustration of `payload.json`:

```
[{
    "SecretManager":"AwsSecretManager",
    "Name":"wallet-sandbox.test.ubiquity_auth_token",
    "Value":"..."
},
{
    "SecretManager":"AwsSecretManager",
    "Name":"wallet-sandbox.test.policy-node0.node-public-key",
    "Value":"MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEKm0Msp9mcR1mxnfqdAqMhYwozfJnWfSpu+n1JnYs6V80sHl/l6vufdcZUkiS8lemsd2lizVyZXk5NU/tjvoFIg=="
},
{
    "SecretManager":"AwsSecretManager",
    "Name":"wallet-sandbox.test.policy-node1.node-public-key",
    "Value":"MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAE7/3ofb5Me55Ibu1zbFEjQWxtuoDSex6cUWqg9dv8MCqAdCZqA1jj97RWM8vi56ycRv1gx8QTcop05++3REp35w=="
},
{
    "SecretManager":"AwsSecretManager",
    "Name":"wallet-sandbox.test.policy-node2.node-public-key",
    "Value":"MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEqtRV/tu75oXyeVuyq66m9s7+DZ41fbuP6de6gzb4qFHGOlXNFgUM1NJQPPJ9kS2eVACEOm0koWeOoXtpe3DocA=="
},
{
    "SecretManager":"AwsSecretManager",
    "Name":"wallet-sandbox.test.auth0",
    "Value":"{\"ISSUER\":\"<https://test.us.auth0.com\",\"CLIENT_ID_NATIVE\":\"GHJF....FnM\"}">
}]
```

## Step 6: Perform the Provisioning

Perform the provisioning secrets into AWS Secrets Manager by using the code below:

```
mpagen secret -i payload.json push
```

> 🚧 Warning:
>
> If a secret already exists provide `mpagen` with `--overwrite` flag to overwrite the value.

## Step 7: Upload Common and Node Configuration Files to S3 Buckets

Upload the configuration files to S3 buckets using the code below:

```
aws s3 cp common.conf s3://nitro-mpa/
aws s3 cp node0.conf s3://nitro-mpa/
aws s3 cp node1.conf s3://nitro-mpa/
aws s3 cp node2.conf s3://nitro-mpa/
aws s3 cp keyfile.enc s3://nitro-mpa/
```

Once the above steps are performed, the admins of each MPA node can launch their respective nitro-aware MPA node.

<Support />

<br/>