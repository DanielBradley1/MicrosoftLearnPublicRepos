<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetailsdata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-21 -->

# plannerTaskDetailsData resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a snapshot of additional [details](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-beta) about a [planner task](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta) at a specific point in time. This resource is used in [plannerTaskData](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdata?view=graph-rest-beta) to capture extended task information before and after changes.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalAttachment | [plannerBaseApprovalAttachment](https://learn.microsoft.com/en-us/graph/api/resources/plannerbaseapprovalattachment?view=graph-rest-beta) | Detailed information about the approval that is attached to the task. |
| checklist | [plannerChecklistItems](https://learn.microsoft.com/en-us/graph/api/resources/plannerchecklistitems?view=graph-rest-beta) | The collection of checklist items on the task. |
| completionRequirements | [plannerTaskCompletionRequirementDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskcompletionrequirementdetails?view=graph-rest-beta) | Contains detailed information about requirements on the task. |
| description | String | Description of the task. |
| forms | [plannerFormsDictionary](https://learn.microsoft.com/en-us/graph/api/resources/plannerformsdictionary?view=graph-rest-beta) | The collection of forms associated with the task. |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta) | Rich text description of the task for use by applications that support HTML content. |
| previewType | plannerPreviewType | The type of preview that shows up on the task. The possible values are: `automatic`, `noPreview`, `checklist`, `description`, `reference`. |
| references | [plannerExternalReferences](https://learn.microsoft.com/en-us/graph/api/resources/plannerexternalreferences?view=graph-rest-beta) | The collection of references on the task. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskDetailsData",
  "description": "String",
  "notes": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "previewType": "String",
  "references": {
    "@odata.type": "microsoft.graph.plannerExternalReferences"
  },
  "checklist": {
    "@odata.type": "microsoft.graph.plannerChecklistItems"
  },
  "forms": {
    "@odata.type": "microsoft.graph.plannerFormsDictionary"
  },
  "completionRequirements": {
    "@odata.type": "microsoft.graph.plannerTaskCompletionRequirementDetails"
  },
  "approvalAttachment": {
    "@odata.type": "microsoft.graph.plannerBaseApprovalAttachment"
  }
}
```
