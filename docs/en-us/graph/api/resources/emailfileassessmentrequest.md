<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/emailfileassessmentrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# emailFileAssessmentRequest resource type

Represents a resource that creates and retrieves an email file threat assessment. The email file can be an .eml file type.

Inherits from [threatAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentrequest?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/informationprotection-post-threatassessmentrequests?view=graph-rest-1.0) | [emailFileAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/emailfileassessmentrequest?view=graph-rest-1.0) | Create a new email file assessment request by posting an **emailFileAssessmentRequest** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/threatassessmentrequest-get?view=graph-rest-1.0) | [emailFileAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/emailfileassessmentrequest?view=graph-rest-1.0) | Read the properties and relationships of an **emailFileAssessmentRequest** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentData | String | Base64 encoded .eml email file content. The file content can't fetch back because it isn't stored. |
| destinationRoutingReason | [mailDestinationRoutingReason](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#maildestinationroutingreason-values) | The reason for mail routed to its destination. The possible values are: `none`, `mailFlowRule`, `safeSender`, `blockedSender`, `advancedSpamFiltering`, `domainAllowList`, `domainBlockList`, `notInAddressBook`, `firstTimeSender`, `autoPurgeToInbox`, `autoPurgeToJunk`, `autoPurgeToDeleted`, `outbound`, `notJunk`, `junk`. |
| category | [threatCategory](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatcategory-values) | The threat category. The possible values are: `spam`, `phishing`, `malware`. |
| contentType | [threatAssessmentContentType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatassessmentcontenttype-values) | The content type of threat assessment. The possible values are: `mail`, `url`, `file`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The threat assessment request creator. |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| expectedAssessment | [threatExpectedAssessment](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatexpectedassessment-values) | The expected assessment from submitter. The possible values are: `block`, `unblock`. |
| id | String | The threat assessment request ID is a globally unique identifier \(GUID\). |
| recipientEmail | String | The mail recipient whose policies are used to assess the mail. |
| requestSource | [threatAssessmentRequestSource](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatassessmentrequestsource-values) | The source of threat assessment request. The possible values are: `administrator`. |
| status | [threatAssessmentStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatassessmentstatus-values) | The assessment process status. The possible values are: `pending`, `completed`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| results | [threatAssessmentResult](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentresult?view=graph-rest-1.0) collection | A collection of threat assessment results. Read-only. By default, a `GET /threatAssessmentRequests/{id}` doesn't return this property unless you apply `$expand` on it. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "category": "String",
  "contentData": "String",
  "contentType": "String",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "destinationRoutingReason": "String",
  "expectedAssessment": "String",
  "id": "String (identifier)",
  "recipientEmail": "String",
  "requestSource": "String",
  "status": "String"
}
```
