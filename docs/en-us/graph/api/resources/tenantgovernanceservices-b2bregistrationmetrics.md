<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetrics?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# b2bRegistrationMetrics resource type

Namespace: microsoft.graph

Represents B2B collaboration metrics that track guest registrations between the calling tenant and a [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0). Includes both initial and recent snapshots showing inbound and outbound guest counts.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| initial | [microsoft.graph.b2BRegistrationMetricsInitial](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsinitial?view=graph-rest-1.0) | B2B registration metrics corresponding to initial snapshots where metrics were aggregated for the first time. |
| recent | [microsoft.graph.b2BRegistrationMetricsRecent](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsrecent?view=graph-rest-1.0) | B2B registration metrics corresponding to recent snapshots where metrics were found to have sufficiently changed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.b2bRegistrationMetrics"
}
```
