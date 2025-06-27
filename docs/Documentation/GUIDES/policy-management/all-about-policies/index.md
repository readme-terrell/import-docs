---
title: All About Policies
excerpt: 🚨 Become familiar with Institutional Vault Policies
deprecated: false
hidden: false
metadata:
  title: All about policies
  description: >-
    Discover all about policies in Blockdaemon Wallet. Learn how to configure
    and manage policies for enhanced control and security of your digital
    assets.
  image: https://files.readme.io/447f536-image_3.png
  robots: index
next:
  description: ''
---
# Overview

A policy is a set of rules applicable to specific activity categories. A policy can accompany each operation conducted within the wallet. 

### Default Mode

When there are no policies or rules for specific actions, authorization will be required to perform the operation, and everything is prohibited.

> 🚧 Warning: Pay attention to the policy ordering
>
> Our wallet runs the operation based on the policy order. For example, suppose you set a policy for account A where you block all transfers over $500, you need to set a policy that allows transfers for all accounts. **You must put the allow all policy needs to be set below/ after the policy blocking transfers related to account A.** If you put it before, then the blocking policy for account A will not be performed.

# Three Types of Policy

Three types of policies can be used on the Institutional Vault:

<Image align="center" src="https://files.readme.io/84abe2d-Asset_3300x_5.png" />

## Administration Policy

> 📘 Note:
>
> Administration Policies are only accessible via the API endpoint.

Administration policy is a collection of administrative regulations governing all wallet operations. This policy specifies the behaviour of a wallet for every operation performed on it. This policy is only adjustable by users with the Admin role. This policy addresses user management, group management, and the modification of the transfer policy.

## Transfer Policy

A transfer policy is a list of rules about how transfers or transactions should be done. This policy is only adjustable via the administration policy.

> 📘 Note:
>
> The wallet can be launched with default transfer policies or no transfer policies.

## Staking Policy

A staking policy acts like a rulebook that guides how the staking process works in the Institutional Vault. This policy includes a set of clear instructions and settings that control everything when you're staking your assets. This policy ensures that everything happens smoothly and securely.

All the policies can be set up before the wallet is launched as part of the wallet configuration process. 

After the wallet has been launched, only users with the admin role are authorized to modify rules or change any other settings.

<Support />
