<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-dimension?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# dimension resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a dimension in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get dimension](https://learn.microsoft.com/en-us/graph/api/dynamics-dimension-get?view=graph-rest-beta) | dimension | Gets a dimension. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The unique ID of the item. |
| code | string, maximum size 20 | The dimension code. |
| displayName | string | Specifies the dimension's name. This name appears where the dimension is used. |
| lastModifiedDateTime | datetime | The last datetime the dimension was modified. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "id": "GUID",
    "code": "string",
    "displayName": "string",
    "lastModifiedDateTime": "datetime"
}
```
