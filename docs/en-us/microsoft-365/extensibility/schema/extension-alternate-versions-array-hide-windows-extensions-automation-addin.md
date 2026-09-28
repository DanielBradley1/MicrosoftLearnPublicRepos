<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions-automation-addin?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionAlternateVersionsArray.hide.windowsExtensions.automationAddin object

Specifies the equivalent automation add-ins

Properties that reference this object type:

- [root.extensions.alternates.hide.windowsExtensions.automationAddin](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-alternate-versions-array-hide-windows-extensions?view=m365-app-1.30#automationAddin-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "progIds": [
    "{string}"
  ]
}
```

```json
{
  "type": "object",
  "description": "Specifies the equivalent automation add-ins",
  "properties": {
    "progIds": {
      "type": "array",
      "description": "Specifies the program Ids of the equivalent automation add-ins",
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
    "progIds"
  ]
}
```

## Properties

#### progIds

Specifies the program Ids of the equivalent automation add-ins

**Type**  
Array of string

**Required**  
✅

**Constraints**  
Minimum string length: 1. Maximum string length: 64. Minimum array items: 1. Maximum array items: 5.

**Supported values**
