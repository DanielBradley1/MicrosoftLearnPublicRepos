<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsUpdateCatalogItem resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows update catalog item entity

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsUpdateCatalogItems](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsupdatecatalogitem-list?view=graph-rest-beta) | [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) collection | List properties and relationships of the [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) objects. |
| [Get windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsupdatecatalogitem-get?view=graph-rest-beta) | [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) | Read properties and relationships of the [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The catalog item id. |
| displayName | String | The display name for the catalog item. |
| releaseDateTime | DateTimeOffset | The date the catalog item was released |
| endOfSupportDate | DateTimeOffset | The last supported date for a catalog item |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdateCatalogItem",
  "id": "String (identifier)",
  "displayName": "String",
  "releaseDateTime": "String (timestamp)",
  "endOfSupportDate": "String (timestamp)"
}
```
