---
title: Quick Start - Institutional Vault APIs
excerpt: 👋 Welcome! Get started with the Institutional Vault API.
deprecated: false
hidden: false
metadata:
  title: Quick Start - Blockdaemon Wallet
  description: >-
    Learn how to obtain an API key in Blockdaemon Wallet by creating a system
    user. Explore the API reference and seamlessly integrate wallet
    functionality into your applications.
  image: https://files.readme.io/6b48730-image_3.png
  robots: index
next:
  description: ''
---
This guide will walk you through the steps to get the Institutional Vault's API Key and use it in the API reference documents.

Follow the steps below, and you'll be up and running with the Institutional Vault quickly!

# 1. Log In to the Institutional Vault

Navigate to the Institutional Vault [here](https://qa.staging.blockdaemon-wallet.com/). Log in using your organization's identity provider [here](https://mpa-demo-stg.us.auth0.com/u/login?state=hKFo2SBoek1OZEFwMEw3TndmcUNSQkMwaFZwLUdFejZRYlRkVKFur3VuaXZlcnNhbC1sb2dpbqN0aWTZIHJmbEtlV0RvOFRhSVFFMF84Q2c1MFBLMFN0N2gwX1Fzo2NpZNkgc3JEM1ZpZXJSemxDcDhDeTBRbTM2ZUxXSXA2UjN6ekw). 

> 📘 Note:
>
> If you have not signed up for the Institutional Vault account, please sign up [here](https://mpa-demo-stg.us.auth0.com/u/signup?state=hKFo2SBoek1OZEFwMEw3TndmcUNSQkMwaFZwLUdFejZRYlRkVKFur3VuaXZlcnNhbC1sb2dpbqN0aWTZIHJmbEtlV0RvOFRhSVFFMF84Q2c1MFBLMFN0N2gwX1Fzo2NpZNkgc3JEM1ZpZXJSemxDcDhDeTBRbTM2ZUxXSXA2UjN6ekw).

# 2. Onboarding the Institutional Vault

Set up your Institutional Vault environment by installing the Institutional Vault approver app from the iOS app store and setting up the wallet environment. Follow the steps listed [here](https://vault.docs.blockdaemon.com/docs/onboarding-the-wallet) to onboard your Institutional Vault properly.

# 3. Get Wallet's API Key

You can get your Wallet's API Key by following the steps below:

* Log in to Institutional Wallet App UI.
* Go to **Settings** .

![](https://files.readme.io/9f0774e-3c163c9-Group_14_1.png)

* Click the **Create System Users** on the top right side of your screen.

![](https://files.readme.io/698122a-Group_18_44.png)

* Specify the System User's **Name**, **Role**, and **Confirmer**.

![](https://files.readme.io/f693f08-Group_18_45.png)

* Click **Create**.

![](https://files.readme.io/d5891f5-Group_18_47.png)

* Approve the operation on your **Institutional Vault Approver** application.
* This list will include the newly created System User and the API Key, which you can use to test the wallet's API reference.

![](https://files.readme.io/cec77be-Group_18_48.png)

> 📘 Note:
>
> Ensure that your account is the system user's confirmer.

# 4. Try Calling the API

Let's try calling the Institutional Vault API from our API reference documentation:

1. Navigate to the **API Reference** > Select a specific endpoint you want to try.

![](https://files.readme.io/67e0ae0-Group_18_49.png)

2. Paste your **API Key** in the **Authentication** field as a **Header**.

![](https://files.readme.io/951349b-Group_18_50.png)

3. Specify your **Base Url** in the **URL** field.

![](https://files.readme.io/f2d9764-Group_18_51.png)

4. Specify the required **path or query parameters**.

![](https://files.readme.io/d5362fe-Group_18_52.png)

5. Click on the **"Try it"** button.

![](https://files.readme.io/bc685df-Group_18_54.png)

6. Receive a **Response**.

![](https://files.readme.io/a369f1f-Group_18_55.png)

# 5. Integrate the API Into Your Application

Once you have tested the API and are familiar with its endpoints, you can integrate it into your application, use it to streamline your cryptocurrency operations, manage your cryptocurrency assets, transfer assets, and interact with major protocols through their native APIs.
