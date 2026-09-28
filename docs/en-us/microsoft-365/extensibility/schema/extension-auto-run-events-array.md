<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionAutoRunEventsArray object

The `extensions.autoRunEvents` property defines event-based activation extension points.

Properties that reference this object type:

- [root.extensions.autoRunEvents](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#autoRunEvents-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "events": [
    {
      "type": "{string}",
      "actionId": "{string}",
      "options": {
        options object
      }
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "events": {
      "type": "array",
      "maxItems": 20,
      "description": "Specifies the type of event. For supported types, please see: https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/autolaunch?tabs=xmlmanifest#supported-events.",
      "items": {
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
    }
  },
  "additionalProperties": false,
  "required": [
    "events"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "events": [
    {
      "type": "{string}",
      "actionId": "{string}",
      "options": {
        options object
      }
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "events": {
      "type": "array",
      "maxItems": 20,
      "description": "Specifies the type of event. For supported types, please see: https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/autolaunch?tabs=xmlmanifest#supported-events.",
      "items": {
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
    }
  },
  "additionalProperties": false,
  "required": [
    "events"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "events": [
    {
      "type": "{string}",
      "actionId": "{string}",
      "options": {
        options object
      }
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "events": {
      "type": "array",
      "maxItems": 20,
      "description": "Specifies the type of event. For supported types, please see: https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/autolaunch?tabs=xmlmanifest#supported-events.",
      "items": {
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
    }
  },
  "additionalProperties": false,
  "required": [
    "events"
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "requirements": {
    "capabilities": [
      {
        capabilities object
      }
    ],
    "scopes": [
      "mail | workbook | document | presentation"
    ],
    "formFactors": [
      "desktop | mobile"
    ]
  },
  "events": [
    {
      "type": "{string}",
      "actionId": "{string}",
      "options": {
        options object
      }
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "events": {
      "type": "array",
      "maxItems": 20,
      "description": "Specifies the type of event. For supported types, please see: https://review.learn.microsoft.com/en-us/office/dev/add-ins/outlook/autolaunch?tabs=xmlmanifest#supported-events.",
      "items": {
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
    }
  },
  "additionalProperties": false,
  "required": [
    "events"
  ]
}
```

## Properties

#### requirements

Specifies the scopes, formFactors, and Office JavaScript library requirement sets that must be supported on the Office client in order for the event handling code to run. For more information, see [Specify Office Add-in requirements in the unified manifest for Microsoft 365](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requirements-property-unified-manifest).

**Type**  
[requirementsExtensionElement](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### events

Configures the event that cause actions in an Outlook Add-in to run automatically. For example, see [use smart alerts and the `OnMessageSend` and `OnAppointmentSend` events in your Outlook Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/smart-alerts-onmessagesend-walkthrough?tabs=jsonmanifest).

**Type**  
Array of [events](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-auto-run-events-array-events?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Maximum array items: 20.

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
