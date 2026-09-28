<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationcustomquestion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# virtualEventRegistrationCustomQuestion resource type

Namespace: microsoft.graph

Represents a custom registration question associated with a [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0).

Inherits from [virtualEventRegistrationQuestionBase](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| answerChoices | String collection | Answer choices when **answerInputType** is `singleChoice` or `multiChoice`. |
| answerInputType | virtualEventRegistrationQuestionAnswerInputType | Input type of the registration question answer. Possible values are `text`, `multilineText`, `singleChoice`, `multiChoice`, `boolean`, and `unknownFutureValue`. |
| displayName | String | Display name of the registration question. Inherited from [virtualEventRegistrationQuestionBase](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionbase?view=graph-rest-1.0). |
| id | String | Unique identifier of the registration question. Inherited from [virtualEventRegistrationQuestionBase](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionbase?view=graph-rest-1.0). |
| isRequired | Boolean | Indicates whether an answer to the question is required. The default value is `false`. Inherited from [virtualEventRegistrationQuestionBase](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionbase?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventRegistrationCustomQuestion",
  "answerChoices": [
    "String"
  ],
  "answerInputType": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isRequired": "Boolean"
}
```
