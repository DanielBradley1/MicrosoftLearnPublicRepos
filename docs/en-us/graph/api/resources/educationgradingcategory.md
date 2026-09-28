<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationgradingcategory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# educationGradingCategory resource type

Namespace: microsoft.graph

Represents the weighted contribution of an assignment to a class average grade.

> **Note:** Configure grading categories by using [Assignment settings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Add](https://learn.microsoft.com/en-us/graph/api/educationassignment-post-gradingcategory?view=graph-rest-1.0) | [gradingCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingcategory?view=graph-rest-1.0) | Add a new **gradingCategory**. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/educationassignment-delete-gradingcategory?view=graph-rest-1.0) | [educationCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingcategory?view=graph-rest-1.0) | Remove existing **gradingCategory**. |
| [Update](https://learn.microsoft.com/en-us/graph/api/educationgradingcategory-update?view=graph-rest-1.0) | [educationCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingcategory?view=graph-rest-1.0) | Update a single **gradingCategory**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the grading category ID. This separate ID allows teachers to rename a grading category without losing the link to each assignment. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |
| displayName | String | The name of the grading category. |
| percentageWeight | Int32 | The weight of the category; an integer between 0 and 100. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationGradingCategory",
  "id": "String (identifier)",
  "displayName": "String",
  "percentageWeight": "Int32"
}
```
