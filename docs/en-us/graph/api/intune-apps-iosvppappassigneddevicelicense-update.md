<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneddevicelicense-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update iosVppAppAssignedDeviceLicense

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceAppManagement/mobileApps/{mobileAppId}/microsoft.graph.iosVppApp/assignedLicenses/{iosVppAppAssignedLicenseId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userEmailAddress | String | The user email address. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userId | String | The user ID. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userName | String | The user name. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userPrincipalName | String | The user principal name. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| managedDeviceId | String | The managed device ID. |
| deviceName | String | The device name. |

## Response

If successful, this method returns a `200 OK` response code and an updated [iosVppAppAssignedDeviceLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneddevicelicense?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceAppManagement/mobileApps/{mobileAppId}/microsoft.graph.iosVppApp/assignedLicenses/{iosVppAppAssignedLicenseId}
Content-type: application/json
Content-length: 327

{
  "@odata.type": "#microsoft.graph.iosVppAppAssignedDeviceLicense",
  "userEmailAddress": "User Email Address value",
  "userId": "User Id value",
  "userName": "User Name value",
  "userPrincipalName": "User Principal Name value",
  "managedDeviceId": "Managed Device Id value",
  "deviceName": "Device Name value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 376

{
  "@odata.type": "#microsoft.graph.iosVppAppAssignedDeviceLicense",
  "id": "bed943d0-43d0-bed9-d043-d9bed043d9be",
  "userEmailAddress": "User Email Address value",
  "userId": "User Id value",
  "userName": "User Name value",
  "userPrincipalName": "User Principal Name value",
  "managedDeviceId": "Managed Device Id value",
  "deviceName": "Device Name value"
}
```
