---
title: System User
excerpt: 🧑‍🏫Find out how to create the user responsible for operation requests
deprecated: false
hidden: false
metadata:
  title: System User
  description: >-
    Learn about the crucial role of the system user in Blockdaemon Wallet.
    Discover how system users approve or deny operation requests, ensuring
    secure and controlled management of your digital assets.
  image: https://files.readme.io/dd914cd-image_3.png
  robots: index
next:
  description: ''
---
# Overview

The system user is the one who may approve or deny operation requests. Most system users are already set up before the wallet launches. However, you can add or enable a system user through the Institutional Vault's Settings menu. Creating a System User allows an Admin user to provide a Public Key to request the wallet on behalf of an already registered System User.

# Create a System User

To enable the system user, follow the steps below:

1. Click **Settings** on the main navigation menu.

<Image align="center" src="https://files.readme.io/568e4cf60b23ec1041a1f0e130fb23634d1b18e9505e8a531e21e66d152081b8-Group_18_-_2024-09-10T140320.704.png" />

2. Select the **System Users** tab.

<Image align="center" src="https://files.readme.io/a81a65dbed06e92d6afc9b3059fd562f817631417fe089b6b2c05eb7c3f8dfff-Group_18_-_2024-09-11T122937.957.png" />

3. Click **Create System Users.**

<Image align="center" src="https://files.readme.io/198876d12f14d44b33322b6e81c359ef2cd5a64c1652ceb76b28bdf1ed4583ed-Group_18_-_2024-09-11T122948.391.png" />

4. Fill in all the fields.

| Field     | Description                       |
| :-------- | :-------------------------------- |
| Name      | The name of the system user.      |
| Role      | The name of the system user.      |
| Confirmer | The confirmer of the system user. |

> 📘 Note:
>
> A System User with an Admin role cannot have a confirmer with a lower privileges, such as MarketOps.

<Image align="center" src="https://files.readme.io/15ae900f6e61231d6b25ecebbc341640893f86d123751dffa9c3067ae704749a-Group_18_-_2024-09-11T123051.259.png" />

5. Click **Create** to confirm the operation.

<Image align="center" src="https://files.readme.io/67d4002fd1a98231116eb39df41ba3ff04242857c6afa161d1595a6299e1add9-Group_18_-_2024-09-11T123036.788.png" />

The newly created user will appear in the system user list with an associated API key. This API key and the secret key generated in the above steps are required to create and send API requests to the wallet.

# Delete a System User

To delete a system user, follow the steps below:

1. Click **Settings** on the main navigation menu.

<Image align="center" src="https://files.readme.io/0df9640b7d1fc24db9657158988fe2361c99a30628a2e724d057ee50eacf67d9-Group_18_-_2024-09-10T140320.704.png" />

2. Select the **System Users** tab.

<Image align="center" src="https://files.readme.io/413d31acd1f55303b5e984a3beee681a13c0990faaab6c23c2b2daae07501e4f-Group_18_-_2024-09-11T122937.957.png" />

3. Select the **system user** you want to delete and click the **Overflow icon**.

<Image align="center" src="https://files.readme.io/cc137de0d80b570a28842a91ea66c01ee131e548bf537493ec278898ffb82a0c-Group_18_-_2024-09-11T123928.517.png" />

4. Select **Delete** to confirm the operation.

<Image align="center" src="https://files.readme.io/fd21a4cb2d9a671b1f9a03ef228a03251bee000d5e1395c834271f591d7bfe83-Group_18_-_2024-09-11T123958.020.png" />

> 📘 Note:
>
> Creating and deleting System users have no bearing on the position of system users inside the MPA (policy engine). Only the wallet service is responsible for keeping track of who sends API calls. The policy engine is concerned with the entity that validates or denies requests, and the information linked to that entity is specified in the config file. It cannot be modified via the wallet's user interface. Refer to the MPC Wallet Architecture for further details.

<Support />
