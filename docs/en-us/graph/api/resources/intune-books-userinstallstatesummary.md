<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userInstallStateSummary resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the installation state summary for a user.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userInstallStateSummaries](https://learn.microsoft.com/en-us/graph/api/intune-books-userinstallstatesummary-list?view=graph-rest-1.0) | [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0) collection | List properties and relationships of the [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0) objects. |
| [Get userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-books-userinstallstatesummary-get?view=graph-rest-1.0) | [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0) | Read properties and relationships of the [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0) object. |
| [Create userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-books-userinstallstatesummary-create?view=graph-rest-1.0) | [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0) | Create a new [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0) object. |
| [Delete userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-books-userinstallstatesummary-delete?view=graph-rest-1.0) | None | Deletes a [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0). |
| [Update userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-books-userinstallstatesummary-update?view=graph-rest-1.0) | [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0) | Update the properties of a [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| userName | String | User name. |
| installedDeviceCount | Int32 | Installed Device Count. |
| failedDeviceCount | Int32 | Failed Device Count. |
| notInstalledDeviceCount | Int32 | Not installed device count. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deviceStates | [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0) collection | The install state of the eBook. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userInstallStateSummary",
  "id": "String (identifier)",
  "userName": "String",
  "installedDeviceCount": 1024,
  "failedDeviceCount": 1024,
  "notInstalledDeviceCount": 1024
}
```
