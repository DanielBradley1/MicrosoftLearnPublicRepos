<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelhealththreshold?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# microsoftTunnelHealthThreshold resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that represents the health thresholds of a health metric

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List microsoftTunnelHealthThresholds](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelhealththreshold-list?view=graph-rest-beta) | [microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelhealththreshold?view=graph-rest-beta) collection | List properties and relationships of the [microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelhealththreshold?view=graph-rest-beta) objects. |
| [Get microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelhealththreshold-get?view=graph-rest-beta) | [microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelhealththreshold?view=graph-rest-beta) | Read properties and relationships of the [microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelhealththreshold?view=graph-rest-beta) object. |
| [Create microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelhealththreshold-create?view=graph-rest-beta) | [microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelhealththreshold?view=graph-rest-beta) | Create a new [microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelhealththreshold?view=graph-rest-beta) object. |
| [Delete microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelhealththreshold-delete?view=graph-rest-beta) | None | Deletes a [microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelhealththreshold?view=graph-rest-beta). |
| [Update microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelhealththreshold-update?view=graph-rest-beta) | [microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelhealththreshold?view=graph-rest-beta) | Update the properties of a [microsoftTunnelHealthThreshold](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelhealththreshold?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the metric name. Supports: $delete, $update. $Insert, $skip, $top is not supported. Read-only. |
| healthyThreshold | Int64 | The threshold for being healthy based on default health status metrics: CPU usage healthy < 50%, Memory usage healthy < 50%, Disk space healthy > 5GB, Latency healthy < 10ms, health metrics can be customized. |
| unhealthyThreshold | Int64 | The threshold for being unhealthy based on default health status metrics: CPU usage unhealthy > 75%, Memory usage unhealthy > 75%, Disk space < 3GB, Latency Unhealthy > 20ms, health metrics can be customized. |
| defaultHealthyThreshold | Int64 | The threshold for being healthy based on default health status metrics: CPU usage healthy < 50%, Memory usage healthy < 50%, Disk space healthy > 5GB, Latency healthy < 10ms, health metrics can be customized. Read-only. |
| defaultUnhealthyThreshold | Int64 | The threshold for being unhealthy based on default health status metrics: CPU usage unhealthy > 75%, Memory usage unhealthy > 75%, Disk space < 3GB, Latency unhealthy > 20ms, health metrics can be customized. Read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.microsoftTunnelHealthThreshold",
  "id": "String (identifier)",
  "healthyThreshold": 1024,
  "unhealthyThreshold": 1024,
  "defaultHealthyThreshold": 1024,
  "defaultUnhealthyThreshold": 1024
}
```
