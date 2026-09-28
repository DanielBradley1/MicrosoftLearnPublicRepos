<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-devicemanagementreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementReports resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

DeviceManagementReports class for Reporting V2

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-devicemanagementreports-get?view=graph-rest-beta) | [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-devicemanagementreports?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-devicemanagementreports?view=graph-rest-beta) object. |
| [Update deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-devicemanagementreports-update?view=graph-rest-beta) | [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-devicemanagementreports?view=graph-rest-beta) | Update the properties of a [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-devicemanagementreports?view=graph-rest-beta) object. |
| [getRemoteAssistanceSessionsReport action](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-devicemanagementreports-getremoteassistancesessionsreport?view=graph-rest-beta) | Stream |  |
| [getRemoteAssistanceMonitorActiveSessionsReport action](https://learn.microsoft.com/en-us/graph/api/api/intune-remoteassistance-devicemanagementreports-getremoteassistancemonitoractivesessionsreport.md?view=graph-rest-beta) | Stream |  |
| [getRemoteAssistanceMonitorTotalSessionsReport action](https://learn.microsoft.com/en-us/graph/api/api/intune-remoteassistance-devicemanagementreports-getremoteassistancemonitortotalsessionsreport.md?view=graph-rest-beta) | Stream |  |
| [getRemoteAssistanceMonitorAvgSessionTimeReport action](https://learn.microsoft.com/en-us/graph/api/api/intune-remoteassistance-devicemanagementreports-getremoteassistancemonitoravgsessiontimereport.md?view=graph-rest-beta) | Stream |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key of the entity |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementReports",
  "id": "String (identifier)"
}
```
