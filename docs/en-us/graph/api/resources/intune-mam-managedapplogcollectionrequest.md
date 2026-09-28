<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedAppLogCollectionRequest resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The Managed App log collection response

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedAppLogCollectionRequests](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedapplogcollectionrequest-list?view=graph-rest-beta) | [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta) collection | List properties and relationships of the [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta) objects. |
| [Get managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedapplogcollectionrequest-get?view=graph-rest-beta) | [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta) | Read properties and relationships of the [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta) object. |
| [Create managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedapplogcollectionrequest-create?view=graph-rest-beta) | [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta) | Create a new [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta) object. |
| [Delete managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedapplogcollectionrequest-delete?view=graph-rest-beta) | None | Deletes a [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta). |
| [Update managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedapplogcollectionrequest-update?view=graph-rest-beta) | [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta) | Update the properties of a [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the managed app log collection request. This id is assigned during request creation time. Read-only. |
| managedAppRegistrationId | String | The unique identifier of the app instance for which diagnostic logs were collected. Read-only. |
| status | String | Indicates the status for the app log collection request - pending, completed or failed. Default is pending. |
| requestedBy | String | The user principal name associated with the request for the managed application log collection. Read-only. |
| requestedByUserPrincipalName | String | The user principal name associated with the request for the managed application log collection. Read-only. |
| requestedDateTime | DateTimeOffset | DateTime of when the log upload request was received. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Returned by default. Read-only. |
| completedDateTime | DateTimeOffset | DateTime of when the log upload request was completed. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Returned by default. Read-only. |
| userLogUploadConsent | [managedAppLogUploadConsent](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapploguploadconsent?view=graph-rest-beta) | Indicates whether the user associated with the device provided consent for the log collection. The user must consent before the diagnostic logs can be collected. accepted means the user consented. declined means the user declined. unknown is the default value. The Log Collection Request must be completed within 24 hours or it will be abandoned and deleted. Read-only. Possible values are: `unknown`, `declined`, `accepted`, `unknownFutureValue`. |
| uploadedLogs | [managedAppLogUpload](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogupload?view=graph-rest-beta) collection | The collection of log upload results as reported by each component on the device. Such components can be the application itself, the Mobile Application Management \(MAM\) SDK, and other on-device components that are requested to upload diagnostic logs. Read-only. |
| version | String | Version of the entity. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppLogCollectionRequest",
  "id": "String (identifier)",
  "managedAppRegistrationId": "String",
  "status": "String",
  "requestedBy": "String",
  "requestedByUserPrincipalName": "String",
  "requestedDateTime": "String (timestamp)",
  "completedDateTime": "String (timestamp)",
  "userLogUploadConsent": "String",
  "uploadedLogs": [
    {
      "@odata.type": "microsoft.graph.managedAppLogUpload",
      "managedAppComponent": "String",
      "managedAppComponentDescription": "String",
      "status": "String",
      "referenceId": "String"
    }
  ],
  "version": "String"
}
```
