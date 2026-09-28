<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-30 -->

# educationAssignmentSettings resource type

Namespace: microsoft.graph

Specifies class-level assignments settings.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/educationassignmentsettings-get?view=graph-rest-1.0) | [educationAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0) | Read the properties and relationships of an [educationAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/educationassignmentsettings-update?view=graph-rest-1.0) | [educationAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0) | Update the properties of an [educationAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0) object. |
| [Add default grading scheme](https://learn.microsoft.com/en-us/graph/api/educationassignmentsettings-put-defaultgradingscheme?view=graph-rest-1.0) | [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) | Add the default [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) to an [educationAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0) object. |
| [Update educationGradingCategory](https://learn.microsoft.com/en-us/graph/api/educationgradingcategory-update?view=graph-rest-1.0) | [educationGradingCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingcategory?view=graph-rest-1.0) | Update the gradingCategory on the assignment settings. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **educationAssignmentSettings**. |
| submissionAnimationDisabled | Boolean | Indicates whether to show the turn-in celebration animation. If `true`, indicates to skip the animation. The default value is `false`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| defaultGradingScheme | [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) | The default grading scheme for assignments created in this class. |
| gradingCategories | [educationGradingCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingcategory?view=graph-rest-1.0) collection | When set, enables users to weight assignments differently when computing a class average grade. |
| gradingSchemes | [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) collection | The grading schemes that can be attached to assignments created in this class. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "submissionAnimationDisabled": "Boolean"
}
```
