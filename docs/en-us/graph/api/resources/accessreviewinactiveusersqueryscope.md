<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinactiveusersqueryscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewInactiveUsersQueryScope resource type

Namespace: microsoft.graph

In an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0), the **scope** property can be configured with this type to review only inactive users. The duration of inactivity is calculated based on the user's last sign-in date against the access review instance's start date as defined in the **settings** property.

Inherits from [accessReviewQueryScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewqueryscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inactiveDuration | Duration | Defines the duration of inactivity. Inactivity is based on the last sign in date of the user compared to the access review instance's start date. If this property is not specified, it's assigned the default value `PT0S`. |
| query | String | Inherited from [accessReviewQueryScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewqueryscope?view=graph-rest-1.0). |
| queryRoot | String | Inherited from [accessReviewQueryScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewqueryscope?view=graph-rest-1.0). |
| queryType | String | Inherited from [accessReviewQueryScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewqueryscope?view=graph-rest-1.0). |

You must also specify the **@odata.type** type property with the value `#microsoft.graph.accessReviewInactiveUsersQueryScope`. For more about configuration options for **scope** using **accessReviewInactiveUsersQueryScope**, see [Configure the scope of your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept).

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewInactiveUsersQueryScope",
  "inactiveDuration": "String (duration)",
  "query": "String",
  "queryRoot": "String",
  "queryType": "String"
  
}
```
