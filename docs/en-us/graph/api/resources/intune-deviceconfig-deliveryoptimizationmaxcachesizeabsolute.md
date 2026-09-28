<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deliveryoptimizationmaxcachesizeabsolute?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deliveryOptimizationMaxCacheSizeAbsolute resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Delivery Optimization max cache size absolute type.

Inherits from [deliveryOptimizationMaxCacheSize](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deliveryoptimizationmaxcachesize?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| maximumCacheSizeInGigabytes | Int64 | Specifies the maximum size in GB of Delivery Optimization cache. Valid values 0 to 4294967295 |
| The value 0 \(zero\) means "unlimited" cache. Delivery Optimization will clear the cache when the device is running low on disk space. Valid values 0 to 4294967295 |  |  |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deliveryOptimizationMaxCacheSizeAbsolute",
  "maximumCacheSizeInGigabytes": 1024
}
```
