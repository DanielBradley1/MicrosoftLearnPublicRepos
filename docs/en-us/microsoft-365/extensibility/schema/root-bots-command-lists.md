<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.bots.commandLists object

A list of commands that your bot can recommend to users, including their usage, description, and the scope for which the commands are valid. The object is an array \(maximum of three elements\) with all elements of type `object`; you must define a separate command list for each scope that your bot supports. To learn more see [Command bot in Teams](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/conversations/command-bot-in-teams).

Properties that reference this object type:

- [root.bots.commandLists](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#commandLists-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "triggers": [
    "mention | slash"
  ],
  "scopes": [
    "team | personal | groupChat | copilot"
  ],
  "commands": [
    {
      "title": "{string}",
      "description": "{string}",
      "type": "basic | prompt",
      "prompt": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "triggers": {
      "type": "array",
      "maxItems": 2,
      "items": {
        "type": "string",
        "enum": [
          "mention",
          "slash"
        ]
      },
      "default": [
        "mention"
      ],
      "description": "Controls where the commands in this commandLists entry are surfaced. \u0022mention\u0022 = @mention trigger (current behavior). \u0022slash\u0022 = slash commands list (targeted messages)."
    },
    "scopes": {
      "type": "array",
      "description": "Specifies the scopes for which the command list is valid",
      "maxItems": 4,
      "items": {
        "enum": [
          "team",
          "personal",
          "groupChat",
          "copilot"
        ]
      }
    },
    "commands": {
      "type": "array",
      "maxItems": 12,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "title": {
            "type": "string",
            "description": "The bot command name",
            "maxLength": 128
          },
          "description": {
            "type": "string",
            "description": "A simple text description or an example of the command syntax and its arguments.",
            "maxLength": 4000
          },
          "type": {
            "type": "string",
            "enum": [
              "basic",
              "prompt"
            ],
            "description": "Type of the command. Default is basic",
            "default": "basic"
          },
          "prompt": {
            "type": "string",
            "maxLength": 4000,
            "description": "The prompt text to be used by Teams when user initiates the command from one of the entry points"
          }
        },
        "required": [
          "title"
        ]
      }
    }
  },
  "required": [
    "scopes",
    "commands"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "scopes": [
    "team | personal | groupChat | copilot"
  ],
  "commands": [
    {
      "title": "{string}",
      "description": "{string}",
      "type": "basic | prompt",
      "prompt": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "scopes": {
      "type": "array",
      "description": "Specifies the scopes for which the command list is valid",
      "maxItems": 4,
      "items": {
        "enum": [
          "team",
          "personal",
          "groupChat",
          "copilot"
        ]
      }
    },
    "commands": {
      "type": "array",
      "maxItems": 12,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "title": {
            "type": "string",
            "description": "The bot command name",
            "maxLength": 128
          },
          "description": {
            "type": "string",
            "description": "A simple text description or an example of the command syntax and its arguments.",
            "maxLength": 4000
          },
          "type": {
            "type": "string",
            "enum": [
              "basic",
              "prompt"
            ],
            "description": "Type of the command. Default is basic",
            "default": "basic"
          },
          "prompt": {
            "type": "string",
            "maxLength": 4000,
            "description": "The prompt text to be used by Teams when user initiates the command from one of the entry points"
          }
        },
        "required": [
          "title"
        ]
      }
    }
  },
  "required": [
    "scopes",
    "commands"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "scopes": [
    "team | personal | groupChat | copilot"
  ],
  "commands": [
    {
      "title": "{string}",
      "description": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "scopes": {
      "type": "array",
      "description": "Specifies the scopes for which the command list is valid",
      "maxItems": 4,
      "items": {
        "enum": [
          "team",
          "personal",
          "groupChat",
          "copilot"
        ]
      }
    },
    "commands": {
      "type": "array",
      "maxItems": 12,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "title": {
            "type": "string",
            "description": "The bot command name",
            "maxLength": 128
          },
          "description": {
            "type": "string",
            "description": "A simple text description or an example of the command syntax and its arguments.",
            "maxLength": 4000
          }
        },
        "required": [
          "title",
          "description"
        ]
      }
    }
  },
  "required": [
    "scopes",
    "commands"
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "scopes": [
    "team | personal | groupChat | copilot"
  ],
  "commands": [
    {
      "title": "{string}",
      "description": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "scopes": {
      "type": "array",
      "description": "Specifies the scopes for which the command list is valid",
      "maxItems": 4,
      "items": {
        "enum": [
          "team",
          "personal",
          "groupChat",
          "copilot"
        ]
      }
    },
    "commands": {
      "type": "array",
      "maxItems": 10,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "title": {
            "type": "string",
            "description": "The bot command name",
            "maxLength": 128
          },
          "description": {
            "type": "string",
            "description": "A simple text description or an example of the command syntax and its arguments.",
            "maxLength": 4000
          }
        },
        "required": [
          "title",
          "description"
        ]
      }
    }
  },
  "required": [
    "scopes",
    "commands"
  ]
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "scopes": [
    "team | personal | groupChat"
  ],
  "commands": [
    {
      "title": "{string}",
      "description": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "scopes": {
      "type": "array",
      "description": "Specifies the scopes for which the command list is valid",
      "maxItems": 3,
      "items": {
        "enum": [
          "team",
          "personal",
          "groupChat"
        ]
      }
    },
    "commands": {
      "type": "array",
      "maxItems": 10,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "title": {
            "type": "string",
            "description": "The bot command name",
            "maxLength": 32
          },
          "description": {
            "type": "string",
            "description": "A simple text description or an example of the command syntax and its arguments.",
            "maxLength": 128
          }
        },
        "required": [
          "title",
          "description"
        ]
      }
    }
  },
  "required": [
    "scopes",
    "commands"
  ]
}
```

## Properties

#### triggers

Controls where the commands in this commandLists entry are surfaced. "mention" = @mention trigger \(current behavior\). "slash" = slash commands list \(targeted messages\).

**Type**  
Array of string

**Required**  
—

**Constraints**  
Maximum array items: 2.

**Supported values**  
Allowed values: `mention`, `slash`.

#### scopes

Specifies the scope for which the command list applies.

**Type**  
Array of enum

**Required**  
✅

**Constraints**  
Maximum array items: 4.

**Supported values**  
Allowed values: `team`, `personal`, `groupChat`, `copilot`.

#### scopes

Specifies the scope for which the command list applies.

**Type**  
Array of enum

**Required**  
✅

**Constraints**  
Maximum array items: 3.

**Supported values**  
Allowed values: `team`, `personal`, `groupChat`.

#### commands

An array of commands the bot supports.

**Type**  
Array of [commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Maximum array items: 12.

**Supported values**  


#### commands

An array of commands the bot supports.

**Type**  
Array of [commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Maximum array items: 10.

**Supported values**  


## Remarks

Note

Teams mobile client doesn't support the bot app when there is no value in the `commandLists` property.

## Examples

```json
{
 "bots": [
        "commandLists": [
            {
                "scopes": [
                    "team",
                    "groupChat"
                ],
                "commands": [
                    {
                        "title": "Command 1",
                        "description": "Description of Command 1"
                    },
                    {
                        "title": "Command 2",
                        "description": "Description of Command 2"
                    }
                ]
            },
            {
                "scopes": [
                    "personal",
                    "groupChat"
                ],
                "commands": [
                    {
                        "title": "Personal command 1",
                        "description": "Description of Personal command 1"
                    },
                    {
                        "title": "Personal command N",
                        "description": "Description of Personal command N"
                    }
                ]
            }
        ]
    ]
}
```
