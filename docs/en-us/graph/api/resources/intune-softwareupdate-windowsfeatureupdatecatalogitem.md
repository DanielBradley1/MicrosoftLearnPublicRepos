<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsFeatureUpdateCatalogItem resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows update catalog item entity

Inherits from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsFeatureUpdateCatalogItems](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdatecatalogitem-list?view=graph-rest-beta) | [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta) collection | List properties and relationships of the [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta) objects. |
| [Get windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdatecatalogitem-get?view=graph-rest-beta) | [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta) | Read properties and relationships of the [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta) object. |
| [Create windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdatecatalogitem-create?view=graph-rest-beta) | [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta) | Create a new [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta) object. |
| [Delete windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdatecatalogitem-delete?view=graph-rest-beta) | None | Deletes a [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta). |
| [Update windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdatecatalogitem-update?view=graph-rest-beta) | [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta) | Update the properties of a [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The catalog item id. Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| displayName | String | The display name for the catalog item. Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| releaseDateTime | DateTimeOffset | The date the catalog item was released Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| endOfSupportDate | DateTimeOffset | The last supported date for a catalog item Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| version | String | The feature update version |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsFeatureUpdateCatalogItem",
  "id": "String (identifier)",
  "displayName": "String",
  "releaseDateTime": "String (timestamp)",
  "endOfSupportDate": "String (timestamp)",
  "version": "String"
}
```
