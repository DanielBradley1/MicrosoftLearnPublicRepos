<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminservicemanagementdetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# delegatedAdminServiceManagementDetail resource type

Namespace: microsoft.graph

Contains the management details of a service in the customer tenant that's managed by delegated administration.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/delegatedadmincustomer-list-servicemanagementdetails?view=graph-rest-1.0) | [delegatedAdminServiceManagementDetail](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminservicemanagementdetail?view=graph-rest-1.0) collection | Get a list of the **delegatedAdminServiceManagementDetail** objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of a managed service. Read-only. |
| serviceManagementUrl | String | The URL of the management portal for the managed service. Read-only. |
| serviceName | String | The name of a managed service. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegatedAdminServiceManagementDetail",
  "id": "String (identifier)",
  "serviceManagementUrl": "String",
  "serviceName": "String"
}
```
