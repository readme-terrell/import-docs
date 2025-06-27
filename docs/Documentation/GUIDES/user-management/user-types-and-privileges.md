---
title: User Types and Privileges
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
There are two user types in the Institutional Vault: 

* **Users (Human Users)**: These are standard, non-administrative individuals who interact with the wallet through a UI or similar interactive methods. They can access the wallet’s features but cannot modify its policies or administrative settings. Users are often assigned to a group (e.g., "all-approvers") to manage permissions across the platform.
* **System Users**: These are users created for programmatic access, typically for automated systems or applications interacting with the wallet via the API. System Users are managed by administrators and can have specific roles and API keys. 

Each user type can be assigned one of the following roles:

* **Admins** have the highest authority in the Institutional Vault and can create Users and System Users with assigned roles.
* **Non-Admin** users can hold one of two roles: **MarketOps** or **Viewer**. Each role grants access to different features and privileges.

The table below outlines the privileges available to Admins and Non-Admin roles (MarketOps and Viewer):

| Feature              | Admin | MarketOps | Viewer |
| :------------------- | :---- | :-------- | :----- |
| Backup Key           | ✅     | ❌         | ❌      |
| View Vault           | ✅     | ✅         | ❌      |
| Create Vault         | ✅     | ✅         | ❌      |
| View Asset           | ✅     | ✅         | ✅      |
| Create Asset         | ✅     | ✅         | ❌      |
| Update Asset         | ✅     | ✅         | ❌      |
| Manage Exchange Rate | ✅     | ❌         | ❌      |
| View User Info       | ✅     | ✅         | ✅      |
| View User List       | ✅     | ❌         | ❌      |
| Create User          | ✅     | ❌         | ❌      |
| Update User          | ✅     | ❌         | ❌      |
| Delete User          | ✅     | ❌         | ❌      |
| View System User     | ✅     | ❌         | ❌      |
| Create System User   | ✅     | ❌         | ❌      |
| Delete System User   | ✅     | ❌         | ❌      |
| View Group           | ✅     | ❌         | ❌      |
| Create Group         | ✅     | ❌         | ❌      |
| Update Group         | ✅     | ❌         | ❌      |
| View Policy          | ✅     | ❌         | ❌      |
| Create Policy        | ✅     | ❌         | ❌      |
| Update Policy        | ✅     | ❌         | ❌      |
| Delete Policy        | ✅     | ❌         | ❌      |
| View Audit           | ✅     | ❌         | ❌      |
| Update Notification  | ✅     | ✅         | ✅      |
| View Notification    | ✅     | ✅         | ✅      |
| Create Transaction   | ✅     | ✅         | ❌      |
| View Transaction     | ✅     | ✅         | ✅      |
| View Staking         | ✅     | ✅         | ✅      |
| Create Staking       | ✅     | ✅         | ❌      |
| Freeze Wallet        | ✅     | ❌         | ❌      |
| Update Vault         | ✅     | ✅         | ❌      |
| Create Public Key    | ✅     | ❌         | ❌      |
| View Public Key      | ✅     | ❌         | ❌      |

<Support />
