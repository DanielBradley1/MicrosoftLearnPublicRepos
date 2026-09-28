<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerbasicapprovalattachment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-16 -->

# plannerBasicApprovalAttachment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the approval attachment, of type basic, that is created by the approval extensibility service and is added to a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta).

Inherits from [plannerBaseApprovalAttachment](https://learn.microsoft.com/en-us/graph/api/resources/plannerbaseapprovalattachment?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalId | String | Read-only. The identifier of the approval in the approval service. |
| status | [plannerApprovalStatus](https://learn.microsoft.com/en-us/graph/api/resources/plannerbaseapprovalattachment?view=graph-rest-beta#plannerapprovalstatus-values) | The status of the approval. Inherited from [plannerBaseApprovalAttachment](https://learn.microsoft.com/en-us/graph/api/resources/plannerbaseapprovalattachment?view=graph-rest-beta). The possible values are: `requested`, `approved`, `rejected`, `cancelled`, `unknownFutureValue`. Read-only. |

### plannerApprovalStatus values

| Member | Description |
| :--- | :--- |
| requested | Default. Approval is requested. |
| approved | The plannerTask is approved. |
| rejected | The plannerTask is rejected. |
| cancelled | The requestor canceled the approval. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerBasicApprovalAttachment",
  "status": "String",
  "approvalId": "String"
}
```
