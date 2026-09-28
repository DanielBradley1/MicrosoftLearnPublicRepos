<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-osversioncount?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# osVersionCount resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Count of devices with malware for each OS version

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| osVersion | String | OS version |
| deviceCount | Int32 | Count of devices with malware for the OS version |
| lastUpdateDateTime | DateTimeOffset | The Timestamp of the last update for the device count in UTC |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.osVersionCount",
  "osVersion": "String",
  "deviceCount": 1024,
  "lastUpdateDateTime": "String (timestamp)"
}
```
