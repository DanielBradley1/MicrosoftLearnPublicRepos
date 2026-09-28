<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-dialog-info?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# elementActions.handlers.dialogInfo object

Properties that reference this object type:

- [root.actions.handlers.dialogInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers?view=m365-app-prev#dialogInfo-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "dialogType": "url | adaptiveCard",
  "url": "{string}",
  "width": "{string}",
  "height": "{string}",
  "parameters": [
    {
      "name": "{string}",
      "title": "{string}",
      "description": "{string}",
      "inputType": "{string}"
    }
  ],
  "title": "{string}"
}
```

```json
{
  "type": "object",
  "required": [
    "dialogType",
    "width",
    "height"
  ],
  "properties": {
    "dialogType": {
      "type": "string",
      "description": "Dialog type, defines how the developer build the dialog.",
      "enum": [
        "url",
        "adaptiveCard"
      ]
    },
    "url": {
      "type": "string",
      "description": "Required for html based dialog."
    },
    "width": {
      "description": "Dialog width - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027.",
      "$ref": "#/definitions/taskInfoDimension"
    },
    "height": {
      "description": "Dialog height - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027.",
      "$ref": "#/definitions/taskInfoDimension"
    },
    "parameters": {
      "type": "array",
      "minItems": 1,
      "description": "Array of parameter object, each contains: name, title, description, inputType.",
      "items": {
        "type": "object",
        "required": [
          "name",
          "title",
          "description",
          "inputType"
        ],
        "properties": {
          "name": {
            "type": "string",
            "description": "Parameter name."
          },
          "title": {
            "type": "string",
            "description": "Parameter title."
          },
          "description": {
            "type": "string",
            "description": "Parameter description."
          },
          "inputType": {
            "type": "string",
            "description": "Parameter input type."
          }
        }
      }
    },
    "title": {
      "type": "string",
      "description": "Dialog title."
    }
  }
}
```

## Properties

#### dialogType

Dialog type, defines how the developer build the dialog.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `url`, `adaptiveCard`.

#### url

Required for html based dialog.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  


#### width

Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 16.

**Supported values**  
The string value must be a number or `Large`, `Medium`, `Small`.

#### height

Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 16.

**Supported values**  
The string value must be a number or `Large`, `Medium`, `Small`.

#### parameters

Array of parameter object, each contains: name, title, description, inputType.

**Type**  
Array of [parameters](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-dialog-info-parameters?view=m365-app-prev)

**Required**  
—

**Constraints**  
Minimum array items: 1.

**Supported values**  


#### title

Dialog title.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**
