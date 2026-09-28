<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprestartsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# win32LobAppRestartSettings resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties describing restart coordination following an app installation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| gracePeriodInMinutes | Int32 | The number of minutes to wait before restarting the device after an app installation. |
| countdownDisplayBeforeRestartInMinutes | Int32 | The number of minutes before the restart time to display the countdown dialog for pending restarts. |
| restartNotificationSnoozeDurationInMinutes | Int32 | The number of minutes to snooze the restart notification dialog when the snooze button is selected. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppRestartSettings",
  "gracePeriodInMinutes": 1024,
  "countdownDisplayBeforeRestartInMinutes": 1024,
  "restartNotificationSnoozeDurationInMinutes": 1024
}
```
