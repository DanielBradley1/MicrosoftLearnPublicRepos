<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/exchangesettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# exchangeSettings resource type

Namespace: microsoft.graph

Represents the Exchange settings for mailbox discovery.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/usersettings-list-exchange?view=graph-rest-1.0) | [exchangeSettings](https://learn.microsoft.com/en-us/graph/api/resources/exchangesettings?view=graph-rest-1.0) | Get a list of Exchange mailboxes that belong to a user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| primaryMailboxId | String | The unique identifier for the user's primary mailbox. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.exchangeSettings",
  "primaryMailboxId": "String"
}
```
