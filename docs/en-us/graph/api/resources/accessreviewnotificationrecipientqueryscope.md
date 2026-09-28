<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewnotificationrecipientqueryscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewNotificationRecipientQueryScope resource type

Namespace: microsoft.graph

In an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0), the **scope** property can be configured with this type to review only inactive users. The duration of inactivity is calculated based on the user's last sign-in date against the access review instance's start date as defined in the **settings** property.

Inherits from [accessReviewNotificationRecipientScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewnotificationrecipientscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| query | String | Represents the query for who the recipients are. For example, `/groups/{group id}/members` for group members and `/users/{user id}` for a specific user. |
| queryRoot | String | In the scenario where reviewers need to be specified dynamically, indicates the relative source of the query. This property is only required if a relative query \(that is, `./manager`\) is specified. |
| queryType | String | Indicates the type of query. Allowed value is `MicrosoftGraph`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewNotificationRecipientQueryScope",
  "query": "String",
  "queryRoot": "String",
  "queryType": "String"
}
```
