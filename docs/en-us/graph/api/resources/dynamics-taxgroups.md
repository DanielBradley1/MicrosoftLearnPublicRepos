<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-taxgroups?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# taxGroup resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a taxGroup object in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get tax groups](https://learn.microsoft.com/en-us/graph/api/dynamics-taxgroups-get?view=graph-rest-beta) | taxGroup | Get a tax group object. |
| [Create tax groups](https://learn.microsoft.com/en-us/graph/api/dynamics-create-taxgroups?view=graph-rest-beta) | taxGroup | Create a tax group object. |
| [Update tax groups](https://learn.microsoft.com/en-us/graph/api/dynamics-taxgroups-update?view=graph-rest-beta) | taxGroup | Update a tax group object. |
| [Delete tax groups](https://learn.microsoft.com/en-us/graph/api/dynamics-taxgroups-delete?view=graph-rest-beta) | None | Delete a tax group object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | Indicates the tax group. |
| displayName | String | The display name of the tax group. |
| id | String | The unique identifier for the tax group. Read-Only. |
| lastModifiedDateTime | datetime | The date and time when the tax group was last modified. Read-Only. |
| taxType | string | The tax type for the group. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "code": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "taxType": "String"
}
```
