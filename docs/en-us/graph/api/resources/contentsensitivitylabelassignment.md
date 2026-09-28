<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contentsensitivitylabelassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-12 -->

# contentSensitivityLabelAssignment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the sensitivity label assignment for plan. This resource type is used to apply Microsoft Information Protection \(MIP\) sensitivity labels to plans in Microsoft Planner, enabling data governance and access control based on organizational policies.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentMethod | sensitivityLabelAssignmentMethod | The method used to assign the sensitivity label. The possible values are: `standard`, `privileged`, `auto`, `unknownFutureValue`. |
| justificationText | String | The justification text provided when you change the sensitivity label. Used during label downgrade to document the reason. Optional. |
| sensitivityLabelId | String | The unique identifier of the sensitivity label applied to the content. This ID corresponds to a label defined in the Microsoft Information Protection policy. |
| tenantId | String | The unique identifier of the tenant where the sensitivity label is defined and applied. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.contentSensitivityLabelAssignment",
  "assignmentMethod": "String",
  "justificationText": "String",
  "sensitivityLabelId": "String",
  "tenantId": "String"
}
```
