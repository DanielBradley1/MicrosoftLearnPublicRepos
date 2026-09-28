<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# sharePointGroupMember resource type

Namespace: microsoft.graph

Represents a user or Microsoft 365 group within a [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/sharepointgroup-list-members?view=graph-rest-1.0) | [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) collection | Get a list of the [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/sharepointgroup-post-members?view=graph-rest-1.0) | [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) | Create a new [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) object within a [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/sharepointgroupmember-get?view=graph-rest-1.0) | [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) | Read the properties and relationships of a [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/sharepointgroup-delete-members?view=graph-rest-1.0) | None | Delete a [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) object from a [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique stable identifier of the **sharePointGroupMember**. Read-only. |
| identity | [sharePointIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentityset?view=graph-rest-1.0) | The identity represented by the **sharePointGroupMember** object. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointGroupMember",
  "id": "String (identifier)",
  "identity": {
    "@odata.type": "microsoft.graph.sharePointIdentitySet"
  }
}
```
