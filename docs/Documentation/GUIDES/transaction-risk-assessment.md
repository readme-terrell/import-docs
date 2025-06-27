---
title: Transaction Risk Assessment
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
## Overview

The Institutional Vault integrates [Chainalysis](https://www.chainalysis.com/) for real-time transaction risk assessment. This integration allows for risk analysis of every transaction using Chainanalysis's advanced data analytics and ensures high security and compliance.

It provides real-time alerts to monitor high-risk blockchain transactions. These alerts help financial institutions, crypto businesses, and sanctioned activities before transactions are processed.

> 📘 Note
>
> We assume you already have a Chainalysis account for this guide.

## Configure the Risk Assessment Settings

To configure your Institutional Vault risk assessment settings, follow the steps below:

1. Navigate to your **Institutional Vault**.
2. Click **Settings** > **Risk Assessment** tab.

<Image align="center" width="740px" src="https://files.readme.io/925aeba-a8c20dcf-ecc1-400c-a7dc-76d3042976e1.png" />

3. Provide your **Chainalysis key**.
4. Set up the Risk settings. There are two main configurations that you can configure:

| Configuration                                       | Description                                                                                        |
| :-------------------------------------------------- | :------------------------------------------------------------------------------------------------- |
| Screen every transaction with Chainalysis           | This option activates the Screen with Chainalysis toggle on all transactions.                      |
| Only allow admins to toggle Screen with Chainalysis | This option ensures that only administrators can turn the Chainalysis screening feature on or off. |

## Activate the Risk Assessment in a Transaction

To use a Chainalysis risk assessment in a transaction, follow the steps below:

1. Click the **Transfer Funds** button from the main navigation menu.

<Image align="center" width="740px" src="https://files.readme.io/b27bf8b-605a226e-1630-4de2-a9a9-9e34000cf017.png" />

2. Specify all the fields.

<Image align="center" width="740px" src="https://files.readme.io/da30a71-2ce459f9-aa95-48ee-b465-883a9cdc1b8a.png" />

| Field                   | Description                                                                                                                                                                                                                   |
| :---------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Asset                   | Select the asset you want to transfer.                                                                                                                                                                                        |
| Source                  | Select the source account.                                                                                                                                                                                                    |
| Destination             | Select the destination account. You can choose between an Internal Account or an External Address.                                                                                                                            |
| Cypto Amount            | Specify the amount of asset you want to transfer. You can choose between Net or Gross transfer.                                                                                                                               |
| Fee Rate                | Specify the fee priority to determine the fee rate.                                                                                                                                                                           |
| Reference               | The referenced field is optional, enabling users to include relevant references or notes related to the staking transaction. It can be used for personal record-keeping or to provide additional information about the stake. |
| Screen with Chainalysis | Determine if transactions will undergo risk assessment via Chainalysis.                                                                                                                                                       |

3. Switch the **Screen with Chainalysis** to activate the transaction risk assessment.

<Image align="center" width="740px" src="https://files.readme.io/04f011e-e254c50b-635d-4be5-849e-bb33b5d1385a.png" />

4. Click **Transfer** to submit the transfer operation.

<Image align="center" width="740px" src="https://files.readme.io/c67289c-24c76201-a05a-45fd-865e-b80f0e1d3ffe.png" />

5. Chainalysis screens the transaction to determine whether it is safe or high risk, and assigning a risk level based on potential suspicious activity.

   1. If the transaction is considered low risk, meaning it has only indirect exposure to risky entities, you can select **Continue** to proceed.

      <Image align="center" width="740px" src="https://files.readme.io/f38485f7b267d5f67e70ef3eea8c56abf3e7ac83337170ac595d135b70c7fec7-Untitled_design_90.png" />
   2. If the destination address is flagged as high risk, a warning will raised but you can still choose to proceed. This warning indicates that the funds are linked to illicit or sanctioned activities.

      <Image align="center" width="740px" src="https://files.readme.io/94002a1b69dc10fb353945ecc4a3eabed106710d9d4ab81163f3656b4f08026d-Untitled_design_91.png" />
6. Check out the [Transaction History](https://vault.docs.blockdaemon.com/docs/transaction-history) to review the status and details of the transaction.

<Support />
