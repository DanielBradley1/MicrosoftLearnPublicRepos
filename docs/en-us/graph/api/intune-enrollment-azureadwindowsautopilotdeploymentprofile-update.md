<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-enrollment-azureadwindowsautopilotdeploymentprofile-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# Update azureADWindowsAutopilotDeploymentProfile

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta) object.

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
PATCH /deviceManagement/windowsAutopilotDeploymentProfiles/{windowsAutopilotDeploymentProfileId}
PATCH /deviceManagement/windowsAutopilotDeviceIdentities/{windowsAutopilotDeviceIdentityId}/deploymentProfile
PATCH /deviceManagement/windowsAutopilotDeviceIdentities/{windowsAutopilotDeviceIdentityId}/intendedDeploymentProfile
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Profile Key Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| displayName | String | The display name of the deployment profile. Max allowed length is 200 chars. Returned by default. Supports: $select, $top, $skip, $orderby. $Search and $filter are not supported. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| description | String | A description of the deployment profile. Max allowed length is 1500 chars. Supports: $select, $top, $skip, $orderBy. $Search and $filter are not supported. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| language | String | The language code to be used when configuring the device. E.g. en-US. The default value is os-default. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported. Read-Only. Starting from May 2024 this property will no longer be supported and will be marked as deprecated. Use locale instead. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| locale | String | The locale \(language\) to be used when configuring the device. E.g. en-US. The default value is os-default. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The date and time of when the deployment profile was created. The value cannot be modified and is automatically populated when the profile was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported. Read-Only. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time of when the deployment profile was last modified. The value cannot be updated manually and is automatically populated when any changes are made to the profile. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported Read-Only. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| outOfBoxExperienceSettings | [outOfBoxExperienceSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-outofboxexperiencesettings?view=graph-rest-beta) | The Windows Autopilot Deployment Profile settings used by the Autopilot device for out-of-box experience. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported. Read-Only. Starting from May 2024 this property will no longer be supported and will be marked as deprecated. Use outOfBoxExperienceSetting instead. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| outOfBoxExperienceSetting | [outOfBoxExperienceSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-outofboxexperiencesetting?view=graph-rest-beta) | The Windows Autopilot Deployment Profile settings used by the device for the out-of-box experience. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| enrollmentStatusScreenSettings | [windowsEnrollmentStatusScreenSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsenrollmentstatusscreensettings?view=graph-rest-beta) | Enrollment status screen setting Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| extractHardwareHash | Boolean | Indicates whether the profile supports the extraction of hardware hash values and registration of the device into Windows Autopilot. When TRUE, indicates if hardware extraction and Windows Autopilot registration will happen on the next successful check-in. When FALSE, hardware hash extraction and Windows Autopilot registration will not happen. Default value is FALSE. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported. Read-Only. Starting from May 2024 this property will no longer be supported and will be marked as deprecated. Use hardwareHashExtractionEnabled instead. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| hardwareHashExtractionEnabled | Boolean | Indicates whether the profile supports the extraction of hardware hash values and registration of the device into Windows Autopilot. When TRUE, indicates if hardware extraction and Windows Autopilot registration will happen on the next successful check-in. When FALSE, hardware hash extraction and Windows Autopilot registration will not happen. Default value is FALSE. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| deviceNameTemplate | String | The template used to name the Autopilot device. This can be a custom text and can also contain either the serial number of the device, or a randomly generated number. The total length of the text generated by the template can be no more than 15 characters. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| deviceType | [windowsAutopilotDeviceType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdevicetype?view=graph-rest-beta) | The Windows device type that this profile is applicable to. Possible values include windowsPc, holoLens, and virtualMachine. The default is windowsPc. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta). Possible values are: `windowsPc`, `holoLens`, `surfaceHub2`, `surfaceHub2S`, `virtualMachine`, `unknownFutureValue`. |
| enableWhiteGlove | Boolean | Indicates whether the user is allowed to use Windows Autopilot for pre-provisioned deployment mode during Out of Box experience \(OOBE\). When TRUE, indicates that Windows Autopilot for pre-provisioned deployment mode is allowed. When false, Windows Autopilot for pre-provisioned deployment mode is not allowed. The default is FALSE. Read-Only. Starting from May 2024 this property will no longer be supported and will be marked as deprecated. Use preprovisioningAllowed instead. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| preprovisioningAllowed | Boolean | Indicates whether the user is allowed to use Windows Autopilot for pre-provisioned deployment mode during Out of Box experience \(OOBE\). When TRUE, indicates that Windows Autopilot for pre-provisioned deployment mode for OOBE is allowed to be used. When false, Windows Autopilot for pre-provisioned deployment mode for OOBE is not allowed. The default is FALSE. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of role scope tags for the deployment profile. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| managementServiceAppId | String | The Entra management service App ID which gets used during client device-based enrollment discovery. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |

