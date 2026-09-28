<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approvalsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# approvalSettings resource type

Namespace: microsoft.graph

The settings for approval as defined in a role management policy rule.

In entitlement management, this object is configured in the **requestApprovalSettings** property of [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalMode | String | One of `SingleStage`, `Serial`, `Parallel`, `NoApproval` \(default\). `NoApproval` is used when `isApprovalRequired` is `false`. |
| approvalStages | [unifiedApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/unifiedapprovalstage?view=graph-rest-1.0) collection | If approval is required, the one or two elements of this collection define each of the stages of approval. An empty array if no approval is required. |
| isApprovalRequired | Boolean | Indicates whether approval is required for requests in this policy. |
| isApprovalRequiredForExtension | Boolean | Indicates whether approval is required for a user to extend their assignment. |
| isRequestorJustificationRequired | Boolean | Indicates whether the requestor is required to supply a justification in their request. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approvalSettings",
  "approvalMode": "String",
  "approvalStages": [
    {
      "@odata.type": "microsoft.graph.unifiedApprovalStage"
    }],
  "isApprovalRequired": "Boolean",
  "isApprovalRequiredForExtension": "Boolean",
  "isRequestorJustificationRequired": "Boolean"
}
```
