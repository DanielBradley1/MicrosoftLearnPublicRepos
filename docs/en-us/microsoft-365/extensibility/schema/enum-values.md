<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum-values?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# enum.values object

Array that defines the constants for the enum.

Properties that reference this object type:

- [root.extensions.runtimes.customFunctions.enums.values](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30#values-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "name": "{string}",
  "numberValue": number | null,
  "stringValue": "{string}",
  "tooltip": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "description": "A brief description of the constant.",
      "maxLength": 256
    },
    "numberValue": {
      "type": [
        "number",
        "null"
      ],
      "description": "When enum type is number, the actual number value of the constant."
    },
    "stringValue": {
      "type": "string",
      "description": "When enum type is string, the actual string value of the constant."
    },
    "tooltip": {
      "type": "string",
      "description": "Additional information about the constant, intended to provide more context or details.",
      "maxLength": 256
    }
  },
  "additionalProperties": false,
  "required": [
    "name"
  ]
}
```

## Properties

#### name

A brief description of the constant.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 256.

**Supported values**  


#### numberValue

When enum type is number, the actual number value of the constant.

**Type**  
number \| null

**Required**  
—

**Constraints**  


**Supported values**  


#### stringValue

When enum type is string, the actual string value of the constant.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  


#### tooltip

Additional information about the constant, intended to provide more context or details.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 256.

**Supported values**
