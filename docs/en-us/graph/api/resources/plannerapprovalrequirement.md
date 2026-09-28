<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerapprovalrequirement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-07 -->

# plannerApprovalRequirement resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents whether a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta) must have an approval completion requirement created for it. Setting this property directly is not recommended, as approval requirements can only be added via the task publishing feature. Use this field to query published tasks for approval requirements.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isApprovalRequired | Boolean | Specifies whether [approval](https://learn.microsoft.com/en-us/graph/api/resources/plannerbaseapprovalattachment?view=graph-rest-beta) is required to complete the [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). If set to `true`, the task can only be marked as complete if an approval is created for the task and approved. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerApprovalRequirement",
  "isApprovalRequired": "Boolean"
}
```
