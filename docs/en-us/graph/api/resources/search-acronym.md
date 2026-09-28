<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# acronym resource type

Namespace: microsoft.graph.search

Represents an acronym that is an administrative answer in Microsoft Search results to define common acronyms in an organization.

Inherits from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/search-searchentity-list-acronyms?view=graph-rest-1.0) | [microsoft.graph.search.acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) collection | Get a list of the [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/search-searchentity-post-acronyms?view=graph-rest-1.0) | [microsoft.graph.search.acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) | Create a new [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/search-acronym-get?view=graph-rest-1.0) | [microsoft.graph.search.acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) | Read the properties and relationships of an [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/search-acronym-update?view=graph-rest-1.0) | [microsoft.graph.search.acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) | Update the properties of an [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/search-acronym-delete?view=graph-rest-1.0) | None | Delete an [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A brief description of the acronym that gives users more information about the acronym and what it stands for. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| displayName | String | The actual short form or acronym. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| id | String | The unique identifier \(GUID\) for the acronym. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Details of the user who created or last modified the acronym. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the acronym was created or last edited. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). Read-only. |
| standsFor | String | What the acronym stands for. |
| state | microsoft.graph.search.answerState | State of the acronym. The possible values are: `published`, `draft`, `excluded`, `unknownFutureValue`. |
| webUrl | String | The URL of the page or website where users can go for more information about the acronym. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.search.acronym",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "standsFor": "String",
  "state": "String",
  "webUrl": "String"
}
```
