---
title: Get the Transfer Details
excerpt: >-
  It will always return a list of all Assets. If the Asset Parameter is set, it
  will also return AssetDetails, where different data related to the asset can
  be found. If the add_vault parameter is also set, the AssetDetails will
  contain the vault. If the exclude_empty parameter is also set, only Assets
  with currency will be returned.
api:
  file: blockdaemon-wallet-api.json
  operationId: GetTransferDetails
deprecated: false
hidden: false
metadata:
  title: Get the Data Needed to Make Transfers
  description: >-
    Unlock the power of Blockdaemon API with our comprehensive reference
    documentation. Explore code snippets, examples, and unleash seamless
    integration possibilities for your digital asset management.
  image: https://files.readme.io/9c79dfb-image_3.png
  robots: index
next:
  description: ''
---
> 📘 Note:
>
> * If the Asset Parameter is set, it will also return `AssetDetails`.
> * If the `add_vault` parameter is also set, the AssetDetails will contain the vault.
