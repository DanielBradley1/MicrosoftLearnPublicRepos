<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-parameters?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.composeExtensions.commands.parameters object

The list of parameters the command takes.

Properties that reference this object type:

- [root.composeExtensions.commands.parameters](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#parameters-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "name": "{string}",
  "inputType": "text | textarea | number | date | time | toggle | choiceset",
  "isRequired": {boolean},
  "title": "{string}",
  "description": "{string}",
  "value": "{string}",
  "choices": [
    {
      "title": "{string}",
      "value": "{string}"
    }
  ],
  "semanticDescription": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "name": {
      "type": "string",
      "description": "Name of the parameter.",
      "maxLength": 64
    },
    "inputType": {
      "type": "string",
      "enum": [
        "text",
        "textarea",
        "number",
        "date",
        "time",
        "toggle",
        "choiceset"
      ],
      "description": "Type of the parameter",
      "default": "text"
    },
    "isRequired": {
      "type": "boolean",
      "description": "Indicates whether this parameter is required or not. By default, it is not."
    },
    "title": {
      "type": "string",
      "description": "Title of the parameter.",
      "maxLength": 32
    },
    "description": {
      "type": "string",
      "description": "Description of the parameter.",
      "maxLength": 128
    },
    "value": {
      "type": "string",
      "description": "Initial value for the parameter",
      "maxLength": 512
    },
    "choices": {
      "type": "array",
      "maxItems": 10,
      "description": "The choice options for the parameter",
      "items": {
        "type": "object",
        "properties": {
          "title": {
            "type": "string",
            "description": "Title of the choice",
            "maxLength": 128
          },
          "value": {
            "type": "string",
            "description": "Value of the choice",
            "maxLength": 512
          }
        },
        "additionalProperties": false,
        "required": [
          "title",
          "value"
        ]
      }
    },
    "semanticDescription": {
      "type": "string",
      "description": "semantic description of the parameter. This is typically meant for consumption by the large language model.",
      "maxLength": 2000
    }
  },
  "required": [
    "name",
    "title"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "name": "{string}",
  "inputType": "text | textarea | number | date | time | toggle | choiceset",
  "title": "{string}",
  "description": "{string}",
  "isRequired": {boolean},
  "value": "{string}",
  "choices": [
    {
      "title": "{string}",
      "value": "{string}"
    }
  ],
  "semanticDescription": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "name": {
      "type": "string",
      "description": "Name of the parameter.",
      "maxLength": 64
    },
    "inputType": {
      "type": "string",
      "enum": [
        "text",
        "textarea",
        "number",
        "date",
        "time",
        "toggle",
        "choiceset"
      ],
      "description": "Type of the parameter",
      "default": "text"
    },
    "title": {
      "type": "string",
      "description": "Title of the parameter.",
      "maxLength": 32
    },
    "description": {
      "type": "string",
      "description": "Description of the parameter.",
      "maxLength": 128
    },
    "isRequired": {
      "type": "boolean",
      "description": "The value indicates if this parameter is a required field.",
      "default": false
    },
    "value": {
      "type": "string",
      "description": "Initial value for the parameter",
      "maxLength": 512
    },
    "choices": {
      "type": "array",
      "maxItems": 10,
      "description": "The choice options for the parameter",
      "items": {
        "type": "object",
        "properties": {
          "title": {
            "type": "string",
            "description": "Title of the choice",
            "maxLength": 128
          },
          "value": {
            "type": "string",
            "description": "Value of the choice",
            "maxLength": 512
          }
        },
        "additionalProperties": false,
        "required": [
          "title",
          "value"
        ]
      }
    },
    "semanticDescription": {
      "type": "string",
      "description": "Semantic description for the parameter.",
      "maxLength": 2000
    }
  },
  "required": [
    "name",
    "title"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "name": "{string}",
  "inputType": "text | textarea | number | date | time | toggle | choiceset",
  "title": "{string}",
  "description": "{string}",
  "value": "{string}",
  "isRequired": {boolean},
  "semanticDescription": "{string}",
  "choices": [
    {
      "title": "{string}",
      "value": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "name": {
      "type": "string",
      "description": "Name of the parameter.",
      "maxLength": 64
    },
    "inputType": {
      "type": "string",
      "enum": [
        "text",
        "textarea",
        "number",
        "date",
        "time",
        "toggle",
        "choiceset"
      ],
      "description": "Type of the parameter",
      "default": "text"
    },
    "title": {
      "type": "string",
      "description": "Title of the parameter.",
      "maxLength": 32
    },
    "description": {
      "type": "string",
      "description": "Description of the parameter.",
      "maxLength": 128
    },
    "value": {
      "type": "string",
      "description": "Initial value for the parameter",
      "maxLength": 512
    },
    "isRequired": {
      "type": "boolean",
      "description": "The value indicates if this parameter is a required field.",
      "default": false
    },
    "semanticDescription": {
      "type": "string",
      "description": "Semantic description for the parameter.",
      "maxLength": 2000
    },
    "choices": {
      "type": "array",
      "maxItems": 10,
      "description": "The choice options for the parameter",
      "items": {
        "type": "object",
        "properties": {
          "title": {
            "type": "string",
            "description": "Title of the choice",
            "maxLength": 128
          },
          "value": {
            "type": "string",
            "description": "Value of the choice",
            "maxLength": 512
          }
        },
        "additionalProperties": false,
        "required": [
          "title",
          "value"
        ]
      }
    }
  },
  "required": [
    "name",
    "title"
  ]
}
```

## Properties

#### name

The name of the parameter as it appears in the client. This is included in the user request.  
For Api-based message extension, The name must map to the `parameters.name` in the OpenAPI Description. If you're referencing a property in the request body schema, then the name must map to `properties.name` or query parameters.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### inputType

Defines the type of control displayed on a dialog for `fetchTask: false`.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`.

#### isRequired

Indicates whether this parameter is required or not. By default, it is not.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  


#### isRequired

Indicates whether this parameter is required or not. By default, it is not.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### title

User-friendly title for the parameter.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### description

User-friendly description of parameter’s purpose.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### value

Initial value for the parameter.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 512.

**Supported values**  


#### choices

The choice options for the parameter. Use only when `parameters.inputType` is `choiceset`.

**Type**  
Array of [choices](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-parameters-choices?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 10.

**Supported values**  


#### semanticDescription

Semantic description of the parameter. This is typically meant for consumption by the large language model \(LLM\).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2000.

**Supported values**  


## Examples

```json
{
"composeExtensions": [
        {
            "commands": [
                {
                    "parameters": [
                        {
                            "name": "keyword",
                            "title": "Search keywords",
                            "inputType": "choiceset",
                            "description": "Enter the keywords to search for",
                            "value": "Initial value for the parameter",
                            "choices": [
                                {
                                    "title": "Title of the choice",
                                    "value": "Value of the choice"
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}
```
