<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxcontainedapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# windowsUniversalAppXContainedApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class that represents a contained app of a WindowsUniversalAppX app.

Inherits from [mobileContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilecontainedapp?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsUniversalAppXContainedApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsuniversalappxcontainedapp-list?view=graph-rest-1.0) | [windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxcontainedapp?view=graph-rest-1.0) collection | List properties and relationships of the [windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxcontainedapp?view=graph-rest-1.0) objects. |
| [Get windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsuniversalappxcontainedapp-get?view=graph-rest-1.0) | [windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxcontainedapp?view=graph-rest-1.0) | Read properties and relationships of the [windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxcontainedapp?view=graph-rest-1.0) object. |
| [Create windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsuniversalappxcontainedapp-create?view=graph-rest-1.0) | [windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxcontainedapp?view=graph-rest-1.0) | Create a new [windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxcontainedapp?view=graph-rest-1.0) object. |
| [Delete windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsuniversalappxcontainedapp-delete?view=graph-rest-1.0) | None | Deletes a [windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxcontainedapp?view=graph-rest-1.0). |
| [Update windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsuniversalappxcontainedapp-update?view=graph-rest-1.0) | [windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxcontainedapp?view=graph-rest-1.0) | Update the properties of a [windowsUniversalAppXContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxcontainedapp?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. Inherited from [mobileContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilecontainedapp?view=graph-rest-1.0) |
| appUserModelId | String | The app user model ID of the contained app of a WindowsUniversalAppX app. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsUniversalAppXContainedApp",
  "id": "String (identifier)",
  "appUserModelId": "String"
}
```
