<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleuserinitiatedenrollmentprofile-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Create appleUserInitiatedEnrollmentProfile

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementServiceConfig.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementServiceConfig.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/appleUserInitiatedEnrollmentProfiles
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the appleUserInitiatedEnrollmentProfile object.

The following table shows the properties that are required when you create the appleUserInitiatedEnrollmentProfile.

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultEnrollmentType | [appleUserInitiatedEnrollmentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmenttype?view=graph-rest-beta) | The default profile enrollment type. Possible values are: `unknown`, `device`, `user`, `accountDrivenUserEnrollment`, `webDeviceEnrollment`, `unknownFutureValue`. |
| availableEnrollmentTypeOptions | [appleOwnerTypeEnrollmentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleownertypeenrollmenttype?view=graph-rest-beta) collection | List of available enrollment type options |
| id | String | The GUID for the object |
| displayName | String | Name of the profile |
| description | String | Description of the profile |
| priority | Int32 | Priority, 0 is highest |
| platform | [devicePlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deviceplatformtype?view=graph-rest-beta) | The platform of the Device. Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidAOSP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`, `windowsMobileApplicationManagement`. |
| createdDateTime | DateTimeOffset | Profile creation time |
| lastModifiedDateTime | DateTimeOffset | Profile last modified time |

## Response

If successful, this method returns a `201 Created` response code and a [appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/appleUserInitiatedEnrollmentProfiles
Content-type: application/json
Content-length: 439

{
  "@odata.type": "#microsoft.graph.appleUserInitiatedEnrollmentProfile",
  "defaultEnrollmentType": "device",
  "availableEnrollmentTypeOptions": [
    {
      "@odata.type": "microsoft.graph.appleOwnerTypeEnrollmentType",
      "ownerType": "company",
      "enrollmentType": "device"
    }
  ],
  "displayName": "Display Name value",
  "description": "Description value",
  "priority": 8,
  "platform": "androidForWork"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 611

{
  "@odata.type": "#microsoft.graph.appleUserInitiatedEnrollmentProfile",
  "defaultEnrollmentType": "device",
  "availableEnrollmentTypeOptions": [
    {
      "@odata.type": "microsoft.graph.appleOwnerTypeEnrollmentType",
      "ownerType": "company",
      "enrollmentType": "device"
    }
  ],
  "id": "5a11d98e-d98e-5a11-8ed9-115a8ed9115a",
  "displayName": "Display Name value",
  "description": "Description value",
  "priority": 8,
  "platform": "androidForWork",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00"
}
```
