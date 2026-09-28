<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentapprovalsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageAssignmentApprovalSettings resource type

Namespace: microsoft.graph

Used for the **requestApprovalSettings** property of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0). Provides additional settings to indicate if approval is needed for new requests for an access package assignment through that policy or for updates to existing requests, and to select who must approve each request.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isApprovalRequiredForAdd | Boolean | If `false,` then approval isn't required for new requests in this policy. |
| isApprovalRequiredForUpdate | Boolean | If `false`, then approval isn't required for updates to requests in this policy. |
| isRequestorJustificationRequired | Boolean | If `false`, then requestor justification isn't required for updates to requests in this policy. |
| stages | [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0) collection | If approval is required, the one, two or three elements of this collection define each of the stages of approval. An empty array is present if no approval is required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentApprovalSettings",
  "isApprovalRequiredForAdd": "Boolean",
  "isApprovalRequiredForUpdate": "Boolean",
  "isRequestorJustificationRequired": "Boolean",
  "stages": [
    {
      "@odata.type": "microsoft.graph.accessPackageApprovalStage"
    }
  ]
}
```
