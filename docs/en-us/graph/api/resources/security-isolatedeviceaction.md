<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-isolatedeviceaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# isolateDeviceAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a [deviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-deviceaction?view=graph-rest-beta) that isolates a device returned by a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) hunting query. The action uses the device ID column from the query output to identify the device to isolate.

Inherits from [deviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-deviceaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceIdColumn | String | Name of the hunting-query result column that contains the device ID for the targeted device. Inherited from [deviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-deviceaction?view=graph-rest-beta). |
| isolationType | microsoft.graph.security.isolationType | Type of isolation to apply to the device. The possible values are: `full`, `selective`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.isolateDeviceAction",
  "deviceIdColumn": "String",
  "isolationType": "String"
}
```
