<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deviceusagesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# deviceUsageSummary resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A summary for device usage.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeDeviceCount | Int32 | The number of distinct device IDs between the discovery pivot time and the end of the reporting period. |
| inactiveDeviceCount | Int32 | The discovery pivot time and the end of the reporting period, but were seen between the start of the reporting period and the discovery pivot time. |
| totalDeviceCount | Int32 | The total number of distinct device IDs that were seen during the reporting period. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.deviceUsageSummary",
  "totalDeviceCount": "Integer",
  "activeDeviceCount": "Integer",
  "inactiveDeviceCount": "Integer"
}
```
