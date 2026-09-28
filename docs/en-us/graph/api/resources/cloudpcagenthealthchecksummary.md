<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagenthealthchecksummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# cloudPcAgentHealthCheckSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the details of an agent health status.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agentHealthCheckDetails | [cloudPcAgentHealthCheckDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagenthealthcheckdetail?view=graph-rest-beta) collection | A list of health check results performed for the target agent. Provides detailed information about the health checks. Empty by default. Read-only. |
| lastSucceededHealthCheckDateTime | DateTimeOffset | Indicates the date and time when the last health check finished successfully. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| latestHealthCheckStatus | [cloudPcAgentHealthCheckStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagenthealthcheckstatusdetail?view=graph-rest-beta) | Indicates the status of the latest agent health check. It can be an ongoing agent health check or the last finished health check. Tracks the latest triggered health check. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAgentHealthCheckSummary",
  "agentHealthCheckDetails": [{"@odata.type": "microsoft.graph.cloudPcAgentHealthCheckDetail"}],
  "lastSucceededHealthCheckDateTime": "String (timestamp)",
  "latestHealthCheckStatus": {"@odata.type": "microsoft.graph.cloudPcAgentHealthCheckStatusDetail"}
}
```
