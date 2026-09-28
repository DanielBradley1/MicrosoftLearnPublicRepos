<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# eBookInstallSummary resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the installation summary of a book for a device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/intune-books-ebookinstallsummary-get?view=graph-rest-1.0) | [eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary?view=graph-rest-1.0) | Read properties and relationships of the [eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary?view=graph-rest-1.0) object. |
| [Update eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/intune-books-ebookinstallsummary-update?view=graph-rest-1.0) | [eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary?view=graph-rest-1.0) | Update the properties of a [eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| installedDeviceCount | Int32 | Number of Devices that have successfully installed this book. |
| failedDeviceCount | Int32 | Number of Devices that have failed to install this book. |
| notInstalledDeviceCount | Int32 | Number of Devices that does not have this book installed. |
| installedUserCount | Int32 | Number of Users whose devices have all succeeded to install this book. |
| failedUserCount | Int32 | Number of Users that have 1 or more device that failed to install this book. |
| notInstalledUserCount | Int32 | Number of Users that did not install this book. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.eBookInstallSummary",
  "id": "String (identifier)",
  "installedDeviceCount": 1024,
  "failedDeviceCount": 1024,
  "notInstalledDeviceCount": 1024,
  "installedUserCount": 1024,
  "failedUserCount": 1024,
  "notInstalledUserCount": 1024
}
```
