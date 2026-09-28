<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-wingetappassignmentsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# winGetAppAssignmentSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to assign a WinGet app to a group.

Inherits from [mobileAppAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileappassignmentsettings?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| notifications | [winGetAppNotification](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-wingetappnotification?view=graph-rest-beta) | The notification status for this app assignment. The possible values are: `showAll`, `showReboot`, `hideAll`, `unknownFutureValue`. |
| restartSettings | [winGetAppRestartSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-wingetapprestartsettings?view=graph-rest-beta) | The reboot settings to apply for this app assignment. |
| installTimeSettings | [winGetAppInstallTimeSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-wingetappinstalltimesettings?view=graph-rest-beta) | The install time settings to apply for this app assignment. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.winGetAppAssignmentSettings",
  "notifications": "String",
  "restartSettings": {
    "@odata.type": "microsoft.graph.winGetAppRestartSettings",
    "gracePeriodInMinutes": 1024,
    "countdownDisplayBeforeRestartInMinutes": 1024,
    "restartNotificationSnoozeDurationInMinutes": 1024
  },
  "installTimeSettings": {
    "@odata.type": "microsoft.graph.winGetAppInstallTimeSettings",
    "useLocalTime": true,
    "deadlineDateTime": "String (timestamp)"
  }
}
```
