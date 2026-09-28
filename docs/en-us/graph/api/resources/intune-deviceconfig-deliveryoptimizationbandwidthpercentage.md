<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deliveryoptimizationbandwidthpercentage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deliveryOptimizationBandwidthPercentage resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Bandwidth limits specified as a percentage.

Inherits from [deliveryOptimizationBandwidth](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deliveryoptimizationbandwidth?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| maximumBackgroundBandwidthPercentage | Int32 | Specifies the maximum background download bandwidth that Delivery Optimization uses across all concurrent download activities as a percentage of available download bandwidth \(0-100\). Valid values 0 to 100 |
| The default value 0 \(zero\) means that Delivery Optimization dynamically adjusts to use the available bandwidth for background downloads. Valid values 0 to 100 |  |  |
| maximumForegroundBandwidthPercentage | Int32 | Specifies the maximum foreground download bandwidth that Delivery Optimization uses across all concurrent download activities as a percentage of available download bandwidth \(0-100\). Valid values 0 to 100 |
| The default value 0 \(zero\) means that Delivery Optimization dynamically adjusts to use the available bandwidth for foreground downloads. Valid values 0 to 100 |  |  |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deliveryOptimizationBandwidthPercentage",
  "maximumBackgroundBandwidthPercentage": 1024,
  "maximumForegroundBandwidthPercentage": 1024
}
```
