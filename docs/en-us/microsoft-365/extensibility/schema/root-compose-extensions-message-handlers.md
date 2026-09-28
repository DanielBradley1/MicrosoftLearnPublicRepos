<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-message-handlers?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.composeExtensions.messageHandlers object

A list of handlers that allow apps to be invoked when certain conditions are met. Domains must also be listed in `validDomains`.

Properties that reference this object type:

- [root.composeExtensions.messageHandlers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions?view=m365-app-1.30#messageHandlers-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "type": "link",
  "value": {
    "domains": [
      "{string}"
    ],
    "supportsAnonymousAccess": {boolean},
    "supportsAnonymizedPayloads": {boolean}
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "type": {
      "type": "string",
      "enum": [
        "link"
      ],
      "description": "Type of the message handler"
    },
    "value": {
      "type": "object",
      "properties": {
        "domains": {
          "type": "array",
          "description": "A list of domains that the link message handler can register for, and when they are matched the app will be invoked",
          "items": {
            "type": "string",
            "maxLength": 2048
          }
        },
        "supportsAnonymousAccess": {
          "type": "boolean",
          "description": "A boolean value that indicates whether the app\u0027s link message handler supports anonymous invoke flow. [Deprecated]. This property has been superceded by \u0027supportsAnonymizedPayloads\u0027.",
          "default": false
        },
        "supportsAnonymizedPayloads": {
          "type": "boolean",
          "description": "A boolean value that indicates whether the app\u0027s link message handler supports anonymous invoke flow.",
          "default": false
        }
      }
    }
  },
  "required": [
    "type",
    "value"
  ],
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "type": "link",
  "value": {
    "domains": [
      "{string}"
    ],
    "supportsAnonymizedPayloads": {boolean}
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "type": {
      "type": "string",
      "enum": [
        "link"
      ],
      "description": "Type of the message handler"
    },
    "value": {
      "type": "object",
      "properties": {
        "domains": {
          "type": "array",
          "description": "A list of domains that the link message handler can register for, and when they are matched the app will be invoked",
          "items": {
            "type": "string",
            "maxLength": 2048
          }
        },
        "supportsAnonymizedPayloads": {
          "type": "boolean",
          "description": "A boolean that indicates whether the app\u0027s link message handler supports anonymous invoke flow.",
          "default": false
        }
      },
      "additionalProperties": false
    }
  },
  "required": [
    "type",
    "value"
  ],
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "type": "link",
  "value": {
    "domains": [
      "{string}"
    ],
    "supportsAnonymizedPayloads": {boolean}
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "type": {
      "type": "string",
      "enum": [
        "link"
      ],
      "description": "Type of the message handler"
    },
    "value": {
      "type": "object",
      "properties": {
        "domains": {
          "type": "array",
          "description": "A list of domains that the link message handler can register for, and when they are matched the app will be invoked",
          "items": {
            "type": "string",
            "maxLength": 2048
          }
        },
        "supportsAnonymizedPayloads": {
          "type": "boolean",
          "description": "A boolean that indicates whether the app\u0027s link message handler supports anonymous invoke flow.",
          "default": false
        }
      }
    }
  },
  "required": [
    "type",
    "value"
  ],
  "additionalProperties": false
}
```

## Properties

#### type

The type of message handler.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `link`.

#### value

Configuration info for the message handler.

**Type**  
[value](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-message-handlers-value?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


## Examples

```json
{
"composeExtensions": [
        {
            "messageHandlers": [
                {
                    "type": "link",
                    "value": {
                        "domains": [
                            "mysite.someplace.com",
                            "othersite.someplace.com"
                        ],
                        "supportsAnonymizedPayloads": false
                    }
                }
            ]
        }
    ]
}
```
