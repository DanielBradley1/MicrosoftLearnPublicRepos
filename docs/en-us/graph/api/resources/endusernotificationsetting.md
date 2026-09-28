<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# endUserNotificationSetting resource type

Namespace: microsoft.graph

Represents an end user notification setting provided by an administrator during a simulation creation.

Base type of [noTrainingNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/notrainingnotificationsetting?view=graph-rest-1.0) and [trainingNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingnotificationsetting?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| notificationPreference | endUserNotificationPreference | Notification preference. The possible values are: `unknown`, `microsoft`, `custom`, `unknownFutureValue`. |
| positiveReinforcement | [positiveReinforcementNotification](https://learn.microsoft.com/en-us/graph/api/resources/positivereinforcementnotification?view=graph-rest-1.0) | Positive reinforcement detail. |
| settingType | endUserNotificationSettingType | End user notification type. The possible values are: `unknown`, `noTraining`, `trainingSelected`, `noNotification`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.endUserNotificationSetting",
  "notificationPreference": "String",
  "positiveReinforcement": {"@odata.type": "microsoft.graph.positiveReinforcementNotification"},
  "settingType": "String"
}
```
