<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-durationdrivenrolloutsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# durationDrivenRolloutSettings resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings for controlling how to roll out over a specific duration.

Inherits from [gradualRolloutSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-gradualrolloutsettings?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| durationBetweenOffers | String | The duration between each set of devices being offered the update, which has an effect when **durationUntilDeploymentEnd** is defined. The value is represented in ISO 8601 format for duration. Default value is `P1D` \(one day\). Inherited from [microsoft.graph.windowsUpdates.gradualRolloutSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-gradualrolloutsettings?view=graph-rest-beta). |
| durationUntilDeploymentEnd | Duration | The target duration of the rollout. Given **durationBetweenOffers** and **durationUntilDeploymentEnd**, the system will automatically calculate how many devices are in each offering. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.durationDrivenRolloutSettings",
  "durationBetweenOffers": "String (duration)",
  "durationUntilDeploymentEnd": "String (duration)"
}
```
