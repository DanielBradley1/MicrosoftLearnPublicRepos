<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info-additional-languages?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.localizationInfo.additionalLanguages object

An array of objects, each with the following properties to specify additional language translations.

Properties that reference this object type:

- [root.localizationInfo.additionalLanguages](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-localization-info?view=m365-app-1.30#additionalLanguages-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "languageTag": "{string}",
  "file": "{string}"
}
```

```json
{
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
```

## Properties

#### languageTag

The language tag of the strings in the provided file.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
The value must be a language tag, like `en-us`.

#### file

A relative file path to the .json file that contains the translated strings.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  


## Examples

```json
{
    "localizationInfo": {
        "additionalLanguages": [
            {
                "languageTag": "es",
                "file": "es.json"
            }
        ]
    }
}
```
