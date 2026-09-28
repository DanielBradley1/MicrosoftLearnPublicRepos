<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/documentprocessingjob?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-12 -->

# documentProcessingJob resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains information related to the processing of a document or documents in a folder by an applied [contentModel](https://learn.microsoft.com/en-us/graph/api/resources/contentmodel?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/site-post-documentprocessingjobs?view=graph-rest-beta) | [documentProcessingJob](https://learn.microsoft.com/en-us/graph/api/resources/documentprocessingjob?view=graph-rest-beta) | Create a new **documentProcessingJob** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Date and time of item creation. Read-only. |
| Id | String | The ID of the document processing job. Read-only. |
| jobType | documentProcessingJobType | The document processing job type. The possible values are: `file`, `folder` |
| listItemUniqueId | String | The listItemUniqueId of the file, or folder to process. Use GET [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-beta) resource operation and read [sharepointIds](https://learn.microsoft.com/en-us/graph/api/resources/sharepointids?view=graph-rest-beta) property to get listItemUniqueId. |
| status | documentProcessingJobStatus | The document processing Job status. The possible values are: `inProgress`, `completed`, `failed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.documentProcessingJob",
  "id": "String (identifier)",
  "jobType": "String",
  "status": "String",
  "createdDateTime": "String (timestamp)",
  "listItemUniqueId": "String"
}
```
