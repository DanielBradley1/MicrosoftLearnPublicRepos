<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-powerliftdownloadrequest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# powerliftDownloadRequest resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Request used to download app diagnostic files.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| powerliftId | Guid | The unique id for the request |
| files | String collection | The list of files to download |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.powerliftDownloadRequest",
  "powerliftId": "Guid",
  "files": [
    "String"
  ]
}
```
