<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailassessmentrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# mailAssessmentRequest resource type

Used to create and retrieve a mail threat assessment, derived from [threatAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/threatassessmentrequest?view=graph-rest-1.0).

When you create a mail threat assessment request, the mail should be received by the user specified in `recipientEmail`. Delegated [Mail permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#mail-permissions) \(Mail.Read or Mail.Read.Shared\) are required to access the mail received by the user or shared by someone else.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/informationprotection-post-threatassessmentrequests?view=graph-rest-1.0) | [mailAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/mailassessmentrequest?view=graph-rest-1.0) | Create a new mail assessment request by posting a **mailAssessmentRequest** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/threatassessmentrequest-get?view=graph-rest-1.0) | [mailAssessmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/mailassessmentrequest?view=graph-rest-1.0) | Read the properties and relationships of a **mailAssessmentRequest** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | [threatCategory](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatcategory-values) | The threat category. The possible values are: `spam`, `phishing`, `malware`. |
| contentType | [threatAssessmentContentType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatassessmentcontenttype-values) | The content type of threat assessment. The possible values are: `mail`, `url`, `file`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The threat assessment request creator. |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| destinationRoutingReason | [mailDestinationRoutingReason](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#maildestinationroutingreason-values) | The reason for mail routed to its destination. The possible values are: `none`, `mailFlowRule`, `safeSender`, `blockedSender`, `advancedSpamFiltering`, `domainAllowList`, `domainBlockList`, `notInAddressBook`, `firstTimeSender`, `autoPurgeToInbox`, `autoPurgeToJunk`, `autoPurgeToDeleted`, `outbound`, `notJunk`, `junk`. |
| expectedAssessment | [threatExpectedAssessment](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#threatexpectedassessment-values) | The expected assessment from submitter. The possible values are: `block`, `unblock`. |
| id | String | The threat assessment request ID is a globally unique identifier \(GUID\). |
| messageUri | String | The resource URI of the mail message for assessment. |
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
  "destinationRoutingReason": "String",
  "messageUri": "String",
  "recipientEmail": "String",
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
