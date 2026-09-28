<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# mobileAppInstallStatus resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the installation state of a mobile app for a device. This will be deprecated in May, 2023

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileAppInstallStatuses](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappinstallstatus-list?view=graph-rest-beta) | [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta) collection | List properties and relationships of the [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta) objects. |
| [Get mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappinstallstatus-get?view=graph-rest-beta) | [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta) | Read properties and relationships of the [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta) object. |
| [Create mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappinstallstatus-create?view=graph-rest-beta) | [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta) | Create a new [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta) object. |
| [Delete mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappinstallstatus-delete?view=graph-rest-beta) | None | Deletes a [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta). |
| [Update mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappinstallstatus-update?view=graph-rest-beta) | [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta) | Update the properties of a [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| deviceName | String | Device name |
| deviceId | String | Device ID |
| lastSyncDateTime | DateTimeOffset | Last sync date time |
| mobileAppInstallStatusValue | [resultantAppState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-resultantappstate?view=graph-rest-beta) | The install state of the app. The possible values are: `installed`, `failed`, `notInstalled`, `uninstallFailed`, `pendingInstall`, `unknown`, `notApplicable`. |
| installState | [resultantAppState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-resultantappstate?view=graph-rest-beta) | The install state of the app. The possible values are: `installed`, `failed`, `notInstalled`, `uninstallFailed`, `pendingInstall`, `unknown`, `notApplicable`. |
| installStateDetail | [resultantAppStateDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-resultantappstatedetail?view=graph-rest-beta) | The install state detail of the app. The possible values are: `noAdditionalDetails`, `dependencyFailedToInstall`, `dependencyWithRequirementsNotMet`, `dependencyPendingReboot`, `dependencyWithAutoInstallDisabled`, `supersededAppUninstallFailed`, `supersededAppUninstallPendingReboot`, `removingSupersededApps`, `iosAppStoreUpdateFailedToInstall`, `vppAppHasUpdateAvailable`, `userRejectedUpdate`, `uninstallPendingReboot`, `supersedingAppsDetected`, `supersededAppsDetected`, `seeInstallErrorCode`, `autoInstallDisabled`, `managedAppNoLongerPresent`, `userRejectedInstall`, `userIsNotLoggedIntoAppStore`, `untargetedSupersedingAppsDetected`, `appRemovedBySupersedence`, `seeUninstallErrorCode`, `pendingReboot`, `installingDependencies`, `contentDownloaded`, `supersedingAppsNotApplicable`, `powerShellScriptRequirementNotMet`, `registryRequirementNotMet`, `fileSystemRequirementNotMet`, `platformNotApplicable`, `minimumCpuSpeedNotMet`, `minimumLogicalProcessorCountNotMet`, `minimumPhysicalMemoryNotMet`, `minimumOsVersionNotMet`, `minimumDiskSpaceNotMet`, `processorArchitectureNotApplicable`. |
| errorCode | Int32 | The error code for install or uninstall failures. |
| osVersion | String | OS Version |
| osDescription | String | OS Description |
| userName | String | Device User Name |
| userPrincipalName | String | User Principal Name |
| displayVersion | String | Human readable version of the application |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| app | [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) | The navigation link to the mobile app. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppInstallStatus",
  "id": "String (identifier)",
  "deviceName": "String",
  "deviceId": "String",
  "lastSyncDateTime": "String (timestamp)",
  "mobileAppInstallStatusValue": "String",
  "installState": "String",
  "installStateDetail": "String",
  "errorCode": 1024,
  "osVersion": "String",
  "osDescription": "String",
  "userName": "String",
  "userPrincipalName": "String",
  "displayVersion": "String"
}
```
