<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# mobileAppInstallSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the installation summary of a mobile app. This will be deprecated in May, 2023

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get mobileAppInstallSummary](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappinstallsummary-get?view=graph-rest-beta) | [mobileAppInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallsummary?view=graph-rest-beta) | Read properties and relationships of the [mobileAppInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallsummary?view=graph-rest-beta) object. |
| [Update mobileAppInstallSummary](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappinstallsummary-update?view=graph-rest-beta) | [mobileAppInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallsummary?view=graph-rest-beta) | Update the properties of a [mobileAppInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallsummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| installedDeviceCount | Int32 | Number of Devices that have successfully installed this app. |
| failedDeviceCount | Int32 | Number of Devices that have failed to install this app. |
| notApplicableDeviceCount | Int32 | Number of Devices that are not applicable for this app. |
| notInstalledDeviceCount | Int32 | Number of Devices that does not have this app installed. |
| pendingInstallDeviceCount | Int32 | Number of Devices that have been notified to install this app. |
| installedUserCount | Int32 | Number of Users whose devices have all succeeded to install this app. |
| failedUserCount | Int32 | Number of Users that have 1 or more device that failed to install this app. |
| notApplicableUserCount | Int32 | Number of Users whose devices were all not applicable for this app. |
| notInstalledUserCount | Int32 | Number of Users that have 1 or more devices that did not install this app. |
| pendingInstallUserCount | Int32 | Number of Users that have 1 or more device that have been notified to install this app and have 0 devices with failures. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppInstallSummary",
  "id": "String (identifier)",
  "installedDeviceCount": 1024,
  "failedDeviceCount": 1024,
  "notApplicableDeviceCount": 1024,
  "notInstalledDeviceCount": 1024,
  "pendingInstallDeviceCount": 1024,
  "installedUserCount": 1024,
  "failedUserCount": 1024,
  "notApplicableUserCount": 1024,
  "notInstalledUserCount": 1024,
  "pendingInstallUserCount": 1024
}
```
