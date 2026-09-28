<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-17 -->

# educationSubmissionResource resource type

Namespace: microsoft.graph

A wrapper around a resource for use on a submission.

The wrapper adds a pointer to the assignment resource if the resource was copied from the assignment.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/educationsubmission-list-resources?view=graph-rest-1.0) | [educationSubmissionResource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) objects | Returns a list of **educationSubmissionResource** objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/educationsubmissionresource-get?view=graph-rest-1.0) | [educationSubmissionResource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) | Read properties and relationships of an **educationSubmissionResource** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/educationsubmissionresource-delete?view=graph-rest-1.0) | None | Delete an **educationSubmissionResource** object. |
| [List dependent resources](https://learn.microsoft.com/en-us/graph/api/educationsubmissionresource-list-dependentresources?view=graph-rest-1.0) | [educationSubmissionResource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) collection | List the dependent [education submission resources](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) for a given [education submission resource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentResourceUrl | String | Pointer to the assignment from which the resource was copied. If the value is `null`, the student uploaded the resource. |
| id | String | Read-only. |
| resource | [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0) | Resource object. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| dependentResources | [educationSubmissionResource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) collection | A collection of submission resources that depend on the parent **educationSubmissionResource**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "assignmentResourceUrl": "String",
  "id": "String (identifier)",
  "resource": {"@odata.type": "microsoft.graph.educationResource"}
}
```
