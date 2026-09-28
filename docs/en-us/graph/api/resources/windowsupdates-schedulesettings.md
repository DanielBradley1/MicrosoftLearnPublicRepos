<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-schedulesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# scheduleSettings resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings for controlling how and when Windows Autopatch deploys an update over time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| gradualRollout | [microsoft.graph.windowsUpdates.gradualRolloutSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-gradualrolloutsettings?view=graph-rest-beta) | Settings for governing how to rollout content to devices. One of: [microsoft.graph.windowsUpdates.dateDrivenRolloutSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-datedrivenrolloutsettings?view=graph-rest-beta), [microsoft.graph.windowsUpdates.durationDrivenRolloutSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-durationdrivenrolloutsettings?view=graph-rest-beta), or [microsoft.graph.windowsUpdates.rateDrivenRolloutSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ratedrivenrolloutsettings?view=graph-rest-beta). |
| startDateTime | DateTimeOffset | The date on which devices in the deployment start receiving the update. When not set, the deployment starts as soon as devices are assigned. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.scheduleSettings",
  "gradualRollout": {"@odata.type": "microsoft.graph.windowsUpdates.gradualRolloutSettings"},
  "startDateTime": "String (timestamp)"
}
```
