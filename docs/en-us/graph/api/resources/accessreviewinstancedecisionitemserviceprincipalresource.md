<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemserviceprincipalresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# accessReviewInstanceDecisionItemServicePrincipalResource resource type

Namespace: microsoft.graph

In an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0), the **resource** property can contain an **accessReviewInstanceDecisionItemServicePrincipalResource** object for a service principal resource. This open type allows other properties to be passed in.

Inherits from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The globally unique identifier of the application to which access has been granted. |
| appRoleDisplayName | String | The display name of the app role. |
| appRoleId | String | The identifier of the app role. |
| displayName | String | Display name of the resource. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| id | String | Identifier of the decision item resource. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| type | String | Type of resource. Type will always be `ServicePrincipal`. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessreviewinstancedecisionitemserviceprincipalresource",
  "appId": "String",
  "appRoleDisplayName": "String",
  "appRoleId": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "type": "String"
}
```
