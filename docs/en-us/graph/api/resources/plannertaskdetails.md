<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# plannerTaskDetails resource type

Namespace: microsoft.graph

Represents the additional information about a task. Each [task](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) object has a details object.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get task details](https://learn.microsoft.com/en-us/graph/api/plannertaskdetails-get?view=graph-rest-1.0) | [plannerTaskDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-1.0) | Read properties and relationships of **plannerTaskDetails** object. |
| [Update task details](https://learn.microsoft.com/en-us/graph/api/plannertaskdetails-update?view=graph-rest-1.0) | [plannerTaskDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-1.0) | Update **plannerTaskDetails** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| checklist | [plannerChecklistItems](https://learn.microsoft.com/en-us/graph/api/resources/plannerchecklistitems?view=graph-rest-1.0) | The collection of checklist items on the task. |
| description | String | Description of the task. |
| id | String | Read-only. ID of the task details. It's 28 characters long and case-sensitive. [Format validation](https://learn.microsoft.com/en-us/graph/api/resources/planner-identifiers-disclaimer?view=graph-rest-1.0) is done on the service. |
| previewType | string | This sets the type of preview that shows up on the task. The possible values are: `automatic`, `noPreview`, `checklist`, `description`, `reference`. When set to `automatic` the displayed preview is chosen by the app viewing the task. |
| references | [plannerExternalReferences](https://learn.microsoft.com/en-us/graph/api/resources/plannerexternalreferences?view=graph-rest-1.0) | The collection of references on the task. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "checklist": {"@odata.type": "microsoft.graph.plannerChecklistItems"},
  "description": "String",
  "id": "String (identifier)",
  "previewType": "string",
  "references": {"@odata.type": "microsoft.graph.plannerExternalReferences"}
}
```
