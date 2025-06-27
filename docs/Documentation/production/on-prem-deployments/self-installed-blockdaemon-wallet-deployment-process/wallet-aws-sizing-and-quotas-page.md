---
title: AWS Deployment Specifications
excerpt: 📝 Understand the Wallet AWS networking, sizing and quotas.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## High-level AWS Deployment Networking Diagram

<Image align="center" src="https://files.readme.io/1533034-Asset_10300x_1.png" />

### Recommended Service and Infrastructure Sizing

Here is a comprehensive list of Institutional Vault AWS-recommended services and infrastructure sizes:

| Service Name          | Resource Type            | CPU Cores | Memory (GB) | AWS Specification |
| :-------------------- | :----------------------- | :-------- | :---------- | :---------------- |
| Wallet service        | microservice container   | 1         | 1           | container         |
| Approval service      | microservice container   | 0.5       | 0.5         | container         |
| Orchestrator facade   | microservice container   | 0.5       | 0.5         | container         |
| Message Broker        | microservice container   | 0.5       | 0.5         | container         |
| MPA Policy-nodes (x3) | virtual machine instance | 4         | 16          | m5.xlarge         |
| Relational Database   | database PaaS            | 2         | 4           | t4g.medium        |

## Service Limits and Quotas

You don't need to request any limit increases for default Service Quotas when using the Automated AWS deployment tooling.

<Support />
