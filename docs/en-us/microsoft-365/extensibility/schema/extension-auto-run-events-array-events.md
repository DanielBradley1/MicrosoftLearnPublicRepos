<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array-events?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# extensionAutoRunEventsArray.events object

Configures the event that cause actions in an Outlook Add-in to run automatically. For example, see [use smart alerts and the `OnMessageSend` and `OnAppointmentSend` events in your Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/smart-alerts-onmessagesend-walkthrough?tabs=jsonmanifest).

Properties that reference this object type:

- [root.extensions.autoRunEvents.events](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array?view=m365-app-1.30#events-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "type": "{string}",
  "actionId": "{string}",
  "options": {
    "sendMode": "promptUser | softBlock | block",
    "headerName": "{string}"
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "type": {
      "type": "string",
      "maxLength": 64
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an action defined in runtimes. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "options": {
      "type": "object",
      "description": "Configures how Outlook responds to the event.",
      "properties": {
        "sendMode": {
          "type": "string",
          "description": "Specifies the actions to take during a mail send event.",
          "enum": [
            "promptUser",
            "softBlock",
            "block"
          ]
        },
        "headerName": {
          "type": "string",
          "description": "Specifies the internet header name used to identify a message during a decryption event. Follows email header name constraints.",
          "regex": "^[A-Za-z0-9][A-Za-z0-9-]*$"
        }
      },
      "additionalProperties": false,
      "anyOf": [
        {
          "required": [
            "sendMode"
          ],
          "not": {
            "required": [
              "headerName"
            ]
          }
        },
        {
          "required": [
            "headerName"
          ],
          "not": {
            "required": [
              "sendMode"
            ]
          }
        }
      ]
    }
  },
  "additionalProperties": false,
  "required": [
    "type",
    "actionId"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "type": "{string}",
  "actionId": "{string}",
  "options": {
    "sendMode": "promptUser | softBlock | block | ",
    "headerName": "{string}"
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "type": {
      "type": "string",
      "maxLength": 64
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an action defined in runtimes. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "options": {
      "type": "object",
      "description": "Configures how Outlook responds to the event.",
      "properties": {
        "sendMode": {
          "type": "string",
          "description": "Specifies the actions to take during a mail send event. The property may be omitted, but a literal null is not a valid value.",
          "enum": [
            "promptUser",
            "softBlock",
            "block",
            null
          ]
        },
        "headerName": {
          "type": "string",
          "description": "Specifies the internet header name used to identify a message during a decryption event. Follows email header name constraints.",
          "pattern": "^[A-Za-z0-9][A-Za-z0-9-]*$"
        }
      },
      "additionalProperties": false,
      "anyOf": [
        {
          "required": [
            "sendMode"
          ],
          "not": {
            "required": [
              "headerName"
            ]
          }
        },
        {
          "required": [
            "headerName"
          ],
          "not": {
            "required": [
              "sendMode"
            ]
          }
        }
      ]
    }
  },
  "additionalProperties": false,
  "required": [
    "type",
    "actionId"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "type": "{string}",
  "actionId": "{string}",
  "options": {
    "sendMode": "promptUser | softBlock | block"
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "type": {
      "type": "string",
      "maxLength": 64
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an action defined in runtimes. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "options": {
      "type": "object",
      "description": "Configures how Outlook responds to the event.",
      "properties": {
        "sendMode": {
          "type": "string",
          "enum": [
            "promptUser",
            "softBlock",
            "block"
          ]
        }
      },
      "additionalProperties": false,
      "required": [
        "sendMode"
      ]
    }
  },
  "additionalProperties": false,
  "required": [
    "type",
    "actionId"
  ]
}
```

## Properties

#### type

Specifies the type of event. For supported types, see [supported events](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/autolaunch?tabs=xmlmanifest#supported-events).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### actionId

Identifies the action that is taken when the event fires. The `actionId` must match with `runtime.actions.id`.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### options

Configures how Outlook responds to the event. Specify one of the supported values in the `options` object: `sendMode` or `headerName`.

**Type**  
[options](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array-events-options?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


## Examples

```json
{
  "events": [
    {
      "type": "newMessageComposeCreated",
      "actionId": "onNewMessageComposeCreated"
    },
    {
      "type": "messageSending",
      "actionId": "onMessageSending",
      "options": {
        "sendMode": "promptUser"
      }
    }
  ]
}
```
