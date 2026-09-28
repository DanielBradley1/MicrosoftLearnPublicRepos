<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/fallbackpolicyproperties?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# fallbackPolicyProperties resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Allows fallback policy to be specified for high-priority raw notifications on iOS endpoints only, with additional properties for specifying fallback wait time \(delay\) and corresponding visual notification content.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| platformTypes | String collection | Specifies the platforms that a developer wants to enable raw-to-visual toast notification fallback on. Currently, if **fallbackPolicy** is specified, **targetPolicy.platformTypes** must include `iOS` and optionally other platforms. In addition, **fallbackPolicy.endpointFallback.platformTypes** is required and the only supported platform is currently `iOS`. |
| fallbackDelayInSeconds | Int32 | This delay represents the amount of time that will pass \(in seconds\) before a direct toast notification will be sent as a fallback to each users� iOS device subscription that does not fetch the raw notification. The value must be between 60 and 600. |
| visualContent | [visualProperties](https://learn.microsoft.com/en-us/graph/api/resources/visualproperties?view=graph-rest-beta) | The visual content of a fallback initiated, raw-to-visual user notification on iOS. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "platformTypes": ["String"],
  "fallbackDelayInSeconds": 60,
  "visualContent": {"@odata.type": "microsoft.graph.visualProperties"}
}
```
