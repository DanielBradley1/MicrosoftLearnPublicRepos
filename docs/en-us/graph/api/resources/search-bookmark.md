<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# bookmark resource type

Namespace: microsoft.graph.search

Represents a bookmark that is an administrative answer in Microsoft Search results for common search queries in an organization. A bookmark has many properties that allow administrators to make common resources more accessible in their organization.

Inherits from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/search-searchentity-list-bookmarks?view=graph-rest-1.0) | [microsoft.graph.search.bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) collection | Get a list of the [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/search-searchentity-post-bookmarks?view=graph-rest-1.0) | [microsoft.graph.search.bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) | Create a new [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/search-bookmark-get?view=graph-rest-1.0) | [microsoft.graph.search.bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) | Read the properties and relationships of a [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/search-bookmark-update?view=graph-rest-1.0) | [microsoft.graph.search.bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) | Update the properties of a [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/search-bookmark-delete?view=graph-rest-1.0) | None | Delete a [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| availabilityEndDateTime | DateTimeOffset | Date and time when the bookmark stops appearing as a search result. Set as `null` for always available. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| availabilityStartDateTime | DateTimeOffset | Date and time when the bookmark starts to appear as a search result. Set as `null` for always available. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| categories | String collection | Categories commonly used to describe this bookmark. For example, `IT` and `HR`. |
| description | String | The bookmark description that is shown on the search results page. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| displayName | String | The bookmark name that is displayed in search results. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| groupIds | String collection | The list of security groups that are able to view this bookmark. |
| isSuggested | Boolean | `True` if this bookmark was suggested to the admin, by a user, or was mined and suggested by Microsoft. Read-only. |
| id | String | The unique identifier \(GUID\) for the bookmark. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| keywords | [microsoft.graph.search.answerKeyword](https://learn.microsoft.com/en-us/graph/api/resources/search-answerkeyword?view=graph-rest-1.0) | Keywords that trigger this bookmark to appear in search results. |
| languageTags | String collection | A list of geographically specific language names in which this bookmark can be viewed. Each language tag value follows the pattern {language}-{region}. For example, `en-us` is English as used in the United States. For the list of possible values, see [Supported language tags](https://learn.microsoft.com/en-us/graph/api/resources/search-api-answers-overview?view=graph-rest-1.0#supported-language-tags). |
| lastModifiedBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Details of the user who created or last modified the bookmark. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the bookmark was created or last edited. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). Read-only. |
| platforms | microsoft.graph.devicePlatformType collection | List of devices and operating systems that are able to view this bookmark. The possible values are: `android`, `androidForWork`, `ios`, `macOS`, `windowsPhone81`, `windowsPhone81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidASOP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`. |
| powerAppIds | String collection | List of Power Apps associated with this bookmark. If users add existing Power Apps to a bookmark, they can complete tasks directly on the search results page, such as entering vacation time or reporting expenses. |
| state | microsoft.graph.search.answerState | State of the bookmark. The possible values are: `published`, `draft`, `excluded`, `unknownFutureValue`. |
| targetedVariations | [microsoft.graph.search.answerVariant](https://learn.microsoft.com/en-us/graph/api/resources/search-answervariant?view=graph-rest-1.0) collection | Variations of a bookmark for different countries/regions or devices. Use when you need to show different content to users based on their device, country/region, or both. The date and group settings apply to all variations. |
| webUrl | String | The URL link for the bookmark. When users select this bookmark from the search results, they're directed to the specified URL. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.search.bookmark",
  "availabilityEndDateTime": "String (timestamp)",
  "availabilityStartDateTime": "String (timestamp)",
  "categories": ["String"],
  "description": "String",
  "displayName": "String",
  "groupIds": ["String"],
  "id": "String (identifier)",
  "isSuggested": "Boolean",
  "keywords": {"@odata.type": "microsoft.graph.search.answerKeyword"},
  "languageTags": ["String"],
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "platforms": ["String"],
  "powerAppIds": ["String"],
  "state": "String",
  "targetedVariations": [{"@odata.type": "microsoft.graph.search.answerVariant"}],
  "webUrl": "String"
}
```
