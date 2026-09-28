<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-10 -->

# Microsoft Entra Health monitoring API overview

Namespace: microsoft.graph.healthMonitoring

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The Microsoft Entra Health monitoring alerts APIs allow you to view anomalous usage patterns for your tenant on business-critical identity scenarios and receive alert notifications. The API is built to fire alerts based on monitoring the health metric streams in [serviceActivity APIs](https://learn.microsoft.com/en-us/graph/api/resources/serviceactivity?view=graph-rest-beta). These alerts contain information about the type, date, and impact of the anomalous usage patterns and allow you to investigate and remediate issues that you find.

## Licenses

For more information about the licenses required to use this premium feature, see [Microsoft Entra licensing: Microsoft Entra monitoring and health](https://learn.microsoft.com/en-us/entra/fundamentals/licensing#microsoft-entra-monitoring-and-health).

## Common requests

The following table lists some common requests that you can use with this API.

| Scenarios | API |
| --- | --- |
| Retrieve all alerts of a Microsoft Entra tenant | [List alerts](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-healthmonitoringroot-list-alerts?view=graph-rest-beta) |
| Retrieve an alert and its associated data, including the impacted resources | [Get alert](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-alert-get?view=graph-rest-beta) |
| Update the state of an alert | [Update alert](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-alert-update?view=graph-rest-beta) |
| Retrieve alert configurations for all alert types | [List alert configurations](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-healthmonitoringroot-list-alertconfigurations?view=graph-rest-beta) |
| Retrieve alert configuration for an alert type | [Get alert configuration](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-alertconfiguration-get?view=graph-rest-beta) |
| Update alert configuration for an alert type | [Update alert configuration](https://learn.microsoft.com/en-us/graph/api/healthmonitoring-alertconfiguration-update?view=graph-rest-beta) |

Note

You might see `unknownFutureValue` as a member in enums due to evolvable enumerations. Here's how you can [handle future members in evolvable enumerations](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations).

## Related content

- [What is Microsoft Entra Health?](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-microsoft-entra-health)
