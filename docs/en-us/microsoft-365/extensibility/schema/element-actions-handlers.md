<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-04-06 -->

# elementActions.handlers object

Defines an array of one or more handler objects for the Action. Each Action must have at least one handler. If an app has more than one handler defined, the host application will decide which action to display based on which experience is supported.

Properties that reference this object type:

- [root.actions.handlers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions?view=m365-app-prev#handlers-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "type": "openURL | openPage | openDialog | openTaskpane | invokeAPI | invokeBot",
  "supportedObjects": {
    "file": {
      file object
    },
    "folder": object | null
  },
  "supportsMultiSelect": {boolean},
  "pageInfo": {
    "pageId": "{string}",
    "subpageId": "{string}"
  },
  "dialogInfo": {
    "dialogType": "url | adaptiveCard",
    "url": "{string}",
    "width": "{string}",
    "height": "{string}",
    "parameters": [
      {
        parameters object
      }
    ],
    "title": "{string}"
  },
  "url": "{string}",
  "botInfo": {
    "botId": "{string}",
    "fetchTask": {boolean}
  }
}
```

```json
{
  "type": "object",
  "required": [
    "type"
  ],
  "properties": {
    "type": {
      "type": "string",
      "enum": [
        "openURL",
        "openPage",
        "openDialog",
        "openTaskpane",
        "invokeAPI",
        "invokeBot"
      ],
      "description": "Required both for File Handlers and Content Actions."
    },
    "supportedObjects": {
      "type": "object",
      "properties": {
        "file": {
          "type": "object",
          "additionalProperties": false,
          "properties": {
            "extensions": {
              "type": "array",
              "items": {
                "type": "string",
                "description": "File extension, e.g. .pdf, .docx."
              }
            }
          }
        },
        "folder": {
          "type": [
            "object",
            "null"
          ],
          "description": "A null value indicates that the file handler is not available when a folder is selected. An object with no parameters indicates that the file handler is available when a folder is selected or when no files are selected."
        }
      }
    },
    "supportsMultiSelect": {
      "type": "boolean",
      "description": "If true, multiple files can be selected and the action will still be displayed. If false or missing, the action is only displayed when a single item is selected. "
    },
    "pageInfo": {
      "type": "object",
      "required": [
        "pageId"
      ],
      "properties": {
        "pageId": {
          "type": "string",
          "description": "Used to navigate to the page in MetaOS app."
        },
        "subpageId": {
          "type": "string",
          "description": "Used to navigate to the subpage in MetaOS app."
        }
      }
    },
    "dialogInfo": {
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
    },
    "url": {
      "type": "string",
      "description": "Url for handler type openURL, invokeAPI, openTaskpane, and others."
    },
    "botInfo": {
      "type": "object",
      "required": [
        "botId"
      ],
      "properties": {
        "botId": {
          "type": "string",
          "description": "Bot ID."
        },
        "fetchTask": {
          "type": "boolean",
          "description": "Fetch task from bot."
        }
      }
    }
  }
}
```

## Properties

#### type

Specifies the handler type for the Action. Required both for File Handlers and Content Actions.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `openURL`, `openPage`, `openDialog`, `openTaskpane`, `invokeAPI`, `invokeBot`.

#### supportedObjects

The supported object types that can trigger this Action.

**Type**  
[supportedObjects](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-supported-objects?view=m365-app-prev)

**Required**  
—

**Constraints**  


**Supported values**  


#### supportsMultiSelect

If true, multiple files can be selected and the action will still be displayed. If false or missing, the action is only displayed when a single item is selected.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  


#### pageInfo

Object containing metadata of the page to open. Required if the handler type is `openPage`.

**Type**  
[pageInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-page-info?view=m365-app-prev)

**Required**  
—

**Constraints**  


**Supported values**  


#### dialogInfo

**Type**  
[dialogInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-dialog-info?view=m365-app-prev)

**Required**  
—

**Constraints**  


**Supported values**  


#### url

Url for handler type openURL, invokeAPI, openTaskpane, and others.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  


#### botInfo

**Type**  
[botInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers-bot-info?view=m365-app-prev)

**Required**  
—

**Constraints**  


**Supported values**  


## Examples

```json
{
  "handlers": [
    {
      "type": "openPage",
      "supportedObjects": {
        "file": {
          "extensions": [
            "doc",
            "pdf"
          ]
        }
      },
      "pageInfo": {
        "pageId": "newTaskPage",
        "subPageId": ""
      }
    }
  ]
}
```
