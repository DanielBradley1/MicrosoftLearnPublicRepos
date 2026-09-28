<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/notificationrecipients?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-06 -->

# notificationRecipients resource type

Namespace: microsoft.graph

Represents the recipients of multi-admin notifications.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customRecipients | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) collection | A list of users or groups that receive notifications. Only specify this property when **role** is set to `custom`. |
| role | notificationRecipientsType | Indicates whether the recipient type is an admin role or a custom list. The possible values are: `none`, `globalAdmins`, `backupAdmins`, `custom`, `allAdmins`, `unknownFutureValue`. The default value is `custom`. This property is read-only for third-party partners. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.notificationRecipients",
  "customRecipients": [{"@odata.type": "microsoft.graph.emailIdentity"}],
  "role": "String"
}
```
