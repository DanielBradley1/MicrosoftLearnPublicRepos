<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-softwareupdatecatalogentry?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# softwareUpdateCatalogEntry resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Metadata for a software update that you can approve for deployment.

Inherits from [catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). Base type for [featureUpdateCatalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-featureupdatecatalogentry?view=graph-rest-beta) and [qualityUpdateCatalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatecatalogentry?view=graph-rest-beta).

This is an abstract type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deployableUntilDateTime | DateTimeOffset | The date on which the content is no longer available for deployment. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). |
| displayName | String | The display name of the content. Read-only. Inherited from [catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). |
| id | String | The unique identifier for the catalog entry. Read-only. Inherited from [catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). |
| releaseDateTime | DateTimeOffset | The release date for the content. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.softwareUpdateCatalogEntry",
  "id": "String (identifier)",
  "displayName": "String",
  "releaseDateTime": "String (timestamp)",
  "deployableUntilDateTime": "String (timestamp)"
}
```
