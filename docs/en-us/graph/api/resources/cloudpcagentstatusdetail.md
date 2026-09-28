<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentstatusdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# cloudPcAgentStatusDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the agent status of a Cloud PC.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agentVersionNumber | String | Indicates the version of the Cloud PC agent. For example, `1.2.02783.221`. Read-only. |
| cloudPcId | String | Indicates the unique identifier of the Cloud PC where the agent is installed. This identifier correlates the agent status with the target Cloud PC. It represents the unique identifier of the related Cloud PC entity, which is defined when the entity is created. Read-only. |
| diagnosticResultMessage | String | Indicates a detailed message related to the diagnostic result type. Maximum length is 1,500 characters. Read-only. |
| diagnosticResultType | [cloudPcAgentDiagnosticResultType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentstatusdetail?view=graph-rest-beta#cloudpcagentdiagnosticresulttype-values) | Indicates the diagnostic result type detected. Describes the overall issue identified. The possible values are: `healthy`, `versionOutdated`, `functionalityDefect`, `communicationUnhealthy`, `unknownError`, `unknownFutureValue`. Read-only. |
| healthCheckSummary | [cloudPcAgentHealthCheckSummary](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagenthealthchecksummary?view=graph-rest-beta) | Describes the details of health checks performed on the agent. Read-only. |
| healthStatus | [cloudPcAgentHealthStatus](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentstatusdetail?view=graph-rest-beta#cloudpcagenthealthstatus-values) | The health status of the agent. Used to query agents with the same health status. Default value is `healthy`. The possible values are: `healthy`, `warning`, `unavailable`, `unknownFutureValue`. |
| lastHealthStatusCheckedDateTime | DateTimeOffset | Indicates the date and time when the last agent health status check was completed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| managedDeviceName | String | Indicates the Intune enrolled device name of the Cloud PC. Read-only. |
| userPrincipalName | String | Indicates the principal name of the user assigned to the Cloud PC, with a maximum length of 113 characters. Read-only. |

### cloudPcAgentHealthStatus values

| Member | Description |
| :--- | :--- |
| healthy | Default. Indicates that the agent is healthy. |
| warning | Indicates that an issue was detected with the agent, but it remains partially operational. |
| unavailable | Indicates that the agent is either not installed, unable to communicate, or nonfunctional. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### cloudPcAgentDiagnosticResultType values

| Member | Description |
| :--- | :--- |
| healthy | Default. Indicates the agent is healthy. |
| versionOutdated | Indicates that the agent is functional but outdated. |
| functionalityDefect | Indicates that some agent functionality is unavailable, but the agent might still operate with reduced functionality. |
| communicationUnhealthy | Indicates that communication is currently unhealthy. The communication between the agent and the service might have partially or completely failed. |
| unknownError | Indicates that unknown errors occurred. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAgentStatusDetail",
  "agentVersionNumber": "String",
  "cloudPcId": "String",
  "diagnosticResultMessage": "String",
  "diagnosticResultType": "String",
  "healthCheckSummary": {"@odata.type": "microsoft.graph.cloudPcAgentHealthCheckSummary"},
  "healthStatus": "String",
  "lastHealthStatusCheckedDateTime": "String (timestamp)",
  "managedDeviceName": "String",
  "userPrincipalName": "String"
}
```
