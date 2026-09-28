<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# enum object

Array of custom defined enum objects.

Properties that reference this object type:

- [root.extensions.runtimes.customFunctions.enums](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions?view=m365-app-1.30#enums-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "type": "number | string",
  "values": [
    {
      "name": "{string}",
      "numberValue": number | null,
      "stringValue": "{string}",
      "tooltip": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "id": {
      "type": "string",
      "description": "A unique ID for the enum.",
      "maxLength": 64,
      "minLength": 3,
      "pattern": "^[A-Za-z][A-Za-z0-9._]*$"
    },
    "type": {
      "type": "string",
      "description": "The type of the values in this enum.",
      "enum": [
        "number",
        "string"
      ]
    },
    "values": {
      "type": "array",
      "description": "Array that defines the constants for the enum.",
      "items": {
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
    }
  },
  "required": [
    "id",
    "type",
    "values"
  ],
  "additionalProperties": false
}
```

## Properties

#### id

A unique ID for the enum.

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 3. Maximum string length: 64.

**Supported values**  
The string value must start with a letter and can contain only letters, numbers, periods, and underscores.

#### type

The type of the values in this enum.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `number`, `string`.

#### values

Array that defines the constants for the enum.

**Type**  
Array of [values](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/enum-values?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**
