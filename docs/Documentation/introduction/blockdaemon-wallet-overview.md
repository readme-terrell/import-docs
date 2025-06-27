---
title: Institutional Vault Overview
excerpt: 👀 Find out what Institutional Vault is and how it works
deprecated: false
hidden: false
metadata:
  title: Blockdaemon Wallet Overview
  description: >-
    Explore the user-friendly and secure Blockdaemon Wallet, a comprehensive
    blockchain wallet solution. Discover its features, benefits, and multi-chain
    support. Experience frictionless transactions, token swaps, and portfolio
    tracking. Empower yourself in the decentralized landscape with ease.
  image: https://files.readme.io/e18941b-image_3.png
  robots: index
next:
  description: ''
---
Institutional Vault streamlines crypto operations and treasury management for institutional banks, stock brokers, and large institutional companies. The most reliable blockchain infrastructure backs it. With a single integration, the Institutional Vault assists the institution in managing its digital assets.

You can also check out our video guide on how to onboard the Institutional Vault here:

<Embed url="https://www.youtube.com/watch?v=tWcn607jA5s" title="Blockdaemon Institutional Vault Demo" favicon="https://www.youtube.com/favicon.ico" image="https://i.ytimg.com/vi/tWcn607jA5s/hqdefault.jpg" provider="youtube.com" href="https://www.youtube.com/watch?v=tWcn607jA5s" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FtWcn607jA5s%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DtWcn607jA5s%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FtWcn607jA5s%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

## 1\. Institutional Vault Features

Institutional Vault offers five important features that make it suited for numerous industries, including traditional Web2 companies, crypto-accepting payment companies and custodians, and Web3 or crypto foundations.

<Image align="center" width="650px" src="https://files.readme.io/b9c7a64-Asset_15300x.png" />

## 2\. Institutional Vault Environments

Institutional Vault offers three different environments that can be used to demonstrate the experience to prospective customers or users.

<Image align="center" width="550px" src="https://files.readme.io/44de670-Asset_8300x_4.png" />

### 2.1. Demo Sandbox

Our team leverages this environment for product demonstrations, allowing you to evaluate the wallet without needing personal installation. To obtain access to the Demo sandbox, please get in touch with us at **[support@blockdaemon.com](mailto:support@blockdaemon.com)**. 

### 2.2. Self-Installed Sandbox Environment - Testnet

This option allows you to fully experience and evaluate the complete feature set and configuration process of the Institutional Vault while also assessing the product's security. The sandbox environment is not a limited version of the wallet. Instead, it offers comprehensive functionality for testnet network(s) and enables users to engage in the entire process of setting up and managing the wallet.

> 📘 **Note**:
>
> This environment is not intended for production.

### 2.3. Self-Installed Production Environment - Mainnet

The Production Environment of the Institutional Vault refers to the fully operational and functional state of the wallet specifically designed for utilization on mainnet network(s). It serves as the live and active environment where users can engage with the Institutional Vault's complete set of features and capabilities in a production-ready setting.

## 3\. Assets Support

The term "**asset**" in this context refers to the tokens or native tokens of each cryptocurrency network. Institutional Vault supports numerous cryptocurrency networks that have their own tokens, including the following networks:

<Image align="center" width="550px" src="https://files.readme.io/1a8b538-Asset_71300x_1.png" />

Institutional Vault supports the aforementioned networks and enables its users to store, see, transact, and withdraw their tokens.

## 4\. Institutional Vault Policies

Institutional Vault applies a set of principles to a specific set of operations, including both transaction and staking operations. The policy framework guides the decision-making process to determine whether an operation should be approved, rejected, or completed.

