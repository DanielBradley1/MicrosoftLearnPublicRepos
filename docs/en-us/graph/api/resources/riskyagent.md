<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-04 -->

# riskyAgent resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Microsoft Entra agents that are at risk as evaluated by Microsoft Entra ID Protection based on various signals and machine learning. This API provides programmatic access to all at-risk agents in your Microsoft Entra tenant, the **@odata.type** indicates the exact type of this agent. The supported types are [riskyAgentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/riskyagentidentity?view=graph-rest-beta), [riskyAgentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/riskyagentidentityblueprintprincipal?view=graph-rest-beta), and [riskyAgentUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyagentuser?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/riskyagent-list?view=graph-rest-beta) | [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta) collection | Get a list of the riskyAgent objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/riskyagent-get?view=graph-rest-beta) | [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta) | Read the properties and relationships of [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta) object. |
| [Dismiss](https://learn.microsoft.com/en-us/graph/api/riskyagent-dismiss?view=graph-rest-beta) | None | Dismiss the risk of one or more riskyAgent objects. |
| [Confirm compromised](https://learn.microsoft.com/en-us/graph/api/riskyagent-confirmcompromised?view=graph-rest-beta) | None | Confirm one or more riskyAgent objects as compromised. |
| [Confirm safe](https://learn.microsoft.com/en-us/graph/api/riskyagent-confirmsafe?view=graph-rest-beta) | None | Confirm one or more riskyAgent objects as safe. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agentDisplayName | String | Name of the agent.  <br>  <br>Supports `$filter` \(`eq`, `startsWith`\). |
| blueprintId | String | The identifier of the [blueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-beta) associated with the agent. Nullable. |
| id | String | The object **id** of the [riskyAgentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/riskyagentidentity?view=graph-rest-beta), [riskyAgentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/riskyagentidentityblueprintprincipal?view=graph-rest-beta) or [riskyAgentUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyagentuser?view=graph-rest-beta). Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).  <br>  <br>Supports `$filter` \(`eq`, `startsWith`\). |
| identityType | [agentIdentityType](https://learn.microsoft.com/en-us/graph/api/resources/agentidentitytype?view=graph-rest-beta) | The type of agent identity. The possible values are: `agentIdentity`, `agentUser`, `unknownFutureValue`, `agentIdentityBlueprintPrincipal`. You must use the `Prefer: include-unknown-enum-members` request header to get the following value in this evolvable enum: `agentIdentityBlueprintPrincipal`. Required.  <br>  <br>Supports `$filter` \(`eq`\). |
| isDeleted | Boolean | Indicates whether the agent is deleted. |
| isEnabled | Boolean | Indicates whether the agent is enabled. |
| isProcessing | Boolean | Indicates whether an agent's risky state is processing in the backend. |
| riskDetail | [riskDetail](https://learn.microsoft.com/en-us/graph/api/resources/riskdetail?view=graph-rest-beta) | Details of the detected risk of the agent.  <br>  <br>Supports `$filter` \(`eq`\). |
| riskLastModifiedDateTime | DateTimeOffset | The date and time that the risky agent was last updated. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z.  <br>  <br>Supports `$filter` \(`eq`, `le`, and `ge`\). |
| riskLevel | riskLevel | Level of the detected risky agent. The possible values are: `low`, `medium`, `high`, `hidden`, `none`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`\). |
| riskState | riskState | State of the agent's risk. The possible values are: `none`, `confirmedSafe`, `dismissed`, `atRisk`, `confirmedCompromised`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.riskyAgent",
  "id": "String (identifier)",
  "agentDisplayName": "String",
  "blueprintId": "String",
  "identityType": "String",
  "isDeleted": "Boolean",
  "isEnabled": "Boolean",
  "isProcessing": "Boolean",
  "riskLastModifiedDateTime": "String (timestamp)",
  "riskState": "String",
  "riskLevel": "String",
  "riskDetail": "String"
}
```
