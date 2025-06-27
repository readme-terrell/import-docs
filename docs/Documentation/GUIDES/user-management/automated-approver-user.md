---
title: Automated Approver User
excerpt: 👩‍💻 Find out how to delegate the approval process to the server
deprecated: false
hidden: false
metadata:
  title: System Approver User
  description: Find out how to delegate the approval process to the server
  keywords:
    - system
    - approver
    - user
  robots: index
next:
  description: ''
---
# Overview

Users will still need to interact with the approver app to confirm operations, such as transfers or staking. However, the "approval" process can be delegated to the server. Once the HTTP approver server is configured, approval requests can be routed to it, allowing users to approve or reject requests programmatically.

# Prerequisites

The HTTP server must provide several parameters to allow its correct configuration in the wallet.

1. Signature verification key — the public key of the public-private key pair that the server uses to sign operations. It must be a 65-byte ECDSA public key encoded in base64. See an example code to generate the key pair [here](https://go.dev/play/p/EJklaWidze0).
2. TLS public key (optional) – The public key of the TLS certificate used for TLS authentication. See an example code of creating a self-signed TLS certificate and printing the TLS public key [here](https://go.dev/play/p/_GL1ZIlrVXM).
3. The automated approver HTTP server is to be added to the `wallet.yaml` configuration file. Example:

```
    automated_approvers:
      - signature_verification_key: "" // The key from Prerequisite step 1
        url: "" // The url of the automated approver HTTP server
        tls_public_key: "(Optional) the key from Prerequisite step 2"
```

> 📘 Note:
>
> Following this guide, it is likely the automated approver user and group will need to be approved using the mobile BD Approver app in accordance with the administrative policies preconfigured at installation.

# Create Automated Approver User

To create an automated approver user, follow the steps below:

1. Go to the **Settings** menu.

<Image align="center" src="https://files.readme.io/8e8c0510f69371261df0679b1e4367767859ce36f933efc5cc6be39b6a005fb5-Group_18_-_2024-09-10T140320.704.png" />

2. Within the Settings menu, under the **User** tab, select **Register User**.

<Image align="center" src="https://files.readme.io/590cf7c09b383bfdd3ba7b848de54a511b1a28014583cca10bfcb04dd07a34e5-Group_18_-_2024-09-10T142623.832.png" />

3. Fill out the name and the role fields.

> 📘 Note:
>
> Ensure that the Role of the user is **AutomatedApprover**.

<Image align="center" src="https://files.readme.io/67f772b1bb41755ab6d9c3fc4a33aa0e30453e3f2a8784d4490f52108e3f6b5c-Asset_7300x.png" />

4. The newly added use will have the “**Pending Onboarding**” status. To activate the user, we have to pair the user with a “**Signature verification key**.” 

> 📘 Note:
>
> The “**Signature verification key**” must be the same one in the config.

<Image align="center" src="https://files.readme.io/944b4b78f83662ef29dd7d6dcb321c1301e7f5487ebaae169924f0284b2c12bf-Asset_8300x.png" />

5. Insert the **Signature verification key/Public key**. Once the pairing is complete, the user’s status changes to active.

<Image align="center" src="https://files.readme.io/6e4bcb98aa86fbaddffc900fa592f20303c7c16015c903ccebfb40bc8f214d65-Asset_9300x.png" />

<Image align="center" src="https://files.readme.io/2ee11bcbe8264aa2fa6568fe5332cb771a6e22ca11b46751b69000d4e0f25cfd-Group_18_-_2024-11-13T085957.772.png" />

6. Create a new group and add the automated approver user to the group.

<Image align="center" src="https://files.readme.io/c37bf266ea49858289c920a9a6209148a34b334790e80774410e5cb608c5626a-Asset_10300x.png" />

7. Create a transfer policy requiring approval from the newly created group.

<Image align="center" src="https://files.readme.io/9a027c31967bd3fedc9875696cb42e0b4d96c7b43de4846fe834729ef132271f-Asset_11300x.png" />

<Support />
