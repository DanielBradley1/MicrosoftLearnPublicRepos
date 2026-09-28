<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-configuration-team?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.bots.configuration.team object

Dialog configuration info for bot in team scope

Properties that reference this object type:

- [root.bots.configuration.team](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-configuration?view=m365-app-1.30#team-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "fetchTask": {boolean},
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
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "fetchTask": {boolean},
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
    "fetchTask": {
      "$ref": "#/properties/composeExtensions/items/properties/commands/items/properties/fetchTask"
    },
    "taskInfo": {
      "$ref": "#/properties/composeExtensions/items/properties/commands/items/properties/taskInfo"
    }
  }
}
```

## Properties

#### fetchTask

A boolean value that indicates if it should fetch dialogs \(referred as task modules in TeamsJS v1.x\) dynamically.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### taskInfo

The dialog to preload when you use a bot.

**Type**  
[taskInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/task-info?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**
