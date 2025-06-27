---
title: System Components
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
# Institutional Vault High-Level Components

<Image align="center" src="https://files.readme.io/70bb7ec4a88e98f5241de721079124c0eadc8131957a24a252ec4ef75139e585-Asset_70300x_1.png" />

## Online Wallet Front End

This section shows where consumer actions are performed or operated. Consumers have complete authority over their actions, accounts, and data.

## Integration Services Section

This section shows where the Institutional Vault controls periphery wallet-supporting services.

## Approval Service

Approval Service mediates MPA node to Institutional Vault Approver App interactions. The Approval Service links users' public keys to their mobile device ID. If a regular user through the UI initiates the action, Approver Service will send the approval request for user approval to the proper device, signed by the MPA's secret signing key. The Approver Service also sends the signed answer from the Institutional Vault Approver app to the MPA nodes. If an API call initiates the action, the MPA will use the Approver Service to reach the specified callback address for a signed affirmation or denial.

## Wallet Service

The Wallet Service provides the interface for browser-based and API-based access to the MPA. It provides a user with account, policy, and user administration options and access to the Wallet's transaction history.

## MPC Policy Authority

The MPA Facade serves a purpose comparable to that of the Approval Service but for the Wallet Service. It depicts the Wallet Service's multiparty policy authority as a singular entity.

## Message Broker/Orchestrator

Message Broker is responsible for asynchronous communications between various services, functioning as an intermediary between senders and receivers so that the services can communicate without direct connections.

## MPC Policy Agent (MPA) Node

Each MPA node has a TSM node that can run a multiparty protocol to compute the functions of secret keys kept on the TSM database and make signatures and new addresses. MPA nodes hold policies, user IDs, jobs, and public keys. They also check rules and request Approval Service approvals. Finally, MPA nodes access Blockchain API services to create transactions or important information.

## Air-Gapped MPC Policy Authority (Cold Wallet)

The cold storage is a secure key isolation and signing tool, kept separate from online connections. The cold wallet is a local wallet physically linked to your computer. Combining Hot and Cold wallets enables secure communication through public key exchange. Despite being a cold wallet, signing is still required through an air-gapped manual transfer for key exchange.

<Support />
