<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/delegatedadmincustomer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# delegatedAdminCustomer resource type

Namespace: microsoft.graph

Represents a Microsoft Entra organization that is a customer of a Microsoft partner and has a delegated admin relationship with the Microsoft partner. This object is automatically created by the system when at least one delegated admin relationship exists between the partner and customer and is deleted when no more active relationships exist.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tenantrelationship-list-delegatedadmincustomers?view=graph-rest-1.0) | [delegatedAdminCustomer](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadmincustomer?view=graph-rest-1.0) collection | Get a list of the **delegatedAdminCustomer** objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/delegatedadmincustomer-get?view=graph-rest-1.0) | [delegatedAdminCustomer](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadmincustomer?view=graph-rest-1.0) | Read the properties and relationships of a **delegatedAdminCustomer** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The Microsoft Entra ID display name of the customer tenant. Read-only. Supports `$orderby`. |
| id | String | The Microsoft Entra ID-assigned unique identifier of the customer. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| tenantId | String | The Microsoft Entra ID-assigned tenant ID of the customer. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| serviceManagementDetails | [delegatedAdminServiceManagementDetail](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminservicemanagementdetail?view=graph-rest-1.0) collection | Contains the management details of a service in the customer tenant that's managed by delegated administration. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegatedAdminCustomer",
  "id": "String (identifier)",
  "tenantId": "String",
  "displayName": "String"
}
```
