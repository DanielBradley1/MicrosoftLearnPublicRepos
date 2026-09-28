<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswerchoice?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageAnswerChoice resource type

Namespace: microsoft.graph

Indicates an answer option for an [accessPackageMultipleChoiceQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagemultiplechoicequestion?view=graph-rest-1.0). Multiple accessPackageAnswerChoices can be added to an [accessPackageMultipleChoiceQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagemultiplechoicequestion?view=graph-rest-1.0).

In entitlement management, this subtype is used in the:

- **answers** property of [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0)
- **answers** property of [accessPackageAssignmentRequestCalloutData](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcalloutdata?view=graph-rest-1.0)
- **existingAnswers** property of [accessPackageAssignmentRequestRequirements](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestrequirements?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actualValue | String | The actual value of the selected choice. This is typically a string value which is understandable by applications. Required. |
| localizations | [accessPackageLocalizedText](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagelocalizedtext?view=graph-rest-1.0) collection | The text of the answer choice represented in a format for a specific locale. |
| text | String | The string to display for this answer; if an `Accept-Language` header is provided, and there is a matching localization in `localizations`, this string will be the matching localized string; otherwise, this string remains as the default non-localized string. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAnswerChoice",
  "actualValue": "String",
  "text": "String",
  "localizations": [
    {
      "@odata.type": "microsoft.graph.accessPackageLocalizedText"
    }
  ]
}
```
