<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagelocalizedtext?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageLocalizedText resource type

Namespace: microsoft.graph

Represents a question in a specific language.

In entitlement management, this object is configured in the **localizedTexts** property of **accessPackageLocalizedContent**.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| languageCode | String | The language code that **text** is in. For example, "en-us". The language component follows 2-letter codes as defined in [ISO 639-1](https://www.iso.org/iso-639-language-codes.html), and the country component follows 2-letter codes as defined in [ISO 3166-1 alpha-2](https://www.iso.org/iso-3166-country-codes.html). Required. |
| text | String | The question in the specific language. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageLocalizedText",
  "text": "String",
  "languageCode": "String"
}
```
