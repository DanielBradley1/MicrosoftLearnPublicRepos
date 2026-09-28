<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentriskdetection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-24 -->

# agentRiskDetection resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the agentic risk detections as evaluated by Microsoft Entra ID Protection based on various signals and machine learning.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identityprotectionroot-list-agentriskdetections?view=graph-rest-beta) | [agentRiskDetection](https://learn.microsoft.com/en-us/graph/api/resources/agentriskdetection?view=graph-rest-beta) collection | Get a list of the agentRiskDetection objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/agentriskdetection-get?view=graph-rest-beta) | [agentRiskDetection](https://learn.microsoft.com/en-us/graph/api/resources/agentriskdetection?view=graph-rest-beta) | Read the properties and relationships of [agentRiskDetection](https://learn.microsoft.com/en-us/graph/api/resources/agentriskdetection?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityDateTime | DateTimeOffset | Date and time that the risky activity occurred. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z.  <br>  <br>Supports `$filter` \(`eq`, `le`, and `ge`\). |
| additionalInfo | String | Additional information associated with the risk detection. |
| blueprintId | String | The identifier of the [blueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-beta) associated with the agent. Nullable. |
| detectedDateTime | DateTimeOffset | Date and time that the risk was detected. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z.  <br>  <br>Supports `$filter` \(`eq`, `le`, and `ge`\). |
| detectionTimingType | riskDetectionTimingType | Timing of the detected risk \(real-time/offline\). The possible values are: `notDefined`, `realtime`, `nearRealtime`, `offline`, `unknownFutureValue`. |
| displayName | String | Human-readable name of the identity associated with this risk detection.  <br>  <br>Supports `$filter` \(`eq`, `startsWith`\). |
| id | String | Unique ID of the risk detection. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| identityId | String | Unique identifier of the identity associated with this risk detection.  <br>  <br>Supports `$filter` \(`eq`, `startsWith`\). |
| identityType | [agentIdentityType](https://learn.microsoft.com/en-us/graph/api/resources/agentidentitytype?view=graph-rest-beta) | The type of agent identity associated with this risk detection. The possible values are: `agentIdentity`, `agentIdentityBlueprintPrincipal`, `agentUser`, `user`, `unknownFutureValue`. You must use the `Prefer: include-unknown-enum-members` request header to get the following value in this evolvable enum: `agentIdentityBlueprintPrincipal`. Required.  <br>  <br>Supports `$filter` \(`eq`\). |
| lastModifiedDateTime | DateTimeOffset | Date and time that the risk detection was last updated.  <br>  <br>Supports `$filter` \(`eq`, `le`, and `ge`\). |
| riskDetail | [riskDetail](https://learn.microsoft.com/en-us/graph/api/resources/riskdetail?view=graph-rest-beta) | Details of the detected risk.  <br>  <br>Supports `$filter` \(`eq`\). |
| riskEventType | String | The type of risk event detected.  <br>  <br>Supports `$filter` \(`eq`\). |
| riskEvidence | String | Evidence on the risky activity occurred.  <br>  <br>Supports `$filter` \(`eq`\). |
| riskLevel | riskLevel | Level of the detected risk. The possible values are: `low`, `medium`, `high`, `hidden`, `none`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`\). |
| riskState | riskState | The state of a detected agentic risk. The possible values are: `none`, `confirmedSafe`, `dismissed`, `atRisk`, `confirmedCompromised`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`\). |
| source | String | The source system that generated the risk detection. Nullable. |
| agentDisplayName \(deprecated\) | String | Name of the agent. **Deprecated. Use `displayName` instead. This property will be removed after 2027-04-28.**  <br>  <br>Supports `$filter` \(`eq`, `startsWith`\). |
| agentId \(deprecated\) | String | The unique identifier for the agent. **Deprecated. Use `identityId` instead. This property will be removed after 2027-04-28.** See [riskyAgentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/riskyagentidentity?view=graph-rest-beta), [riskyAgentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/riskyagentidentityblueprintprincipal?view=graph-rest-beta), and [riskyAgentUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyagentuser?view=graph-rest-beta).  <br>  <br>Supports `$filter` \(`eq`, `startsWith`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentRiskDetection",
  "id": "String (identifier)",
  "activityDateTime": "String (timestamp)",
  "additionalInfo": "String",
  "agentDisplayName": "String",
  "agentId": "String",
  "blueprintId": "String",
  "detectedDateTime": "String (timestamp)",
  "detectionTimingType": "String",
  "displayName": "String",
  "identityId": "String",
  "identityType": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "riskDetail": "String",
  "riskEventType": "String",
  "riskEvidence": "String",
  "riskLevel": "String",
  "riskState": "String",
  "source": "String"
}
```
