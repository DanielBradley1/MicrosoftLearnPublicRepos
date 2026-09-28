<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# mobileAppCategory resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for a single Intune app category.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileAppCategories](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcategory-list?view=graph-rest-1.0) | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) collection | List properties and relationships of the [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) objects. |
| [Get mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcategory-get?view=graph-rest-1.0) | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) | Read properties and relationships of the [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) object. |
| [Create mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcategory-create?view=graph-rest-1.0) | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) | Create a new [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) object. |
| [Delete mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcategory-delete?view=graph-rest-1.0) | None | Deletes a [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0). |
| [Update mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcategory-update?view=graph-rest-1.0) | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) | Update the properties of a [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key of the entity. This property is read-only. |
| displayName | String | The name of the app category. |
| lastModifiedDateTime | DateTimeOffset | The date and time the mobileAppCategory was last modified. This property is read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppCategory",
  "id": "String (identifier)",
  "displayName": "String",
  "lastModifiedDateTime": "String (timestamp)"
}
```
