<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/riskyuserhistoryitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# riskyUserHistoryItem resource type

Namespace: microsoft.graph

Represents the risk history of a Microsoft Entra user as determined by Microsoft Entra ID Protection.

Inherits from [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0).

Note

1. Using this API requires a Microsoft Entra ID P2 license.
2. The availability of risk history data is governed by the [Microsoft Entra data retention policies](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/reference-reports-data-retention#how-long-does-azure-ad-store-the-data).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List history](https://learn.microsoft.com/en-us/graph/api/riskyuser-list-history?view=graph-rest-1.0) | [riskyUserHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/riskyuserhistoryitem?view=graph-rest-1.0) collection | Get the riskyUserHistoryItems from the history navigation property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activity | [riskUserActivity](https://learn.microsoft.com/en-us/graph/api/resources/riskuseractivity?view=graph-rest-1.0) | The activity related to user risk level change. |
| id | String | The unique identifier for the **riskyUserHistoryItem** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| initiatedBy | String | The ID of actor that does the operation. |
| isDeleted | Boolean | Indicates whether the user is deleted. Inherited from [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0). |
| isProcessing | Boolean | Indicates whether a user's risky state is being processed by the backend. Inherited from [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0). |
| riskDetail | riskDetail | Details of the detected risk. Inherited from [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0). The possible values are: `none`, `adminGeneratedTemporaryPassword`, `userPerformedSecuredPasswordChange`, `userPerformedSecuredPasswordReset`, `adminConfirmedSigninSafe`, `aiConfirmedSigninSafe`, `userPassedMFADrivenByRiskBasedPolicy`, `adminDismissedAllRiskForUser`, `adminConfirmedSigninCompromised`, `hidden`, `adminConfirmedUserCompromised`, `unknownFutureValue`. |
| riskLastUpdatedDateTime | DateTimeOffset | The date and time when the risky user was last updated. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0). |
| riskLevel | riskLevel | Level of the detected risky user. Inherited from [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0). The possible values are: `low`, `medium`, `high`, `hidden`, `none`, `unknownFutureValue`. |
| riskState | riskState | State of the user's risk. Inherited from [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0). The possible values are: `none`, `confirmedSafe`, `remediated`, `dismissed`, `atRisk`, `confirmedCompromised`, `unknownFutureValue`. |
| userDisplayName | String | Risky user display name. Inherited from [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0). |
| userId | String | The ID of the user. |
| userPrincipalName | String | Risky user principal name. Inherited from [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| history | [riskyUserHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/riskyuserhistoryitem?view=graph-rest-1.0) collection | The activity related to user risk level change. Inherited from [riskyUser](https://learn.microsoft.com/en-us/graph/api/resources/riskyuser?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.riskyUserHistoryItem",
  "id": "String (identifier)",
  "isDeleted": "Boolean",
  "isProcessing": "Boolean",
  "riskLastUpdatedDateTime": "String (timestamp)",
  "riskLevel": "String",
  "riskState": "String",
  "riskDetail": "String",
  "userDisplayName": "String",
  "userPrincipalName": "String",
  "userId": "String",
  "initiatedBy": "String",
  "activity": {
    "@odata.type": "microsoft.graph.riskUserActivity"
  }
}
```
