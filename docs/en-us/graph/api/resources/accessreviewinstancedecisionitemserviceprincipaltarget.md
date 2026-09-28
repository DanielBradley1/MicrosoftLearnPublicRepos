<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemserviceprincipaltarget?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewInstanceDecisionItemServicePrincipalTarget resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

This is the recommended API for access reviews. The previous version of the [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta&preserve-view=true) is deprecated.

In an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-beta), the **target** property can contain an **accessReviewInstanceDecisionItemServicePrincipalTarget** object for a service principal under review.

Inherits from [accessReviewInstanceDecisionItemTarget](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemtarget?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| servicePrincipalId | String | The identifier of the service principal whose access is being reviewed. |
| servicePrincipalDisplayName | String | The display name of the service principal whose access is being reviewed. |
| appId | String | The appId for the service principal entity being reviewed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewInstanceDecisionItemServicePrincipalTarget",
  "servicePrincipalId": "String",
  "servicePrincipalDisplayName": "String",
  "appId": "String"
}
```
