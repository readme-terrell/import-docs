---
title: Metrics and Health
excerpt: 💖 Understand wallet metrics and system health.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Prometheus Metrics for the Wallet Service

The wallet service exposes an HTTP metrics API that collates metrics in the Prometheus format. These application-level Wallet metrics can be queried using curl requests or a Prometheus collector, and Grafana dashboards.

> 📘 Note:
>
> The metrics service is active by **default** and operates exclusively on **port 9090**.

Here is the complete list of metric names, along with their corresponding dimensions:

| Metric Name                                              | Dimensions             |
| :------------------------------------------------------- | :--------------------- |
| wallet\_assets\_get\_coin\_info\_ms\_count               | coin, network          |
| wallet\_assets\_stored                                   | coin, is\_erc\_20      |
| wallet\_http\_inbound\_client\_ip\_requests\_total       | ip\_addr               |
| wallet\_http\_inbound\_request\_duration\_seconds\_count | path, status           |
| wallet\_http\_inbound\_request\_inbound\_total           | path, status           |
| wallet\_http\_outbound\_request\_in\_flight              | \-                     |
| wallet\_mediatr\_requests\_duration\_sum                 | mpa\_id, request\_type |
| wallet\_mediatr\_requests\_duration\_count               | mpa\_id, request\_type |
| wallet\_mediatr\_requests\_total                         | mpa\_id, request\_type |
| wallet\_ubiquity\_requests                               | network, path, status  |
| wallet\_ubiquity\_watches                                | network, platform      |

## Health Status for the Wallet Stack Services

To maintain smooth operations, each service within the deployment provides a `/health` endpoint. This endpoint is responsible for indicating the health status of the service through HTTP status codes. Follow the steps outlined below to ensure the reliability of the system.

<Image align="center" src="https://files.readme.io/478bd7a-flow_2300x.png" />

### 1\. Enable Micro-Service Health Monitoring

For optimal micro-service performance, consistently check the `/health` endpoint, which reflects the current status.

### 2\. Decode Status Codes

The `/health` endpoint status codes reveal service health. **200 - OK** indicates success; others like **503 - service unavailable** suggest possible issues.

### 3\. Set up Instant Alerts

Arrange to receive notifications when `/health` status codes deviate from 200 for rapid issue resolution.

### 4\. Apply Auto-Restart

When a service repeatedly fails health checks, trigger an automatic restart. Fine-tune the number of failures needed to invoke this to ensure system stability.

### 5\. Connect Health Checks and Logs

Link health checks with logs for additional failure cause insight, aiding in swift problem resolution.

<Support />
