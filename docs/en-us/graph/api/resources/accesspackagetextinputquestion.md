<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagetextinputquestion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageTextInputQuestion resource type

Namespace: microsoft.graph

A child of **accessPackageQuestion** that has text input as an answer and is used in the **questions** property of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) and inside an [accessPackageResourceAttribute](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattribute?view=graph-rest-1.0) of an access package resource.

Inherits from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ID of the question. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |
| isAnswerEditable | Boolean | Specifies whether the requestor is allowed to edit answers to questions. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |
| isRequired | Boolean | Indicates whether the requestor is required to supply an answer or not. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |
| isSingleLineQuestion | Boolean | Indicates whether the answer is in single or multiple line format. |
| localizations | [accessPackageLocalizedText](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagelocalizedtext?view=graph-rest-1.0) collection | The text of the question represented in a format for a specific locale. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |
| regexPattern | String | The regular expression pattern that any answer to this question must match. |
| sequence | Int32 | Relative position of this question when displaying a list of questions to the requestor. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |
| text | String | The text of the question to show to the requestor. Inherited from [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
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
  "isSingleLineQuestion": "Boolean",
  "regexPattern": "String"
}
```
