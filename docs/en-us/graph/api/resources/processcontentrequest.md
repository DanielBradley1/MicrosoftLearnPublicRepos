<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/processcontentrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# processContentRequest resource type

Namespace: microsoft.graph

Defines the input payload for the [processContent](https://learn.microsoft.com/en-us/graph/api/userdatasecurityandgovernance-processcontent?view=graph-rest-1.0) and [processContentAsync](https://learn.microsoft.com/en-us/graph/api/tenantdatasecurityandgovernance-processcontentasync?view=graph-rest-1.0) actions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityMetadata | [microsoft.graph.activityMetadata](https://learn.microsoft.com/en-us/graph/api/resources/activitymetadata?view=graph-rest-1.0) | Metadata about the user activity \(like upload, download\) and location \(URL\). Required. |
| contentEntries | Collection\([microsoft.graph.processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0)\) | A collection of content entries to be processed. Each entry contains the content itself and its metadata. Use [conversation metadata](https://learn.microsoft.com/en-us/graph/api/resources/processconversationmetadata?view=graph-rest-1.0) for content like prompts and responses and [file metadata](https://learn.microsoft.com/en-us/graph/api/resources/processfilemetadata?view=graph-rest-1.0) for files. Required. |
| deviceMetadata | [microsoft.graph.deviceMetadata](https://learn.microsoft.com/en-us/graph/api/resources/devicemetadata?view=graph-rest-1.0) | Metadata about the device from which the content originates. Required. |
| integratedAppMetadata | [microsoft.graph.integratedApplicationMetadata](https://learn.microsoft.com/en-us/graph/api/resources/integratedapplicationmetadata?view=graph-rest-1.0) | Metadata about the integrated application making the request. Required. |
| protectedAppMetadata | [microsoft.graph.protectedApplicationMetadata](https://learn.microsoft.com/en-us/graph/api/resources/protectedapplicationmetadata?view=graph-rest-1.0) | Metadata about the protected application making the request. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.processContentRequest",
  "activityMetadata": {
    "@odata.type": "microsoft.graph.activityMetadata"
  },
  "contentEntries": [
    {
      "@odata.type": "microsoft.graph.processContentMetadataBase"
    }
  ],
  "deviceMetadata": {
    "@odata.type": "microsoft.graph.deviceMetadata"
  },
  "integratedAppMetadata": {
    "@odata.type": "microsoft.graph.integratedApplicationMetadata"
  },
  "protectedAppMetadata": {
    "@odata.type": "microsoft.graph.protectedApplicationMetadata"
  }
}
```
