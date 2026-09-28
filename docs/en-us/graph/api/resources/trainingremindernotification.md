<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trainingremindernotification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# trainingReminderNotification resource type

Namespace: microsoft.graph

Represents notification content details for a training reminder during a simulation creation.

Inherits from [baseEndUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/baseendusernotification?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultLanguage | String | Default language. Inherited from [baseEndUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/baseendusernotification?view=graph-rest-1.0). |
| deliveryFrequency | notificationDeliveryFrequency | Configurable frequency for the reminder email introduced during simulation creation. The possible values are: `unknown`, `weekly`, `biWeekly`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| endUserNotification | [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) | End user notification detail. Inherited from [baseEndUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/baseendusernotification?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trainingReminderNotification",
  "defaultLanguage": "String",
  "deliveryFrequency": "String"
}
```
