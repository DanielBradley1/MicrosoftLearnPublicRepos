<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importeddeviceidentity-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update importedDeviceIdentity

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementServiceConfig.ReadWrite.All, DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementServiceConfig.ReadWrite.All, DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/importedDeviceIdentities/{importedDeviceIdentityId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Id of the imported device identity |
| importedDeviceIdentifier | String | Imported Device Identifier |
| importedDeviceIdentityType | [importedDeviceIdentityType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentitytype?view=graph-rest-beta) | Type of Imported Device Identity. Possible values are: `unknown`, `imei`, `serialNumber`, `manufacturerModelSerial`. |
| lastModifiedDateTime | DateTimeOffset | Last Modified DateTime of the description |
| createdDateTime | DateTimeOffset | Created Date Time of the device |
| lastContactedDateTime | DateTimeOffset | Last Contacted Date Time of the device |
| description | String | The description of the device |
| enrollmentState | [enrollmentState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enrollmentstate?view=graph-rest-beta) | The state of the device in Intune. Possible values are: `unknown`, `enrolled`, `pendingReset`, `failed`, `notContacted`, `blocked`. |
| platform | [platform](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-platform?view=graph-rest-beta) | The platform of the Device. Possible values are: `unknown`, `ios`, `android`, `windows`, `windowsMobile`, `macOS`, `visionOS`, `tvos`, `unknownFutureValue`. |

## Response

If successful, this method returns a `200 OK` response code and an updated [importedDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentity?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/importedDeviceIdentities/{importedDeviceIdentityId}
Content-type: application/json
Content-length: 332

{
  "@odata.type": "#microsoft.graph.importedDeviceIdentity",
  "importedDeviceIdentifier": "Imported Device Identifier value",
  "importedDeviceIdentityType": "imei",
  "lastContactedDateTime": "2016-12-31T23:58:44.2908994-08:00",
  "description": "Description value",
  "enrollmentState": "enrolled",
  "platform": "ios"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 504

{
  "@odata.type": "#microsoft.graph.importedDeviceIdentity",
  "id": "9f70a12f-a12f-9f70-2fa1-709f2fa1709f",
  "importedDeviceIdentifier": "Imported Device Identifier value",
  "importedDeviceIdentityType": "imei",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastContactedDateTime": "2016-12-31T23:58:44.2908994-08:00",
  "description": "Description value",
  "enrollmentState": "enrolled",
  "platform": "ios"
}
```
