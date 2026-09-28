<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerbaseapprovalattachment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-16 -->

# plannerBaseApprovalAttachment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the base approval attachment, which contains the common properties that are required for an approval, that is added to a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). The derived types, such as [plannerBasicApprovalAttachment](https://learn.microsoft.com/en-us/graph/api/resources/plannerbasicapprovalattachment?view=graph-rest-beta), have details corresponding to the type of approval.

This type is abstract.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| status | [plannerApprovalStatus](https://learn.microsoft.com/en-us/graph/api/resources/plannerbaseapprovalattachment?view=graph-rest-beta#plannerapprovalstatus-values) | Status of the approval. The possible values are: `requested`, `approved`, `rejected`, `cancelled`, `unknownFutureValue`. Read-only. |

### plannerApprovalStatus values

| Member |
| :--- |
| requested |
| approved |
| rejected |
| cancelled |
| unknownFutureValue |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerBaseApprovalAttachment",
  "status": "String"
}
```
