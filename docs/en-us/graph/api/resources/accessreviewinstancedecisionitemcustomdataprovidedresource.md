<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemcustomdataprovidedresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# accessReviewInstanceDecisionItemCustomDataProvidedResource resource type

Namespace: microsoft.graph

In an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0), the **resource** property can contain an **accessReviewInstanceDecisionItemCustomDataProvidedResource** object for an external customer-provided resource. This open type allows other properties to be passed in.

Inherits from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customData | String | Custom data to include with the decision. |
| description | String | The description of the custom data provided resource. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| displayName | String | The display name of the custom data provided resource. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| id | String | The identifier of the custom data provided resource. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |
| scopeDisplayName | String | The name of the scope for the decision. |
| scopeId | String | The identifier of the scope for the decision. |
| type | String | The type of the custom data provided resource. Inherited from [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewInstanceDecisionItemCustomDataProvidedResource",
  "id": "String",
  "displayName": "String",
  "type": "String",
  "description": "String",
  "customData": "String",
  "scopeId": "String",
  "scopeDisplayName": "String"
}
```
