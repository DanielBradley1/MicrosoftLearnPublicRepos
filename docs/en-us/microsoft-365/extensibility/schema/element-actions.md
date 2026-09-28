<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# elementActions object

Array of objects each representing a custom file handling action your app can perform when invoked by the user from the context menu of a file in Microsoft 365 \(Office\) app. See [Actions in Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/actions-in-m365) for further information.

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "intent": "create | addTo | open | preview | share | sign | custom",
  "displayName": "{string}",
  "description": "{string}",
  "icons": [
    {
      "size": {number},
      "url": "{string}"
    }
  ],
  "handlers": [
    {
      "type": "openURL | openPage | openDialog | openTaskpane | invokeAPI | invokeBot",
      "supportedObjects": {
        supportedObjects object
      },
      "supportsMultiSelect": {boolean},
      "pageInfo": {
        pageInfo object
      },
      "dialogInfo": {
        dialogInfo object
      },
      "url": "{string}",
      "botInfo": {
        botInfo object
      }
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "required": [
    "id",
    "intent",
    "displayName",
    "description",
    "handlers"
  ],
  "properties": {
    "id": {
      "type": "string",
      "minLength": 1,
      "description": "A unique identifier string in the default locale that is used to catalog actions."
    },
    "intent": {
      "description": "An enum string that describes the intent of the action.",
      "type": "string",
      "enum": [
        "create",
        "addTo",
        "open",
        "preview",
        "share",
        "sign",
        "custom"
      ]
    },
    "displayName": {
      "type": "string",
      "minLength": 1,
      "description": "A display name for the action."
    },
    "description": {
      "type": "string",
      "minLength": 1,
      "description": "A display string in the default locale to represent the action."
    },
    "icons": {
      "type": "array",
      "description": "Object containing URLs to icon images for this action intent.",
      "items": {
        "type": "object",
        "properties": {
          "size": {
            "type": "number",
            "description": "Icon size in pixels."
          },
          "url": {
            "$ref": "#/definitions/anyHttpUrl",
            "description": "URL for the icon."
          }
        },
        "additionalProperties": false,
        "required": [
          "size",
          "url"
        ]
      }
    },
    "handlers": {
      "type": "array",
      "minItems": 1,
      "description": "Defining how actions can be handled. If an app has more than 1 handler, only one experience will show up at one entry point. The hub will decide which action to show up based on which experience is supported.",
      "items": {
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
    }
  }
}
```

## Properties

#### id

An identifier string in the default locale that is used to catalog actions. Must be unique across all actions for this app. For example, `openDocInContoso`.

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 1.

**Supported values**  


#### intent

An enum string that describes the intent of the action.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `create`, `addTo`, `open`, `preview`, `share`, `sign`, `custom`.

#### displayName

A display name for the action. Capitalize first letter and brand name. For example, *Add to suppliers*, *Open in Contoso*, or *Request signatures*.

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 1.

**Supported values**  


#### description

A display string in the default locale that represents the action.

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 1.

**Supported values**  


#### icons

Object containing URLs to icon images for this action intent.

**Type**  
Array of [icons](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-icons?view=m365-app-prev)

**Required**  
—

**Constraints**  


**Supported values**  


#### handlers

An array of handler objects defining how Actions are managed. In the current public preview, adds a single handler for each action.

**Type**  
Array of [handlers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-actions-handlers?view=m365-app-prev)

**Required**  
✅

**Constraints**  
Minimum array items: 1.

**Supported values**  


## Examples

```json
{
"actions": [
    {
      "id": "addTodoTask",
      "displayName": "Add ToDo task",
      "intent": "addTo",
      "description": "Add this file with a short note to my to do list",
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
    },
  ]
}
```
