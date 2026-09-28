<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions-xll-custom-functions?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionAlternateVersionsArray.hide.windowsExtensions.xllCustomFunctions object

Specifies the XLL-based add-ins custom function

Properties that reference this object type:

- [root.extensions.alternates.hide.windowsExtensions.xllCustomFunctions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30#xllCustomFunctions-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "fileNames": [
    "{string}"
  ]
}
```

```json
{
  "type": "object",
  "description": "Specifies the XLL-based add-ins custom function",
  "properties": {
    "fileNames": {
      "type": "array",
      "description": "Specifies the file names of the XLL-based add-ins custom function",
      "minItems": 1,
      "maxItems": 5,
      "items": {
        "type": "string",
        "minLength": 1,
        "maxLength": 64
      }
    }
  },
  "additionalProperties": false,
  "required": [
    "fileNames"
  ]
}
```

## Properties

#### fileNames

Specifies the file names of the XLL-based add-ins custom function

**Type**  
Array of string

**Required**  
✅

**Constraints**  
Minimum string length: 1. Maximum string length: 64. Minimum array items: 1. Maximum array items: 5.

**Supported values**
