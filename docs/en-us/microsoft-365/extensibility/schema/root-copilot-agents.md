<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.copilotAgents object

Defines one or more agents to Microsoft 365 Copilot, selectable as **Agents** from the Microsoft 365 Copilot navigation panel. [Declarative agents](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent) are customizations of Microsoft 365 Copilot that run on the same orchestrator and foundation models. [Custom engine agents](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-custom-engine-agent) use custom AI language models and orchestration.

Note

Custom engine agents support in Microsoft 365 Copilot is currently in public preview.

Properties that reference this object type:

- [root.copilotAgents](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#copilotAgents-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "declarativeAgents": [
    {
      "id": "{string}",
      "file": "{string}"
    }
  ],
  "customEngineAgents": [
    {
      "id": "{string}",
      "type": "bot",
      "disclaimer": {
        disclaimer object
      },
      "functionsAs": "agentOnly | agenticUserOnly",
      "agenticUserTemplateId": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "declarativeAgents": {
      "type": "array",
      "description": "An array of declarative agent elements references. Currently, only one declarative agent per application is supported.",
      "items": {
        "$ref": "#/definitions/declarativeAgentRef"
      },
      "minItems": 1,
      "maxItems": 1
    },
    "customEngineAgents": {
      "type": "array",
      "description": "An array of Custom Engine Agents. Currently only one Custom Engine Agent per application is supported.",
      "items": {
        "type": "object",
        "properties": {
          "id": {
            "$ref": "#/definitions/guid",
            "description": "The id of the Custom Engine Agent. If it is of type bot, the id must match the id specified in a bot in the bots node and the referenced bot must have personal scope. The app short name and short description must also be defined."
          },
          "type": {
            "type": "string",
            "enum": [
              "bot"
            ],
            "description": "The type of the Custom Engine Agent. Currently only type bot is supported."
          },
          "disclaimer": {
            "type": "object",
            "properties": {
              "text": {
                "type": "string",
                "description": "The message shown to users before they interact with this application. ",
                "maxLength": 500
              }
            },
            "required": [
              "text"
            ]
          },
          "functionsAs": {
            "type": "string",
            "enum": [
              "agentOnly",
              "agenticUserOnly"
            ],
            "default": "agentOnly",
            "description": "Possible values: \u0027agenticUserOnly\u0027, \u0027agentOnly\u0027. \u0027agenticUserOnly\u0027 means the customEngineAgent must be hired and cannot be installed as a regular agent. \u0027agentOnly\u0027 means it supports being installed as a regular agent only (default)."
          },
          "agenticUserTemplateId": {
            "type": "string",
            "description": "Unique identifier for the agentic user template. This id must match the id specified in an agentic user template in the agenticUserTemplates node"
          }
        },
        "required": [
          "id",
          "type"
        ],
        "additionalProperties": false
      },
      "minItems": 1,
      "maxItems": 1
    }
  },
  "additionalProperties": false,
  "oneOf": [
    {
      "required": [
        "declarativeAgents"
      ]
    },
    {
      "required": [
        "customEngineAgents"
      ]
    }
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "declarativeAgents": [
    {
      "id": "{string}",
      "file": "{string}"
    }
  ],
  "customEngineAgents": [
    {
      "id": "{string}",
      "type": "bot",
      "disclaimer": {
        disclaimer object
      }
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "declarativeAgents": {
      "type": "array",
      "description": "An array of declarative agent elements references. Currently, only one declarative agent per application is supported.",
      "items": {
        "$ref": "#/definitions/declarativeAgentRef"
      },
      "minItems": 1,
      "maxItems": 1
    },
    "customEngineAgents": {
      "type": "array",
      "description": "An array of Custom Engine Agents. Currently only one Custom Engine Agent per application is supported. Support is currently in public preview.",
      "items": {
        "type": "object",
        "properties": {
          "id": {
            "$ref": "#/definitions/guid",
            "description": "The id of the Custom Engine Agent. If it is of type bot, the id must match the id specified in a bot in the bots node and the referenced bot must have personal scope. The app short name and short description must also be defined."
          },
          "type": {
            "type": "string",
            "enum": [
              "bot"
            ],
            "description": "The type of the Custom Engine Agent. Currently only type bot is supported."
          },
          "disclaimer": {
            "type": "object",
            "properties": {
              "text": {
                "type": "string",
                "description": "The message shown to users before they interact with this application. ",
                "maxLength": 500
              }
            },
            "required": [
              "text"
            ]
          }
        },
        "required": [
          "id",
          "type"
        ],
        "additionalProperties": false
      },
      "minItems": 1,
      "maxItems": 1
    }
  },
  "additionalProperties": false,
  "anyOf": []
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "declarativeAgents": [
    {
      "id": "{string}",
      "file": "{string}"
    }
  ],
  "customEngineAgents": [
    {
      "id": "{string}",
      "type": "bot",
      "disclaimer": {
        disclaimer object
      }
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "declarativeAgents": {
      "type": "array",
      "description": "An array of declarative agent elements references. Currently, only one declarative agent per application is supported.",
      "items": {
        "$ref": "#/definitions/declarativeAgentRef"
      },
      "minItems": 1,
      "maxItems": 1
    },
    "customEngineAgents": {
      "type": "array",
      "description": "An array of Custom Engine Agents. Currently only one Custom Engine Agent per application is supported. Support is currently in public preview.",
      "items": {
        "type": "object",
        "properties": {
          "id": {
            "$ref": "#/definitions/guid",
            "description": "The id of the Custom Engine Agent. If it is of type bot, the id must match the id specified in a bot in the bots node and the referenced bot must have personal scope. The app short name and short description must also be defined."
          },
          "type": {
            "type": "string",
            "enum": [
              "bot"
            ],
            "description": "The type of the Custom Engine Agent. Currently only type bot is supported."
          },
          "disclaimer": {
            "type": "object",
            "properties": {
              "text": {
                "type": "string",
                "description": "The message shown to users before they interact with this application. ",
                "maxLength": 500
              }
            },
            "required": [
              "text"
            ]
          }
        },
        "required": [
          "id",
          "type"
        ],
        "additionalProperties": false
      },
      "minItems": 1,
      "maxItems": 1
    }
  },
  "additionalProperties": false,
  "oneOf": [
    {
      "required": [
        "declarativeAgents"
      ]
    },
    {
      "required": [
        "customEngineAgents"
      ]
    }
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "declarativeAgents": [
    {
      "id": "{string}",
      "file": "{string}"
    }
  ],
  "customEngineAgents": [
    {
      "id": "{string}",
      "type": "bot"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "declarativeAgents": {
      "type": "array",
      "description": "An array of declarative agent elements references. Currently, only one declarative agent per application is supported.",
      "items": {
        "$ref": "#/definitions/declarativeAgentRef"
      },
      "minItems": 1,
      "maxItems": 1
    },
    "customEngineAgents": {
      "type": "array",
      "description": "An array of Custom Engine Agents. Currently only one Custom Engine Agent per application is supported. Support is currently in public preview.",
      "items": {
        "type": "object",
        "properties": {
          "id": {
            "$ref": "#/definitions/guid",
            "description": "The id of the Custom Engine Agent. If it is of type bot, the id must match the id specified in a bot in the bots node and the referenced bot must have personal scope. The app short name and short description must also be defined."
          },
          "type": {
            "type": "string",
            "enum": [
              "bot"
            ],
            "description": "The type of the Custom Engine Agent. Currently only type bot is supported."
          }
        },
        "required": [
          "id",
          "type"
        ],
        "additionalProperties": false
      },
      "minItems": 1,
      "maxItems": 1
    }
  },
  "additionalProperties": false,
  "oneOf": [
    {
      "required": [
        "declarativeAgents"
      ]
    },
    {
      "required": [
        "customEngineAgents"
      ]
    }
  ]
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "declarativeAgents": [
    {
      "id": "{string}",
      "file": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "declarativeAgents": {
      "type": "array",
      "description": "An array of declarative agent elements references. Currently, only one declarative agent per application is supported.",
      "items": {
        "$ref": "#/definitions/declarativeAgentRef"
      },
      "minItems": 1,
      "maxItems": 1
    }
  },
  "additionalProperties": false,
  "required": [
    "declarativeAgents"
  ]
}
```

## Properties

#### declarativeAgents

Array of objects that each define a declarative agent.

The `declarativeAgents` property is required if `customEngineAgents` is not specified.

**Type**  
Array of [declarativeAgentRef](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/declarative-agent-ref?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 1.

**Supported values**  


#### declarativeAgents

Array of objects that each define a declarative agent.

**Type**  
Array of [declarativeAgentRef](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/declarative-agent-ref?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 1. Maximum array items: 1.

**Supported values**  


#### customEngineAgents

Array of objects that each define a custom engine agent.

The `customEngineAgents` property is required if `declarativeAgents` is not specified.

**Type**  
Array of [customEngineAgents](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents-custom-engine-agents?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 1.

**Supported values**  


## Remarks

Note

Custom engine agents support in Microsoft 365 Copilot is currently in limited private preview and not all developers have access during the staged rollout.

## Examples

```json
{
    "copilotAgents": {
        "declarativeAgents": [
            {
                "id": "agent1",
                "file": "declarativeAgent1.json"
            }
        ]
    }
}
```
