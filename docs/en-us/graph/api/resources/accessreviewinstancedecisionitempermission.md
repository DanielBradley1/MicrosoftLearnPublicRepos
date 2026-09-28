<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitempermission?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# accessReviewInstanceDecisionItemPermission resource type

Namespace: microsoft.graph

In an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0), the **permission** property represents the permission that grants a principal access to a resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the permission. |
| displayName | String | The display name of the permission. |
| id | String | The identifier of the permission. |
| type | String | The type of the permission. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewInstanceDecisionItemPermission",
  "id": "String",
  "displayName": "String",
  "type": "String",
  "description": "String"
}
```