> 📘 Note:
>
> For more details regarding Institutional Vault Policy, please see [here](https://vault.docs.blockdaemon.com/docs/all-about-policies).

### 4.1. Three Types of Policies

Institutional Vault divides the policies into three categories based on the wallet configuration:

<Image align="center" width="650px" src="https://files.readme.io/03f5e35-84abe2d-Asset_3300x_5.png" />

### 4.1.1. Administration Policy

Administration Policy is a collection of rules governing all wallet operations. This policy specifies the behaviour of a wallet for every operation performed on it. This policy is only modifiable by users with the Admin role. This policy addresses user management, group management, and the modification of the transfer policy.

### 4.1.2. Transfer Policy

A transfer policy is a list of rules for making transfers or transactions. It is only modifiable via the administration policy.

> 📘 **Note**:
>
> Launching a wallet with default transfer policies or without transfer policies is possible.

### 4.1.3. Staking Policy

A staking policy serves as a guidebook for how staking functions in the Institutional Vault. This policy provides clear directions and settings for overseeing the asset staking process, ensuring its smooth and secure operation.

## 5\. User Management

User Management refers to the process of defining and controlling access within the Institutional Vault system. It involves categorizing users into [different types](https://vault.docs.blockdaemon.com/docs/user-types-and-privileges) and [ assigning them roles](https://vault.docs.blockdaemon.com/docs/register-user#how-to-register-a-user).

### 5.1. User Types

User types categorize users based on access and interaction with the wallet:

* **Users (Human Users)**: A non-administrator with general access. They can access features but cannot modify policies or settings. Each user must belong to at least one group. If not explicitly assigned, they default to the "all-approvers" group.
* **System Users**: Programmatic users created for automated access. They are managed by admins, can have roles, and use API keys for authentication in API requests.

> 👍 Tips
>
> Both types of users can be assigned the same roles, meaning they could have the same privileges in terms of what actions they are allowed to perform.

### 5.2. Roles

Roles define what a user can do within the wallet system. Regardless of whether the user is a human or system user, roles define the specific actions or permissions granted to that user. Available roles are:

| Roles     | Description                                                                                                                                                                  |
| :-------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MarketOps | A role for users who need more permissions than a standard user but fewer than an admin. They manage trading operations, transfers, and asset monitoring.                    |
| Viewer    | A read-only role that allows users to view transaction history and export data without making any changes to the system.                                                     |
| Admin     | The highest level of access. Admin users have full control over the wallet system, including creating and managing groups, assigning roles, and configuring wallet policies. |

> 📘 Note:
>
> For more information regarding the privileges of each roles, please see [here](https://vault.docs.blockdaemon.com/docs/user-types-and-privileges).

## 6\. Approval Process User Role

Institutional Vault is a secure platform that allows users to manage their cryptocurrencies easily. The platform includes features such as transaction intents, policies, and approval rules, which help ensure transaction security and integrity. The approver and the confirmer are two distinct roles in the transaction approval process.

### 6.1. Approver

The approver is any user granted permission to approve transactions through the approval app. These users are typically part of a group quorum defined by the wallet's policy and related rules. The approver is responsible for evaluating the transaction request and deciding whether or not to approve it. This role is critical for preventing fraud and unauthorized access to user funds.

### 6.2. Confirmer

The confirmer is typically the user who initiated the transaction intent and is responsible for initiating the confirmation process by sending a confirmation request to the approval app. 

By separating the confirmer and approver roles and requiring multiple approvals for certain transactions, Institutional Vault ensures that all transactions are securely executed.

## 7\. Supported Protocols and Networks

Institutional Vault supports the following protocols and networks:

| Protocols                                             | Networks                 |
| :---------------------------------------------------- | :----------------------- |
| Bitcoin                                               | Mainnet/Testnet          |
| Ethereum (incl. ERC-20, ERC-1404 and ERC-3643 tokens) | Mainnet/Holesky Testnets |
| Polkadot                                              | Mainnet/Westend          |
| Polygon (incl. ERC-20, ERC-1404 and ERC-3643 tokens)  | Mainnet/Amoy             |
| Solana                                                | Mainnet/Testnet          |

## 8\. Supported Confidential Computing Configurations

<HTMLBlock>{`
<style type="text/css">
  
    .narrower-table {
      font-size: 85%;
    }
    
    .markdown-body table.narrower-table th, .markdown-body table.narrower-table td {
      padding-left: 9px;
      padding-right: 9px;
    }
    
    .markdown-body table.narrower-table th {
     
    }
    
    .markdown-body table.narrower-table td {
    
    }
  
    
  </style>
  
  <table class="narrower-table">
      <thead>
          <tr>
              <th style="text-align:left">Provider</th>
              <th style="text-align:left">Technology</th>
              <th style="text-align:left">Signed Software Images</th>
              <th style="text-align:left">Full Remote Attestation for Secrets Injection through KMS</th>
              <th style="text-align:left">Institutional Vault Supported</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td style="text-align:left">AWS</td>
              <td style="text-align:left">Nitro Enclaves</td>
          
              <td style="text-align:left">Yes</td>
              <td style="text-align:left">Yes</td>
              <td style="text-align:left", bgcolor="#90EE90"><strong>Yes</strong></td>
          </tr>
          <tr>
              <td style="text-align:left">Azure</td>
              <td style="text-align:left">AMD SEV</td>
              
              <td style="text-align:left">No</td>
              <td style="text-align:left">No</td>
              <td style="text-align:left", bgcolor="#90EE90"><strong>Yes</strong></td>
          </tr>
      </tbody>
  </table>
`}</HTMLBlock>

<Support />