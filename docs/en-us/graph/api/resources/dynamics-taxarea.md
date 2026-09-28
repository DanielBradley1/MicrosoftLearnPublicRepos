<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-taxarea?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-08 -->

# taxArea resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a tax area resource type in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get tax area](https://learn.microsoft.com/en-us/graph/api/dynamics-taxarea-get?view=graph-rest-beta) | taxArea | Gets a tax area object. |
| [Create tax area](https://learn.microsoft.com/en-us/graph/api/dynamics-create-taxarea?view=graph-rest-beta) | taxArea | Creates a tax area object. |
| [Update tax area](https://learn.microsoft.com/en-us/graph/api/dynamics-taxarea-update?view=graph-rest-beta) | taxArea | Updates a tax area object. |
| [Delete tax area](https://learn.microsoft.com/en-us/graph/api/dynamics-taxarea-delete?view=graph-rest-beta) | none | Deletes a tax area object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The unique ID of the tax area. Non-editable. |
| code | string, maximum size 20 | The code of the tax area. |
| displayName | string, maximum size 50 | The display name of the tax area. |
| taxType | string | The tax type of the tax area. |
| lastModifiedDateTime | datetime | The last datetime the tax area was modified. Read-Only. |

## Relationships

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "GUID",
  "code": "String",
  "displayName": "String",
  "taxType": "String",
  "lastModifiedDateTime": "datetime"
}
```
