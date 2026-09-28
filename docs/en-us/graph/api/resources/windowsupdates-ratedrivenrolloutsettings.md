<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ratedrivenrolloutsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# rateDrivenRolloutSettings resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings for governing rate driven rollouts. A rate driven rollout deploys content over time at a specific rate determined by **devicesPerOffer** and **durationBetweenOffers**.

Inherits from [gradualRolloutSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-gradualrolloutsettings?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| devicesPerOffer | Int32 | Specifies the number of devices that are offered at the same time. When not set, all devices in the deployment are offered content at the same time. |
| durationBetweenOffers | Duration | The duration between each set of devices being offered the update, which has an effect when **devicesPerOffer** is defined. The value is represented in ISO 8601 format for duration. Default value is `P1D` \(1 day\). Inherited from [microsoft.graph.windowsUpdates.gradualRolloutSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-gradualrolloutsettings?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings",
  "durationBetweenOffers": "String (duration)",
  "devicesPerOffer": "Int32"
}
```
