<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-rulethreshold?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# ruleThreshold resource type

Namespace: microsoft.graph.deviceManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents details about the threshold settings of an [alert rule](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta).

Note

This API is part of the [alert monitoring API set](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-monitoring?view=graph-rest-beta&preserve-view=true) which currently supports only [Windows 365](https://learn.microsoft.com/en-us/windows-365/overview) and Cloud PC scenarios. The API set allows admins to set up rules to alert issues with provisioning Cloud PCs, uploading Cloud PC images, and checking Azure network connections.

Have a different scenario that can use additional programmatic alert support on the Microsoft Endpoint Manager admin center? [Suggest the feature or vote for existing feature requests](https://developer.microsoft.com/en-us/graph/support).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aggregation | [microsoft.graph.deviceManagement.aggregationType](#aggregationtype-values) | Indicates the built-in aggregation methods. The possible values are: `count`, `percentage`, `affectedCloudPcCount`, `affectedCloudPcPercentage`, `unknownFutureValue`. |
| operator | [microsoft.graph.deviceManagement.operatorType](#operatortype-values) | Indicates the built-in operator. The possible values are: `greaterOrEqual`, `equal`, `greater`, `less`, `lessOrEqual`, `notEqual`, `unknownFutureValue`. |
| target | Int32 | The target threshold value. |

### aggregationType values

| Member | Description |
| :--- | :--- |
| count | Indicates aggregated data by performing a count on the number of items that match the alert rule conditions. |
| percentage | Indicates a percentage of the items that match the alert rule conditions. |
| affectedCloudPcCount | Indicates the total number of Cloud PCs that meet the alert rule conditions. |
| affectedCloudPcPercentage | Indicates the percentage of Cloud PCs that meet the alert rule conditions. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

### operatorType values

| Member | Description |
| :--- | :--- |
| greaterOrEqual | Indicates that the operator is greater than or equal to the threshold target set by an administrator. |
| equal | Indicates that the operator is equal to the threshold target set by an administrator. |
| greater | Indicates that the operator is greater than the threshold target set by an administrator. |
| less | Indicates that the operator is less than the threshold target set by an administrator. |
| lessOrEqual | Indicates that the operator is less than or equal to the threshold target set by an administrator. |
| notEqual | Indicates that the operator is not equal to the threshold target set by an administrator. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagement.ruleThreshold",
  "aggregation": "String",
  "operator": "String",
  "target": "Int32"
}
```
