<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/securescore?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# secureScore resource type

Namespace: microsoft.graph

Represents a tenant's secure score per day of scoring data, at the tenant and control level. By default, 90 days of data is held. This data is sorted by **createdDateTime**, from latest to earliest. This will allow you to page responses by using $top=n, where n = the number of days of data that you want to retrieve.

For more information, see [Microsoft Secure Score](https://learn.microsoft.com/en-us/defender-xdr/microsoft-secure-score).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-list-securescores?view=graph-rest-1.0) | [secureScores](https://learn.microsoft.com/en-us/graph/api/resources/securescore?view=graph-rest-1.0) collection | Get secureScore object collection. |
| [Get](https://learn.microsoft.com/en-us/graph/api/securescore-get?view=graph-rest-1.0) | [secureScore](https://learn.microsoft.com/en-us/graph/api/resources/securescore?view=graph-rest-1.0) | Read properties and metadata of a secureScore object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeUserCount | Int32 | Active user count of the given tenant. |
| averageComparativeScores | [averageComparativeScore](https://learn.microsoft.com/en-us/graph/api/resources/averagecomparativescore?view=graph-rest-1.0) collection | Average score by different scopes \(for example, average by industry, average by seating\) and control category \(Identity, Data, Device, Apps, Infrastructure\) within the scope. |
| azureTenantId | String | GUID string for tenant ID. |
| controlScores | [controlScore](https://learn.microsoft.com/en-us/graph/api/resources/controlscore?view=graph-rest-1.0) collection | Contains tenant scores for a set of controls. |
| createdDateTime | DateTimeOffset | When the report was created. |
| currentScore | Double | Tenant current attained score on specified date. |
| enabledServices | String collection | Microsoft-provided services for the tenant \(for example, Exchange online, Skype, Sharepoint\). |
| id | String | Provider-generated GUID/unique identifier. Read-only. Required. |
| licensedUserCount | Int32 | Licensed user count of the given tenant. |
| maxScore | Double | Tenant maximum possible score on specified date. |
| vendorInformation | [securityVendorInformation](https://learn.microsoft.com/en-us/graph/api/resources/securityvendorinformation?view=graph-rest-1.0) | Complex type containing details about the security product/service vendor, provider, and subprovider \(for example, vendor=Microsoft; provider=SecureScore\). Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
"id": "String (identifier)",
"azureTenantId": "String",
"activeUserCount": "Int32",
"createdDateTime": "String (timestamp)",
"currentScore": "Double",
"enabledServices": ["String"],
"licensedUserCount": "Int32",
"maxScore": "Double",
"averageComparativeScores": [{"@odata.type": "microsoft.graph.averageComparativeScore"}],
"controlScores": [{"@odata.type": "microsoft.graph.controlScore"}],
"vendorInformation": {"@odata.type": "microsoft.graph.securityVendorInformation"},
}
```
