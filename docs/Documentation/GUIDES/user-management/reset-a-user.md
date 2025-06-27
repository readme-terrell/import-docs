---
title: Reset a User
excerpt: 🔁Reset a user to register new Policy Engine
deprecated: false
hidden: false
metadata:
  title: Reset a User
  description: >-
    Reset a user in Blockdaemon Wallet to enable registration of a new Public
    Key (PK) with the Policy Engine. Enhance security and streamline user
    management effortlessly.
  image: https://files.readme.io/39e6fe8-image_3.png
  robots: index
next:
  description: ''
---
# Overview

Reset is a feature that allows you to reset a specific user so they can register a new PK with the Policy Engine. This suggests they wish to utilize a new SK. This frequently occurs when people lose their phone, which has the Institutional Vault Approver. This action deletes the PK for the user who wishes to be reset and prepares to register a new PK for the same user. 

> 📘 Note:
>
> The initiator of the operation needs to confirm this operation on their Institutional Vault Approver app, and according to the administrative policies of the wallet, additional approvals may be required before the operation is completed. If any approval request is rejected, the operation will fail.

> 📘 Note:
>
> * Only an administrator can perform this operation.
> * This operation will not remove the user from any group.

# How to Reset a User

To reset a user from your wallet, follow the steps below:

1. Click the **Settings** menu on the main navigation.

<Image align="center" src="https://files.readme.io/685ced1d38a8fe38dd6f3a03d7b846d37ec8908008a07732449997ecc7745331-Group_18_-_2024-09-10T140320.704.png" />

2. Select the user you want to reset under the Users tab.
3. Click the **Overflow** icon next to the user.

<Image align="center" src="https://files.readme.io/f7de05e0f2b5f9f38aaf261f40b827ae9f2a6d62ce6885c2f84a16141e140bfe-Group_18_-_2024-09-10T142424.702.png" />

4. Select **Reset User**.

<Image align="center" src="https://files.readme.io/9adb425e15503944c0fb46b2b79ba63014d5003d405abcd96d2ff018cdcc6632-Group_18_-_2024-09-10T143200.840.png" />

## Reset a User Who Has Lost Their Phone

This operation can also reset a user whose phone was lost since they cannot add themselves to the system. They require assistance from an administrator to reset and re-register their wallet account. This is the reset procedure for a user who has lost their phone:

1. An Admin User resets the user with the lost phone.
2. Then the admin confirms the operation on their approver app.
3. The user then installs the app on their new phone and registers a new PK with the MPA so they can log in back to the wallet.

<Support />
