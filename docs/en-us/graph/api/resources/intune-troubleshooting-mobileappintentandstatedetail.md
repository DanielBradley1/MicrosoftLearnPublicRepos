<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstatedetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# mobileAppIntentAndStateDetail resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Mobile App Intent and Install State for a given device.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationId | String | MobieApp identifier. |
| displayName | String | The admin provided or imported title of the app. |
| mobileAppIntent | [mobileAppIntent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintent?view=graph-rest-beta) | Mobile App Intent. Possible values are: `available`, `notAvailable`, `requiredInstall`, `requiredUninstall`, `requiredAndAvailableInstall`, `availableInstallWithoutEnrollment`, `exclude`. |
| displayVersion | String | Human readable version of the application |
| installState | [resultantAppState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-resultantappstate?view=graph-rest-beta) | The install state of the app. Possible values are: `installed`, `failed`, `notInstalled`, `uninstallFailed`, `pendingInstall`, `unknown`, `notApplicable`. |
| supportedDeviceTypes | [mobileAppSupportedDeviceType](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappsupporteddevicetype?view=graph-rest-beta) collection | The supported platforms for the app. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppIntentAndStateDetail",
  "applicationId": "String",
  "displayName": "String",
  "mobileAppIntent": "String",
  "displayVersion": "String",
  "installState": "String",
  "supportedDeviceTypes": [
    {
      "@odata.type": "microsoft.graph.mobileAppSupportedDeviceType",
      "type": "String",
      "minimumOperatingSystemVersion": "String",
      "maximumOperatingSystemVersion": "String"
    }
  ]
}
```
