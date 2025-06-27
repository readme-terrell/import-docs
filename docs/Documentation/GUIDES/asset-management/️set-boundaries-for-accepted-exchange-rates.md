---
title: Set Boundaries for Accepted Exchange Rates
excerpt: ✍️ Set a range of acceptable exchange rates or a set rate
deprecated: false
hidden: false
metadata:
  title: Set Boundaries for Accepted Exchange Rates
  description: >-
    Set boundaries for accepted exchange rates with Blockdaemon Wallet. Explore
    how to define and manage rate limits for seamless digital asset
    transactions.
  image: https://files.readme.io/3d6d6b8-image_3.png
  robots: index
next:
  description: ''
---
# Overview

Transaction policies across all assets are established in US dollars. The current exchange rate for each asset is sourced from reputable third-party providers. 

As a security measure, it's essential to specify an acceptable range of exchange rates or a fixed rate. As long as third-party services provide rates falling within this defined acceptable range, transaction policies will utilize these rates to determine the necessary authorization level. The Institutional Vault will prevent the corresponding transaction from proceeding if the reported rates surpass your acceptable range. In cases where the rate is set as fixed, it will be applied regardless of the actual market value of the asset.

# Edit the Boundaries for the Exchange Rates

Via the online wallet's settings menu, an administrator may set boundaries for each asset by following the steps below:

1. Go to the **Settings** menu.

<Image align="center" src="https://files.readme.io/01c09c43d4a1ae2ff241280a00d88cd884b1a64045a535fd14e0fe9f2fe5d249-Group_18_-_2024-09-10T140320.704.png" />

2. Click the **Assets** section of the settings menu. In the asset section, you can see all assets available in your wallet and their exchange rate boundaries.

<Image align="center" src="https://files.readme.io/af24fb2a50b863e485a2384069eb2707caec889e10607c2c2124e9584850a80e-Group_18_-_2024-09-12T134943.002.png" />

3. Click the **Edit** button to edit exchange rates.

<Image align="center" src="https://files.readme.io/a51cbc34e4a82e75175f056a5515a43be5a95d1b6eec152f404b1e25d5881ae4-Group_18_-_2024-09-12T135110.286.png" />

4. You can choose between **Fixed** and **Ranged** rates.

<Image align="center" src="https://files.readme.io/533dea68ab38b61f75390de175a2d230e9c744434e967db5d6955e0334fb006e-Group_18_-_2024-09-12T140100.279.png" />

5. Click **Submit** to confirm to change the exchange rates.

<Image align="center" src="https://files.readme.io/9f908a919617f6ec36aab4d10c5fb4a9a61519722cffbf08fcf726f14aa333fb-Group_18_-_2024-09-12T140112.757.png" />

6. Confirm the request on your **Institutional Vault Approver**.
7. When an operation has been confirmed, it is evaluated for approval requirements. The relevant users are notified through the Institutional Vault Approver if approval is needed.
8. When the operation has cleared approval, the exchange rates are successfully updated.

<Support />
