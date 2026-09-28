<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/fallbackpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# fallbackPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Allows fallback policy to be specified for iOS endpoints only and is designed to be used for high-priority raw notifications that might not be delivered to devices due to platform specific restrictions \(for example, battery saver mode\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endpointFallback | [fallbackpolicyProperties](https://learn.microsoft.com/en-us/graph/api/resources/fallbackpolicyproperties?view=graph-rest-beta) | EndpointFallback policy object handles notification fallback policy at an end point level and is currently limited to iOS. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "endpointFallback": {"@odata.type": "microsoft.graph.fallbackpolicyProperties"}
}
```
