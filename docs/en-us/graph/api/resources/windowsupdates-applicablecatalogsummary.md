<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalogsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# applicableCatalogSummary resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents tenant-level applicability information for a Windows update catalog entry across Windows Autopatch policies. Use this resource to identify affected devices and policies.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List applicableCatalogSummaries](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatedata-list-applicablecatalogsummaries?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.applicableCatalogSummary](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalogsummary?view=graph-rest-beta) collection | List catalog applicability summaries across Windows Autopatch policies. |
| [Get applicable catalog summary](https://learn.microsoft.com/en-us/graph/api/windowsupdates-applicablecatalogsummary-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.applicableCatalogSummary](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalogsummary?view=graph-rest-beta) | Read a catalog applicability summary. |
| [List aggregatedDevices](https://learn.microsoft.com/en-us/graph/api/windowsupdates-applicablecatalogsummary-list-aggregateddevices?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.applicableDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicabledevice?view=graph-rest-beta) collection | List devices included in the applicability summary. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aggregatedDeviceCount | Int32 | The number of devices included in the summary. Read-only. |
| hasRecommendedDevice | Boolean | Indicates whether the catalog entry is recommended for at least one device in the summary. Read-only. |
| id | String | The identifier of the associated catalog entry. Read-only. |
| policies | String collection | The identifiers of Windows Autopatch policies for which the catalog entry is applicable. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| aggregatedDevices | [microsoft.graph.windowsUpdates.applicableDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicabledevice?view=graph-rest-beta) collection | The devices included in the applicability summary. |
| catalogEntry | [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta) | The associated Windows update catalog entry. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.applicableCatalogSummary",
  "aggregatedDeviceCount": "Int32",
  "hasRecommendedDevice": "Boolean",
  "id": "String (identifier)",
  "policies": [
    "String"
  ]
}
```
