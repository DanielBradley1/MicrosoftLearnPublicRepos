<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.composeExtensions.commands object

The command object represents configuration info and metadata about a specific search or action command supported by the message extension. o learn more about message extension commands, see [Types of message extension commands](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/design/messaging-extension-design#types-of-message-extensions).

Properties that reference this object type:

- [root.composeExtensions.commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions?view=m365-app-1.30#commands-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "type": "query | action",
  "triggers": [
    "slash"
  ],
  "samplePrompts": [
    {
      "text": "{string}"
    }
  ],
  "apiResponseRenderingTemplateFile": "{string}",
  "context": [
    "compose | commandBox | message"
  ],
  "title": "{string}",
  "description": "{string}",
  "initialRun": {boolean},
  "fetchTask": {boolean},
  "parameters": [
    {
      "name": "{string}",
      "inputType": "text | textarea | number | date | time | toggle | choiceset",
      "isRequired": {boolean},
      "title": "{string}",
      "description": "{string}",
      "value": "{string}",
      "choices": [
        {
          choices object
        }
      ],
      "semanticDescription": "{string}"
    }
  ],
  "taskInfo": {
    "title": "{string}",
    "width": "{string}",
    "height": "{string}",
    "url": "{string}"
  },
  "semanticDescription": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "Id of the command.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "query",
        "action"
      ],
      "description": "Type of the command",
      "default": "query"
    },
    "triggers": {
      "type": "array",
      "maxItems": 1,
      "items": {
        "type": "string",
        "enum": [
          "slash"
        ]
      },
      "description": "Adding \u0022slash\u0022 to the array makes the command appear in the / slash commands list in group chat or channel. Note: \u0022mention\u0022 is not a valid value for composeExtension command triggers \u2014 it applies only to bots[].commandLists[]."
    },
    "samplePrompts": {
      "type": "array",
      "maxItems": 5,
      "minItems": 1,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "text": {
            "type": "string",
            "description": "This string will hold the sample prompt",
            "maxLength": 128
          }
        },
        "required": [
          "text"
        ]
      }
    },
    "apiResponseRenderingTemplateFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path for api response rendering template file. The schema of the file can be referred to in this link:\u0027https://developer.microsoft.com/json-schemas/teams/vDevPreview/MicrosoftTeams.ResponseRenderingTemplate.schema.json\u0027."
    },
    "context": {
      "type": "array",
      "maxItems": 3,
      "items": {
        "enum": [
          "compose",
          "commandBox",
          "message"
        ]
      },
      "description": "Context where the command would apply",
      "default": [
        "compose",
        "commandBox"
      ]
    },
    "title": {
      "type": "string",
      "description": "Title of the command.",
      "maxLength": 32
    },
    "description": {
      "type": "string",
      "description": "Description of the command.",
      "maxLength": 128
    },
    "initialRun": {
      "type": "boolean",
      "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
      "default": false
    },
    "fetchTask": {
      "type": "boolean",
      "description": "A boolean value that indicates if it should fetch task module dynamically",
      "default": false
    },
    "parameters": {
      "type": "array",
      "maxItems": 5,
      "minItems": 1,
      "items": {
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
    },
    "taskInfo": {
      "$ref": "#/definitions/taskInfo",
      "description": "Task module to be launched when fetch task set to false."
    },
    "semanticDescription": {
      "type": "string",
      "description": "semantic description of the command. This is typically meant for consumption by the large language model.",
      "maxLength": 5000
    }
  },
  "required": [
    "id",
    "title"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "type": "query | action",
  "triggers": [
    "slash"
  ],
  "samplePrompts": [
    {
      "text": "{string}"
    }
  ],
  "apiResponseRenderingTemplateFile": "{string}",
  "context": [
    "compose | commandBox | message"
  ],
  "title": "{string}",
  "description": "{string}",
  "initialRun": {boolean},
  "fetchTask": {boolean},
  "parameters": [
    {
      "name": "{string}",
      "inputType": "text | textarea | number | date | time | toggle | choiceset",
      "title": "{string}",
      "description": "{string}",
      "isRequired": {boolean},
      "value": "{string}",
      "choices": [
        {
          choices object
        }
      ],
      "semanticDescription": "{string}"
    }
  ],
  "taskInfo": {
    "title": "{string}",
    "width": "{string}",
    "height": "{string}",
    "url": "{string}"
  },
  "semanticDescription": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "Id of the command.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "query",
        "action"
      ],
      "description": "Type of the command",
      "default": "query"
    },
    "triggers": {
      "type": "array",
      "maxItems": 1,
      "items": {
        "type": "string",
        "enum": [
          "slash"
        ]
      },
      "description": "Adding \u0022slash\u0022 to the array makes the command appear in the / slash commands list in group chat or channel. Note: \u0022mention\u0022 is not a valid value for composeExtension command triggers \u2014 it applies only to bots[].commandLists[]."
    },
    "samplePrompts": {
      "type": "array",
      "maxItems": 5,
      "minItems": 1,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "text": {
            "type": "string",
            "description": "This string will hold the sample prompt",
            "maxLength": 128
          }
        },
        "required": [
          "text"
        ]
      }
    },
    "apiResponseRenderingTemplateFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path for api response rendering template file."
    },
    "context": {
      "type": "array",
      "maxItems": 3,
      "items": {
        "enum": [
          "compose",
          "commandBox",
          "message"
        ]
      },
      "description": "Context where the command would apply",
      "default": [
        "compose",
        "commandBox"
      ]
    },
    "title": {
      "type": "string",
      "description": "Title of the command.",
      "maxLength": 32
    },
    "description": {
      "type": "string",
      "description": "Description of the command.",
      "maxLength": 128
    },
    "initialRun": {
      "type": "boolean",
      "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
      "default": false
    },
    "fetchTask": {
      "type": "boolean",
      "description": "A boolean value that indicates if it should fetch task module dynamically",
      "default": false
    },
    "parameters": {
      "type": "array",
      "maxItems": 5,
      "minItems": 1,
      "items": {
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
    },
    "taskInfo": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "title": {
          "type": "string",
          "description": "Initial dialog title",
          "maxLength": 64
        },
        "width": {
          "$ref": "#/definitions/taskInfoDimension",
          "description": "Dialog width - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027"
        },
        "height": {
          "$ref": "#/definitions/taskInfoDimension",
          "description": "Dialog height - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027"
        },
        "url": {
          "$ref": "#/definitions/anyHttpUrl",
          "description": "Initial webview URL"
        }
      }
    },
    "semanticDescription": {
      "type": "string",
      "description": "Semantic description for the command.",
      "maxLength": 5000
    }
  },
  "required": [
    "id",
    "title"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "id": "{string}",
  "type": "query | action",
  "samplePrompts": [
    {
      "text": "{string}"
    }
  ],
  "apiResponseRenderingTemplateFile": "{string}",
  "context": [
    "compose | commandBox | message"
  ],
  "title": "{string}",
  "description": "{string}",
  "initialRun": {boolean},
  "fetchTask": {boolean},
  "parameters": [
    {
      "name": "{string}",
      "inputType": "text | textarea | number | date | time | toggle | choiceset",
      "title": "{string}",
      "description": "{string}",
      "isRequired": {boolean},
      "value": "{string}",
      "choices": [
        {
          choices object
        }
      ],
      "semanticDescription": "{string}"
    }
  ],
  "taskInfo": {
    "title": "{string}",
    "width": "{string}",
    "height": "{string}",
    "url": "{string}"
  },
  "semanticDescription": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "Id of the command.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "query",
        "action"
      ],
      "description": "Type of the command",
      "default": "query"
    },
    "samplePrompts": {
      "type": "array",
      "maxItems": 5,
      "minItems": 1,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "text": {
            "type": "string",
            "description": "This string will hold the sample prompt",
            "maxLength": 128
          }
        },
        "required": [
          "text"
        ]
      }
    },
    "apiResponseRenderingTemplateFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path for api response rendering template file."
    },
    "context": {
      "type": "array",
      "maxItems": 3,
      "items": {
        "enum": [
          "compose",
          "commandBox",
          "message"
        ]
      },
      "description": "Context where the command would apply",
      "default": [
        "compose",
        "commandBox"
      ]
    },
    "title": {
      "type": "string",
      "description": "Title of the command.",
      "maxLength": 32
    },
    "description": {
      "type": "string",
      "description": "Description of the command.",
      "maxLength": 128
    },
    "initialRun": {
      "type": "boolean",
      "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
      "default": false
    },
    "fetchTask": {
      "type": "boolean",
      "description": "A boolean value that indicates if it should fetch task module dynamically",
      "default": false
    },
    "parameters": {
      "type": "array",
      "maxItems": 5,
      "minItems": 1,
      "items": {
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
    },
    "taskInfo": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "title": {
          "type": "string",
          "description": "Initial dialog title",
          "maxLength": 64
        },
        "width": {
          "$ref": "#/definitions/taskInfoDimension",
          "description": "Dialog width - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027"
        },
        "height": {
          "$ref": "#/definitions/taskInfoDimension",
          "description": "Dialog height - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027"
        },
        "url": {
          "$ref": "#/definitions/anyHttpUrl",
          "description": "Initial webview URL"
        }
      }
    },
    "semanticDescription": {
      "type": "string",
      "description": "Semantic description for the command.",
      "maxLength": 5000
    }
  },
  "required": [
    "id",
    "title"
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "id": "{string}",
  "type": "query | action",
  "samplePrompts": [
    {
      "text": "{string}"
    }
  ],
  "apiResponseRenderingTemplateFile": "{string}",
  "context": [
    "compose | commandBox | message"
  ],
  "title": "{string}",
  "description": "{string}",
  "initialRun": {boolean},
  "fetchTask": {boolean},
  "parameters": [
    {
      "name": "{string}",
      "inputType": "text | textarea | number | date | time | toggle | choiceset",
      "title": "{string}",
      "description": "{string}",
      "isRequired": {boolean},
      "value": "{string}",
      "choices": [
        {
          choices object
        }
      ],
      "semanticDescription": "{string}"
    }
  ],
  "taskInfo": {
    "title": "{string}",
    "width": "{string}",
    "height": "{string}",
    "url": "{string}"
  },
  "semanticDescription": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "Id of the command.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "query",
        "action"
      ],
      "description": "Type of the command",
      "default": "query"
    },
    "samplePrompts": {
      "type": "array",
      "maxItems": 5,
      "minItems": 1,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "text": {
            "type": "string",
            "description": "This string will hold the sample prompt",
            "maxLength": 128
          }
        },
        "required": [
          "text"
        ]
      }
    },
    "apiResponseRenderingTemplateFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path for api response rendering template file."
    },
    "context": {
      "type": "array",
      "maxItems": 3,
      "items": {
        "enum": [
          "compose",
          "commandBox",
          "message"
        ]
      },
      "description": "Context where the command would apply",
      "default": [
        "compose",
        "commandBox"
      ]
    },
    "title": {
      "type": "string",
      "description": "Title of the command.",
      "maxLength": 32
    },
    "description": {
      "type": "string",
      "description": "Description of the command.",
      "maxLength": 128
    },
    "initialRun": {
      "type": "boolean",
      "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
      "default": false
    },
    "fetchTask": {
      "type": "boolean",
      "description": "A boolean value that indicates if it should fetch task module dynamically",
      "default": false
    },
    "parameters": {
      "type": "array",
      "maxItems": 5,
      "minItems": 1,
      "items": {
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
    },
    "taskInfo": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "title": {
          "type": "string",
          "description": "Initial dialog title",
          "maxLength": 64
        },
        "width": {
          "$ref": "#/definitions/taskInfoDimension",
          "description": "Dialog width - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027"
        },
        "height": {
          "$ref": "#/definitions/taskInfoDimension",
          "description": "Dialog height - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027"
        },
        "url": {
          "$ref": "#/definitions/httpsUrl",
          "description": "Initial webview URL"
        }
      }
    },
    "semanticDescription": {
      "type": "string",
      "description": "Semantic description for the command.",
      "maxLength": 5000
    }
  },
  "required": [
    "id",
    "title"
  ]
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "id": "{string}",
  "type": "query | action",
  "samplePrompts": [
    {
      "text": "{string}"
    }
  ],
  "apiResponseRenderingTemplateFile": "{string}",
  "context": [
    "compose | commandBox | message"
  ],
  "title": "{string}",
  "description": "{string}",
  "initialRun": {boolean},
  "fetchTask": {boolean},
  "semanticDescription": "{string}",
  "parameters": [
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
          choices object
        }
      ]
    }
  ],
  "taskInfo": {
    "title": "{string}",
    "width": "{string}",
    "height": "{string}",
    "url": "{string}"
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "id": {
      "type": "string",
      "description": "Id of the command.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "query",
        "action"
      ],
      "description": "Type of the command",
      "default": "query"
    },
    "samplePrompts": {
      "type": "array",
      "maxItems": 5,
      "minItems": 1,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "text": {
            "type": "string",
            "description": "This string will hold the sample prompt",
            "maxLength": 128
          }
        },
        "required": [
          "text"
        ]
      }
    },
    "apiResponseRenderingTemplateFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path for api response rendering template file."
    },
    "context": {
      "type": "array",
      "maxItems": 3,
      "items": {
        "enum": [
          "compose",
          "commandBox",
          "message"
        ]
      },
      "description": "Context where the command would apply",
      "default": [
        "compose",
        "commandBox"
      ]
    },
    "title": {
      "type": "string",
      "description": "Title of the command.",
      "maxLength": 32
    },
    "description": {
      "type": "string",
      "description": "Description of the command.",
      "maxLength": 128
    },
    "initialRun": {
      "type": "boolean",
      "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
      "default": false
    },
    "fetchTask": {
      "type": "boolean",
      "description": "A boolean value that indicates if it should fetch task module dynamically",
      "default": false
    },
    "semanticDescription": {
      "type": "string",
      "description": "Semantic description for the command.",
      "maxLength": 5000
    },
    "parameters": {
      "type": "array",
      "maxItems": 5,
      "minItems": 1,
      "items": {
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
    },
    "taskInfo": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "title": {
          "type": "string",
          "description": "Initial dialog title",
          "maxLength": 64
        },
        "width": {
          "$ref": "#/definitions/taskInfoDimension",
          "description": "Dialog width - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027"
        },
        "height": {
          "$ref": "#/definitions/taskInfoDimension",
          "description": "Dialog height - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027"
        },
        "url": {
          "$ref": "#/definitions/httpsUrl",
          "description": "Initial webview URL"
        }
      }
    }
  },
  "required": [
    "id",
    "title"
  ]
}
```

## Properties

#### id

Id of the command.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### type

Type of the command. One of `query` or `action`.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `query`, `action`.

#### triggers

Adding "slash" to the array makes the command appear in the / slash commands list in group chat or channel. Note: "mention" is not a valid value for composeExtension command triggers — it applies only to bots\[\].commandLists\[\].

**Type**  
Array of string

**Required**  
—

**Constraints**  
Maximum array items: 1.

**Supported values**  
Allowed values: `slash`.

#### samplePrompts

Property used by Microsoft 365 Copilot to display prompts supported by the agent to the user. For Microsoft 365 Copilot scenarios, this property is required in order to pass app validation for store submission.

**Type**  
Array of [samplePrompts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-sample-prompts?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 5.

**Supported values**  


#### apiResponseRenderingTemplateFile

A relative file path for api [response rendering template](https://developer.microsoft.com/json-schemas/teams/vDevPreview/MicrosoftTeams.ResponseRenderingTemplate.schema.json) file used to format the JSON response from developer’s API to Adaptive Card response.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### context

Defines where the message extension can be invoked from. Any combination of `compose`, `commandBox`, `message`.

**Type**  
Array of enum

**Required**  
—

**Constraints**  
Maximum array items: 3.

**Supported values**  
Allowed values: `compose`, `commandBox`, `message`.

#### title

The user-friendly command name.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### description

The description that appears to users to indicate the purpose of this command.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### initialRun

A boolean value that indicates if the command should be run once initially with no parameter.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### fetchTask

A boolean value that indicates if it should fetch the dialog \(referred as task module in TeamsJS v1.x\) dynamically.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### parameters

The list of parameters the command takes.

**Type**  
Array of [parameters](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-parameters?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 5.

**Supported values**  


#### taskInfo

Specifies the dialog to preload when using a message extension command.

**Type**  
[taskInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/task-info?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### semanticDescription

Semantic description of the command. This is typically meant for consumption by the large language model\(LLM\).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 5000.

**Supported values**  


## Examples

```json
{
    "commands": [
        {
            "id": "exampleCmd1",
            "title": "Example Command",
            "type": "query",
            "context": [
                "compose",
                "commandBox"
            ],
            "description": "Command Description; e.g., Search on the web",
            "initialRun": true,
            "fetchTask": false,
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
```
