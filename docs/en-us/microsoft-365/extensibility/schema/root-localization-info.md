<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.localizationInfo object

Allows the specification of a default language, and pointers to additional language files. See [localization](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/apps-localization).

Properties that reference this object type:

- [root.localizationInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#localizationInfo-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "defaultLanguageTag": "{string}",
  "defaultLanguageFile": "{string}",
  "additionalLanguages": [
    {
      "languageTag": "{string}",
      "file": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "defaultLanguageTag": {
      "$ref": "#/definitions/languageTag",
      "description": "The language tag of the strings in this top level manifest file.",
      "default": "en-us"
    },
    "defaultLanguageFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to a the .json file containing strings in the default language."
    },
    "additionalLanguages": {
      "type": "array",
      "uniqueItems": true,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "languageTag": {
            "$ref": "#/definitions/languageTag",
            "description": "The language tag of the strings in the provided file."
          },
          "file": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path to a the .json file containing the translated strings."
          }
        },
        "required": [
          "languageTag",
          "file"
        ]
      }
    }
  },
  "required": [
    "defaultLanguageTag"
  ]
}
```

## Properties

#### defaultLanguageTag

The language tag for the strings in this top-level app manifest file.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
The value must be a language tag, like `en-us`.

#### defaultLanguageFile

A relative file path to the .json file that contains the strings. If unspecified, strings are taken directly from the app manifest file. A default language file is required for [agents that support multiple languages](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/localize-agents).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### additionalLanguages

An array of objects, each with properties to specify additional language translations.

**Type**  
Array of [additionalLanguages](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info-additional-languages?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Array items must be unique.

**Supported values**  


## Examples

```json
{
    "localizationInfo": {
        "defaultLanguageTag": "en",
        "defaultLanguageFile": "en.json",
        "additionalLanguages": [
            {
                "languageTag": "es",
                "file": "es.json"
            }
        ]
    }
}
```
