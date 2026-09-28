<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userAppInstallStatus resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the installation status for a user. This will be deprecated in May, 2023

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userAppInstallStatuses](https://learn.microsoft.com/en-us/graph/api/intune-apps-userappinstallstatus-list?view=graph-rest-beta) | [userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus?view=graph-rest-beta) collection | List properties and relationships of the [userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus?view=graph-rest-beta) objects. |
| [Get userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-userappinstallstatus-get?view=graph-rest-beta) | [userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus?view=graph-rest-beta) | Read properties and relationships of the [userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus?view=graph-rest-beta) object. |
| [Create userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-userappinstallstatus-create?view=graph-rest-beta) | [userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus?view=graph-rest-beta) | Create a new [userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus?view=graph-rest-beta) object. |
| [Delete userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-userappinstallstatus-delete?view=graph-rest-beta) | None | Deletes a [userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus?view=graph-rest-beta). |
| [Update userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-userappinstallstatus-update?view=graph-rest-beta) | [userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus?view=graph-rest-beta) | Update the properties of a [userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| userName | String | User name. |
| userPrincipalName | String | User Principal Name. |
| installedDeviceCount | Int32 | Installed Device Count. |
| failedDeviceCount | Int32 | Failed Device Count. |
| notInstalledDeviceCount | Int32 | Not installed device count. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| app | [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) | The navigation link to the mobile app. |
| deviceStatuses | [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta) collection | The install state of the app on devices. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userAppInstallStatus",
  "id": "String (identifier)",
  "userName": "String",
  "userPrincipalName": "String",
  "installedDeviceCount": 1024,
  "failedDeviceCount": 1024,
  "notInstalledDeviceCount": 1024
}
```
