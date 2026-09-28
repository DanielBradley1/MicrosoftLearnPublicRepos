<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageQuestion resource type

Namespace: microsoft.graph

Used for the **accessPackageQuestion** property of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) and the **accessPackageResourceAttributeQuestion** in an [accessPackageResourceAttribute](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattribute?view=graph-rest-1.0).

Subtypes include [accessPackageTextInputQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagetextinputquestion?view=graph-rest-1.0) and [accessPackageMultipleChoiceQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagemultiplechoicequestion?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ID of the question. |
| isAnswerEditable | Boolean | Specifies whether the requestor is allowed to edit answers to questions for an assignment [by posting an update to accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-assignmentrequests?view=graph-rest-1.0). |
| isRequired | Boolean | Whether the requestor is required to supply an answer or not. |
| localizations | [accessPackageLocalizedText](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagelocalizedtext?view=graph-rest-1.0) collection | The text of the question represented in a format for a specific locale. |
| text | String | The text of the question to show to the requestor. |
| sequence | Int32 | Relative position of this question when displaying a list of questions to the requestor. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageQuestion",
  "id": "String (identifier)",
  "sequence": "Integer",
  "isRequired": "Boolean",
  "isAnswerEditable": "Boolean", 
  "text": "String",
  "localizations": [
    {
      "@odata.type": "microsoft.graph.accessPackageLocalizedText"
    }
  ]
}
```
