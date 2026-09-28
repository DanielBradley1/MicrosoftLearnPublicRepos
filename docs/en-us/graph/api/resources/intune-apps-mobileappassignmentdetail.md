<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignmentdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# mobileAppAssignmentDetail resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Type capturing mobile app specific assignment details/properties excluding assignment source and target details.

Inherits from [deviceAndAppManagementAssignmentDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmentdetail?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| intent | [mobileAppEnforcementIntentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappenforcementintenttype?view=graph-rest-beta) | Indicates the enforcement intent for the mobile app assignment. Possible values are: `requiredInstall`, `requiredUninstall`, `available`, and `availableWithoutEnrollment`. The default value is `requiredInstall`. Possible values are: `requiredInstall`, `requiredUninstall`, `available`, `availableWithoutEnrollment`, `unknownFutureValue`. |
| settings | [mobileAppAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileappassignmentsettings?view=graph-rest-beta) | Indicates the app-type-specific settings properties contained within the assignment as a polymorphic type. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppAssignmentDetail",
  "intent": "String",
  "settings": {
    "@odata.type": "microsoft.graph.winGetAppAssignmentSettings",
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
}
```
