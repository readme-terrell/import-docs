---
title: Set Exchange Rate of an Asset
excerpt: >-
  Sets the exchange rate of asset specified by asset.The Rate should be set in
  USD. You can either set a fixed rate or set a range the rate is allowed to
  move in. If the range is set, the rate will be set by querying 3'rd parties
  and used so long they are in the given range. The exchange rate can only be
  set on assets with "Status" = "Success"
api:
  file: blockdaemon-wallet-api.json
  operationId: setExchangeRate
deprecated: false
hidden: false
metadata:
  title: Set Exchange Rate of An Asset
  description: >-
    Unlock the power of Blockdaemon API with our comprehensive reference
    documentation. Explore code snippets, examples, and unleash seamless
    integration possibilities for your digital asset management.
  image: https://files.readme.io/068091b-image_3.png
  robots: index
next:
  description: ''
---
> 📘 Note:
>
> * The Rate should be set in USD.
> * You have the option to either set a fixed rate or a rate range.
> * This endpoint operates synchronously, so you'll need to wait for the API response before proceeding with any other tasks in the wallet.
