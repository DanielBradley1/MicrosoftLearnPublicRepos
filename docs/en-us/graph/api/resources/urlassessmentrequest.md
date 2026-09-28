<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/urlassessmentrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# urlAssessmentRequest resource type

Used to create and retrieve a URL threat assessment, derived from [threatAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentrequest?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/informationprotection-post-threatassessmentrequests?view=graph-rest-1.0) | [urlAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/urlassessmentrequest?view=graph-rest-1.0) | Create a new URL assessment request by posting an **urlAssessmentRequest** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/threatassessmentrequest-get?view=graph-rest-1.0) | [urlAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/urlassessmentrequest?view=graph-rest-1.0) | Read the properties and relationships of a **urlAssessmentRequest** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | [threatCategory](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatcategory-values) | The threat category. The possible values are: `spam`, `phishing`, `malware`. |
| contentType | [threatAssessmentContentType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatassessmentcontenttype-values) | The content type of the threat assessment. The possible values are: `mail`, `url`, `file`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The threat assessment request creator. |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| expectedAssessment | [threatExpectedAssessment](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatexpectedassessment-values) | The expected assessment from the submitter. The possible values are: `block`, `unblock`. |
| id | String | The threat assessment request ID is a globally unique identifier \(GUID\). |
| requestSource | [threatAssessmentRequestSource](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatassessmentrequestsource-values) | The source of the threat assessment request. The possible values are: `administrator`. |
| status | [threatAssessmentStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatassessmentstatus-values) | The assessment process status. The possible values are: `pending`, `completed`. |
| url | String | The URL string. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| results | [threatAssessmentResult](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentresult?view=graph-rest-1.0) collection | A collection of threat assessment results. Read-only. By default, a `GET /threatAssessmentRequests/{id}` doesn't return this property unless you apply `$expand` on it. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "url": "String",
  "category": "String",
  "contentType": "String",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "expectedAssessment": "String",
  "id": "String (identifier)",
  "requestSource": "String",
  "status": "String"
}
```
