<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/planusageright?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-12 -->

# planUsageRight resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the usage rights evaluation result for a Microsoft Planner plan based on its sensitivity label assignment. This resource provides information about whether a plan has a sensitivity label applied and which specific permissions the requesting user has on the plan content.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hasSensitivityLabel | Boolean | Indicates whether the plan has a sensitivity label applied. If `true`, the plan has a sensitivity label assignment; if `false`, no sensitivity label is applied. |
| planId | String | The unique identifier of the plan for which usage rights are under evaluation. |
| usageRights | [usageRightsInfo](https://learn.microsoft.com/en-us/graph/api/resources/usagerightsinfo?view=graph-rest-beta) | The detailed usage rights information for the requesting user on the plan. This property is `null` when no sensitivity label is applied to the plan. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.planUsageRight",
  "hasSensitivityLabel": "Boolean",
  "planId": "String",
  "usageRights": {"@odata.type": "microsoft.graph.usageRightsInfo"}
}
```
