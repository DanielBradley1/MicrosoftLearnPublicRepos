<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/uploadsession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-04 -->

# uploadSession resource type

Namespace: microsoft.graph

The **uploadSession** resource provides information about how to upload large files to OneDrive, OneDrive for Business, or SharePoint document libraries, or to Outlook [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) and [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) items as attachments.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expirationDateTime | DateTimeOffset | The date and time in UTC that the upload session expires. The complete file must be uploaded before this expiration time is reached. Each fragment uploaded during the session extends the expiration time. |
| nextExpectedRanges | String collection | A collection of byte ranges that the server is missing for the file. These ranges are zero indexed and of the format "start-end" \(for example "0-26" to indicate the first 27 bytes of the file\). When uploading files as Outlook attachments, instead of a collection of ranges, this property always indicates a single value "{start}", the location in the file where the next upload should begin. |
| uploadUrl | String | The URL endpoint that accepts PUT requests for byte ranges of the file. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "uploadUrl": "https://sn3302.up.1drv.com/up/fe6987415ace7X4e1eF866337",
  "expirationDateTime": "2015-01-29T09:21:55.523Z",
  "nextExpectedRanges": ["0-"]
}
```

## Related content

- [Attach large files to Outlook messages and events as attachments](https://learn.microsoft.com/en-us/graph/outlook-large-attachments)
- [Upload large files with an upload session](https://learn.microsoft.com/en-us/graph/api/driveitem-createuploadsession?view=graph-rest-1.0)
