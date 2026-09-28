<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/simulationnotification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# simulationNotification resource type

Namespace: microsoft.graph

Represents the content of a notification that targets users who are part of a simulation.

Inherits from [baseEndUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/baseendusernotification?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultLanguage | String | Default language. Inherited from [baseEndUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/baseendusernotification?view=graph-rest-1.0). |
| targettedUserType | targettedUserType | Target user type. The possible values are: `unknown`, `clicked`, `compromised`, `allUsers`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| endUserNotification | [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) | End user notification detail. Inherited from [baseEndUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/baseendusernotification?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.simulationNotification",
  "defaultLanguage": "String",
  "targettedUserType": "String"
}
```
