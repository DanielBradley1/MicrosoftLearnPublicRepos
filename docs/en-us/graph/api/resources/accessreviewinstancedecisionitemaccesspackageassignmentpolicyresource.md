<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemaccesspackageassignmentpolicyresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewInstanceDecisionItemAccessPackageAssignmentPolicyResource resource type

Namespace: microsoft.graph

In an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0), the **resource** property can contain an **accessReviewInstanceDecisionItemAccessPackageAssignmentPolicyResource** object for an access package assignment policy. This open type allows other properties to be passed in.

Inherits from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessPackageDisplayName | String | Display name of the access package to which access has been granted. |
| accessPackageId | String | Identifier of the access package to which access has been granted. |
| displayName | String | Display name of the access package. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| id | String | Identifier of the decision item resource. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| type | String | Type of resource. Type will always be `AccessPackageAssignmentPolicy`. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewInstanceDecisionItemAccessPackageAssignmentPolicyResource",
  "accessPackageDisplayName": "String",
  "accessPackageId": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "type": "String"
}
```
