<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskcompletionrequirementdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-16 -->

# plannerTaskCompletionRequirementDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information about [completionRequirements](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta#plannertaskcompletionrequirements-values) for a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalRequirement | [plannerApprovalRequirement](https://learn.microsoft.com/en-us/graph/api/resources/plannerapprovalrequirement?view=graph-rest-beta) | Information about the requirements of an approval. |
| checklistRequirement | [plannerChecklistRequirement](https://learn.microsoft.com/en-us/graph/api/resources/plannerchecklistrequirement?view=graph-rest-beta) | Information about the requirements for completing the checklist. |
| formsRequirement | [plannerFormsRequirement](https://learn.microsoft.com/en-us/graph/api/resources/plannerformsrequirement?view=graph-rest-beta) | Information about the requirements for completing the forms. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskCompletionRequirementDetails",
  "checklistRequirement": {"@odata.type": "microsoft.graph.plannerChecklistRequirement"},
  "formsRequirement": {"@odata.type": "microsoft.graph.plannerFormsRequirement"},
  "approvalRequirement":  {"@odata.type": "microsoft.graph.plannerApprovalRequirement" }
}
```
