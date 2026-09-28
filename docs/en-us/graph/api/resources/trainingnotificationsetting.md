<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trainingnotificationsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# trainingNotificationSetting resource type

Namespace: microsoft.graph

Represents the settings associated with a training notification.

Inherits from [endUserNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| notificationPreference | endUserNotificationPreference | Notification preference. The possible values are: `unknown`, `microsoft`, `custom`, `unknownFutureValue`. Inherited from [endUserNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-1.0). |
| positiveReinforcement | [positiveReinforcementNotification](https://learn.microsoft.com/en-us/graph/api/resources/positivereinforcementnotification?view=graph-rest-1.0) | Positive reinforcement details. Inherited from [endUserNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-1.0). |
| settingType | endUserNotificationSettingType | Setting type. The possible values are: `unknown`, `noTraining`, `trainingSelected`, `noNotification`, `unknownFutureValue`. Inherited from [endUserNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-1.0). |
| trainingAssignment | [baseEndUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/baseendusernotification?view=graph-rest-1.0) | Training assignment details. |
| trainingReminder | [trainingReminderNotification](https://learn.microsoft.com/en-us/graph/api/resources/trainingremindernotification?view=graph-rest-1.0) | Training reminder details. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trainingNotificationSetting",
  "notificationPreference": "String",
  "positiveReinforcement": {"@odata.type": "microsoft.graph.positiveReinforcementNotification"},
  "settingType": "String",
  "trainingAssignment": {"@odata.type": "microsoft.graph.baseEndUserNotification"},
  "trainingReminder": {"@odata.type": "microsoft.graph.trainingReminderNotification"}
}
```
