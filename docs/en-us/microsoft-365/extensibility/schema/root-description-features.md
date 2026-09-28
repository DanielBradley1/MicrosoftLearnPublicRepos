<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description-features?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.description.features object

Array of features sections describing what the app can do.

Properties that reference this object type:

- [root.description.features](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-description?view=m365-app-1.30#features-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "title": "{string}",
  "description": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "title": {
      "type": "string",
      "maxLength": 45,
      "description": "Title of the feature the app provides."
    },
    "description": {
      "type": "string",
      "maxLength": 120,
      "description": "Detailed description of the specific feature."
    }
  },
  "required": [
    "title",
    "description"
  ]
}
```

## Properties

#### title

Title of the feature the app provides.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 45.

**Supported values**  


#### description

Detailed description of the specific feature.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 120.

**Supported values**
