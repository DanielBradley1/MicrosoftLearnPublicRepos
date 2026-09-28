<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-configuration?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.bots.configuration object

The dialog configuration provides information specific to the bot's scope. It enables users to set up and modify their bot's settings directly within the channel or group chat after installation. To configure your bot experience see, [Configure bot scope](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bot-configuration-experience).

Properties that reference this object type:

- [root.bots.configuration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#configuration-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "team": {
    "fetchTask": {boolean},
    "taskInfo": {
      taskInfo object
    }
  },
  "groupChat": {
    "fetchTask": {boolean},
    "taskInfo": {
      taskInfo object
    }
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "team": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "fetchTask": {
          "type": "boolean",
          "description": "A boolean value that indicates if it should fetch bot config task module dynamically.",
          "default": false
        },
        "taskInfo": {
          "$ref": "#/definitions/taskInfo",
          "description": "Task module to be launched when fetch task set to false."
        }
      }
    },
    "groupChat": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "fetchTask": {
          "type": "boolean",
          "description": "A boolean value that indicates if it should fetch bot config task module dynamically.",
          "default": false
        },
        "taskInfo": {
          "$ref": "#/definitions/taskInfo",
          "description": "Task module to be launched when fetch task set to false."
        }
      }
    }
  }
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "team": {
    "fetchTask": {boolean},
    "taskInfo": {
      taskInfo object
    }
  },
  "groupChat": {
    "fetchTask": {boolean},
    "taskInfo": {
      taskInfo object
    }
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "team": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "fetchTask": {
          "$ref": "#/properties/composeExtensions/items/properties/commands/items/properties/fetchTask"
        },
        "taskInfo": {
          "$ref": "#/properties/composeExtensions/items/properties/commands/items/properties/taskInfo"
        }
      }
    },
    "groupChat": {
      "$ref": "#/properties/bots/items/properties/configuration/properties/team"
    }
  }
}
```

## Properties

#### team

Specifies whether the bot experience is available in the context of a channel in a team.

**Type**  
[team](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-configuration-team?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### groupChat

Specifies whether the bot experience is available in a group chat.

**Type**  
[groupChat](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-configuration-group-chat?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**
