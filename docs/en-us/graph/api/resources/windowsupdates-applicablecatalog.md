<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalog?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# applicableCatalog resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Windows update catalog entry that applies to one or more devices targeted by an Autopatch policy. Use this resource to inspect aggregate applicability and navigate to the affected devices or the associated catalog entry.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get applicable catalog](https://learn.microsoft.com/en-us/graph/api/windowsupdates-applicablecatalog-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.applicableCatalog](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalog?view=graph-rest-beta) | Read the properties and relationships of an applicable catalog. |
| [List devices](https://learn.microsoft.com/en-us/graph/api/windowsupdates-applicablecatalog-list-devices?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.applicableDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicabledevice?view=graph-rest-beta) collection | List the devices for which the catalog entry is applicable. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceCount | Int32 | The number of devices for which the catalog entry is applicable. Read-only. |
| hasRecommendedDevice | Boolean | Indicates whether the catalog entry is recommended for at least one applicable device. Read-only. |
| id | String | The identifier of the associated catalog entry. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| catalogEntry | [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta) | The associated Windows update catalog entry. |
| devices | [microsoft.graph.windowsUpdates.applicableDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicabledevice?view=graph-rest-beta) collection | The devices for which the catalog entry is applicable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.applicableCatalog",
  "deviceCount": "Int32",
  "hasRecommendedDevice": "Boolean",
  "id": "String (identifier)"
}
```
