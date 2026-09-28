<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagemultiplechoicequestion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageMultipleChoiceQuestion resource type

Namespace: microsoft.graph

A child of **accessPackageQuestion** that presents multiple options that the requestor must choose an answer from. This is used in the **questions** property of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) and inside an [accessPackageResourceAttribute](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattribute?view=graph-rest-1.0) of an access package resource.

Inherits from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| choices | [accessPackageAnswerChoice](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswerchoice?view=graph-rest-1.0) collection | List of answer choices. |
| id | String | ID of the question. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |
| isAnswerEditable | Boolean | Specifies whether the requestor is allowed to edit answers to questions. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |
| isMultipleSelectionAllowed | Boolean | Indicates whether requestor can select multiple choices as their answer. |
| isRequired | Boolean | Indicates whether the requestor is required to supply an answer or not. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |
| localizations | [accessPackageLocalizedText](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagelocalizedtext?view=graph-rest-1.0) collection | The text of the question represented in a format for a specific locale. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |
| sequence | Int32 | Relative position of this question when displaying a list of questions to the requestor. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |
| text | String | The text of the question to show to the requestor. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageMultipleChoiceQuestion",
  "id": "String (identifier)",
  "sequence": "Integer",
  "isRequired": "Boolean",
  "isAnswerEditable":"Boolean", 
  "text": "String",
  "localizations": [
    {
      "@odata.type": "microsoft.graph.accessPackageLocalizedText"
    }
  ],
  "isMultipleSelectionAllowed": "Boolean",
  "choices": [
    {
      "@odata.type": "microsoft.graph.accessPackageAnswerChoice"
    }
  ]
}
```
