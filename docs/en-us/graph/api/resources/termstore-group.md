<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/termstore-group?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# Group resource type

Namespace: microsoft.graph.termStore

Represents a group used in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). A group is a logical hierarchy that contains a collection of sets under it.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/termstore-group-post?view=graph-rest-1.0) | [microsoft.graph.termStore.group](https://learn.microsoft.com/en-us/graph/api/resources/termstore-group?view=graph-rest-1.0) | Create a group in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/termstore-group-get?view=graph-rest-1.0) | [microsoft.graph.termStore.group](https://learn.microsoft.com/en-us/graph/api/resources/termstore-group?view=graph-rest-1.0) | Retrieve the data of a group in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/termstore-group-delete?view=graph-rest-1.0) | None | Delete a group in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Date and time of the group creation. Read-only. |
| description | string | Description that gives details on the term usage. |
| displayName | string | Name of the group. |
| id | string | Unique identifier of the group. Read-Only. |
| parentSiteId | string | ID of the parent site of this group. |
| scope | string | Returns the type of the group. The possible values are: `global`, `system`, and `siteCollection`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sets | [microsoft.graph.termStore.set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) collection | All sets under the group in a term [store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0). |

## JSON representation

The following is a JSON representation of a **group** resource.

```json
{
  "@odata.type": "#microsoft.graph.termStore.group",
  "createdDateTime": "string (timestamp)",
  "description": "string",
  "displayName": "string",
  "id": "string",
  "parentSiteId" : "string",
  "scope" : "microsoft.graph.termStore.groupScope"
}
```
