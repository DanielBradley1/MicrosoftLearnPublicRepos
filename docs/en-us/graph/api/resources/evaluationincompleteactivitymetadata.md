<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/evaluationincompleteactivitymetadata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# evaluationIncompleteActivityMetadata resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents metadata for a Secure by Default \(SBD\) policy evaluation that couldn't be completed because of a platform limit, extraction or classification failure, supporting-service failure, or enforcement failure.

Inherits from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta).

Use this type only in the **contentToProcess.contentEntries** collection of a request to [create a contentActivity](https://learn.microsoft.com/en-us/graph/api/activitiescontainer-post-contentactivities?view=graph-rest-beta). This type isn't supported by the **processContent** or **processContentAsync** APIs. Use the `@odata.type` value `#microsoft.graph.evaluationIncompleteActivityMetadata` to identify an entry of this type.

The service derives the audit organization, workload, and operation from the authenticated tenant, **contentToProcess.integratedAppMetadata.name**, and **contentToProcess.activityMetadata.activity**, respectively. Item details reuse inherited properties such as **identifier**, **name**, and **length**. The service resolves additional audit context through runtime data lookups.

The service records this metadata as a `ComplianceEvaluationIncomplete` \(`506`\) audit record. You don't specify a record type in the request.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | [contentBase](https://learn.microsoft.com/en-us/graph/api/resources/contentbase?view=graph-rest-beta) | The content that was evaluated, represented as text or binary data. Don't include this property when you create a content activity. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| contentCategory | [contentCategory](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#contentcategory-values) | The type of content. The possible values are: `none`, `ai`, `unknownFutureValue`. The default value is `ai`, which refers to AI-generated content. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| correlationId | String | An identifier used to group related content entries or correlate the audit record with related evaluation telemetry. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the evaluated content or activity was created. Required. The timestamp is always in UTC. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| errorAction | [errorActions](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#erroractions-values) | The action taken when policy evaluation couldn't be completed. Required. This flagged enumeration allows multiple members to be selected simultaneously. For example, `audit,block` indicates that the activity was audited and blocked. The possible values are: `none`, `audit`, `block`, `unknownFutureValue`. Don't combine `none` with another value. |
| identifier | String | A unique identifier for the content or activity in the enforcement plane; for example, a message ID, file path, or file URL. Required. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| inspectionIncompleteReason | [evaluationErrorDetail](https://learn.microsoft.com/en-us/graph/api/resources/evaluationerrordetail?view=graph-rest-beta) | The structured reason why inspection couldn't be completed. Required. The object requires **errorCategory**, **errorType**, and **errorMessage**. |
| isTruncated | Boolean | Indicates whether the supplied content was shortened from its original form. Required. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| length | Int64 | The length of the original content in bytes. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| modifiedDateTime | DateTimeOffset | The date and time when the evaluated content was last modified. Required. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| name | String | A descriptive name for the content or activity; for example, a file name or interaction name. Required. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| sequenceNumber | Int64 | A sequence number that indicates the order in which related content was generated or should be processed. Required when **correlationId** is used. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.evaluationIncompleteActivityMetadata",
  "content": { "@odata.type": "microsoft.graph.contentBase" },
  "contentCategory": "String",
  "correlationId": "String",
  "createdDateTime": "DateTimeOffset",
  "errorAction": "String",
  "identifier": "String",
  "inspectionIncompleteReason": {
    "@odata.type": "microsoft.graph.evaluationErrorDetail"
  },
  "isTruncated": "Boolean",
  "length": "Int64",
  "modifiedDateTime": "DateTimeOffset",
  "name": "String",
  "sequenceNumber": "Int64"
}
```
