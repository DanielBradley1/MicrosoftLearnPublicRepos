<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-itemcategories?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# itemCategory resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a category for many items in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get item categories](https://learn.microsoft.com/en-us/graph/api/dynamics-itemcategories-get?view=graph-rest-beta) | [itemCategory](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-itemcategories?view=graph-rest-beta) | Get an item category. |
| [Create item categories](https://learn.microsoft.com/en-us/graph/api/dynamics-create-itemcategories?view=graph-rest-beta) | [itemCategory](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-itemcategories?view=graph-rest-beta) | Create an item category. |
| [Update item categories](https://learn.microsoft.com/en-us/graph/api/dynamics-itemcategories-update?view=graph-rest-beta) | [itemCategory](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-itemcategories?view=graph-rest-beta) | Update an item category. |
| [Delete item categories](https://learn.microsoft.com/en-us/graph/api/dynamics-itemcategories-delete?view=graph-rest-beta) | None | Delete an item category. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The item category code. |
| displayName | String | The display name of the item category. |
| id | String | The unique ID of the item category. Noneditable. |
| lastModifiedDateTime | Datetime | The date and time when the item category was last modified. Read-Only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "code": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "Datetime"
}
```
