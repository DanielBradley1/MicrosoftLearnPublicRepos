<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/positivereinforcementnotification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# positiveReinforcementNotification resource type

Namespace: microsoft.graph

Represents positive reinforcement settings for an end user notification during simulation creation. Admins can configure the notification details for a user who identifies the phish message successfully.

Inherits from [baseEndUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/baseendusernotification?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultLanguage | String | Default language. Inherited from [baseEndUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/baseendusernotification?view=graph-rest-1.0). |
| deliveryPreference | notificationDeliveryPreference | Delivery preference. The possible values are: `unknown`, `deliverImmedietly`, `deliverAfterCampaignEnd`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| endUserNotification | [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) | End user notification detail. Inherited from [baseEndUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/baseendusernotification?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.positiveReinforcementNotification",
  "defaultLanguage": "String",
  "deliveryPreference": "String"
}
```
