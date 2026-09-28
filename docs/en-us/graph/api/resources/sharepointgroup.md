<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# sharePointGroup resource type

Namespace: microsoft.graph

Represents a cohort of users or Microsoft 365 groups that are localized to a SharePoint Embedded container.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-list-sharepointgroups?view=graph-rest-1.0) | [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) collection | Get a list of [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-post-sharepointgroups?view=graph-rest-1.0) | [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) | Create a new [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/sharepointgroup-get?view=graph-rest-1.0) | [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) | Read the properties and relationships of a [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/sharepointgroup-update?view=graph-rest-1.0) | [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) | Update the properties of a [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-delete-sharepointgroups?view=graph-rest-1.0) | None | Delete a [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) object that is local to a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [List SharePoint group members](https://learn.microsoft.com/en-us/graph/api/sharepointgroup-list-members?view=graph-rest-1.0) | [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) collection | Get a list of the [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) objects and their properties. |
| [Create SharePoint group member](https://learn.microsoft.com/en-us/graph/api/sharepointgroup-post-members?view=graph-rest-1.0) | [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) | Create a new [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) object within a [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The user-visible description of the **sharePointGroup**. Read-write. |
| id | String | The unique stable identifier of the **sharePointGroup**. This ID is unique only within the context of a single SharePoint Embedded container. Read-only. |
| principalId | String | The principal ID of the SharePoint group in the tenant. Read-only. |
| title | String | The user-visible title of the **sharePointGroup**. Read-write. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) collection | The set of members in the **sharePointGroup**. Read-write. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointGroup",
  "description": "String",
  "id": "String (identifier)",
  "principalId": "String",
  "title": "String"
}
```
