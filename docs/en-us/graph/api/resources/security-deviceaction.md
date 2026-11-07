<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-deviceaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# deviceAction resource type

Namespace: microsoft.graph.security

Represents an [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-1.0) that targets a device returned by a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) hunting query. The action uses a device ID column from the query output to identify the device.

Inherits from [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceIdColumn | String | Name of the hunting-query result column that contains the device ID for the targeted device. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.deviceAction",
  "deviceIdColumn": "String"
}
```