## Response

If successful, this method returns a `200 OK` response code and an updated [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/windowsAutopilotDeploymentProfiles/{windowsAutopilotDeploymentProfileId}
Content-type: application/json
Content-length: 1628

{
  "@odata.type": "#microsoft.graph.azureADWindowsAutopilotDeploymentProfile",
  "displayName": "Display Name value",
  "description": "Description value",
  "language": "Language value",
  "locale": "Locale value",
  "outOfBoxExperienceSettings": {
    "@odata.type": "microsoft.graph.outOfBoxExperienceSettings",
    "hidePrivacySettings": true,
    "hideEULA": true,
    "userType": "standard",
    "deviceUsageType": "shared",
    "skipKeyboardSelectionPage": true,
    "hideEscapeLink": true
  },
  "outOfBoxExperienceSetting": {
    "@odata.type": "microsoft.graph.outOfBoxExperienceSetting",
    "privacySettingsHidden": true,
    "eulaHidden": true,
    "userType": "standard",
    "deviceUsageType": "shared",
    "keyboardSelectionPageSkipped": true,
    "escapeLinkHidden": true
  },
  "enrollmentStatusScreenSettings": {
    "@odata.type": "microsoft.graph.windowsEnrollmentStatusScreenSettings",
    "hideInstallationProgress": true,
    "allowDeviceUseBeforeProfileAndAppInstallComplete": true,
    "blockDeviceSetupRetryByUser": true,
    "allowLogCollectionOnInstallFailure": true,
    "customErrorMessage": "Custom Error Message value",
    "installProgressTimeoutInMinutes": 15,
    "allowDeviceUseOnInstallFailure": true
  },
  "extractHardwareHash": true,
  "hardwareHashExtractionEnabled": true,
  "deviceNameTemplate": "Device Name Template value",
  "deviceType": "holoLens",
  "enableWhiteGlove": true,
  "preprovisioningAllowed": true,
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "managementServiceAppId": "Management Service App Id value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1800

{
  "@odata.type": "#microsoft.graph.azureADWindowsAutopilotDeploymentProfile",
  "id": "e2ec4e69-4e69-e2ec-694e-ece2694eece2",
  "displayName": "Display Name value",
  "description": "Description value",
  "language": "Language value",
  "locale": "Locale value",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "outOfBoxExperienceSettings": {
    "@odata.type": "microsoft.graph.outOfBoxExperienceSettings",
    "hidePrivacySettings": true,
    "hideEULA": true,
    "userType": "standard",
    "deviceUsageType": "shared",
    "skipKeyboardSelectionPage": true,
    "hideEscapeLink": true
  },
  "outOfBoxExperienceSetting": {
    "@odata.type": "microsoft.graph.outOfBoxExperienceSetting",
    "privacySettingsHidden": true,
    "eulaHidden": true,
    "userType": "standard",
    "deviceUsageType": "shared",
    "keyboardSelectionPageSkipped": true,
    "escapeLinkHidden": true
  },
  "enrollmentStatusScreenSettings": {
    "@odata.type": "microsoft.graph.windowsEnrollmentStatusScreenSettings",
    "hideInstallationProgress": true,
    "allowDeviceUseBeforeProfileAndAppInstallComplete": true,
    "blockDeviceSetupRetryByUser": true,
    "allowLogCollectionOnInstallFailure": true,
    "customErrorMessage": "Custom Error Message value",
    "installProgressTimeoutInMinutes": 15,
    "allowDeviceUseOnInstallFailure": true
  },
  "extractHardwareHash": true,
  "hardwareHashExtractionEnabled": true,
  "deviceNameTemplate": "Device Name Template value",
  "deviceType": "holoLens",
  "enableWhiteGlove": true,
  "preprovisioningAllowed": true,
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "managementServiceAppId": "Management Service App Id value"
}
```
