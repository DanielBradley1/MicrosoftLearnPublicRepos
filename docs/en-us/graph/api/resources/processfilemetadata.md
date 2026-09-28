<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/processfilemetadata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-19 -->

# processFileMetadata resource type

Namespace: microsoft.graph

Represents metadata for a content entry that is a file.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | [contentBase](https://learn.microsoft.com/en-us/graph/api/resources/contentbase?view=graph-rest-1.0) | Represents the actual content, either as text \(`textContent`\) or binary data \(`binaryContent`\). Optional if metadata alone is sufficient for policy evaluation. **Do not use for [contentActivities](https://learn.microsoft.com/en-us/graph/api/activitiescontainer-post-contentactivities?view=graph-rest-1.0).** Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| correlationId | String | An identifier used to group multiple related content entries \(for example, different parts of the same file upload, messages in a conversation\). Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | Required. Timestamp indicating when the original content was created \(for example, file creation time, message sent time\). Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| customProperties | [customMetadataDictionary](https://learn.microsoft.com/en-us/graph/api/resources/custommetadatadictionary?view=graph-rest-1.0) | A dictionary containing custom metadata associated with the file, potentially extracted by the calling application. |
| identifier | String | Required. A unique identifier for this specific content entry within the context of the calling application or enforcement plane \(for example, message ID, file path/URL\). Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| isTruncated | Boolean | Required. Indicates if the provided `content` has been truncated from its original form \(for example, due to size limits\). Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| length | Int64 | The length of the original content in bytes. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| modifiedDateTime | DateTimeOffset | Required. Timestamp indicating when the original content was last modified. For ephemeral content like messages, this might be the same as `createdDateTime`. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| name | String | Required. A descriptive name for the content \(for example, file name, web page title, `Chat Message`\). Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| ownerId | String | The unique identifier \(for example, Entra User ID or UPN\) of the owner of the file. |
| sequenceNumber | Int64 | A sequence number indicating the order in which content was generated or should be processed, required when `correlationId` is used. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.processFileMetadata",
  "identifier": "String", 
  "content": { "@odata.type": "microsoft.graph.binaryContent" }, 
  "name": "String", 
  "correlationId": "String",
  "sequenceNumber": "Int64",
  "length": "Int64",
  "isTruncated": "Boolean",
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "customProperties": { "@odata.type": "microsoft.graph.customMetadataDictionary" },
  "ownerId": "String"
}
```
