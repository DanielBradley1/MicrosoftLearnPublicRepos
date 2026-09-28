<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# virtualEventRegistrationQuestionBase resource type

Namespace: microsoft.graph

The abstract base type for a virtual event registration question.

Base type of [virtualEventRegistrationCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationcustomquestion?view=graph-rest-1.0) and [virtualEventRegistrationPredefinedQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationpredefinedquestion?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

Tip

This is an abstract type and can't be used directly. Use the derived types [virtualEventRegistrationCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationcustomquestion?view=graph-rest-1.0) and [virtualEventRegistrationPredefinedQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationpredefinedquestion?view=graph-rest-1.0) instead.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualeventregistrationconfiguration-list-questions?view=graph-rest-1.0) | [virtualEventRegistrationCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationcustomquestion?view=graph-rest-1.0) collection or [virtualEventRegistrationPredefinedQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationpredefinedquestion?view=graph-rest-1.0) collection | Get a list of all [registration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) questions for a [webinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) or [town hall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualeventregistrationconfiguration-post-questions?view=graph-rest-1.0) | [virtualEventRegistrationCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationcustomquestion?view=graph-rest-1.0) object or [virtualEventRegistrationPredefinedQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationpredefinedquestion?view=graph-rest-1.0) object | Create a [registration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) question for a [webinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) or [town hall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/virtualeventregistrationquestionbase-delete?view=graph-rest-1.0) | None | Delete a registration question from a [webinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) or [town hall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the registration question. |
| id | String | Unique identifier of the registration question. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isRequired | Boolean | Indicates whether an answer to the question is required. The default value is `false`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventRegistrationQuestionBase",
  "displayName": "String",  
  "id": "String (identifier)",
  "isRequired": "Boolean"
}
```
