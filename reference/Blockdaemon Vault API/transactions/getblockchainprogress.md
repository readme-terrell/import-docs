---
title: Get the Blockchain Progress
excerpt: >-
  Get the Blockchain Progress, meaning the blockchains current block height, and
  what the highest block we have seen is. With this endpoint we can see if we
  are behind the current block
api:
  file: blockdaemon-wallet-api.json
  operationId: getBlockchainProgress
deprecated: false
hidden: false
metadata:
  title: Get the Blockchain Progress
  description: >-
    Unlock the power of Blockdaemon API with our comprehensive reference
    documentation. Explore code snippets, examples, and unleash seamless
    integration possibilities for your digital asset management.
  image: https://files.readme.io/528a87e-image_3.png
  robots: index
next:
  description: ''
---
> 🚧 Warning:
>
> The endpoint supports only `BTC`, `ETH`, and `WND` cryptocurrencies. `SOL` is not currently supported. To handle `ERC20` tokens, please utilize `ETH` since it operates on the same chain.

> 📘 Note:
>
> This endpoint can be used to determine if we are behind the current block.
