<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-gradualrolloutsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# gradualRolloutSettings resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings for governing how to rollout content to devices.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| durationBetweenOffers | Duration | The duration between each set of devices being offered the update. The value is represented in ISO 8601 format for duration. Default value is `P1D` \(one day\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.gradualRolloutSettings",
  "durationBetweenOffers": "String (duration)"
}
```
