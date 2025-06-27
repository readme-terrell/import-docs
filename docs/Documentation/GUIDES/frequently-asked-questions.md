---
title: Frequently Asked Questions
excerpt: ⁉️ Find Answers to your questions here!
deprecated: false
hidden: false
metadata:
  title: Frequently Asked Questions
  description: >-
    Find answers to frequently asked questions about Blockdaemon Wallet. Explore
    our comprehensive FAQ section to address common queries and gain insights
    into managing your digital assets.
  image: https://files.readme.io/440b05f-image_3.png
  robots: index
next:
  description: ''
---
<details>
  <summary><b>What are the different user types and permissions?</b></summary>
  <br/>

User types are assigned during wallet configuration and can also be updated after the initial setup.

**Admin user**: the highest level of permissions and authority over a wallet. An admin user can add or remove non-admin users, and modify policies.

**Non-admin user**: a standard user with limited capabilities. A non-admin user has access to all Institutional Vault features but can’t manage users or modify policies.

</details>

<details>
  <summary><b>What are the environments in which Institutional Wallet is available?</b></summary>
  <br/>
The institutional wallet is available in Demo Sandbox, Self-installed Sandbox, or Self-installed Production environments, as outlined below.

**Demo Sandbox**:\
Our team uses this environment to demonstrate the product and allows users to experience and evaluate the wallet without any local installation.

**Self-installed sandbox**:\
A replica of the production environment that allows users to go through the full process of setting up and maintaining the wallet. The self-installed sandbox environment provides comprehensive functionality in a scaled-down version of the production environment.

This allows your organization to experience the full feature set and configuration process and evaluate product security.

**Self-installed production environment**:\
An advanced, complete version of the sandbox environment. The production environment replicates the configuration process, capabilities, and features of the “live” Institutional Vault.

</details>

<details>
  <summary><b>How can I edit System Users?</b></summary>
  <br/>
System users can be easily enabled or disabled from the settings menu of the Institutional Wallet account.

1. [Sign in](https://vault.docs.blockdaemon.com/docs/sign-in) to your Institutional Vault account, click **Settings** in the menu on the left of the page.
2. On the settings page, click the **System Users** tab, then click **Enable System User**.
3. In the drop-down menu, set the user type to **Confirm Anything** or **Reject Everything**.
4. Enter the wallet public key (Base64 encoded) and click **Enable**.

You should now see a new System User entry alongside a generated API key and Role.

To disable a system user, simply click the **3 dots** to the right of the Role, then click **Disable**.

For more details, please see [here](https://vault.docs.blockdaemon.com/docs/system-user).

</details>

<details>
  <summary><b>How can I filter and customize the Transaction history?</b></summary>
  <br/>

When you sign in to your wallet account you will be taken to the Transactions page, which you can also access from the menu on the left of every page.

By default, this page lists all transactions and their details in chronological order, starting with the most recent transaction. At the top of the page you’ll see the following options to filter or customize your transaction data:

**Live Updates**: When enabled, the list of transactions and their statuses will update automatically. When disabled you will need to use the Refresh button on the right of the page.

**Set Columns**: Click this drop-down menu to choose which transaction details to display in the table. You can also see the details of any transaction by clicking the round icon to the far right of each transaction.

**Filter**: Allows you to filter the transaction list by criteria such as date range, source, or destination. Click “Advanced filters” to see more criteria options or click “Reset filter” to remove all filter criteria.

**Export**: Click here to save the transaction history as a .CSV file. This file is generated based on the views and filters that have been configured &lt;need confirmation&gt; so make sure to check these settings before exporting.

</details>

<details>
  <summary><b>What are the different policy types?</b></summary>
  <br/>

**Administrative policy**\
These are the high-level rules that regulate all wallet operations. This covers user management, group management, and transfer policy.

This policy is only modifiable by users with Admin roles.

**Transfer policy**\
This policy governs transactions and the rules and restrictions under which the transactions are executed. The transfer policy can only be modified through Administrative policy.

**Staking policy**\
This policy governs the staking process works in the Institutional Vault.

</details>

<details>
  <summary><b>Is it possible for users who have lost their phones to re-add themselves?</b></summary>
  <br/>

It is not possible to re-add themselves. They cannot register again until an Administrator resets their account status to **Pending Onboarding**. After the reset, they can re-register.\
For more details, please see [here](https://vault.docs.blockdaemon.com/docs/reset-a-user#reset-a-user-who-has-lost-their-phone).

</details>

<details>
  <summary><b>What is the difference between a user and an account within the Institutional wallet?</b></summary>
  <br/>

**User**: Refers to an individual accessing the Institutional Vault. A user can create an account associated with specific permissions within the wallet. They can perform various actions within their assigned account(s) based on their permissions.

**Account**: A functionality within the Institutional Vault that segregates different wallet addresses. Each account is associated with a unique address for balance-based chains like Ethereum. For UTXO-based chains like Bitcoin, an account can contain multiple addresses. Accounts can be further restricted by policies. It securely stores and manages digital assets, sends and receives digital assets, tracks balances, and views transaction history.

In most cases, an account can hold one wallet address per protocol, except for Bitcoin, where multiple Bitcoin addresses can be created per account.

In summary, a user can access the Institutional Vault and specific permissions. At the same time, an account is a functionality within the wallet that allows for managing and segregating different wallet addresses.

</details>

<details>
  <summary><b>What is the difference between each type of user role?</b></summary>
  <br/>

The Institutional Vault offers three user roles: Admin, Viewer, and MarketOps, each with distinct capabilities and privileges you can see [here](https://vault.docs.blockdaemon.com/docs/user-types-and-privileges) for more details.

</details>

<details>
  <summary><b>What are the supported Bitcoin address formats by Institutional Wallet?</b></summary>
  <br/>

By default, if no configuration is specified, Bitcoin addresses are of the `P2PKH` (legacy) type. However, we also support `P2SH-P2WPKH` addresses for Bitcoin.

</details>

<Support />