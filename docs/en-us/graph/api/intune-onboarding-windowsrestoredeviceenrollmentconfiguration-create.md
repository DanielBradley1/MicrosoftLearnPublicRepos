<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-onboarding-windowsrestoredeviceenrollmentconfiguration-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Create windowsRestoreDeviceEnrollmentConfiguration

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta) object.

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
POST /deviceManagement/deviceEnrollmentConfigurations
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the windowsRestoreDeviceEnrollmentConfiguration object.

The following table shows the properties that are required when you create the windowsRestoreDeviceEnrollmentConfiguration.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the account Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| displayName | String | The display name of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| description | String | The description of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| priority | Int32 | Priority is used when a user exists in multiple groups that are assigned enrollment configuration. Users are subject only to the configuration with the lowest priority value. Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | Created date time in UTC of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | Last modified date time in UTC of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| version | Int32 | The version of the device enrollment configuration Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| roleScopeTagIds | String collection | Optional role scope tags for the enrollment restrictions. Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) |
| deviceEnrollmentConfigurationType | [deviceEnrollmentConfigurationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceenrollmentconfigurationtype?view=graph-rest-beta) | Support for Enrollment Configuration Type Inherited from [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta). Possible values are: `unknown`, `limit`, `platformRestrictions`, `windowsHelloForBusiness`, `defaultLimit`, `defaultPlatformRestrictions`, `defaultWindowsHelloForBusiness`, `defaultWindows10EnrollmentCompletionPageConfiguration`, `windows10EnrollmentCompletionPageConfiguration`, `deviceComanagementAuthorityConfiguration`, `singlePlatformRestriction`, `unknownFutureValue`, `enrollmentNotificationsConfiguration`, `windowsRestore`. |
| state | [enablement](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enablement?view=graph-rest-beta) | Indicates the configuration state of the Windows Restore setting. Possible values are 'notConfigured', 'enabled', and 'disabled'. Default is: notConfigured. This is a tenant level default setting that is not targetable. This property's value is applied during Enrollment. Possible values are: `notConfigured`, `enabled`, `disabled`. |

## Response

If successful, this method returns a `201 Created` response code and a [windowsRestoreDeviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-windowsrestoredeviceenrollmentconfiguration?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/deviceEnrollmentConfigurations
Content-type: application/json
Content-length: 333

{
  "@odata.type": "#microsoft.graph.windowsRestoreDeviceEnrollmentConfiguration",
  "displayName": "Display Name value",
  "description": "Description value",
  "priority": 8,
  "version": 7,
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "deviceEnrollmentConfigurationType": "limit",
  "state": "enabled"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 505

{
  "@odata.type": "#microsoft.graph.windowsRestoreDeviceEnrollmentConfiguration",
  "id": "b5ef56f0-56f0-b5ef-f056-efb5f056efb5",
  "displayName": "Display Name value",
  "description": "Description value",
  "priority": 8,
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "version": 7,
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "deviceEnrollmentConfigurationType": "limit",
  "state": "enabled"
}
```
