<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/riskyagentidentityblueprintprincipal?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# riskyAgentIdentityBlueprintPrincipal resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Microsoft Entra [agent identity blueprint principal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-beta) that is at risk. Microsoft Entra ID Protection continually evaluates agentic risk based on various signals and machine learning.

Inherits from [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agentDisplayName | String | Name of the agent. Inherited from [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta).  <br>  <br>Supports `$filter` \(`eq`, `startsWith`\). |
| id | String | The object **id** of the [agent identity blueprint principal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-beta). Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).  <br>  <br>Supports `$filter` \(`eq`, `startsWith`\). |
| isDeleted | Boolean | Indicates whether the agent is deleted. Inherited from [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta). |
| isEnabled | Boolean | Indicates whether the agent is enabled. Inherited from [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta). |
| isProcessing | Boolean | Indicates whether an agent's risky state is processing in the backend. Inherited from [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta). |
| riskDetail | riskDetail | Details of the detected risk of the agent. Inherited from [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta). The possible values are: `none`, `adminConfirmedAgentSafe`, `adminConfirmedAgentCompromised`, `adminDismissedRiskForAgent`.  <br>  <br>Supports `$filter` \(`eq`\). |
| riskLastModifiedDateTime | DateTimeOffset | The date and time that the risky agent was last updated. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z. Inherited from [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta).  <br>  <br>Supports `$filter` \(`eq`, `le`, and `ge`\). |
| riskLevel | riskLevel | Level of the detected risky agent. Inherited from [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta). The possible values are: `low`, `medium`, `high`, `hidden`, `none`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`\). |
| riskState | riskState | State of the agent's risk. Inherited from [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta). The possible values are: `none`, `confirmedSafe`, `remediated`, `dismissed`, `atRisk`, `confirmedCompromised`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.riskyAgentIdentityBlueprintPrincipal",
  "id": "String (identifier)",
  "agentDisplayName": "String",
  "isDeleted": "Boolean",
  "isEnabled": "Boolean",
  "isProcessing": "Boolean",
  "riskLastModifiedDateTime": "String (timestamp)",
  "riskState": "String",
  "riskLevel": "String",
  "riskDetail": "String"
}
```
