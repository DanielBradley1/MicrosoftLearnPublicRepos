<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# appLogCollectionRequest resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity for AppLogCollectionRequest contains all logs values.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List appLogCollectionRequests](https://learn.microsoft.com/en-us/graph/api/intune-devices-applogcollectionrequest-list?view=graph-rest-1.0) | [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0) collection | List properties and relationships of the [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0) objects. |
| [Get appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/intune-devices-applogcollectionrequest-get?view=graph-rest-1.0) | [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0) | Read properties and relationships of the [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0) object. |
| [Create appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/intune-devices-applogcollectionrequest-create?view=graph-rest-1.0) | [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0) | Create a new [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0) object. |
| [Delete appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/intune-devices-applogcollectionrequest-delete?view=graph-rest-1.0) | None | Deletes a [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0). |
| [Update appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/intune-devices-applogcollectionrequest-update?view=graph-rest-1.0) | [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0) | Update the properties of a [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0) object. |
| [createDownloadUrl action](https://learn.microsoft.com/en-us/graph/api/intune-devices-applogcollectionrequest-createdownloadurl?view=graph-rest-1.0) | [appLogCollectionDownloadDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectiondownloaddetails?view=graph-rest-1.0) |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique Identifier. This is userId\_DeviceId\_AppId id. |
| status | [appLogUploadState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-apploguploadstate?view=graph-rest-1.0) | Indicates the status for the app log collection request if it is pending, completed or failed, Default is pending. The possible values are: `pending`, `completed`, `failed`, `unknownFutureValue`. |
| errorMessage | String | Indicates error message if any during the upload process. |
| customLogFolders | String collection | List of log folders. |
| completedDateTime | DateTimeOffset | Time at which the upload log request reached a completed state if not completed yet NULL will be returned. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.appLogCollectionRequest",
  "id": "String (identifier)",
  "status": "String",
  "errorMessage": "String",
  "customLogFolders": [
    "String"
  ],
  "completedDateTime": "String (timestamp)"
}
```
