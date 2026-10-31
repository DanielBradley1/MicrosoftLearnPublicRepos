<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-29 -->

# groupResource resource type

Namespace: microsoft.graph

Represents the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) resource in PIM for groups. This entity extends [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/groupresource-get?view=graph-rest-1.0) | [groupResource](https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-1.0) | Read the properties of a [groupResource](https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-1.0) object. |
| [List](https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-list-resources?view=graph-rest-1.0) | [groupResource](https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-1.0) collection | Retrieve a list of [groupResource](https://learn.microsoft.com/en-us/graph/api/resources/groupresource?view=graph-rest-1.0) objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | `null`. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| id | String | The unique identifier for the group. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.groupResource",
  "deletedDateTime": "String (timestamp)",
  "id": "String (identifier)"
}
```
