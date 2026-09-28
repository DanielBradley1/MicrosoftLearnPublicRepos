<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-28 -->

# riskyUser resource type

Namespace: microsoft.graph

Represents Microsoft Entra users who are at risk. Microsoft Entra ID continually evaluates user risk based on various signals and machine learning. This API provides programmatic access to all at-risk users in your Microsoft Entra ID.

For more information about risk events, see [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection).

Note

1. Using the riskyUsers API requires a Microsoft Entra ID P2 license.
2. The availability of risky user data is governed by the [Microsoft Entra data retention policies](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/reference-reports-data-retention#how-long-does-azure-ad-store-the-data).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/riskyuser-list?view=graph-rest-1.0) | [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0) collection | Get a list of the **riskyUser** objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/riskyuser-get?view=graph-rest-1.0) | [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0) | Read the properties and relationships of a **riskyUser** object. |
| [Confirm compromised](https://learn.microsoft.com/en-us/graph/api/riskyuser-confirmcompromised?view=graph-rest-1.0) | None | Confirm one or more **riskyUser** objects as compromised. |
| [Confirm safe](https://learn.microsoft.com/en-us/graph/api/riskyuser-confirmsafe?view=graph-rest-1.0) | None | Confirm one or more **riskyUser** objects as safe. |
| [Dismiss](https://learn.microsoft.com/en-us/graph/api/riskyuser-dismiss?view=graph-rest-1.0) | None | Dismiss the risk of one or more **riskyUser** objects. |
| [List history](https://learn.microsoft.com/en-us/graph/api/riskyuser-list-history?view=graph-rest-1.0) | [riskyUserHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/riskyuserhistoryitem?view=graph-rest-1.0) collection | Get the **riskyUserHistoryItems** from the history navigation property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique ID of the user at risk. |
| isDeleted | Boolean | Indicates whether the user is deleted. The possible values are: `true`, `false`. |
| isProcessing | Boolean | Indicates whether the backend is processing a user's risky state. |
| riskLastUpdatedDateTime | DateTimeOffset | The date and time that the risky user was last updated. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| riskLevel | riskLevel | Level of the detected risky user. The possible values are: `low`, `medium`, `high`, `hidden`, `none`, `unknownFutureValue`. |
| riskState | riskState | State of the user's risk. The possible values are: `none`, `confirmedSafe`, `remediated`, `dismissed`, `atRisk`, `confirmedCompromised`, `unknownFutureValue`. |
| riskDetail | [riskDetail](https://learn.microsoft.com/en-us/graph/api/resources/riskdetail?view=graph-rest-1.0) | Details of the detected risk. |
| userDisplayName | String | Risky user display name. |
| userPrincipalName | String | Risky user principal name. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| history | [riskyUserHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/riskyuserhistoryitem?view=graph-rest-1.0) collection | The activity related to user risk level change |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.riskyUser",
  "id": "String (identifier)",
  "isDeleted": "Boolean",
  "isProcessing": "Boolean",
  "riskLastUpdatedDateTime": "String (timestamp)",
  "riskLevel": "String",
  "riskState": "String",
  "riskDetail": "String",
  "userDisplayName": "String",
  "userPrincipalName": "String"
}
```
