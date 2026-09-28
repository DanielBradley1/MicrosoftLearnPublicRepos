<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/riskyserviceprincipal?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-28 -->

# riskyServicePrincipal resource type

Namespace: microsoft.graph

Represents Microsoft Entra service principals that are at-risk. Microsoft Entra ID continually evaluates service principal risk based on various signals and machine learning. This API provides programmatic access to all at-risk service principals in your Microsoft Entra tenant.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

> **Note:** Using the riskyServicePrincipal API requires a Workload Identities Premium license.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identityprotectionroot-list-riskyserviceprincipals?view=graph-rest-1.0) | [riskyServicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/riskyserviceprincipal?view=graph-rest-1.0) collection | List risky service principals and their risk properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/riskyserviceprincipal-get?view=graph-rest-1.0) | [riskyServicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/riskyserviceprincipal?view=graph-rest-1.0) | Get a specific risky service principal and its risk properties. |
| [Dismiss](https://learn.microsoft.com/en-us/graph/api/riskyserviceprincipal-dismiss?view=graph-rest-1.0) | None | Dismiss the risk of a risky service principal. |
| [Confirm compromised](https://learn.microsoft.com/en-us/graph/api/riskyserviceprincipal-confirmcompromised?view=graph-rest-1.0) | None | Confirm a risky service principal as compromised. |
| [List history](https://learn.microsoft.com/en-us/graph/api/riskyserviceprincipal-list-history?view=graph-rest-1.0) | [riskyServicePrincipalHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/riskyserviceprincipalhistoryitem?view=graph-rest-1.0) collection | Get the risk history of a Microsoft Entra service principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The globally unique identifier for the associated application \(its **appId** property\), if any. |
| displayName | String | The display name for the service principal. |
| id | String | The unique identifier assigned to the service principal at risk. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | `true` if the service principal account is enabled; otherwise, `false`. |
| isProcessing | Boolean | Indicates whether Microsoft Entra ID is currently processing the service principal's risky state. |
| riskDetail | [riskDetail](https://learn.microsoft.com/en-us/graph/api/resources/riskdetail?view=graph-rest-1.0) | Details of the detected risk.  <br>**Note:** Details for this property are only available for Workload Identities Premium customers. Events in tenants without this license will be returned `hidden`. |
| riskLastUpdatedDateTime | DateTimeOffset | The date and time that the risk state was last updated. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2021 is `2021-01-01T00:00:00Z`. Supports `$filter` \(`eq`\). |
| riskLevel | riskLevel | Level of the detected risky workload identity. The possible values are: `low`, `medium`, `high`, `hidden`, `none`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| riskState | riskState | State of the service principal's risk. The possible values are: `none`, `confirmedSafe`, `remediated`, `dismissed`, `atRisk`, `confirmedCompromised`, `unknownFutureValue`. |
| servicePrincipalType | String | Identifies whether the service principal represents an `Application`, a `ManagedIdentity`, or a legacy application \(`socialIdp`\). This is set by Microsoft Entra ID internally and is inherited from [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| history | [riskyServicePrincipalHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/riskyserviceprincipalhistoryitem?view=graph-rest-1.0) collection | Represents the risk history of Microsoft Entra service principals. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.riskyServicePrincipal",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "isProcessing": "Boolean",
  "riskLastUpdatedDateTime": "String (timestamp)",
  "riskLevel": "String",
  "riskState": "String",
  "riskDetail": "String",
  "displayName": "String",
  "appId": "String",
  "servicePrincipalType": "String"
}
```
