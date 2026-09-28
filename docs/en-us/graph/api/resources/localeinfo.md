<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/localeinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# localeInfo resource type

Namespace: microsoft.graph

Information about the locale, including the preferred language and country/region, of the signed-in user.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | string | A name representing the user's locale in natural language, for example, "English \(United States\)". |
| locale | string | A locale representation for the user, which includes the user's preferred language and country/region. For example, "en-us". The language component follows 2-letter codes as defined in [ISO 639-1](https://www.iso.org/iso/home/standards/language_codes.htm), and the country component follows 2-letter codes as defined in [ISO 3166-1 alpha-2](https://www.iso.org/iso/country_codes.htm). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "locale": "string",
  "displayName": "string"
}
```
