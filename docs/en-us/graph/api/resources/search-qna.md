<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# qna resource type

Namespace: microsoft.graph.search

Represents a question and answer \(Q&A\) in Microsoft Search. Q&As are administrative answer results in the search results page that provide answers for specific search keywords. Q&As allow administrators to answer the user's questions directly in search instead of providing a link to a webpage. A Q&A has many properties that allow administrators to make common resources more accessible in their organization.

Inherits from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/search-searchentity-list-qnas?view=graph-rest-1.0) | [microsoft.graph.search.qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) collection | Get a list of the [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/search-searchentity-post-qnas?view=graph-rest-1.0) | [microsoft.graph.search.qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) | Create a new [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/search-qna-get?view=graph-rest-1.0) | [microsoft.graph.search.qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) | Read the properties and relationships of a [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/search-qna-update?view=graph-rest-1.0) | [microsoft.graph.search.qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) | Update the properties of a [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/search-qna-delete?view=graph-rest-1.0) | None | Delete a [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| availabilityEndDateTime | DateTimeOffset | Date and time when the QnA stops appearing as a search result. Set as `null` for always available. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| availabilityStartDateTime | DateTimeOffset | Date and time when the QnA starts to appear as a search result. Set as `null` for always available. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | Answer that is displayed in search results. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| displayName | String | Question that is displayed in search results. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| groupIds | String collection | The list of security groups that are able to view this QnA. |
| id | String | The unique identifier \(GUID\) for the QnA. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| isSuggested | Boolean | `True` if a user or Microsoft suggested this QnA to the admin. Read-only. |
| keywords | [microsoft.graph.search.answerKeyword](https://learn.microsoft.com/en-us/graph/api/resources/search-answerkeyword?view=graph-rest-1.0) | Keywords that trigger this QnA to appear in search results. |
| languageTags | String collection | A list of geographically specific language names in which this QnA can be viewed. Each language tag value follows the pattern {language}-{region}. For example, `en-us` is English as used in the United States. For the list of possible values, see [Supported language tags](https://learn.microsoft.com/en-us/graph/api/resources/search-api-answers-overview?view=graph-rest-1.0#supported-language-tags). |
| lastModifiedBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Details of the user who created or last modified the QnA. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the QnA was created or last edited. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). Read-only. |
| platforms | microsoft.graph.devicePlatformType collection | List of devices and operating systems that are able to view this QnA. The possible values are: `android`, `androidForWork`, `ios`, `macOS`, `windowsPhone81`, `windowsPhone81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidASOP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`. |
| state | microsoft.graph.search.answerState | State of the QnA. The possible values are: `published`, `draft`, `excluded`, `unknownFutureValue`. |
| targetedVariations | [microsoft.graph.search.answerVariant](https://learn.microsoft.com/en-us/graph/api/resources/search-answervariant?view=graph-rest-1.0) collection | Variations of a QnA for different countries/regions or devices. Use when you need to show different content to users based on their device, country/region, or both. The date and group settings apply to all variations. |
| webUrl | String | The URL link for the QnA. When users select this QnA from the search results, they're directed to the specified URL. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.search.qna",
  "availabilityEndDateTime": "String (timestamp)",
  "availabilityStartDateTime": "String (timestamp)",
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
  "state": "String",
  "targetedVariations": [{"@odata.type": "microsoft.graph.search.answerVariant"}],
  "webUrl": "String"
}
```
