<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/emailnotificationssetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-06 -->

# emailNotificationsSetting resource type

Namespace: microsoft.graph

Represents the email settings for multi-admin notifications.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/emailnotificationssetting-get?view=graph-rest-1.0) | [emailNotificationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/emailnotificationssetting?view=graph-rest-1.0) | Read the properties and relationships of an [emailNotificationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/emailnotificationssetting?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/emailnotificationssetting-update?view=graph-rest-1.0) | [emailNotificationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/emailnotificationssetting?view=graph-rest-1.0) | Update the properties of an [emailNotificationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/emailnotificationssetting?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalEvents | notificationEventsType | Indicates whether to opt in to additional policy and restore updates. Possible values: `none`, `restoreAndPolicyUpdates`, `unknownFutureValue`. |
| isEnabled | Boolean | Indicates whether notifications are enabled. |
| recipients | [notificationRecipients](https://learn.microsoft.com/en-us/graph/api/resources/notificationrecipients?view=graph-rest-1.0) | The **notificationRecipients** object that specifies the recipients who receive the notifications. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.emailNotificationsSetting",
  "additionalEvents": "String",
  "isEnabled": "Boolean",
  "recipients": {"@odata.type": "microsoft.graph.notificationRecipients"}
}
```
