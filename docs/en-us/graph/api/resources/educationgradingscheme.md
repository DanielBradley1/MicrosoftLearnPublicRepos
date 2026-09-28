<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-30 -->

# educationGradingScheme resource type

Namespace: microsoft.graph

Represents a custom scheme for grading.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/educationassignmentsettings-post-gradingschemes?view=graph-rest-1.0) | [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) | Create a new [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) on an [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/educationgradingscheme-get?view=graph-rest-1.0) | [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) | Read the properties and relationships of an [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/educationgradingscheme-update?view=graph-rest-1.0) | [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) | Update the properties of an [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/educationgradingscheme-delete?view=graph-rest-1.0) | None | Delete an [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the grading scheme. |
| grades | [educationGradingSchemeGrade](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingschemegrade?view=graph-rest-1.0) collection | The grades that make up the scheme. |
| hidePointsDuringGrading | Boolean | The display setting for the UI. Indicates whether teachers can grade with points in addition to letter grades. |
| id | String | The ID of the grading scheme. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationGradingScheme",
  "displayName": "String",
  "grades": [{"@odata.type": "microsoft.graph.educationGradingSchemeGrade"}],
  "hidePointsDuringGrading": "Boolean",
  "id": "String (identifier)"
}
```
