<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-applogcollectionrequest-create?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Create appLogCollectionRequest

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementManagedDevices.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementManagedDevices.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/mobileAppTroubleshootingEvents/{mobileAppTroubleshootingEventId}/appLogCollectionRequests
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the appLogCollectionRequest object.

The following table shows the properties that are required when you create the appLogCollectionRequest.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique Identifier. This is userId\_DeviceId\_AppId id. |
| status | [appLogUploadState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-apploguploadstate?view=graph-rest-1.0) | Indicates the status for the app log collection request if it is pending, completed or failed, Default is pending. The possible values are: `pending`, `completed`, `failed`, `unknownFutureValue`. |
| errorMessage | String | Indicates error message if any during the upload process. |
| customLogFolders | String collection | List of log folders. |
| completedDateTime | DateTimeOffset | Time at which the upload log request reached a completed state if not completed yet NULL will be returned. |

## Response

If successful, this method returns a `201 Created` response code and a [appLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-applogcollectionrequest?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/v1.0/deviceManagement/mobileAppTroubleshootingEvents/{mobileAppTroubleshootingEventId}/appLogCollectionRequests
Content-type: application/json
Content-length: 257

{
  "@odata.type": "#microsoft.graph.appLogCollectionRequest",
  "status": "completed",
  "errorMessage": "Error Message value",
  "customLogFolders": [
    "Custom Log Folders value"
  ],
  "completedDateTime": "2016-12-31T23:58:52.3534526-08:00"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 306

{
  "@odata.type": "#microsoft.graph.appLogCollectionRequest",
  "id": "cca685ff-85ff-cca6-ff85-a6ccff85a6cc",
  "status": "completed",
  "errorMessage": "Error Message value",
  "customLogFolders": [
    "Custom Log Folders value"
  ],
  "completedDateTime": "2016-12-31T23:58:52.3534526-08:00"
}
```
