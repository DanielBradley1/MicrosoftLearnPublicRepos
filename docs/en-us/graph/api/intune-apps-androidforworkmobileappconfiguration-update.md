<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-apps-androidforworkmobileappconfiguration-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Update androidForWorkMobileAppConfiguration

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceAppManagement/mobileAppConfigurations/{managedDeviceMobileAppConfigurationId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| targetedMobileApps | String collection | the associated app. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of Scope Tags for this App configuration entity. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| description | String | Admin provided description of the Device Configuration. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| displayName | String | Admin provided name of the device configuration. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| version | Int32 | Version of the device configuration. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| packageId | String | Android For Work app configuration package id. |
| payloadJson | String | Android For Work app configuration JSON payload. |
| permissionActions | [androidPermissionAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidpermissionaction?view=graph-rest-beta) collection | List of Android app permissions and corresponding permission actions. |
| profileApplicability | [androidProfileApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidprofileapplicability?view=graph-rest-beta) | Android Enterprise profile applicability \(AndroidWorkProfile, DeviceOwner, or default \(applies to both\)\). Possible values are: `default`, `androidWorkProfile`, `androidDeviceOwner`. |
| connectedAppsEnabled | Boolean | Setting to specify whether to allow ConnectedApps experience for this app. |
| credentialProviderRoleState | [androidAppCredentialProviderRoleState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidappcredentialproviderrolestate?view=graph-rest-beta) | Indicates whether the app is allowed to act as a credential provider. Applies to Android 14 and above. The default value is 'notConfigured'. Possible values are: 'notConfigured' and 'allowed'. When set to 'notConfigured', the Android OS will determine whether the app is allowed to act as a credential provider or not. Possible values are: `notConfigured`, `allowed`, `unknownFutureValue`. |

## Response

If successful, this method returns a `200 OK` response code and an updated [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceAppManagement/mobileAppConfigurations/{managedDeviceMobileAppConfigurationId}
Content-type: application/json
Content-length: 687

{
  "@odata.type": "#microsoft.graph.androidForWorkMobileAppConfiguration",
  "targetedMobileApps": [
    "Targeted Mobile Apps value"
  ],
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "description": "Description value",
  "displayName": "Display Name value",
  "version": 7,
  "packageId": "Package Id value",
  "payloadJson": "Payload Json value",
  "permissionActions": [
    {
      "@odata.type": "microsoft.graph.androidPermissionAction",
      "permission": "Permission value",
      "action": "autoGrant"
    }
  ],
  "profileApplicability": "androidWorkProfile",
  "connectedAppsEnabled": true,
  "credentialProviderRoleState": "allowed"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 859

{
  "@odata.type": "#microsoft.graph.androidForWorkMobileAppConfiguration",
  "id": "6204ae6d-ae6d-6204-6dae-04626dae0462",
  "targetedMobileApps": [
    "Targeted Mobile Apps value"
  ],
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "description": "Description value",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "displayName": "Display Name value",
  "version": 7,
  "packageId": "Package Id value",
  "payloadJson": "Payload Json value",
  "permissionActions": [
    {
      "@odata.type": "microsoft.graph.androidPermissionAction",
      "permission": "Permission value",
      "action": "autoGrant"
    }
  ],
  "profileApplicability": "androidWorkProfile",
  "connectedAppsEnabled": true,
  "credentialProviderRoleState": "allowed"
}
```
