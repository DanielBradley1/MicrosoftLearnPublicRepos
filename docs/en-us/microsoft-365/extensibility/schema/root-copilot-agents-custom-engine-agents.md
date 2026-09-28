<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents-custom-engine-agents?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.copilotAgents.customEngineAgents object

Custom engine agents represent advanced, custom workflows and provide full control over orchestration, AI models, and data integrations. These agents are integrated into the Microsoft Copilot UI, providing a seamless experience for end-users, similar to declarative agents. To learn more about custom engine agents, see [Custom engine agents for Microsoft 365 overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-custom-engine-agent).

Properties that reference this object type:

- [root.copilotAgents.customEngineAgents](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents?view=m365-app-1.30#customEngineAgents-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "type": "bot",
  "disclaimer": {
    "text": "{string}"
  },
  "functionsAs": "agentOnly | agenticUserOnly",
  "agenticUserTemplateId": "{string}"
}
```

```json
{
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
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "type": "bot",
  "disclaimer": {
    "text": "{string}"
  }
}
```

```json
{
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
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "id": "{string}",
  "type": "bot"
}
```

```json
{
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
}
```

## Properties

#### id

Unique \(bot\) identifier for the custom engine agent. Must match the `botId` specified in the `bots` section of the manifest, and the referenced bot must be of `personal` scope. The app `short` name and description must also be defined.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
The string value must be a [guid](https://en.wikipedia.org/wiki/Universally_unique_identifier).

#### type

Type of the custom engine agent.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `bot`.

#### disclaimer

The disclaimer message shown to users before they interact with this application.

**Type**  
[disclaimer](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents-custom-engine-agents-disclaimer?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### functionsAs

Value of 'agenticUserOnly' means the customEngineAgent must be hired and cannot be installed as a regular agent. 'agentOrAgenticUser' means the customEngineAgent supports both being installed as a regular agent and being hired. 'agentOnly' \(default\) means it supports being installed as a regular agent only.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `agentOnly`, `agenticUserOnly`.

#### agenticUserTemplateId

Unique identifier for the agentic user template. This id must match the id specified in an agentic user template in the agenticUserTemplates node

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**
