<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# mobileAppContent resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains content properties for a specific app version. Each mobileAppContent can have multiple mobileAppContentFile.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileAppContents](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontent-list?view=graph-rest-1.0) | [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-1.0) collection | List properties and relationships of the [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-1.0) objects. |
| [Get mobileAppContent](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontent-get?view=graph-rest-1.0) | [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-1.0) | Read properties and relationships of the [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-1.0) object. |
| [Create mobileAppContent](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontent-create?view=graph-rest-1.0) | [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-1.0) | Create a new [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-1.0) object. |
| [Delete mobileAppContent](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontent-delete?view=graph-rest-1.0) | None | Deletes a [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-1.0). |
| [Update mobileAppContent](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontent-update?view=graph-rest-1.0) | [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-1.0) | Update the properties of a [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The app content version. This property is read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| files | [mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile?view=graph-rest-1.0) collection | The list of files for this app content version. |
| containedApps | [mobileContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilecontainedapp?view=graph-rest-1.0) collection | The collection of contained apps in a MobileLobApp acting as a package. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppContent",
  "id": "String (identifier)"
}
```
