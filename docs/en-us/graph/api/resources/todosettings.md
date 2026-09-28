<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/todosettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# todoSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Company-wide settings for Microsoft Todo. This object is configured in the **settings** property of [adminTodo](https://learn.microsoft.com/en-us/graph/api/resources/admintodo?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isExternalJoinEnabled | Boolean | Controls whether users can join lists from users external to your organization. |
| isExternalShareEnabled | Boolean | Controls whether users can share lists with external users. |
| isPushNotificationEnabled | Boolean | Controls whether push notifications are enabled for your users. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.todoSettings",
  "isPushNotificationEnabled": "Boolean",
  "isExternalJoinEnabled": "Boolean",
  "isExternalShareEnabled": "Boolean"
}
```
