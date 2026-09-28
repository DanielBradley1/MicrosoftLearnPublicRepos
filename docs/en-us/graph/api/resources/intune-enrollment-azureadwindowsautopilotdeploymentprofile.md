<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# azureADWindowsAutopilotDeploymentProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Autopilot Deployment Profile

Inherits from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List azureADWindowsAutopilotDeploymentProfiles](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-azureadwindowsautopilotdeploymentprofile-list?view=graph-rest-beta) | [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta) collection | List properties and relationships of the [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta) objects. |
| [Get azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-azureadwindowsautopilotdeploymentprofile-get?view=graph-rest-beta) | [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta) | Read properties and relationships of the [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta) object. |
| [Create azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-azureadwindowsautopilotdeploymentprofile-create?view=graph-rest-beta) | [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta) | Create a new [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta) object. |
| [Delete azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-azureadwindowsautopilotdeploymentprofile-delete?view=graph-rest-beta) | None | Deletes a [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta). |
| [Update azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-azureadwindowsautopilotdeploymentprofile-update?view=graph-rest-beta) | [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta) | Update the properties of a [azureADWindowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-azureadwindowsautopilotdeploymentprofile?view=graph-rest-beta) object. |

## Properties

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

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignedDevices | [windowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeviceidentity?view=graph-rest-beta) collection | The list of assigned devices for the profile. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |
| assignments | [windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeploymentprofileassignment?view=graph-rest-beta) collection | The list of group assignments for the profile. Inherited from [windowsAutopilotDeploymentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsautopilotdeploymentprofile?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.azureADWindowsAutopilotDeploymentProfile",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "language": "String",
  "locale": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "outOfBoxExperienceSettings": {
    "@odata.type": "microsoft.graph.outOfBoxExperienceSettings",
    "hidePrivacySettings": true,
    "hideEULA": true,
    "userType": "String",
    "deviceUsageType": "String",
    "skipKeyboardSelectionPage": true,
    "hideEscapeLink": true
  },
  "outOfBoxExperienceSetting": {
    "@odata.type": "microsoft.graph.outOfBoxExperienceSetting",
    "privacySettingsHidden": true,
    "eulaHidden": true,
    "userType": "String",
    "deviceUsageType": "String",
    "keyboardSelectionPageSkipped": true,
    "escapeLinkHidden": true
  },
  "enrollmentStatusScreenSettings": {
    "@odata.type": "microsoft.graph.windowsEnrollmentStatusScreenSettings",
    "hideInstallationProgress": true,
    "allowDeviceUseBeforeProfileAndAppInstallComplete": true,
    "blockDeviceSetupRetryByUser": true,
    "allowLogCollectionOnInstallFailure": true,
    "customErrorMessage": "String",
    "installProgressTimeoutInMinutes": 1024,
    "allowDeviceUseOnInstallFailure": true
  },
  "extractHardwareHash": true,
  "hardwareHashExtractionEnabled": true,
  "deviceNameTemplate": "String",
  "deviceType": "String",
  "enableWhiteGlove": true,
  "preprovisioningAllowed": true,
  "roleScopeTagIds": [
    "String"
  ],
  "managementServiceAppId": "String"
}
```
