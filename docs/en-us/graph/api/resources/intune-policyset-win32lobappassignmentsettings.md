<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-win32lobappassignmentsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# win32LobAppAssignmentSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to assign an Win32 LOB mobile app to a group.

Inherits from [mobileAppAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileappassignmentsettings?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| notifications | [win32LobAppNotification](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-win32lobappnotification?view=graph-rest-beta) | The notification status for this app assignment. The possible values are: `showAll`, `showReboot`, `hideAll`. |
| restartSettings | [win32LobAppRestartSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-win32lobapprestartsettings?view=graph-rest-beta) | The reboot settings to apply for this app assignment. |
| installTimeSettings | [mobileAppInstallTimeSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileappinstalltimesettings?view=graph-rest-beta) | The install time settings to apply for this app assignment. |
| deliveryOptimizationPriority | [win32LobAppDeliveryOptimizationPriority](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-win32lobappdeliveryoptimizationpriority?view=graph-rest-beta) | The delivery optimization priority for this app assignment. This setting is not supported in National Cloud environments. The possible values are: `notConfigured`, `foreground`. |
| autoUpdateSettings | [win32LobAppAutoUpdateSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-win32lobappautoupdatesettings?view=graph-rest-beta) | The auto-update settings to apply for this app assignment. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppAssignmentSettings",
  "notifications": "String",
  "restartSettings": {
    "@odata.type": "microsoft.graph.win32LobAppRestartSettings",
    "gracePeriodInMinutes": 1024,
    "countdownDisplayBeforeRestartInMinutes": 1024,
    "restartNotificationSnoozeDurationInMinutes": 1024
  },
  "installTimeSettings": {
    "@odata.type": "microsoft.graph.mobileAppInstallTimeSettings",
    "useLocalTime": true,
    "startDateTime": "String (timestamp)",
    "deadlineDateTime": "String (timestamp)"
  },
  "deliveryOptimizationPriority": "String",
  "autoUpdateSettings": {
    "@odata.type": "microsoft.graph.win32LobAppAutoUpdateSettings",
    "autoUpdateSupersededApps": "String"
  }
}
```
