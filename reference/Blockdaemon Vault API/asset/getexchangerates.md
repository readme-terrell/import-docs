---
title: Get a List of Assets and Their Exchange Rate
excerpt: >-
  Retrieves a list of all assets and their respective exchange rate. The list is
  in descending order based on the USDRate. If the asset does not have an
  exchange rate, USDRate will be set to null. If the asset has a pending
  exchange rate update the PendingUSDRate field will be set, if not it will be
  null
api:
  file: blockdaemon-wallet-api.json
  operationId: getExchangeRates
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---