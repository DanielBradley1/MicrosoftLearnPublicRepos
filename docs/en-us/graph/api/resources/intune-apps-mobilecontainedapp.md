<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilecontainedapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# mobileContainedApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

An abstract class that represents a contained app in a mobileApp acting as a package.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileContainedApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobilecontainedapp-list?view=graph-rest-1.0) | [mobileContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilecontainedapp?view=graph-rest-1.0) collection | List properties and relationships of the [mobileContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilecontainedapp?view=graph-rest-1.0) objects. |
| [Get mobileContainedApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobilecontainedapp-get?view=graph-rest-1.0) | [mobileContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilecontainedapp?view=graph-rest-1.0) | Read properties and relationships of the [mobileContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilecontainedapp?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileContainedApp",
  "id": "String (identifier)"
}
```
