<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemusertarget?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewInstanceDecisionItemUserTarget resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

This is the recommended API for access reviews. The previous version of the [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta&preserve-view=true) is deprecated.

In an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-beta), the **target** property can contain an **accessReviewInstanceDecisionItemUserTarget** object for a user under review.

Inherits from [accessReviewInstanceDecisionItemTarget](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemtarget?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userDisplayName | String | The name of user. |
| userId | String | The identifier of user. |
| userPrincipalName | String | The user principal name. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewInstanceDecisionItemUserTarget",
  "userId": "String",
  "userDisplayName": "String",
  "userPrincipalName": "String"
}
```
