<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driveitemuploadableproperties?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# driveItemUploadableProperties resource type

Namespace: microsoft.graph

Represents an item being uploaded when [creating an upload session](https://learn.microsoft.com/en-us/graph/api/driveitem-createuploadsession?view=graph-rest-1.0).

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "fileSize": 1024,
  "fileSystemInfo": {"@odata.type": "microsoft.graph.fileSystemInfo"},
  "name": "String"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Provides a user-visible description of the item. Read-write. Only on OneDrive Personal. |
| driveItemSource | [driveItemSource](https://learn.microsoft.com/en-us/graph/api/resources/driveitemsource?view=graph-rest-1.0) | Information about the drive item source. Read-write. Only on OneDrive for Business and SharePoint. |
| fileSize | Int64 | Provides an expected file size to perform a quota check before uploading. Only on OneDrive Personal. |
| fileSystemInfo | [fileSystemInfo](https://learn.microsoft.com/en-us/graph/api/resources/filesysteminfo?view=graph-rest-1.0) | File system information on client. Read-write. |
| mediaSource | [mediaSource](https://learn.microsoft.com/en-us/graph/api/resources/mediasource?view=graph-rest-1.0) | Media source information. Read-write. Only on OneDrive for Business and SharePoint. |
| name | String | The name of the item \(filename and extension\). Read-write. |
