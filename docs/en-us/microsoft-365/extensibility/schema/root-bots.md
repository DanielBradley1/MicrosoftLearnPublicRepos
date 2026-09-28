<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.bots object

Defines a bot solution, along with optional information such as default command properties.

Properties that reference this object type:

- [root.bots](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#bots-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "botId": "{string}",
  "configuration": {
    "team": {
      team object
    },
    "groupChat": {
      groupChat object
    }
  },
  "needsChannelSelector": {boolean},
  "isNotificationOnly": {boolean},
  "requiresSecurityEnabledGroup": {boolean},
  "supportsFiles": {boolean},
  "supportsCalling": {boolean},
  "supportsVideo": {boolean},
  "supportsSessions": {boolean},
  "scopes": [
    "team | personal | groupChat | copilot"
  ],
  "supportsTargetedMessages": {boolean},
  "commandLists": [
    {
      "triggers": [
        "mention | slash"
      ],
      "scopes": [
        "team | personal | groupChat | copilot"
      ],
      "commands": [
        {
          commands object
        }
      ]
    }
  ],
  "requirementSet": {
    "hostMustSupportFunctionalities": [
      {
        hostFunctionality object
      }
    ]
  },
  "registrationInfo": {
    "source": "standard | microsoftCopilotStudio | onedriveSharepoint",
    "environment": "{string}",
    "schemaName": "{string}",
    "clusterCategory": "{string}"
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "configuration": {
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
    },
    "needsChannelSelector": {
      "type": "boolean",
      "description": "This value describes whether or not the bot utilizes a user hint to add the bot to a specific channel.",
      "default": false
    },
    "isNotificationOnly": {
      "type": "boolean",
      "description": "A value indicating whether or not the bot is a one-way notification only bot, as opposed to a conversational bot.",
      "default": false
    },
    "requiresSecurityEnabledGroup": {
      "type": "boolean",
      "description": "A value indicating whether the team\u0027s Office group needs to be security enabled.",
      "default": false
    },
    "supportsFiles": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports uploading/downloading of files.",
      "default": false
    },
    "supportsCalling": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports audio calling.",
      "default": false
    },
    "supportsVideo": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports video calling.",
      "default": false
    },
    "supportsSessions": {
      "type": "boolean",
      "description": "A property set by developers to opt-in to sessions.",
      "default": false
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the bot offers an experience in the context of a channel in a team, in a group chat (groupChat), an experience scoped to an individual user alone (personal) OR within Copilot surfaces. These options are non-exclusive.",
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
    "supportsTargetedMessages": {
      "type": "boolean",
      "description": "When true, the bot is enabled to receive targeted messages and appears in the / slash commands list. Required for slash command support. Developers can optionally add triggers: [\u0022slash\u0022] on commandLists entries to surface specific commands.",
      "default": false
    },
    "commandLists": {
      "type": "array",
      "maxItems": 3,
      "description": "The list of commands that the bot supplies, including their usage, description, and the scope for which the commands are valid. A separate command list should be used for each scope.",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet",
      "description": "The set of requirements for the bot."
    },
    "registrationInfo": {
      "description": "System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
      "type": "object",
      "properties": {
        "source": {
          "type": "string",
          "enum": [
            "standard",
            "microsoftCopilotStudio",
            "onedriveSharepoint"
          ],
          "description": "The partner source through which the bot is registered. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually."
        },
        "environment": {
          "type": "string",
          "description": "A Power Platform environment that serves as a container for building apps under a Microsoft 365 tenant and can only be accessed by users within that tenant. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        },
        "schemaName": {
          "type": "string",
          "description": "The Copilot Studio copilot schema name. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        },
        "clusterCategory": {
          "type": "string",
          "description": "The core services cluster category for Copilot Studio copilots. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        }
      },
      "required": [
        "source"
      ],
      "additionalProperties": false
    }
  },
  "required": [
    "botId",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "botId": "{string}",
  "configuration": {
    "team": {
      team object
    },
    "groupChat": {
      groupChat object
    }
  },
  "needsChannelSelector": {boolean},
  "isNotificationOnly": {boolean},
  "supportsFiles": {boolean},
  "supportsCalling": {boolean},
  "supportsVideo": {boolean},
  "scopes": [
    "team | personal | groupChat | copilot"
  ],
  "supportsTargetedMessages": {boolean},
  "commandLists": [
    {
      "triggers": [
        "mention | slash"
      ],
      "scopes": [
        "team | personal | groupChat | copilot"
      ],
      "commands": [
        {
          commands object
        }
      ]
    }
  ],
  "requirementSet": {
    "hostMustSupportFunctionalities": [
      {
        hostFunctionality object
      }
    ]
  },
  "registrationInfo": {
    "source": "standard | microsoftCopilotStudio | onedriveSharepoint",
    "environment": "{string}",
    "schemaName": "{string}",
    "clusterCategory": "{string}"
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "configuration": {
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
    },
    "needsChannelSelector": {
      "type": "boolean",
      "description": "This value describes whether or not the bot utilizes a user hint to add the bot to a specific channel.",
      "default": false
    },
    "isNotificationOnly": {
      "type": "boolean",
      "description": "A value indicating whether or not the bot is a one-way notification only bot, as opposed to a conversational bot.",
      "default": false
    },
    "supportsFiles": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports uploading/downloading of files.",
      "default": false
    },
    "supportsCalling": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports audio calling.",
      "default": false
    },
    "supportsVideo": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports video calling.",
      "default": false
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the bot offers an experience in the context of a channel in a team, in a group chat (groupChat), an experience scoped to an individual user alone (personal) OR within Copilot surfaces. These options are non-exclusive.",
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
    "supportsTargetedMessages": {
      "type": "boolean",
      "description": "When true, the bot is enabled to receive targeted messages and appears in the / slash commands list. Required for slash command support. Developers can optionally add triggers: [\u0022slash\u0022] on commandLists entries to surface specific commands.",
      "default": false
    },
    "commandLists": {
      "type": "array",
      "maxItems": 3,
      "description": "The list of commands that the bot supplies, including their usage, description, and the scope for which the commands are valid. A separate command list should be used for each scope.",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    },
    "registrationInfo": {
      "description": "System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
      "type": "object",
      "properties": {
        "source": {
          "type": "string",
          "enum": [
            "standard",
            "microsoftCopilotStudio",
            "onedriveSharepoint"
          ],
          "description": "The partner source through which the bot is registered. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually."
        },
        "environment": {
          "type": "string",
          "description": "A Power Platform environment that serves as a container for building apps under a Microsoft 365 tenant and can only be accessed by users within that tenant. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        },
        "schemaName": {
          "type": "string",
          "description": "The Copilot Studio copilot schema name. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        },
        "clusterCategory": {
          "type": "string",
          "description": "The core services cluster category for Copilot Studio copilots. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        }
      },
      "required": [
        "source"
      ],
      "additionalProperties": false
    }
  },
  "required": [
    "botId",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "botId": "{string}",
  "configuration": {
    "team": {
      team object
    },
    "groupChat": {
      groupChat object
    }
  },
  "needsChannelSelector": {boolean},
  "isNotificationOnly": {boolean},
  "supportsFiles": {boolean},
  "supportsCalling": {boolean},
  "supportsVideo": {boolean},
  "scopes": [
    "team | personal | groupChat | copilot"
  ],
  "commandLists": [
    {
      "scopes": [
        "team | personal | groupChat | copilot"
      ],
      "commands": [
        {
          commands object
        }
      ]
    }
  ],
  "requirementSet": {
    "hostMustSupportFunctionalities": [
      {
        hostFunctionality object
      }
    ]
  },
  "registrationInfo": {
    "source": "standard | microsoftCopilotStudio | onedriveSharepoint",
    "environment": "{string}",
    "schemaName": "{string}",
    "clusterCategory": "{string}"
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "configuration": {
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
    },
    "needsChannelSelector": {
      "type": "boolean",
      "description": "This value describes whether or not the bot utilizes a user hint to add the bot to a specific channel.",
      "default": false
    },
    "isNotificationOnly": {
      "type": "boolean",
      "description": "A value indicating whether or not the bot is a one-way notification only bot, as opposed to a conversational bot.",
      "default": false
    },
    "supportsFiles": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports uploading/downloading of files.",
      "default": false
    },
    "supportsCalling": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports audio calling.",
      "default": false
    },
    "supportsVideo": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports video calling.",
      "default": false
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the bot offers an experience in the context of a channel in a team, in a group chat (groupChat), an experience scoped to an individual user alone (personal) OR within Copilot surfaces. These options are non-exclusive.",
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
    "commandLists": {
      "type": "array",
      "maxItems": 3,
      "description": "The list of commands that the bot supplies, including their usage, description, and the scope for which the commands are valid. A separate command list should be used for each scope.",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    },
    "registrationInfo": {
      "description": "System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
      "type": "object",
      "properties": {
        "source": {
          "type": "string",
          "enum": [
            "standard",
            "microsoftCopilotStudio",
            "onedriveSharepoint"
          ],
          "description": "The partner source through which the bot is registered. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually."
        },
        "environment": {
          "type": "string",
          "description": "A Power Platform environment that serves as a container for building apps under a Microsoft 365 tenant and can only be accessed by users within that tenant. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        },
        "schemaName": {
          "type": "string",
          "description": "The Copilot Studio copilot schema name. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        },
        "clusterCategory": {
          "type": "string",
          "description": "The core services cluster category for Copilot Studio copilots. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        }
      },
      "required": [
        "source"
      ],
      "additionalProperties": false
    }
  },
  "required": [
    "botId",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "botId": "{string}",
  "configuration": {
    "team": {
      team object
    },
    "groupChat": {
      groupChat object
    }
  },
  "needsChannelSelector": {boolean},
  "isNotificationOnly": {boolean},
  "supportsFiles": {boolean},
  "supportsCalling": {boolean},
  "supportsVideo": {boolean},
  "scopes": [
    "team | personal | groupChat | copilot"
  ],
  "commandLists": [
    {
      "scopes": [
        "team | personal | groupChat | copilot"
      ],
      "commands": [
        {
          commands object
        }
      ]
    }
  ],
  "requirementSet": {
    "hostMustSupportFunctionalities": [
      {
        hostFunctionality object
      }
    ]
  },
  "registrationInfo": {
    "source": "standard | microsoftCopilotStudio | onedriveSharepoint",
    "environment": "{string}",
    "schemaName": "{string}",
    "clusterCategory": "{string}"
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "configuration": {
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
    },
    "needsChannelSelector": {
      "type": "boolean",
      "description": "This value describes whether or not the bot utilizes a user hint to add the bot to a specific channel.",
      "default": false
    },
    "isNotificationOnly": {
      "type": "boolean",
      "description": "A value indicating whether or not the bot is a one-way notification only bot, as opposed to a conversational bot.",
      "default": false
    },
    "supportsFiles": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports uploading/downloading of files.",
      "default": false
    },
    "supportsCalling": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports audio calling.",
      "default": false
    },
    "supportsVideo": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports video calling.",
      "default": false
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the bot offers an experience in the context of a channel in a team, in a group chat (groupChat), an experience scoped to an individual user alone (personal) OR within Copilot surfaces. These options are non-exclusive.",
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
    "commandLists": {
      "type": "array",
      "maxItems": 3,
      "description": "The list of commands that the bot supplies, including their usage, description, and the scope for which the commands are valid. A separate command list should be used for each scope.",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    },
    "registrationInfo": {
      "description": "System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
      "type": "object",
      "properties": {
        "source": {
          "type": "string",
          "enum": [
            "standard",
            "microsoftCopilotStudio",
            "onedriveSharepoint"
          ],
          "description": "The partner source through which the bot is registered. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually."
        },
        "environment": {
          "type": "string",
          "description": "A Power Platform environment that serves as a container for building apps under a Microsoft 365 tenant and can only be accessed by users within that tenant. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        },
        "schemaName": {
          "type": "string",
          "description": "The Copilot Studio copilot schema name. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        },
        "clusterCategory": {
          "type": "string",
          "description": "The core services cluster category for Copilot Studio copilots. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        }
      },
      "required": [
        "source"
      ],
      "additionalProperties": false
    }
  },
  "required": [
    "botId",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "botId": "{string}",
  "configuration": {
    "team": {
      team object
    },
    "groupChat": {
      groupChat object
    }
  },
  "needsChannelSelector": {boolean},
  "isNotificationOnly": {boolean},
  "supportsFiles": {boolean},
  "supportsCalling": {boolean},
  "supportsVideo": {boolean},
  "scopes": [
    "team | personal | groupChat | copilot"
  ],
  "commandLists": [
    {
      "scopes": [
        "team | personal | groupChat | copilot"
      ],
      "commands": [
        {
          commands object
        }
      ]
    }
  ],
  "requirementSet": {
    "hostMustSupportFunctionalities": [
      {
        hostFunctionality object
      }
    ]
  },
  "registrationInfo": {
    "source": "standard | microsoftCopilotStudio | onedriveSharepoint",
    "environment": "{string}",
    "schemaName": "{string}",
    "clusterCategory": "{string}"
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "configuration": {
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
    },
    "needsChannelSelector": {
      "type": "boolean",
      "description": "This value describes whether or not the bot utilizes a user hint to add the bot to a specific channel.",
      "default": false
    },
    "isNotificationOnly": {
      "type": "boolean",
      "description": "A value indicating whether or not the bot is a one-way notification only bot, as opposed to a conversational bot.",
      "default": false
    },
    "supportsFiles": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports uploading/downloading of files.",
      "default": false
    },
    "supportsCalling": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports audio calling.",
      "default": false
    },
    "supportsVideo": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports video calling.",
      "default": false
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the bot offers an experience in the context of a channel in a team, in a group chat (groupChat), an experience scoped to an individual user alone (personal) OR within Copilot surfaces. These options are non-exclusive.",
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
    "commandLists": {
      "type": "array",
      "maxItems": 3,
      "description": "The list of commands that the bot supplies, including their usage, description, and the scope for which the commands are valid. A separate command list should be used for each scope.",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    },
    "registrationInfo": {
      "description": "System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
      "type": "object",
      "properties": {
        "source": {
          "type": "string",
          "enum": [
            "standard",
            "microsoftCopilotStudio",
            "onedriveSharepoint"
          ],
          "description": "The partner source through which the bot is registered. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually."
        },
        "environment": {
          "type": "string",
          "description": "A Power Platform environment that serves as a container for building apps under a Microsoft 365 tenant and can only be accessed by users within that tenant. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        },
        "schemaName": {
          "type": "string",
          "description": "The Copilot Studio copilot schema name. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        },
        "clusterCategory": {
          "type": "string",
          "description": "The core services cluster category for Copilot Studio copilots. System\u2011generated metadata. This information is maintained by Microsoft services and must not be modified manually.",
          "maxLength": 128
        }
      },
      "required": [
        "source"
      ],
      "additionalProperties": false
    }
  },
  "required": [
    "botId",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_6_syntax)
- [Schema](#tabpanel_6_schema)

```json
{
  "botId": "{string}",
  "configuration": {
    "team": {
      team object
    },
    "groupChat": {
      groupChat object
    }
  },
  "needsChannelSelector": {boolean},
  "isNotificationOnly": {boolean},
  "supportsFiles": {boolean},
  "supportsCalling": {boolean},
  "supportsVideo": {boolean},
  "scopes": [
    "team | personal | groupChat | copilot"
  ],
  "commandLists": [
    {
      "scopes": [
        "team | personal | groupChat | copilot"
      ],
      "commands": [
        {
          commands object
        }
      ]
    }
  ],
  "requirementSet": {
    "hostMustSupportFunctionalities": [
      {
        hostFunctionality object
      }
    ]
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "configuration": {
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
    },
    "needsChannelSelector": {
      "type": "boolean",
      "description": "This value describes whether or not the bot utilizes a user hint to add the bot to a specific channel.",
      "default": false
    },
    "isNotificationOnly": {
      "type": "boolean",
      "description": "A value indicating whether or not the bot is a one-way notification only bot, as opposed to a conversational bot.",
      "default": false
    },
    "supportsFiles": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports uploading/downloading of files.",
      "default": false
    },
    "supportsCalling": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports audio calling.",
      "default": false
    },
    "supportsVideo": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports video calling.",
      "default": false
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the bot offers an experience in the context of a channel in a team, in a group chat (groupChat), an experience scoped to an individual user alone (personal) OR within Copilot surfaces. These options are non-exclusive.",
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
    "commandLists": {
      "type": "array",
      "maxItems": 3,
      "description": "The list of commands that the bot supplies, including their usage, description, and the scope for which the commands are valid. A separate command list should be used for each scope.",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    }
  },
  "required": [
    "botId",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_7_syntax)
- [Schema](#tabpanel_7_schema)

```json
{
  "botId": "{string}",
  "configuration": {
    "team": {
      team object
    },
    "groupChat": {
      groupChat object
    }
  },
  "needsChannelSelector": {boolean},
  "isNotificationOnly": {boolean},
  "supportsFiles": {boolean},
  "supportsCalling": {boolean},
  "supportsVideo": {boolean},
  "scopes": [
    "team | personal | groupChat"
  ],
  "commandLists": [
    {
      "scopes": [
        "team | personal | groupChat"
      ],
      "commands": [
        {
          commands object
        }
      ]
    }
  ],
  "requirementSet": {
    "hostMustSupportFunctionalities": [
      {
        hostFunctionality object
      }
    ]
  }
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "configuration": {
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
    },
    "needsChannelSelector": {
      "type": "boolean",
      "description": "This value describes whether or not the bot utilizes a user hint to add the bot to a specific channel.",
      "default": false
    },
    "isNotificationOnly": {
      "type": "boolean",
      "description": "A value indicating whether or not the bot is a one-way notification only bot, as opposed to a conversational bot.",
      "default": false
    },
    "supportsFiles": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports uploading/downloading of files.",
      "default": false
    },
    "supportsCalling": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports audio calling.",
      "default": false
    },
    "supportsVideo": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports video calling.",
      "default": false
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the bot offers an experience in the context of a channel in a team, in a 1:1 or group chat, or in an experience scoped to an individual user alone. These options are non-exclusive.",
      "maxItems": 3,
      "items": {
        "enum": [
          "team",
          "personal",
          "groupChat"
        ]
      }
    },
    "commandLists": {
      "type": "array",
      "maxItems": 3,
      "description": "The list of commands that the bot supplies, including their usage, description, and the scope for which the commands are valid. A separate command list should be used for each scope.",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    }
  },
  "required": [
    "botId",
    "scopes"
  ]
}
```

- [Syntax](#tabpanel_8_syntax)
- [Schema](#tabpanel_8_schema)

```json
{
  "botId": "{string}",
  "configuration": {
    "team": {
      team object
    },
    "groupChat": {
      groupChat object
    }
  },
  "needsChannelSelector": {boolean},
  "isNotificationOnly": {boolean},
  "supportsFiles": {boolean},
  "supportsCalling": {boolean},
  "supportsVideo": {boolean},
  "scopes": [
    "team | personal | groupChat"
  ],
  "commandLists": [
    {
      "scopes": [
        "team | personal | groupChat"
      ],
      "commands": [
        {
          commands object
        }
      ]
    }
  ]
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "configuration": {
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
    },
    "needsChannelSelector": {
      "type": "boolean",
      "description": "This value describes whether or not the bot utilizes a user hint to add the bot to a specific channel.",
      "default": false
    },
    "isNotificationOnly": {
      "type": "boolean",
      "description": "A value indicating whether or not the bot is a one-way notification only bot, as opposed to a conversational bot.",
      "default": false
    },
    "supportsFiles": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports uploading/downloading of files.",
      "default": false
    },
    "supportsCalling": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports audio calling.",
      "default": false
    },
    "supportsVideo": {
      "type": "boolean",
      "description": "A value indicating whether the bot supports video calling.",
      "default": false
    },
    "scopes": {
      "type": "array",
      "description": "Specifies whether the bot offers an experience in the context of a channel in a team, in a 1:1 or group chat, or in an experience scoped to an individual user alone. These options are non-exclusive.",
      "maxItems": 3,
      "items": {
        "enum": [
          "team",
          "personal",
          "groupChat"
        ]
      }
    },
    "commandLists": {
      "type": "array",
      "maxItems": 3,
      "description": "The list of commands that the bot supplies, including their usage, description, and the scope for which the commands are valid. A separate command list should be used for each scope.",
      "items": {
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
    }
  },
  "required": [
    "botId",
    "scopes"
  ]
}
```

## Properties

#### botId

Note

If your app includes a bot, `id` must be set to the bot ID in [the bot's registration on Azure](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/authentication/add-authentication).

The Microsoft App ID specified for the bot in the Teams Developer Portal \([https://dev.teams.microsoft.com/tools](https://dev.teams.microsoft.com/tools)\).

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
The string value must be a [guid](https://en.wikipedia.org/wiki/Universally_unique_identifier).

#### configuration

Represents configuration information for the given scope of the bot.

**Type**  
[configuration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-configuration?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### needsChannelSelector

This value describes whether or not the bot utilizes a user hint to add the bot to a specific channel.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### isNotificationOnly

A value indicating whether or not the bot is a one-way notification only bot, as opposed to a conversational bot.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### requiresSecurityEnabledGroup

A value indicating whether the team's Office group needs to be security enabled.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### supportsFiles

A value indicating whether the bot supports uploading/downloading of files.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### supportsCalling

A value indicating whether the bot supports audio calling.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### supportsVideo

A value indicating whether the bot supports video calling.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### supportsSessions

A property set by developers to opt-in to sessions.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### scopes

Specifies whether the bot offers an experience in the context of [Copilot \(as a *custom engine agent*\)](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/how-conversation-ai-get-started), a channel in a team, in a 1:1 or group chat, or in an experience scoped to an individual user alone. These options are non-exclusive.

**Type**  
Array of enum

**Required**  
✅

**Constraints**  
Maximum array items: 4.

**Supported values**  
Allowed values: `team`, `personal`, `groupChat`, `copilot`.

#### scopes

Specifies whether the bot offers an experience in the context of a channel in a team, in a 1:1 or group chat, or in an experience scoped to an individual user alone. These options are non-exclusive.

**Type**  
Array of enum

**Required**  
✅

**Constraints**  
Maximum array items: 3.

**Supported values**  
Allowed values: `team`, `personal`, `groupChat`.

#### supportsTargetedMessages

When true, the bot is enabled to receive targeted messages and appears in the / slash commands list. Required for slash command support. Developers can optionally add triggers: \["slash"\] on commandLists entries to surface specific commands.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### commandLists

The list of commands that the bot supplies, including their usage, description, and the scope for which the commands are valid. A separate command list should be used for each scope.

**Type**  
Array of [commandLists](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 3.

**Supported values**  


#### requirementSet

Runtime requirements for the bot to function properly in the Microsoft 365 host application. If one or more of the requirements aren't supported by the runtime host, the host won't load the bot.

**Type**  
[elementRequirementSet](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### registrationInfo

System‑generated metadata. This information is maintained by Microsoft services and must not be modified manually.

**Type**  
[registrationInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-registration-info?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


## Remarks

The item is an array \(maximum of only one element— only one bot is allowed per app\) with all elements of the type `object`. This block is required only for solutions that provide a bot experience.

To enable a custom engine agent in Microsoft 365 Copilot, you need to define both the *copilot* value in `scopes` and the [`customEngineAgent`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents-custom-engine-agents?view=m365-app-1.30). If you define one without the other, it will result in a manifest validation error.

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
