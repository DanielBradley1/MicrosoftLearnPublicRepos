<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-recoveryupdatecatalogentry?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# recoveryUpdateCatalogEntry resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an entity that governs the quick machine recovery update catalog entry.

Inherits from [softwareUpdateCatalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-softwareupdatecatalogentry?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| catalogName | String | The catalog name. Read-only. |
| deployableUntilDateTime | DateTimeOffset | The date on which the content is no longer available to deploy. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). |
| displayName | String | The display name of the content. Read-only. Inherited from [catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). |
| id | String | The unique identifier for the catalog entry. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| releaseDateTime | DateTimeOffset | The release date for the content. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| productRevisions | [microsoft.graph.windowsUpdates.productRevision](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-productrevision?view=graph-rest-beta) collection | A collection of product revisions associated with the update. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.recoveryUpdateCatalogEntry",
  "catalogName": "String",
  "deployableUntilDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "releaseDateTime": "String (timestamp)"
}
```
