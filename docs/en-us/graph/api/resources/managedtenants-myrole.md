<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-myrole?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# myRole resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the role assignments to a signed-in user for a [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-myroles?view=graph-rest-beta) | [microsoft.graph.managedTenants.myRole](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-myrole?view=graph-rest-beta) collection | Get the roles that the signed-in user has through a delegated relationship across [managed tenants](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignments | [microsoft.graph.managedTenants.roleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-roleassignment?view=graph-rest-beta) collection | A collection of role assignments for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.myRole",
  "assignments": [
    {
      "@odata.type": "microsoft.graph.managedTenants.roleAssignment"
    }
  ],
  "tenantId": "String"
}
```
