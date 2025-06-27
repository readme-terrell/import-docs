---
title: Add an Asset to a Vault
excerpt: >-
  Adds an asset of type 'Asset' to the vault specified by 'VaultId'. A vault can
  only contain a single asset of each asset type.
api:
  file: blockdaemon-wallet-api.json
  operationId: addAsset
deprecated: false
hidden: false
metadata:
  title: Add an Asset to a Vault
  description: >-
    Unlock the power of Blockdaemon API with our comprehensive reference
    documentation. Explore code snippets, examples, and unleash seamless
    integration possibilities for your digital asset management.
  image: https://files.readme.io/3752bf8-image_3.png
  robots: index
next:
  description: ''
---
> 📘 Note:
>
> * A vault can only contain a single asset of each asset type.
> * This endpoint operates synchronously if the primary address of an ERC-20 token is already created. However, if no primary address is associated with an ERC-20 token, this endpoint operates asynchronously.
