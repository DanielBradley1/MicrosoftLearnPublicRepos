<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-devicelogcollectionresponse-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Update deviceLogCollectionResponse

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) object.

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
PATCH /deviceManagement/detectedApps/{detectedAppId}/managedDevices/{managedDeviceId}/logCollectionRequests/{deviceLogCollectionResponseId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier in the form of tenantId\_deviceId\_requestId. |
| status | [appLogUploadState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-apploguploadstate?view=graph-rest-1.0) | Indicates the status for the app log collection request if it is pending, completed or failed, Default is pending. The possible values are: `pending`, `completed`, `failed`, `unknownFutureValue`. |
| managedDeviceId | Guid | Indicates Intune device unique identifier. |
| requestedDateTimeUTC | DateTimeOffset | The DateTime of the request. |
| receivedDateTimeUTC | DateTimeOffset | The DateTime the request was received. |
| initiatedByUserPrincipalName | String | The UPN for who initiated the request. |
| expirationDateTimeUTC | DateTimeOffset | The DateTime of the expiration of the logs. |
| sizeInKB | Double | The size of the logs in KB. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| enrolledByUser | String | The User Principal Name \(UPN\) of the user that enrolled the device. |

## Response

If successful, this method returns a `200 OK` response code and an updated [deviceLogCollectionResponse](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionresponse?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceManagement/detectedApps/{detectedAppId}/managedDevices/{managedDeviceId}/logCollectionRequests/{deviceLogCollectionResponseId}
Content-type: application/json
Content-length: 508

{
  "@odata.type": "#microsoft.graph.deviceLogCollectionResponse",
  "status": "completed",
  "managedDeviceId": "3b336f00-6f00-3b33-006f-333b006f333b",
  "requestedDateTimeUTC": "2016-12-31T23:57:40.7845755-08:00",
  "receivedDateTimeUTC": "2016-12-31T23:59:48.6545758-08:00",
  "initiatedByUserPrincipalName": "Initiated By User Principal Name value",
  "expirationDateTimeUTC": "2017-01-01T00:02:49.2157996-08:00",
  "sizeInKB": 2.6666666666666665,
  "enrolledByUser": "Enrolled By User value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 557

{
  "@odata.type": "#microsoft.graph.deviceLogCollectionResponse",
  "id": "05fb97dc-97dc-05fb-dc97-fb05dc97fb05",
  "status": "completed",
  "managedDeviceId": "3b336f00-6f00-3b33-006f-333b006f333b",
  "requestedDateTimeUTC": "2016-12-31T23:57:40.7845755-08:00",
  "receivedDateTimeUTC": "2016-12-31T23:59:48.6545758-08:00",
  "initiatedByUserPrincipalName": "Initiated By User Principal Name value",
  "expirationDateTimeUTC": "2017-01-01T00:02:49.2157996-08:00",
  "sizeInKB": 2.6666666666666665,
  "enrolledByUser": "Enrolled By User value"
}
```
