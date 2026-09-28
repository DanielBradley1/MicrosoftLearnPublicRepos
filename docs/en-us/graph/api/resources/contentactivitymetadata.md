<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contentactivitymetadata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# contentActivityMetadata resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents metadata for a content entry that records the outcome of enforcement after a DLP policy match.

Inherits from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | [contentBase](https://learn.microsoft.com/en-us/graph/api/resources/contentbase?view=graph-rest-beta) | Represents the actual content, either as text \([textContent](https://learn.microsoft.com/en-us/graph/api/resources/textcontent?view=graph-rest-beta)\) or binary data \([binaryContent](https://learn.microsoft.com/en-us/graph/api/resources/binarycontent?view=graph-rest-beta)\). Optional if metadata alone is sufficient for policy evaluation. **Do not use for [Create contentActivity](https://learn.microsoft.com/en-us/graph/api/activitiescontainer-post-contentactivities?view=graph-rest-beta).** Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| contentCategory | microsoft.graph.contentCategory | The type of content. The possible values are: `none`, `ai`, `unknownFutureValue`. The default value is `ai`, which refers to AI-generated content. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| correlationId | String | An identifier used to group multiple related content entries; for example, different parts of the same file upload or messages in a conversation. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the original content was created; for example, file creation time or message sent time. Required. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| enforcementResultStatus | enforcementResultStatus | Indicates the enforcement outcome reported by the enforcement plane after a DLP policy match. The possible values are: `success`, `missingOrInvalidConfiguration`, `userOverride`, `agentFailure`, `enforcementTimeout`, `oSOverride`, `processNonExistent`, `other`. |
| identifier | String | A unique identifier for this specific content entry within the context of the calling application or the enforcement plane; for example, message ID, file path, or file URL. Required. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| isTruncated | Boolean | Indicates whether the provided **content** was shortened from its original form; for example, due to size limits. Required. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| length | Int64 | The length of the original content in bytes. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| modifiedDateTime | DateTimeOffset | Date and time when the original content was last modified. For ephemeral content, such as messages, this property might be the same as **createdDateTime**. Required. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| name | String | A descriptive name for the content; for example, file name, web page title, or chat message. Required. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |
| recordType | [microsoft.graph.security.auditLogRecordType](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecordtype?view=graph-rest-beta) | The type of operation indicated by the record. Currently reserved to indicate `ComplianceDLPEnforcement`. |
| sequenceNumber | Int64 | A sequence number that indicates the order in which content was generated or should be processed. Required when **correlationId** is used. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.contentActivityMetadata",
  "content": { "@odata.type": "microsoft.graph.binaryContent" },
  "contentCategory": "String",
  "correlationId": "String",
  "createdDateTime": "String (timestamp)",
  "enforcementResultStatus": "String",
  "identifier": "String", 
  "isTruncated": "Boolean",
  "length": "Int64",
  "modifiedDateTime": "String (timestamp)",
  "name": "String", 
  "recordType": "String",
  "sequenceNumber": "Int64"
}
```
