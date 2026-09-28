<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemazureroleresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewInstanceDecisionItemAzureRoleResource resource type

Namespace: microsoft.graph

In an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0), the **resource** property can contain an **accessReviewInstanceDecisionItemAzureRoleResource** object for an Azure role. This open type allows other properties to be passed in.

Inherits from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the Azure role. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| id | String | Identifier of the decision item resource. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| type | String | Type of resource. Type will always be `AzureRole`. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| scope | [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0) | Details of the scope this role is associated with. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewInstanceDecisionItemAzureRoleResource",
  "displayName": "String",
  "id": "String (identifier)",
  "scope": {
    "@odata.type": "microsoft.graph.accessReviewInstanceDecisionItemResource"
  },
  "type": "String",
}
```
