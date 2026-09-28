<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/notrainingnotificationsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# noTrainingNotificationSetting resource type

Namespace: microsoft.graph

Represents a notification setting when no training is selected on a simulation creation.

Inherits from [endUserNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| notificationPreference | endUserNotificationPreference | Notification preference. The possible values are: `unknown`, `microsoft`, `custom`, `unknownFutureValue`. Inherited from [endUserNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-1.0). |
| positiveReinforcement | [positiveReinforcementNotification](https://learn.microsoft.com/en-us/graph/api/resources/positivereinforcementnotification?view=graph-rest-1.0) | Notification for users who reported the phish email. Inherited from [endUserNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-1.0). |
| settingType | endUserNotificationSettingType | The setting type. The possible values are: `unknown`, `noTraining`, `trainingSelected`, `noNotification`, `unknownFutureValue`. Inherited from [endUserNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-1.0). |
| simulationNotification | [simulationNotification](https://learn.microsoft.com/en-us/graph/api/resources/simulationnotification?view=graph-rest-1.0) | The notification for the user who is part of the simulation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.noTrainingNotificationSetting",
  "notificationPreference": "String",
  "positiveReinforcement": {"@odata.type": "microsoft.graph.positiveReinforcementNotification"},
  "settingType": "String",
  "simulationNotification": {"@odata.type": "microsoft.graph.simulationNotification"}
}
```
