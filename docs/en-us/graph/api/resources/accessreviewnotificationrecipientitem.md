<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewnotificationrecipientitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewNotificationRecipientItem resource type

Namespace: microsoft.graph

In an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0), the **additionalNotificationRecipients** property configures **accessReviewNotificationRecipientItem** objects for access review notifications. Each item contains an email template type and recipient properties for a given [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| notificationRecipientScope | [accessReviewNotificationRecipientScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewnotificationrecipientscope?view=graph-rest-1.0) | Determines the recipient of the notification email. |
| notificationTemplateType | String | Indicates the type of access review email to be sent. Supported template type is `CompletedAdditionalRecipients`, which sends review completion notifications to the recipients. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type":"#microsoft.graph.accessReviewNotificationRecipientItem",
  "notificationRecipientScope": {
      "@odata.type":"#microsoft.graph.accessReviewNotificationRecipientQueryScope"                
    },
  "notificationTemplateType": "String"
}
```
