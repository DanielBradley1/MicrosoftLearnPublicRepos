<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantgroup?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# tenantGroup resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a logical group of managed tenants.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List tenant groups](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-tenantgroups?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantGroup](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantgroup?view=graph-rest-beta) collection | Get a list of the [tenantGroup](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantgroup?view=graph-rest-beta) objects and their properties. |
| [Get tenant group](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenantgroup-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantGroup](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantgroup?view=graph-rest-beta) | Read the properties and relationships of a [tenantGroup](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantgroup?view=graph-rest-beta) object. |
| [Search for tenant](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenantgroup-tenantsearch?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantGroup](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantgroup?view=graph-rest-beta) collection | Searches for the specific managed tenant across tenant groups. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allTenantsIncluded | Boolean | A flag indicating whether all managed tenant are included in the tenant group. Required. Read-only. |
| displayName | String | The display name for the tenant group. Optional. Read-only. |
| id | String | The unique identifier for the tenant group. Required. Read-only. |
| managementActions | [microsoft.graph.managedTenants.managementActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactioninfo?view=graph-rest-beta) collection | The collection of management action associated with the tenant group. Optional. Read-only. |
| managementIntents | [microsoft.graph.managedTenants.managementIntentInfo](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementintentinfo?view=graph-rest-beta) collection | The collection of management intents associated with the tenant group. Optional. Read-only. |
| tenantIds | String collection | The collection of managed tenant identifiers include in the tenant group. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.tenantGroup",
  "id": "String (identifier)",
  "displayName": "String",
  "allTenantsIncluded": "Boolean",
  "tenantIds": [
    "String"
  ],
  "managementIntents": [
    {
      "@odata.type": "microsoft.graph.managedTenants.managementIntentInfo"
    }
  ],
  "managementActions": [
    {
      "@odata.type": "microsoft.graph.managedTenants.managementActionInfo"
    }
  ]
}
```
