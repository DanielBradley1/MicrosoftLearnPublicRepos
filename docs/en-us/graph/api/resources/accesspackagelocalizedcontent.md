<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagelocalizedcontent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageLocalizedContent resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A complex type used to represent a text in multiple localized forms. It includes a default text, which is used in any case where the requested localization isn't available.

In entitlement management, this object is configured in the following properties and relationships:

- **displayValue** property of [accessPackageAnswerChoice](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswerchoice?view=graph-rest-beta)
- **text** property of [accessPackageMultipleChoiceQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagemultiplechoicequestion?view=graph-rest-beta)
- **text** property of [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-beta)
- **text** property of [accessPackageTextInputQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagetextinputquestion?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultText | String | The fallback string, which is used when a requested localization isn't available. Required. |
| localizedTexts | [accessPackageLocalizedText](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagelocalizedtext?view=graph-rest-beta) collection | Content represented in a format for a specific locale. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageLocalizedContent",
  "defaultText": "String",
  "localizedTexts": [
    {
      "@odata.type": "microsoft.graph.accessPackageLocalizedText"
    }
  ]
}
```
