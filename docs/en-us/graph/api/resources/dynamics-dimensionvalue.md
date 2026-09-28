<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-dimensionvalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# dimensionValue resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a dimension value in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get dimension](https://learn.microsoft.com/en-us/graph/api/dynamics-dimensionvalue-get?view=graph-rest-beta) | dimensionValues | Gets a dimension value object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The unique ID of the item. |
| code | string, maximum size 20 | The dimension value code. |
| displayName | string | Specifies the dimension value's name. This name appears where the dimension value is used. |
| lastModifiedDateTime | datetime | The last datetime the dimension value was modified. |

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
