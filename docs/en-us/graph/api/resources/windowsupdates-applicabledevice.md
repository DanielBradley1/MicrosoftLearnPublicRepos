<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicabledevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# applicableDevice resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a device for which a specific Windows update catalog entry is applicable. The resource also indicates whether the catalog entry is recommended for the device.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List devices](https://learn.microsoft.com/en-us/graph/api/windowsupdates-applicablecatalog-list-devices?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.applicableDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicabledevice?view=graph-rest-beta) collection | List devices for which a policy-specific catalog entry is applicable. |
| [List aggregatedDevices](https://learn.microsoft.com/en-us/graph/api/windowsupdates-applicablecatalogsummary-list-aggregateddevices?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.applicableDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicabledevice?view=graph-rest-beta) collection | List devices included in a tenant-level applicable catalog summary. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The Microsoft Entra device identifier. Read-only. |
| isRecommended | Boolean | Indicates whether the catalog entry is recommended for the device. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.applicableDevice",
  "id": "String (identifier)",
  "isRecommended": "Boolean"
}
```
