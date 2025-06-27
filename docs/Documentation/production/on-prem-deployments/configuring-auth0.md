---
title: Auth0 Configuration
excerpt: ✔️ Configuring Auth0 for wallet and approver application!
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
This is a prerequisite configuration before you deploy your online wallet. In this guide, we will walk you through the steps to configure Auth0 for your wallet and approver application. Auth0 provides a comprehensive identity platform that will enable secure authentication and authorization for your applications.

## Prerequisites

Before you begin, make sure you have the following prerequisites in place:

* An Auth0 account
* Access to the Auth0 Management Dashboard

## Step 1: Create Required Resources

To configure Auth0 for your wallet and approver application, you need to create the following resources in Auth0:

1. **Single Page Application (SPA) Resource**

   * This resource will represent your wallet application, which typically runs in a web browser.
   * To create an SPA resource, follow these steps:
     * Log in to the Auth0 Management Dashboard.
     * Go to the **"Applications"** section.
     * Click on the **"Create Application"** button.
     * Choose the **"Single Page Application"** option.
     * Provide a name for your application (e.g., "Wallet App").
     * Click on the **"Create"** button to create the SPA resource.

2. **Native Application Resource**

   * This resource will represent your approver application, which runs natively on a device (e.g., mobile or desktop).
   * To create a Native application resource, follow these steps:
     * Log in to the Auth0 Management Dashboard.
     * Go to the **"Applications"** section.
     * Click on the **"Create Application"** button.
     * Choose the **"Native"** option.
     * Provide a name for your application (e.g., "Approver App").
     * Click on the **"Create"** button to create the Native application resource.

3. **API Resource**
   * This resource will represent the API that your applications will communicate with.
   * To create an API resource, follow these steps:
     * Log in to the Auth0 Management Dashboard.
     * Go to the **"APIs"** section.
     * Click on the **"Create API"** button.
     * Provide a name for your API (e.g., "Wallet API").
     * Set the `Identifier` to a unique identifier for your API (e.g., "[https://wallet-api/"](https://wallet-api/")).
     * Click on the **"Create"** button to create the API resource.

## Step 2: Configure Application Settings

Once you have created the required resources, you need to configure the settings for each application.

### Configuring Wallet Application (SPA)

1. Navigate to the **Applications** section in the Auth0 Management Dashboard.
2. Select your wallet application (e.g., "Wallet App").
3. In the application **Setting** tab, configure the following:
   * Under **Application URIs**
     * Add `Allowed Callback URLs`, `Allowed Logout URLs`, and `Allowed Web Origins`. These will be the full URL of your wallet front-end. (e.g., "[https://wallet.yourcompany.com"](https://wallet.yourcompany.com"))
   * Under **Cross-Origin Authentication**
     * Enable `Allow Cross-Origin Authentication`
     * Under `Allowed Origins (CORS)` add the full URL of your wallet front-end yet again. (e.g., "[https://wallet.yourcompany.com"](https://wallet.yourcompany.com"))
   * Under **ID Token**
     * Set `ID Token Expiration` to `36000` seconds.
   * Under **Refresh Token Rotation**
     * Enable `Rotation`
     * Set `Reuse Interval` to `0` seconds.
   * Under **Refresh Token Expiration**
     * Enable `Absolute Expiration`
     * Set `Absolute Lifetime` to `2592000`
     * Enable `Inactivity Expiration`
     * Set `Inactivity Lifetime` to `1296000`
   * Under **Advanced Settings**
     * In the **Oauth** tab, make sure `JSON Web Token Signature Algorithm` in  is set to `RS256`
     * Enable the necessary **Grant Types**, which include `Implicit`, `Authorization Code`, and `Refresh Token`
   * Set the **Token Endpoint Authentication Method** according to your security needs.
   * Configure any additional settings specific to your application.
4. Save the changes.

### Configuring Approver Application (Native)

1. Navigate to the "Applications" section in the Auth0 Management Dashboard.
2. Select your approver application (e.g., "Approver App").
3. In the application **Settings** tab, configure the following:
   * Under **Application URIs**
     * Add the appropriate `Allowed Callback URLs` and `Allowed Logout URLs`, these will match each other. For example, for iOS approver app: "com.blockdaemon.reactnativeapproverapp.auth0://\<tenant\_url>/ios/com.blockdaemon.reactnativeapproverapp/callback" **OR** for Android: "com.blockdaemon.reactnativeapproverapp.auth0://\<tenant\_url>/android/com.blockdaemon.reactnativeapproverapp/callback".
   * Under **Cross-Origin** Authentication
     * Enable `Allow Cross-Origin Authentication`
   * Under **ID Token**
     * Set `ID Token Expiration` to `36000`
   * Under **Refresh Token Rotation**
     * Disable `Rotation`
   * Under **Refresh Token Expiration**
     * Disable `Absolute Expiration` and `Inactivity Expiration`
   * Under **Advanced Settings**
     * In the **Oauth** tab, make sure `JSON Web Token Signature Algorithm` in  is set to `RS256`
     * Enable the necessary **Grant Types**, which include `Implicit`, `Authorization Code`, and `Refresh Token`
4. Save the changes.

### Configuring your API

1. Navigate to **APIs** section in the Auth0 Management Dashboard
2. Select your API (e.g, "Wallet API")
3. In the API **Settings** tab, configure the following
   * Under **Access Settings**
     * Enable `Allow Offline Access`
4. Save the changes.

## Step 3: Finding values for Wallet and Approver Apps.

1. Navigate to the **Applications** section in the Auth0 Management Dashboard and select your wallet application (e.g., "Wallet App").
   * Under **Settings** you'll find your `Client ID` value.
   * Please take note of these values since you'll need these to set up your Wallet App.
2. Navigate to the "Applications" section in the Auth0 Management Dashboard and select your approver application (e.g., "Approver App").
   * Under **Settings** you'll find your `Client ID` value.
   * Take note of these values, you'll need these to set up your Approver App.
3. Navigate to the **APIs** second in the Auth0 Management Dashboard and select your API (e.g., "Wallet API")
   * Make note of the `API Audience` as you'll need this value when setting up your Wallet App.
4. Click on **Applications** > Your single page application that you made > Under **Settings** tab, look for the **Domain**, and that will be your ISSUER.

<Support />
