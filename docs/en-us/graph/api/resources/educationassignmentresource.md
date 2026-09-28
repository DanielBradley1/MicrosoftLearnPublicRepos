<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-17 -->

# educationAssignmentResource resource type

Namespace: microsoft.graph

A wrapper object that stores the resources associated with an assignment.

The wrapper adds the **distributeForStudentWork** property and indicates that this resource is copied to the student submission. If the object isn't copied, each student sees a link to the resource on the assignment. The student won't be able to update this resource. This is a handout from the teacher to the student with nothing to be turned in. If the resource is distributed, each student receives a copy of this resource in the resource list of their submission. Each student is able to modify their copy and submit it for grading.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/educationassignment-post-resources?view=graph-rest-1.0) | [educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) | Create an [assignment resource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/educationassignmentresource-get?view=graph-rest-1.0) | [educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) | Get the properties of an [education assignment resource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) associated with an [assignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/educationassignmentresource-delete?view=graph-rest-1.0) | None | Delete a specific [educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) attached to an assignment. |
| [List dependent resources](https://learn.microsoft.com/en-us/graph/api/educationassignmentresource-list-dependentresources?view=graph-rest-1.0) | [educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) collection | List the dependent [education assignment resources](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) for a given [education assignment resource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| distributeForStudentWork | Boolean | Indicates whether this resource should be copied to each student submission for modification and submission. Required |
| id | String | ID of this resource. Read-only. |
| resource | [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0) | Resource object that has been associated with this assignment. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| dependentResources | [educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) collection | A collection of assignment resources that depend on the parent **educationAssignmentResource**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "distributeForStudentWork": true,
  "id": "String (identifier)",
  "resource": {"@odata.type": "microsoft.graph.educationResource"}
}
```
