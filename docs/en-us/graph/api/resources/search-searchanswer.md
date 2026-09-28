<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# searchAnswer resource type

Namespace: microsoft.graph.search

Represents the base type for other search answers.

Base type of [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0), [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0), and [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The search answer description that is shown on the search results page. |
| displayName | String | The search answer name that is displayed in search results. |
| id | String | The unique identifier \(GUID\) for the search answer. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Details of the user who created or last modified the search answer. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the search answer was created or last edited. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| webUrl | String | The URL link for the search answer. When users select this search answer from the search results, they are directed to the specified URL. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.search.searchAnswer",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "webUrl": "String"
}
```
