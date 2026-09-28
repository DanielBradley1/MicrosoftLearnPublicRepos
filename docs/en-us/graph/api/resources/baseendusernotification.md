<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/baseendusernotification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# baseEndUserNotification resource type

Namespace: microsoft.graph

Represents details about an end user notification.

Base type of [positiveReinforcementNotification](https://learn.microsoft.com/en-us/graph/api/resources/positivereinforcementnotification?view=graph-rest-1.0), [simulationNotification](https://learn.microsoft.com/en-us/graph/api/resources/simulationnotification?view=graph-rest-1.0), and [trainingReminderNotification](https://learn.microsoft.com/en-us/graph/api/resources/trainingremindernotification?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultLanguage | String | The default language for the end user notification. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| endUserNotification | [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) | End user notification detail. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.baseEndUserNotification",
  "defaultLanguage": "String"
}
```
