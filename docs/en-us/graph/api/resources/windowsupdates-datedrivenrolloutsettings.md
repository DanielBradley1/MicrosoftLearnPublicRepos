<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-datedrivenrolloutsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# dateDrivenRolloutSettings resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings for controlling how to roll out by a specific end date.

Inherits from [gradualRolloutSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-gradualrolloutsettings?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| durationBetweenOffers | Duration | The duration between each set of devices being offered the update, which has an effect when the **endDateTime** is defined. The value is represented in ISO 8601 format for duration. Default value is `P1D` \(one day\). Inherited from [microsoft.graph.windowsUpdates.gradualRolloutSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-gradualrolloutsettings?view=graph-rest-beta). |
| endDateTime | DateTimeOffset | Specifies the date before which all devices currently in the deployment are offered the update. Devices added after this date are offered immediately. When the **endDateTime** isn't set, all devices in the deployment are offered content at the same time. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.dateDrivenRolloutSettings",
  "durationBetweenOffers": "String (duration)",
  "endDateTime": "String (timestamp)"
}
```
