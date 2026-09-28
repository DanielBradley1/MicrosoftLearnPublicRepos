<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/processconversationmetadata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-19 -->

# processConversationMetadata

Namespace: microsoft.graph

Represents metadata for a content entry that is part of a conversation, for example, a chat message, and an AI interaction.

Inherits from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessedResources\_v2 | [resourceAccessDetail](https://learn.microsoft.com/en-us/graph/api/resources/resourceaccessdetail?view=graph-rest-1.0) collection | Lists details about the resources accessed by AI agents, such as identifiers, access type, and status. |
| agents | [aiAgentInfo](https://learn.microsoft.com/en-us/graph/api/resources/aiagentinfo?view=graph-rest-1.0) collection | Indicates the information about an AI agent that participated in the preparation of the message. |
| content | [contentBase](https://learn.microsoft.com/en-us/graph/api/resources/contentbase?view=graph-rest-1.0) | Represents the actual content, either as text \([textContent](https://learn.microsoft.com/en-us/graph/api/resources/textcontent?view=graph-rest-1.0)\) or binary data \([binaryContent](https://learn.microsoft.com/en-us/graph/api/resources/binarycontent?view=graph-rest-1.0)\). This property is Optional if metadata alone is sufficient for policy evaluation. **Do not use for [contentActivities](https://learn.microsoft.com/en-us/graph/api/activitiescontainer-post-contentactivities?view=graph-rest-1.0)**. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| correlationId | String | An identifier used to group multiple related content entries \(for example, different parts of the same file upload, or related messages in a conversation\). Must be used with sequenceNumber \(described below\). Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | Required. Timestamp when the original content was created \(for example, file creation time, message sent time\). Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| identifier | String | Required. A unique identifier for this specific content entry within the context of the calling application or enforcement plane \(for example, message ID, file path/URL\). Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| isTruncated | Boolean | Required. Indicates if the provided **content** has been truncated from its original form \(for example, due to size limits\). Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| length | Int64 | The length of the original content in bytes. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| modifiedDateTime | DateTimeOffset | Required. Timestamp when the original content was last modified. For ephemeral content like messages, this might be the same as **createdDateTime**. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| name | String | Required. A descriptive name for the content \(for example, file name, web page title, or chat message\). Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| parentMessageId | String | Identifier of the parent message in a threaded conversation, if applicable. |
| plugins | [aiInteractionPlugin](https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionplugin?view=graph-rest-1.0) collection | List of plugins used during the generation of this message \(relevant for AI/bot interactions\). |
| sequenceNumber | Int64 | A sequence number indicating the order in which content was generated or should be processed, required when **correlationId** is used. Inherited from [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0). |
| accessedResources \(deprecated\) | String collection | List of resources \(for example, file URLs, web URLs\) accessed during the generation of this message \(relevant for bot interactions\). The **accessedResources** property is deprecated and stopped returning data on August 20, 2025. Going forward, use the **accessedResources\_v2** property. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.processConversationMetadata",
  "identifier": "String",
  "content": {
    "@odata.type": "microsoft.graph.contentBase"
  },
  "accessedResources": ["String"],
  "accessedResources_v2": [
    {
        "@odata.type": "microsoft.graph.resourceAccessDetail"
    }
  ],
  "agents": [
    {
        "@odata.type": "microsoft.graph.aiAgentInfo"
    }
  ],
  "name": "String",
  "correlationId": "String",
  "sequenceNumber": "Integer",
  "length": "Integer",
  "isTruncated": "Boolean",
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "parentMessageId": "String",
  "plugins": [
    {
      "@odata.type": "microsoft.graph.aiInteractionPlugin"
    }
  ]
}
```
