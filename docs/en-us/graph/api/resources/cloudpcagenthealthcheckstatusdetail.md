<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagenthealthcheckstatusdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# cloudPcAgentHealthCheckStatusDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the working status of an agent health check task.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalHealthCheckMessage | String | The optional information about this health check to help explain its current status. For example, `HealthCheck can't be triggered while installing.` Empty by default. Read-only. |
| cloudPcId | String | The unique identifier of the Cloud PC where the agent health check occurs. Read-only. |
| healthCheckState | [cloudPcAgentHealthCheckState](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagenthealthcheckstatusdetail?view=graph-rest-beta#cloudpcagenthealthcheckstate-values) | Indicates the working status of the health check. Default value is `pending`. The possible values are: `pending`, `processing`, `succeeded`, `failed`, `conflict`, `canceled`, `unknownFutureValue`. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Indicates the date and time when the health check state was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| startDateTime | DateTimeOffset | Indicates the date and time when the latest agent health check started. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |

### cloudPcAgentHealthCheckState values

| Member | Description |
| :--- | :--- |
| pending | Default. Indicates that the health check is submitted but not started. |
| processing | Indicates that the health check is in process. |
| succeeded | Indicates that the health check completed successfully. |
| failed | Indicates that the health check stopped with failure. |
| conflict | Indicates that the health check didn't start because another conflicting health check was already submitted. |
| canceled | Indicates that the health check is canceled. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAgentHealthCheckStatusDetail",
  "additionalHealthCheckMessage": "String",
  "cloudPcId": "String",
  "healthCheckState": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "startDateTime": "String (timestamp)"
}
```
