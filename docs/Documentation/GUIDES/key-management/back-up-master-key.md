---
title: Back Up Master Key
excerpt: 🔐 Back up your Institutional Vault master key
deprecated: false
hidden: false
metadata:
  title: Back Up Master Key
  description: >-
    Securely back up your master key in Blockdaemon Wallet. Learn how to
    safeguard your digital assets by creating a reliable backup of your master
    key.
  image: https://files.readme.io/0e5f2fd-image_3.png
  robots: index
next:
  description: ''
---
# Overview

The Wallet Master Key shares are generated via multiparty computation or MPC. They are created when the Institutional Vault launches for the first time. All the other keys and addresses are derived from the Master Key shares. Institutional Vault employs the Emergency Recovery Service (ERS) to produce recovery material that can be used to retrieve the master key. To achieve this, you should generate a set of public and private keys. Configure the public key in the wallet's configuration file while securely storing the private key offline.

> 📘 Note:
>
> The person who holds both the private key and the backup recovery material can retrieve the master key.

ERS is also a multiparty computation that encrypts key shares on each policy node. For more information, see [Back-up and Emergency Recovery](https://vault.docs.blockdaemon.com/docs/back-up-and-emergency-recovery).

***

Before the wallet uses the master key to derive any keys, the recovery material must be downloaded. Therefore, the first user of the wallet is instructed to download the Backup Key, which is the current term used to reference the recovery material.

# How to Backup Master Key

To backup the master key, follow the steps below:

> 📘 Note:
>
> You can only perform the Backup Master Key operation once. It can only be done when you install and login for the first time.

1. Click the **Settings** button on the main navigation menu.

![](https://files.readme.io/0126772-small-Group_14_1.png)

2. Click the **Backup Key** button next to the **Freeze** on the top-right side of your screen.

![](https://files.readme.io/a57c5ac-Group_18_73.png)

3. Approve the operation on your **Institutional Vault Approver** application.
4. Your browser will download the backup key in **.JSON** format.

> 📘 Note:
>
> Additional approvals are required according to the wallet's administrative policies. For more information, please see [here](https://vault.docs.blockdaemon.com/docs/all-about-policies).

<Support />
