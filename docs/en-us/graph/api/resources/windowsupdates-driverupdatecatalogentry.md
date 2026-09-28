<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatecatalogentry?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# driverUpdateCatalogEntry resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the metadata for driver update content that you can approve for deployment.

Inherits from [softwareUpdateCatalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-softwareupdatecatalogentry?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deployableUntilDateTime | DateTimeOffset | The date on which the content is no longer available for deployment. Read-only. Inherited from [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). |
| description | String | The description of the content. |
| displayName | String | The display name of the content. Read-only. Inherited from [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). |
| driverClass | String | The classification of the driver. |
| id | String | The unique identifier for this catalog entry. Read-only. Inherited from [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). |
| manufacturer | String | The manufacturer of the driver. |
| provider | String | The provider of the driver. |
| releaseDateTime | DateTimeOffset | The release date for the content. Read-only. Inherited from [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). |
| setupInformationFile | String | The setup information file of the driver. |
| version | String | The unique version of the content. |
| versionDateTime | DateTimeOffset | The date and time when a new version of content was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdateCatalogEntry",
  "deployableUntilDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "driverClass": "String",
  "id": "String (identifier)",
  "manufacturer": "String",
  "provider": "String",
  "releaseDateTime": "String (timestamp)",
  "setupInformationFile": "String",
  "version": "String",
  "versionDateTime": "String (timestamp)"
}
```
