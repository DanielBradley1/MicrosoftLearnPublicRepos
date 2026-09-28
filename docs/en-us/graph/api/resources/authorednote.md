<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authorednote?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# authoredNote resource type

Namespace: microsoft.graph

Represents the properties of a note written by an author.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| author | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Identity information about the note's author. |
| content | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The content of the note. |
| createdDateTime | DateTimeOffset | The date and time when the entity was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authoredNote",
  "author": {
    "@odata.type": "microsoft.graph.identity"
  },
  "content": {
    "@odata.type": "microsoft.graph.itemBody",
    "content": "String",
    "contentType": "String"
  },
  "createdDateTime": "String (timestamp)"
}
```
