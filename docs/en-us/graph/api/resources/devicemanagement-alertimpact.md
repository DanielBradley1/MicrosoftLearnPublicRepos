<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertimpact?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# alertImpact resource type

Namespace: microsoft.graph.deviceManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the impact of an alert event.

Note

This API is part of the [alert monitoring API set](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-monitoring?view=graph-rest-beta&preserve-view=true) which currently supports only [Windows 365](https://learn.microsoft.com/en-us/windows-365/overview) and Cloud PC scenarios. The API set allows admins to set up rules to alert issues with provisioning Cloud PCs, uploading Cloud PC images, and checking Azure network connections.

Have a different scenario that can use additional programmatic alert support on the Microsoft Endpoint Manager admin center? [Suggest the feature or vote for existing feature requests](https://developer.microsoft.com/en-us/graph/support).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alertImpactDetails | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) collection | The detail information of the impact. For example, if the *Frontline Cloud PCs near concurrency limit* alert is triggered, the details contain the impacted Frontline license SKU name, such as `Windows 365 Frontline 2 vCPU/8GB/128GB`, and the corresponding impacted value. |
| aggregationType | [microsoft.graph.deviceManagement.aggregationType](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-rulethreshold?view=graph-rest-beta#aggregationtype-values) | The aggregation type of the impact. The possible values are: `count`, `percentage`, `affectedCloudPcCount`, `affectedCloudPcPercentage`, `unknownFutureValue`. |
| value | Int32 | The number value of the impact. For the aggregation types of `count` and `affectedCloudPcCount`, the value indicates the number of affected instances. For example, `6 affectedCloudPcCount` means that six Cloud PCs are affected. For the aggregation types of `percentage` and `affectedCloudPcPercentage`, the value indicates the percent of affected instances. For example, `12 affectedCloudPcPercentage` means that 12% of Cloud PCs are affected. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagement.alertImpact",
  "alertImpactDetails": [{"@odata.type": "microsoft.graph.security.keyValuePair"}],
  "aggregationType": "String",
  "value": "Int32"
}
```
