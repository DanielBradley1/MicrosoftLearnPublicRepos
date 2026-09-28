<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/task-info?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# taskInfo object

Task module to be launched when fetch task set to false.

Properties that reference this object type:

- [root.bots.configuration.groupChat.taskInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-configuration-group-chat?view=m365-app-1.30#taskInfo-property)
- [root.bots.configuration.team.taskInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-configuration-team?view=m365-app-1.30#taskInfo-property)
- [root.composeExtensions.commands.taskInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#taskInfo-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "title": "{string}",
  "width": "{string}",
  "height": "{string}",
  "url": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "title": {
      "type": "string",
      "description": "Initial dialog title.",
      "maxLength": 64
    },
    "width": {
      "$ref": "#/definitions/taskInfoDimension",
      "description": "Dialog width - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027."
    },
    "height": {
      "$ref": "#/definitions/taskInfoDimension",
      "description": "Dialog height - either a number in pixels or default layout such as \u0027large\u0027, \u0027medium\u0027, or \u0027small\u0027."
    },
    "url": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "Initial webview URL."
    }
  }
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "title": "{string}",
  "width": "{string}",
  "height": "{string}",
  "url": "{string}"
}
```

```json
{
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
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "title": "{string}",
  "width": "{string}",
  "height": "{string}",
  "url": "{string}"
}
```

```json
{
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
```

## Properties

#### title

Initial dialog title.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### width

Dialog width.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 16.

**Supported values**  
The string value must be a number or `Large`, `Medium`, `Small`.

#### height

Dialog height.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 16.

**Supported values**  
The string value must be a number or `Large`, `Medium`, `Small`.

#### url

Initial webview URL.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

## Examples

```json
{
    "taskInfo": {
        "title": "Initial dialog title",
        "width": "Dialog width",
        "height": "Dialog height",
        "url": "Initial webview URL"
    }
}
```
