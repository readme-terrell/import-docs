---
title: MacOS System
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
This article will walk you through installing the cold wallet onto a MacOS-based machine.

## Prerequisites

* Docker.
* Docker Compose.
* Ensure you have the permissions to run commands as root.

## Step 1: Generate Emergency Recover Service (ERS) Certificate Key Pair

In an emergency, you must recover the cold wallet's master key shares in order to derive all other private keys within the wallet. The protect the cold wallet master key share contents, the backup is encrypted with an RSA public key created below. For more information, see [Back-up and Emergency Recovery](https://vault.docs.blockdaemon.com/docs/back-up-and-emergency-recovery).

> 📘 Note:
>
> The person who holds the ERS private key and the backup recovery material can retrieve the cold wallet master key.

1. On a separate machine from the cold wallet, open the terminal and run the following command to generate a private key. This private key must be stored securely offline.

```shell
openssl genrsa -out private-key.pem 3072
```

2. Then, enter the following command to generate the associated public key in base64 encoded format:

```shell
openssl rsa -in private-key.pem -pubout -outform DER | base64
```

<Image align="center" src="https://files.readme.io/f7931b4-image.png" />

3. Copy the base64 encoded public key string to the cold wallet machine via SD card or similar medium. This will be needed during the installation, and will be used to encrypt the MPC private key shares during the ERS backup process.

## Step 2: Download and Extract the Installation Package

Download the installer by following the steps below:

1. Download the installation package using the link provided by your sales associate or technical representative.
2. Copy the installation package to your preferred removable storage medium, transfer it to the cold wallet machine, and copy the file to a temporary folder where it can be extracted.
3. Open your terminal in the temporary folder and extract the contents using the following command:

```shell
tar -xvf coldwallet.tar
```

## Step 3: Permit Execution of the Installation Binary

To allow MacOS to execute the installer, follow the steps below:

> 📘 Note:
>
> For Mac, it's necessary to digitally sign software binaries with an Apple account. We're currently working on this.

1. Navigate to the directory using the graphical user interface by entering the following command in your terminal:

```shell
open .
```

2. Doube-click the file `coldwallet-cli-darwin` to execute it. A warning will appear stating *"macOS cannot verify the developer of “coldwallet-cli-darwin”. Are you sure you want to open it?"*
3. Click Open to agree to overriding the system verification.
4. If a new terminal window opens after executing the binary, close it.
5. Return to your usual terminal where you've been working within the cold-wallet folder.

## Step 4: Run the Cold Wallet Install

To run the installer, follow the steps below:

1. Set the APP\_MODE type to the "docker" and run the install using the following command:

```shell
APP_MODE=docker ./coldwallet-cli-darwin init
```

2. The installer allows you to set optional custom configurations, such as where your application and configs will be placed. You **must** however overwrite the `verysecret` entries.

![](https://files.readme.io/d679b25-image.png)

4. You should set all the Cold Wallet details as follows:

| Detail                      | Description                                                                                                               |
| :-------------------------- | :------------------------------------------------------------------------------------------------------------------------ |
| Company Name                | Enter your company name.                                                                                                  |
| Installation Absolute Path  | Enter the path where the cold wallet application will be installed. For docker, this will have your `docker-compose.yml`. |
| Configuration Absolute Path | Enter the path to hold all your node configurations if you want to edit them.                                             |
| Node Encryption Keys        | These values will be used as symmetric encryption keys to protect the nodes' database content at rest.                    |
| Backup Directory            | Enter the path where the database will be periodically backed up.                                                         |
| ERS Public Key              | Enter the base64 encoded ERS public key string created in Step 1.                                                         |

## Step 5: Run the Cold Wallet

To run the cold wallet, follow the steps below:

1. Navigate to the cold wallet app directory specified during install. This contains the `docker-compose.yml` file.
2. Start the cold wallet by using the following command:

```shell
docker compose up -d
```

3. Navigate to `http://localhost:8902` to see your cold wallet UI.

<Image align="center" src="https://files.readme.io/88b96f0-b179faba-1a95-421d-8f6f-51776a706b51.png" />

4. To stop the cold wallet, use the following command:

```shell
docker compose stop
```

<Support />
