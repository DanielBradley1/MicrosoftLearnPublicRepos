<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-conditionalaccesspolicycoverage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# conditionalAccessPolicyCoverage resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information about any Microsoft Entra policy that defines access rules of a resource for a given managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List conditional access coverages](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-conditionalaccesspolicycoverages?view=graph-rest-beta) | [microsoft.graph.managedTenants.conditionalAccessPolicyCoverage](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-conditionalaccesspolicycoverage?view=graph-rest-beta) collection | Get a list of the [conditionalAccessPolicyCoverage](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-conditionalaccesspolicycoverage?view=graph-rest-beta) objects and their properties. |
| [Get conditional access policy coverage](https://learn.microsoft.com/en-us/graph/api/managedtenants-conditionalaccesspolicycoverage-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.conditionalAccessPolicyCoverage](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-conditionalaccesspolicycoverage?view=graph-rest-beta) | Read the properties and relationships of a [conditionalAccessPolicyCoverage](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-conditionalaccesspolicycoverage?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conditionalAccessPolicyState | String | The state for the conditional access policy. The possible values are: `enabled`, `disabled`, `enabledForReportingButNotEnforced`. Required. Read-only. |
| id | String | The unique identifier for this entity. Required. Read-only. |
| latestPolicyModifiedDateTime | DateTimeOffset | The date and time the conditional access policy was last modified. Required. Read-only. |
| requiresDeviceCompliance | Boolean | A flag indicating whether the conditional access policy requires device compliance. Required. Read-only. |
| tenantDisplayName | String | The display name for the managed tenant. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.conditionalAccessPolicyCoverage",
  "id": "String (identifier)",
  "tenantDisplayName": "String",
  "conditionalAccessPolicyState": "String",
  "requiresDeviceCompliance": "Boolean",
  "latestPolicyModifiedDateTime": "String (timestamp)"
}
```
