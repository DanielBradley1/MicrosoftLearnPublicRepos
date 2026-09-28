<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array-events-options?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# extensionAutoRunEventsArray.events.options object

Configures the behavior and handling options for automatic event responses in Outlook Add-ins. These options determine how events like `OnMessageSend` are processed, including settings such as `sendMode` \(which controls whether to block, prompt, or allow message sending\) and other event-specific configurations.

Properties that reference this object type:

- [root.extensions.autoRunEvents.events.options](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array-events?view=m365-app-1.30#options-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "sendMode": "promptUser | softBlock | block",
  "headerName": "{string}"
}
```

```json
{
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
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "sendMode": "promptUser | softBlock | block | ",
  "headerName": "{string}"
}
```

```json
{
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
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "sendMode": "promptUser | softBlock | block"
}
```

```json
{
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
```

## Properties

#### sendMode

Specifies the actions to take during a mail send action. For more information, see [available send mode options](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/onmessagesend-onappointmentsend-events#available-send-mode-options).

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `promptUser`, `softBlock`, `block`.

#### sendMode

Specifies the actions to take during a mail send action. For more information, see [available send mode options](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/smart-alerts-onmessagesend-walkthrough?tabs=jsonmanifest#available-send-mode-options).

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `promptUser`, `softBlock`, `block`, ``.

#### sendMode

Specifies the actions to take during a mail send action. For more information, see [available send mode options](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/onmessagesend-onappointmentsend-events#available-send-mode-options).

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `promptUser`, `softBlock`, `block`.

#### headerName

Specifies the internet header name used to identify a message during a decryption event. Follows email header name constraints. For more information, see [Create an encryption Outlook add-in](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/encryption-decryption).

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  


#### headerName

Specifies the internet header name used to identify a message during a decryption event. Follows email header name constraints.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
The string must match the following regular expression: `^[A-Za-z0-9][A-Za-z0-9-]*$`.

## Examples

```json
{
  "options": {
    "sendMode": "promptUser"
  }
}
```
