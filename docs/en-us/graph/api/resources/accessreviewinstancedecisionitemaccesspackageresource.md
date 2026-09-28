<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemaccesspackageresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# accessReviewInstanceDecisionItemAccessPackageResource resource type

Namespace: microsoft.graph

Note

This is the recommended API for access reviews. The previous version of the [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta&preserve-view=true) is deprecated.

In an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0), the **resource** property can contain an **accessReviewInstanceDecisionItemAccessPackageResource** object for an access package. This open type allows other properties to be passed in.

Inherits from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0).

## Methods

This derived type supports the same methods as the base [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0) resource. For the list of supported operations, see the base type documentation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessPackageAssignmentPolicyDisplayName | String | Display name of the access package assignment policy through which access is granted. |
| accessPackageAssignmentPolicyId | String | Identifier of the access package assignment policy through which access is granted. |
| displayName | String | Display name of the access package. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| id | String | Identifier of the decision item resource. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| type | String | Type of resource. This value is always `AccessPackage`. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewInstanceDecisionItemAccessPackageResource",
  "id": "String (identifier)",
  "displayName": "String",
  "type": "String",
  "accessPackageAssignmentPolicyId": "String",
  "accessPackageAssignmentPolicyDisplayName": "String"
}
```
