<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# root.composeExtensions object

The compose extension property defines a message extension for the app. Currently only one message extension per app is supported. To learn more about message extensions, see the guidance on [how to build a message extension](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions).

Properties that reference this object type:

- [root.composeExtensions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#composeExtensions-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "botId": "{string}",
  "composeExtensionType": "botBased | apiBased",
  "authorization": {
    "authType": "none | apiSecretServiceAuth | microsoftEntra | oAuth2.0",
    "microsoftEntraConfiguration": {
      microsoftEntraConfiguration object
    },
    "apiSecretServiceAuthConfiguration": {
      apiSecretServiceAuthConfiguration object
    },
    "oAuthConfiguration": {
      oAuthConfiguration object
    }
  },
  "apiSpecificationFile": "{string}",
  "canUpdateConfiguration": boolean | null,
  "commands": [
    {
      "id": "{string}",
      "type": "query | action",
      "triggers": [
        "slash"
      ],
      "samplePrompts": [
        {
          samplePrompts object
        }
      ],
      "apiResponseRenderingTemplateFile": "{string}",
      "context": [
        "compose | commandBox | message"
      ],
      "title": "{string}",
      "description": "{string}",
      "initialRun": {boolean},
      "fetchTask": {boolean},
      "parameters": [
        {
          parameters object
        }
      ],
      "taskInfo": {
        taskInfo object
      },
      "semanticDescription": "{string}"
    }
  ],
  "messageHandlers": [
    {
      "type": "link",
      "value": {
        value object
      }
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
    "id": {
      "type": "string",
      "description": "A unique identifier for the compose extension.",
      "maxLength": 64
    },
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot powering the compose extension in the Bot Framework portal (https://dev.botframework.com/bots)"
    },
    "composeExtensionType": {
      "type": "string",
      "enum": [
        "botBased",
        "apiBased"
      ],
      "description": "Type of the compose extension."
    },
    "authorization": {
      "type": "object",
      "description": "Object capturing authorization information.",
      "properties": {
        "authType": {
          "type": "string",
          "enum": [
            "none",
            "apiSecretServiceAuth",
            "microsoftEntra",
            "oAuth2.0"
          ],
          "description": "Enum of possible authorization types."
        },
        "microsoftEntraConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do microsoftEntra auth flow. It will be only present when auth type is microsoftEntra.",
          "properties": {
            "supportsSingleSignOn": {
              "type": "boolean",
              "default": false,
              "description": "Boolean indicating whether single sign on is configured for the app."
            }
          },
          "additionalProperties": false
        },
        "apiSecretServiceAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do service auth. It will be only present when auth type is apiSecretServiceAuth.",
          "properties": {
            "apiSecretRegistrationId": {
              "type": "string",
              "description": "Registration id returned when developer submits the api key through Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        },
        "oAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to match the application\u0027s OAuth configuration for the app. This should be and must be populated only when authType is set to oAuth2.0r",
          "properties": {
            "oAuthConfigurationId": {
              "type": "string",
              "description": "The oAuth configuration id obtained by the Developer when registering their configuration in Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        }
      },
      "additionalProperties": false
    },
    "apiSpecificationFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to the api specification file in the manifest package."
    },
    "canUpdateConfiguration": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "A value indicating whether the configuration of a compose extension can be updated by the user.",
      "default": "null"
    },
    "commands": {
      "type": "array",
      "maxItems": 10,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "type": "string",
            "description": "Id of the command.",
            "maxLength": 64
          },
          "type": {
            "type": "string",
            "enum": [
              "query",
              "action"
            ],
            "description": "Type of the command",
            "default": "query"
          },
          "triggers": {
            "type": "array",
            "maxItems": 1,
            "items": {
              "type": "string",
              "enum": [
                "slash"
              ]
            },
            "description": "Adding \u0022slash\u0022 to the array makes the command appear in the / slash commands list in group chat or channel. Note: \u0022mention\u0022 is not a valid value for composeExtension command triggers \u2014 it applies only to bots[].commandLists[]."
          },
          "samplePrompts": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "text": {
                  "type": "string",
                  "description": "This string will hold the sample prompt",
                  "maxLength": 128
                }
              },
              "required": [
                "text"
              ]
            }
          },
          "apiResponseRenderingTemplateFile": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path for api response rendering template file. The schema of the file can be referred to in this link:\u0027https://developer.microsoft.com/json-schemas/teams/vDevPreview/MicrosoftTeams.ResponseRenderingTemplate.schema.json\u0027."
          },
          "context": {
            "type": "array",
            "maxItems": 3,
            "items": {
              "enum": [
                "compose",
                "commandBox",
                "message"
              ]
            },
            "description": "Context where the command would apply",
            "default": [
              "compose",
              "commandBox"
            ]
          },
          "title": {
            "type": "string",
            "description": "Title of the command.",
            "maxLength": 32
          },
          "description": {
            "type": "string",
            "description": "Description of the command.",
            "maxLength": 128
          },
          "initialRun": {
            "type": "boolean",
            "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
            "default": false
          },
          "fetchTask": {
            "type": "boolean",
            "description": "A boolean value that indicates if it should fetch task module dynamically",
            "default": false
          },
          "parameters": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "name": {
                  "type": "string",
                  "description": "Name of the parameter.",
                  "maxLength": 64
                },
                "inputType": {
                  "type": "string",
                  "enum": [
                    "text",
                    "textarea",
                    "number",
                    "date",
                    "time",
                    "toggle",
                    "choiceset"
                  ],
                  "description": "Type of the parameter",
                  "default": "text"
                },
                "isRequired": {
                  "type": "boolean",
                  "description": "Indicates whether this parameter is required or not. By default, it is not."
                },
                "title": {
                  "type": "string",
                  "description": "Title of the parameter.",
                  "maxLength": 32
                },
                "description": {
                  "type": "string",
                  "description": "Description of the parameter.",
                  "maxLength": 128
                },
                "value": {
                  "type": "string",
                  "description": "Initial value for the parameter",
                  "maxLength": 512
                },
                "choices": {
                  "type": "array",
                  "maxItems": 10,
                  "description": "The choice options for the parameter",
                  "items": {
                    "type": "object",
                    "properties": {
                      "title": {
                        "type": "string",
                        "description": "Title of the choice",
                        "maxLength": 128
                      },
                      "value": {
                        "type": "string",
                        "description": "Value of the choice",
                        "maxLength": 512
                      }
                    },
                    "additionalProperties": false,
                    "required": [
                      "title",
                      "value"
                    ]
                  }
                },
                "semanticDescription": {
                  "type": "string",
                  "description": "semantic description of the parameter. This is typically meant for consumption by the large language model.",
                  "maxLength": 2000
                }
              },
              "required": [
                "name",
                "title"
              ]
            }
          },
          "taskInfo": {
            "$ref": "#/definitions/taskInfo",
            "description": "Task module to be launched when fetch task set to false."
          },
          "semanticDescription": {
            "type": "string",
            "description": "semantic description of the command. This is typically meant for consumption by the large language model.",
            "maxLength": 5000
          }
        },
        "required": [
          "id",
          "title"
        ]
      }
    },
    "messageHandlers": {
      "type": "array",
      "maxItems": 5,
      "description": "A list of handlers that allow apps to be invoked when certain conditions are met",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet",
      "description": "The set of requirements for the compose extension."
    }
  }
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "botId": "{string}",
  "composeExtensionType": "botBased | apiBased",
  "authorization": {
    "authType": "none | apiSecretServiceAuth | microsoftEntra | oAuth2.0",
    "microsoftEntraConfiguration": {
      microsoftEntraConfiguration object
    },
    "apiSecretServiceAuthConfiguration": {
      apiSecretServiceAuthConfiguration object
    },
    "oAuthConfiguration": {
      oAuthConfiguration object
    }
  },
  "apiSpecificationFile": "{string}",
  "canUpdateConfiguration": boolean | null,
  "commands": [
    {
      "id": "{string}",
      "type": "query | action",
      "triggers": [
        "slash"
      ],
      "samplePrompts": [
        {
          samplePrompts object
        }
      ],
      "apiResponseRenderingTemplateFile": "{string}",
      "context": [
        "compose | commandBox | message"
      ],
      "title": "{string}",
      "description": "{string}",
      "initialRun": {boolean},
      "fetchTask": {boolean},
      "parameters": [
        {
          parameters object
        }
      ],
      "taskInfo": {
        taskInfo object
      },
      "semanticDescription": "{string}"
    }
  ],
  "messageHandlers": [
    {
      "type": "link",
      "value": {
        value object
      }
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
    "id": {
      "type": "string",
      "description": "A unique identifier for the compose extension.",
      "maxLength": 64
    },
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot powering the compose extension in the Bot Framework portal (https://dev.botframework.com/bots)"
    },
    "composeExtensionType": {
      "type": "string",
      "enum": [
        "botBased",
        "apiBased"
      ],
      "default": "botBased",
      "description": "Type of the compose extension."
    },
    "authorization": {
      "type": "object",
      "description": "Object capturing authorization information.",
      "properties": {
        "authType": {
          "type": "string",
          "enum": [
            "none",
            "apiSecretServiceAuth",
            "microsoftEntra",
            "oAuth2.0"
          ],
          "description": "Enum of possible authentication types."
        },
        "microsoftEntraConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do single aad auth flow. It will be only present when auth type is entraId.",
          "properties": {
            "supportsSingleSignOn": {
              "type": "boolean",
              "default": false,
              "description": "Boolean indicating whether single sign on is configured for the app."
            }
          },
          "additionalProperties": false
        },
        "apiSecretServiceAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do service auth. It will be only present when auth type is apiSecretServiceAuth.",
          "properties": {
            "apiSecretRegistrationId": {
              "type": "string",
              "description": "Registration id returned when developer submits the api key through Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        },
        "oAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to match the application\u0027s OAuth configuration for the app. This should be and must be populated only when authType is set to oAuth2.0r",
          "properties": {
            "oAuthConfigurationId": {
              "type": "string",
              "description": "The oAuth configuration id obtained by the Developer when registering their configuration in Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        }
      },
      "additionalProperties": false
    },
    "apiSpecificationFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to the api specification file in the manifest package."
    },
    "canUpdateConfiguration": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "A value indicating whether the configuration of a compose extension can be updated by the user.",
      "default": "null"
    },
    "commands": {
      "type": "array",
      "maxItems": 10,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "type": "string",
            "description": "Id of the command.",
            "maxLength": 64
          },
          "type": {
            "type": "string",
            "enum": [
              "query",
              "action"
            ],
            "description": "Type of the command",
            "default": "query"
          },
          "triggers": {
            "type": "array",
            "maxItems": 1,
            "items": {
              "type": "string",
              "enum": [
                "slash"
              ]
            },
            "description": "Adding \u0022slash\u0022 to the array makes the command appear in the / slash commands list in group chat or channel. Note: \u0022mention\u0022 is not a valid value for composeExtension command triggers \u2014 it applies only to bots[].commandLists[]."
          },
          "samplePrompts": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "text": {
                  "type": "string",
                  "description": "This string will hold the sample prompt",
                  "maxLength": 128
                }
              },
              "required": [
                "text"
              ]
            }
          },
          "apiResponseRenderingTemplateFile": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path for api response rendering template file."
          },
          "context": {
            "type": "array",
            "maxItems": 3,
            "items": {
              "enum": [
                "compose",
                "commandBox",
                "message"
              ]
            },
            "description": "Context where the command would apply",
            "default": [
              "compose",
              "commandBox"
            ]
          },
          "title": {
            "type": "string",
            "description": "Title of the command.",
            "maxLength": 32
          },
          "description": {
            "type": "string",
            "description": "Description of the command.",
            "maxLength": 128
          },
          "initialRun": {
            "type": "boolean",
            "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
            "default": false
          },
          "fetchTask": {
            "type": "boolean",
            "description": "A boolean value that indicates if it should fetch task module dynamically",
            "default": false
          },
          "parameters": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "name": {
                  "type": "string",
                  "description": "Name of the parameter.",
                  "maxLength": 64
                },
                "inputType": {
                  "type": "string",
                  "enum": [
                    "text",
                    "textarea",
                    "number",
                    "date",
                    "time",
                    "toggle",
                    "choiceset"
                  ],
                  "description": "Type of the parameter",
                  "default": "text"
                },
                "title": {
                  "type": "string",
                  "description": "Title of the parameter.",
                  "maxLength": 32
                },
                "description": {
                  "type": "string",
                  "description": "Description of the parameter.",
                  "maxLength": 128
                },
                "isRequired": {
                  "type": "boolean",
                  "description": "The value indicates if this parameter is a required field.",
                  "default": false
                },
                "value": {
                  "type": "string",
                  "description": "Initial value for the parameter",
                  "maxLength": 512
                },
                "choices": {
                  "type": "array",
                  "maxItems": 10,
                  "description": "The choice options for the parameter",
                  "items": {
                    "type": "object",
                    "properties": {
                      "title": {
                        "type": "string",
                        "description": "Title of the choice",
                        "maxLength": 128
                      },
                      "value": {
                        "type": "string",
                        "description": "Value of the choice",
                        "maxLength": 512
                      }
                    },
                    "additionalProperties": false,
                    "required": [
                      "title",
                      "value"
                    ]
                  }
                },
                "semanticDescription": {
                  "type": "string",
                  "description": "Semantic description for the parameter.",
                  "maxLength": 2000
                }
              },
              "required": [
                "name",
                "title"
              ]
            }
          },
          "taskInfo": {
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
          },
          "semanticDescription": {
            "type": "string",
            "description": "Semantic description for the command.",
            "maxLength": 5000
          }
        },
        "required": [
          "id",
          "title"
        ]
      }
    },
    "messageHandlers": {
      "type": "array",
      "maxItems": 5,
      "description": "A list of handlers that allow apps to be invoked when certain conditions are met",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    }
  }
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "id": "{string}",
  "botId": "{string}",
  "composeExtensionType": "botBased | apiBased",
  "authorization": {
    "authType": "none | apiSecretServiceAuth | microsoftEntra | oAuth2.0",
    "microsoftEntraConfiguration": {
      microsoftEntraConfiguration object
    },
    "apiSecretServiceAuthConfiguration": {
      apiSecretServiceAuthConfiguration object
    },
    "oAuthConfiguration": {
      oAuthConfiguration object
    }
  },
  "apiSpecificationFile": "{string}",
  "canUpdateConfiguration": boolean | null,
  "commands": [
    {
      "id": "{string}",
      "type": "query | action",
      "triggers": [
        "slash"
      ],
      "samplePrompts": [
        {
          samplePrompts object
        }
      ],
      "apiResponseRenderingTemplateFile": "{string}",
      "context": [
        "compose | commandBox | message"
      ],
      "title": "{string}",
      "description": "{string}",
      "initialRun": {boolean},
      "fetchTask": {boolean},
      "parameters": [
        {
          parameters object
        }
      ],
      "taskInfo": {
        taskInfo object
      },
      "semanticDescription": "{string}"
    }
  ],
  "messageHandlers": [
    {
      "type": "link",
      "value": {
        value object
      }
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
    "id": {
      "type": "string",
      "description": "A unique identifier for the compose extension.",
      "maxLength": 64
    },
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot powering the compose extension in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "composeExtensionType": {
      "type": "string",
      "enum": [
        "botBased",
        "apiBased"
      ],
      "default": "botBased",
      "description": "Type of the compose extension."
    },
    "authorization": {
      "type": "object",
      "description": "Object capturing authorization information.",
      "properties": {
        "authType": {
          "type": "string",
          "enum": [
            "none",
            "apiSecretServiceAuth",
            "microsoftEntra",
            "oAuth2.0"
          ],
          "description": "Enum of possible authentication types."
        },
        "microsoftEntraConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do single aad auth flow. It will be only present when auth type is entraId.",
          "properties": {
            "supportsSingleSignOn": {
              "type": "boolean",
              "default": false,
              "description": "Boolean indicating whether single sign on is configured for the app."
            }
          },
          "additionalProperties": false
        },
        "apiSecretServiceAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do service auth. It will be only present when auth type is apiSecretServiceAuth.",
          "properties": {
            "apiSecretRegistrationId": {
              "type": "string",
              "description": "Registration id returned when developer submits the api key through Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        },
        "oAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to match the application\u0027s OAuth configuration for the app. This should be and must be populated only when authType is set to oAuth2.0r",
          "properties": {
            "oAuthConfigurationId": {
              "type": "string",
              "description": "The oAuth configuration id obtained by the Developer when registering their configuration in Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        }
      },
      "additionalProperties": false
    },
    "apiSpecificationFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to the api specification file in the manifest package."
    },
    "canUpdateConfiguration": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "A value indicating whether the configuration of a compose extension can be updated by the user.",
      "default": "null"
    },
    "commands": {
      "type": "array",
      "maxItems": 10,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "type": "string",
            "description": "Id of the command.",
            "maxLength": 64
          },
          "type": {
            "type": "string",
            "enum": [
              "query",
              "action"
            ],
            "description": "Type of the command",
            "default": "query"
          },
          "triggers": {
            "type": "array",
            "maxItems": 1,
            "items": {
              "type": "string",
              "enum": [
                "slash"
              ]
            },
            "description": "Adding \u0022slash\u0022 to the array makes the command appear in the / slash commands list in group chat or channel. Note: \u0022mention\u0022 is not a valid value for composeExtension command triggers \u2014 it applies only to bots[].commandLists[]."
          },
          "samplePrompts": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "text": {
                  "type": "string",
                  "description": "This string will hold the sample prompt",
                  "maxLength": 128
                }
              },
              "required": [
                "text"
              ]
            }
          },
          "apiResponseRenderingTemplateFile": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path for api response rendering template file."
          },
          "context": {
            "type": "array",
            "maxItems": 3,
            "items": {
              "enum": [
                "compose",
                "commandBox",
                "message"
              ]
            },
            "description": "Context where the command would apply",
            "default": [
              "compose",
              "commandBox"
            ]
          },
          "title": {
            "type": "string",
            "description": "Title of the command.",
            "maxLength": 32
          },
          "description": {
            "type": "string",
            "description": "Description of the command.",
            "maxLength": 128
          },
          "initialRun": {
            "type": "boolean",
            "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
            "default": false
          },
          "fetchTask": {
            "type": "boolean",
            "description": "A boolean value that indicates if it should fetch task module dynamically",
            "default": false
          },
          "parameters": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "name": {
                  "type": "string",
                  "description": "Name of the parameter.",
                  "maxLength": 64
                },
                "inputType": {
                  "type": "string",
                  "enum": [
                    "text",
                    "textarea",
                    "number",
                    "date",
                    "time",
                    "toggle",
                    "choiceset"
                  ],
                  "description": "Type of the parameter",
                  "default": "text"
                },
                "title": {
                  "type": "string",
                  "description": "Title of the parameter.",
                  "maxLength": 32
                },
                "description": {
                  "type": "string",
                  "description": "Description of the parameter.",
                  "maxLength": 128
                },
                "isRequired": {
                  "type": "boolean",
                  "description": "The value indicates if this parameter is a required field.",
                  "default": false
                },
                "value": {
                  "type": "string",
                  "description": "Initial value for the parameter",
                  "maxLength": 512
                },
                "choices": {
                  "type": "array",
                  "maxItems": 10,
                  "description": "The choice options for the parameter",
                  "items": {
                    "type": "object",
                    "properties": {
                      "title": {
                        "type": "string",
                        "description": "Title of the choice",
                        "maxLength": 128
                      },
                      "value": {
                        "type": "string",
                        "description": "Value of the choice",
                        "maxLength": 512
                      }
                    },
                    "additionalProperties": false,
                    "required": [
                      "title",
                      "value"
                    ]
                  }
                },
                "semanticDescription": {
                  "type": "string",
                  "description": "Semantic description for the parameter.",
                  "maxLength": 2000
                }
              },
              "required": [
                "name",
                "title"
              ]
            }
          },
          "taskInfo": {
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
          },
          "semanticDescription": {
            "type": "string",
            "description": "Semantic description for the command.",
            "maxLength": 5000
          }
        },
        "required": [
          "id",
          "title"
        ]
      }
    },
    "messageHandlers": {
      "type": "array",
      "maxItems": 5,
      "description": "A list of handlers that allow apps to be invoked when certain conditions are met",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    }
  }
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "id": "{string}",
  "botId": "{string}",
  "composeExtensionType": "botBased | apiBased",
  "authorization": {
    "authType": "none | apiSecretServiceAuth | microsoftEntra | oAuth2.0",
    "microsoftEntraConfiguration": {
      microsoftEntraConfiguration object
    },
    "apiSecretServiceAuthConfiguration": {
      apiSecretServiceAuthConfiguration object
    },
    "oAuthConfiguration": {
      oAuthConfiguration object
    }
  },
  "apiSpecificationFile": "{string}",
  "canUpdateConfiguration": boolean | null,
  "commands": [
    {
      "id": "{string}",
      "type": "query | action",
      "samplePrompts": [
        {
          samplePrompts object
        }
      ],
      "apiResponseRenderingTemplateFile": "{string}",
      "context": [
        "compose | commandBox | message"
      ],
      "title": "{string}",
      "description": "{string}",
      "initialRun": {boolean},
      "fetchTask": {boolean},
      "parameters": [
        {
          parameters object
        }
      ],
      "taskInfo": {
        taskInfo object
      },
      "semanticDescription": "{string}"
    }
  ],
  "messageHandlers": [
    {
      "type": "link",
      "value": {
        value object
      }
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
    "id": {
      "type": "string",
      "description": "A unique identifier for the compose extension.",
      "maxLength": 64
    },
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot powering the compose extension in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "composeExtensionType": {
      "type": "string",
      "enum": [
        "botBased",
        "apiBased"
      ],
      "default": "botBased",
      "description": "Type of the compose extension."
    },
    "authorization": {
      "type": "object",
      "description": "Object capturing authorization information.",
      "properties": {
        "authType": {
          "type": "string",
          "enum": [
            "none",
            "apiSecretServiceAuth",
            "microsoftEntra",
            "oAuth2.0"
          ],
          "description": "Enum of possible authentication types."
        },
        "microsoftEntraConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do single aad auth flow. It will be only present when auth type is entraId.",
          "properties": {
            "supportsSingleSignOn": {
              "type": "boolean",
              "default": false,
              "description": "Boolean indicating whether single sign on is configured for the app."
            }
          },
          "additionalProperties": false
        },
        "apiSecretServiceAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do service auth. It will be only present when auth type is apiSecretServiceAuth.",
          "properties": {
            "apiSecretRegistrationId": {
              "type": "string",
              "description": "Registration id returned when developer submits the api key through Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        },
        "oAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to match the application\u0027s OAuth configuration for the app. This should be and must be populated only when authType is set to oAuth2.0r",
          "properties": {
            "oAuthConfigurationId": {
              "type": "string",
              "description": "The oAuth configuration id obtained by the Developer when registering their configuration in Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        }
      },
      "additionalProperties": false
    },
    "apiSpecificationFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to the api specification file in the manifest package."
    },
    "canUpdateConfiguration": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "A value indicating whether the configuration of a compose extension can be updated by the user.",
      "default": "null"
    },
    "commands": {
      "type": "array",
      "maxItems": 10,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "type": "string",
            "description": "Id of the command.",
            "maxLength": 64
          },
          "type": {
            "type": "string",
            "enum": [
              "query",
              "action"
            ],
            "description": "Type of the command",
            "default": "query"
          },
          "samplePrompts": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "text": {
                  "type": "string",
                  "description": "This string will hold the sample prompt",
                  "maxLength": 128
                }
              },
              "required": [
                "text"
              ]
            }
          },
          "apiResponseRenderingTemplateFile": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path for api response rendering template file."
          },
          "context": {
            "type": "array",
            "maxItems": 3,
            "items": {
              "enum": [
                "compose",
                "commandBox",
                "message"
              ]
            },
            "description": "Context where the command would apply",
            "default": [
              "compose",
              "commandBox"
            ]
          },
          "title": {
            "type": "string",
            "description": "Title of the command.",
            "maxLength": 32
          },
          "description": {
            "type": "string",
            "description": "Description of the command.",
            "maxLength": 128
          },
          "initialRun": {
            "type": "boolean",
            "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
            "default": false
          },
          "fetchTask": {
            "type": "boolean",
            "description": "A boolean value that indicates if it should fetch task module dynamically",
            "default": false
          },
          "parameters": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "name": {
                  "type": "string",
                  "description": "Name of the parameter.",
                  "maxLength": 64
                },
                "inputType": {
                  "type": "string",
                  "enum": [
                    "text",
                    "textarea",
                    "number",
                    "date",
                    "time",
                    "toggle",
                    "choiceset"
                  ],
                  "description": "Type of the parameter",
                  "default": "text"
                },
                "title": {
                  "type": "string",
                  "description": "Title of the parameter.",
                  "maxLength": 32
                },
                "description": {
                  "type": "string",
                  "description": "Description of the parameter.",
                  "maxLength": 128
                },
                "isRequired": {
                  "type": "boolean",
                  "description": "The value indicates if this parameter is a required field.",
                  "default": false
                },
                "value": {
                  "type": "string",
                  "description": "Initial value for the parameter",
                  "maxLength": 512
                },
                "choices": {
                  "type": "array",
                  "maxItems": 10,
                  "description": "The choice options for the parameter",
                  "items": {
                    "type": "object",
                    "properties": {
                      "title": {
                        "type": "string",
                        "description": "Title of the choice",
                        "maxLength": 128
                      },
                      "value": {
                        "type": "string",
                        "description": "Value of the choice",
                        "maxLength": 512
                      }
                    },
                    "additionalProperties": false,
                    "required": [
                      "title",
                      "value"
                    ]
                  }
                },
                "semanticDescription": {
                  "type": "string",
                  "description": "Semantic description for the parameter.",
                  "maxLength": 2000
                }
              },
              "required": [
                "name",
                "title"
              ]
            }
          },
          "taskInfo": {
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
          },
          "semanticDescription": {
            "type": "string",
            "description": "Semantic description for the command.",
            "maxLength": 5000
          }
        },
        "required": [
          "id",
          "title"
        ]
      }
    },
    "messageHandlers": {
      "type": "array",
      "maxItems": 5,
      "description": "A list of handlers that allow apps to be invoked when certain conditions are met",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    }
  }
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

```json
{
  "id": "{string}",
  "botId": "{string}",
  "composeExtensionType": "botBased | apiBased",
  "authorization": {
    "authType": "none | apiSecretServiceAuth | microsoftEntra | oAuth2.0",
    "microsoftEntraConfiguration": {
      microsoftEntraConfiguration object
    },
    "apiSecretServiceAuthConfiguration": {
      apiSecretServiceAuthConfiguration object
    },
    "oAuthConfiguration": {
      oAuthConfiguration object
    }
  },
  "apiSpecificationFile": "{string}",
  "canUpdateConfiguration": boolean | null,
  "commands": [
    {
      "id": "{string}",
      "type": "query | action",
      "samplePrompts": [
        {
          samplePrompts object
        }
      ],
      "apiResponseRenderingTemplateFile": "{string}",
      "context": [
        "compose | commandBox | message"
      ],
      "title": "{string}",
      "description": "{string}",
      "initialRun": {boolean},
      "fetchTask": {boolean},
      "parameters": [
        {
          parameters object
        }
      ],
      "taskInfo": {
        taskInfo object
      },
      "semanticDescription": "{string}"
    }
  ],
  "messageHandlers": [
    {
      "type": "link",
      "value": {
        value object
      }
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
    "id": {
      "type": "string",
      "description": "A unique identifier for the compose extension.",
      "maxLength": 64
    },
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot powering the compose extension in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "composeExtensionType": {
      "type": "string",
      "enum": [
        "botBased",
        "apiBased"
      ],
      "default": "botBased",
      "description": "Type of the compose extension."
    },
    "authorization": {
      "type": "object",
      "description": "Object capturing authorization information.",
      "properties": {
        "authType": {
          "type": "string",
          "enum": [
            "none",
            "apiSecretServiceAuth",
            "microsoftEntra",
            "oAuth2.0"
          ],
          "description": "Enum of possible authentication types."
        },
        "microsoftEntraConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do single aad auth flow. It will be only present when auth type is entraId.",
          "properties": {
            "supportsSingleSignOn": {
              "type": "boolean",
              "default": false,
              "description": "Boolean indicating whether single sign on is configured for the app."
            }
          },
          "additionalProperties": false
        },
        "apiSecretServiceAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do service auth. It will be only present when auth type is apiSecretServiceAuth.",
          "properties": {
            "apiSecretRegistrationId": {
              "type": "string",
              "description": "Registration id returned when developer submits the api key through Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        },
        "oAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to match the application\u0027s OAuth configuration for the app. This should be and must be populated only when authType is set to oAuth2.0r",
          "properties": {
            "oAuthConfigurationId": {
              "type": "string",
              "description": "The oAuth configuration id obtained by the Developer when registering their configuration in Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        }
      },
      "additionalProperties": false
    },
    "apiSpecificationFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to the api specification file in the manifest package."
    },
    "canUpdateConfiguration": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "A value indicating whether the configuration of a compose extension can be updated by the user.",
      "default": "null"
    },
    "commands": {
      "type": "array",
      "maxItems": 10,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "type": "string",
            "description": "Id of the command.",
            "maxLength": 64
          },
          "type": {
            "type": "string",
            "enum": [
              "query",
              "action"
            ],
            "description": "Type of the command",
            "default": "query"
          },
          "samplePrompts": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "text": {
                  "type": "string",
                  "description": "This string will hold the sample prompt",
                  "maxLength": 128
                }
              },
              "required": [
                "text"
              ]
            }
          },
          "apiResponseRenderingTemplateFile": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path for api response rendering template file."
          },
          "context": {
            "type": "array",
            "maxItems": 3,
            "items": {
              "enum": [
                "compose",
                "commandBox",
                "message"
              ]
            },
            "description": "Context where the command would apply",
            "default": [
              "compose",
              "commandBox"
            ]
          },
          "title": {
            "type": "string",
            "description": "Title of the command.",
            "maxLength": 32
          },
          "description": {
            "type": "string",
            "description": "Description of the command.",
            "maxLength": 128
          },
          "initialRun": {
            "type": "boolean",
            "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
            "default": false
          },
          "fetchTask": {
            "type": "boolean",
            "description": "A boolean value that indicates if it should fetch task module dynamically",
            "default": false
          },
          "parameters": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "name": {
                  "type": "string",
                  "description": "Name of the parameter.",
                  "maxLength": 64
                },
                "inputType": {
                  "type": "string",
                  "enum": [
                    "text",
                    "textarea",
                    "number",
                    "date",
                    "time",
                    "toggle",
                    "choiceset"
                  ],
                  "description": "Type of the parameter",
                  "default": "text"
                },
                "title": {
                  "type": "string",
                  "description": "Title of the parameter.",
                  "maxLength": 32
                },
                "description": {
                  "type": "string",
                  "description": "Description of the parameter.",
                  "maxLength": 128
                },
                "isRequired": {
                  "type": "boolean",
                  "description": "The value indicates if this parameter is a required field.",
                  "default": false
                },
                "value": {
                  "type": "string",
                  "description": "Initial value for the parameter",
                  "maxLength": 512
                },
                "choices": {
                  "type": "array",
                  "maxItems": 10,
                  "description": "The choice options for the parameter",
                  "items": {
                    "type": "object",
                    "properties": {
                      "title": {
                        "type": "string",
                        "description": "Title of the choice",
                        "maxLength": 128
                      },
                      "value": {
                        "type": "string",
                        "description": "Value of the choice",
                        "maxLength": 512
                      }
                    },
                    "additionalProperties": false,
                    "required": [
                      "title",
                      "value"
                    ]
                  }
                },
                "semanticDescription": {
                  "type": "string",
                  "description": "Semantic description for the parameter.",
                  "maxLength": 2000
                }
              },
              "required": [
                "name",
                "title"
              ]
            }
          },
          "taskInfo": {
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
          },
          "semanticDescription": {
            "type": "string",
            "description": "Semantic description for the command.",
            "maxLength": 5000
          }
        },
        "required": [
          "id",
          "title"
        ]
      }
    },
    "messageHandlers": {
      "type": "array",
      "maxItems": 5,
      "description": "A list of handlers that allow apps to be invoked when certain conditions are met",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    }
  }
}
```

- [Syntax](#tabpanel_6_syntax)
- [Schema](#tabpanel_6_schema)

```json
{
  "id": "{string}",
  "botId": "{string}",
  "composeExtensionType": "botBased | apiBased",
  "authorization": {
    "authType": "none | apiSecretServiceAuth | microsoftEntra",
    "microsoftEntraConfiguration": {
      microsoftEntraConfiguration object
    },
    "apiSecretServiceAuthConfiguration": {
      apiSecretServiceAuthConfiguration object
    }
  },
  "apiSpecificationFile": "{string}",
  "canUpdateConfiguration": boolean | null,
  "commands": [
    {
      "id": "{string}",
      "type": "query | action",
      "samplePrompts": [
        {
          samplePrompts object
        }
      ],
      "apiResponseRenderingTemplateFile": "{string}",
      "context": [
        "compose | commandBox | message"
      ],
      "title": "{string}",
      "description": "{string}",
      "initialRun": {boolean},
      "fetchTask": {boolean},
      "semanticDescription": "{string}",
      "parameters": [
        {
          parameters object
        }
      ],
      "taskInfo": {
        taskInfo object
      }
    }
  ],
  "messageHandlers": [
    {
      "type": "link",
      "value": {
        value object
      }
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
    "id": {
      "type": "string",
      "description": "A unique identifier for the compose extension.",
      "maxLength": 64
    },
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot powering the compose extension in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "composeExtensionType": {
      "type": "string",
      "enum": [
        "botBased",
        "apiBased"
      ],
      "description": "Type of the compose extension.",
      "default": "botBased"
    },
    "authorization": {
      "type": "object",
      "description": "Object capturing authorization information.",
      "properties": {
        "authType": {
          "type": "string",
          "enum": [
            "none",
            "apiSecretServiceAuth",
            "microsoftEntra"
          ],
          "description": "Enum of possible authentication types."
        },
        "microsoftEntraConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do single aad auth flow. It will be only present when auth type is entraId.",
          "properties": {
            "supportsSingleSignOn": {
              "type": "boolean",
              "default": false,
              "description": "Boolean indicating whether single sign on is configured for the app."
            }
          },
          "additionalProperties": false
        },
        "apiSecretServiceAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do service auth. It will be only present when auth type is apiSecretServiceAuth.",
          "properties": {
            "apiSecretRegistrationId": {
              "type": "string",
              "description": "Registration id returned when developer submits the api key through Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        }
      },
      "additionalProperties": false
    },
    "apiSpecificationFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to the api specification file in the manifest package."
    },
    "canUpdateConfiguration": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "A value indicating whether the configuration of a compose extension can be updated by the user.",
      "default": "null"
    },
    "commands": {
      "type": "array",
      "maxItems": 10,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "type": "string",
            "description": "Id of the command.",
            "maxLength": 64
          },
          "type": {
            "type": "string",
            "enum": [
              "query",
              "action"
            ],
            "description": "Type of the command",
            "default": "query"
          },
          "samplePrompts": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "text": {
                  "type": "string",
                  "description": "This string will hold the sample prompt",
                  "maxLength": 128
                }
              },
              "required": [
                "text"
              ]
            }
          },
          "apiResponseRenderingTemplateFile": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path for api response rendering template file."
          },
          "context": {
            "type": "array",
            "maxItems": 3,
            "items": {
              "enum": [
                "compose",
                "commandBox",
                "message"
              ]
            },
            "description": "Context where the command would apply",
            "default": [
              "compose",
              "commandBox"
            ]
          },
          "title": {
            "type": "string",
            "description": "Title of the command.",
            "maxLength": 32
          },
          "description": {
            "type": "string",
            "description": "Description of the command.",
            "maxLength": 128
          },
          "initialRun": {
            "type": "boolean",
            "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
            "default": false
          },
          "fetchTask": {
            "type": "boolean",
            "description": "A boolean value that indicates if it should fetch task module dynamically",
            "default": false
          },
          "semanticDescription": {
            "type": "string",
            "description": "Semantic description for the command.",
            "maxLength": 5000
          },
          "parameters": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "name": {
                  "type": "string",
                  "description": "Name of the parameter.",
                  "maxLength": 64
                },
                "inputType": {
                  "type": "string",
                  "enum": [
                    "text",
                    "textarea",
                    "number",
                    "date",
                    "time",
                    "toggle",
                    "choiceset"
                  ],
                  "description": "Type of the parameter",
                  "default": "text"
                },
                "title": {
                  "type": "string",
                  "description": "Title of the parameter.",
                  "maxLength": 32
                },
                "description": {
                  "type": "string",
                  "description": "Description of the parameter.",
                  "maxLength": 128
                },
                "value": {
                  "type": "string",
                  "description": "Initial value for the parameter",
                  "maxLength": 512
                },
                "isRequired": {
                  "type": "boolean",
                  "description": "The value indicates if this parameter is a required field.",
                  "default": false
                },
                "semanticDescription": {
                  "type": "string",
                  "description": "Semantic description for the parameter.",
                  "maxLength": 2000
                },
                "choices": {
                  "type": "array",
                  "maxItems": 10,
                  "description": "The choice options for the parameter",
                  "items": {
                    "type": "object",
                    "properties": {
                      "title": {
                        "type": "string",
                        "description": "Title of the choice",
                        "maxLength": 128
                      },
                      "value": {
                        "type": "string",
                        "description": "Value of the choice",
                        "maxLength": 512
                      }
                    },
                    "additionalProperties": false,
                    "required": [
                      "title",
                      "value"
                    ]
                  }
                }
              },
              "required": [
                "name",
                "title"
              ]
            }
          },
          "taskInfo": {
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
        },
        "required": [
          "id",
          "title"
        ]
      }
    },
    "messageHandlers": {
      "type": "array",
      "maxItems": 5,
      "description": "A list of handlers that allow apps to be invoked when certain conditions are met",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    }
  }
}
```

- [Syntax](#tabpanel_7_syntax)
- [Schema](#tabpanel_7_schema)

```json
{
  "id": "{string}",
  "botId": "{string}",
  "composeExtensionType": "botBased | apiBased",
  "authorization": {
    "authType": "none | apiSecretServiceAuth | microsoftEntra",
    "microsoftEntraConfiguration": {
      microsoftEntraConfiguration object
    },
    "apiSecretServiceAuthConfiguration": {
      apiSecretServiceAuthConfiguration object
    }
  },
  "apiSpecificationFile": "{string}",
  "canUpdateConfiguration": boolean | null,
  "commands": [
    {
      "id": "{string}",
      "type": "query | action",
      "samplePrompts": [
        {
          samplePrompts object
        }
      ],
      "apiResponseRenderingTemplateFile": "{string}",
      "context": [
        "compose | commandBox | message"
      ],
      "title": "{string}",
      "description": "{string}",
      "initialRun": {boolean},
      "fetchTask": {boolean},
      "semanticDescription": "{string}",
      "parameters": [
        {
          parameters object
        }
      ],
      "taskInfo": {
        taskInfo object
      }
    }
  ],
  "messageHandlers": [
    {
      "type": "link",
      "value": {
        value object
      }
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
    "id": {
      "type": "string",
      "description": "A unique identifier for the compose extension.",
      "maxLength": 64
    },
    "botId": {
      "$ref": "#/definitions/guid",
      "description": "The Microsoft App ID specified for the bot powering the compose extension in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "composeExtensionType": {
      "type": "string",
      "enum": [
        "botBased",
        "apiBased"
      ],
      "description": "Type of the compose extension."
    },
    "authorization": {
      "type": "object",
      "description": "Object capturing authorization information.",
      "properties": {
        "authType": {
          "type": "string",
          "enum": [
            "none",
            "apiSecretServiceAuth",
            "microsoftEntra"
          ],
          "description": "Enum of possible authentication types."
        },
        "microsoftEntraConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do single aad auth flow. It will be only present when auth type is entraId.",
          "properties": {
            "supportsSingleSignOn": {
              "type": "boolean",
              "default": false,
              "description": "Boolean indicating whether single sign on is configured for the app."
            }
          },
          "additionalProperties": false
        },
        "apiSecretServiceAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do service auth. It will be only present when auth type is apiSecretServiceAuth.",
          "properties": {
            "apiSecretRegistrationId": {
              "type": "string",
              "description": "Registration id returned when developer submits the api key through Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        }
      },
      "additionalProperties": false
    },
    "apiSpecificationFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to the api specification file in the manifest package."
    },
    "canUpdateConfiguration": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "A value indicating whether the configuration of a compose extension can be updated by the user.",
      "default": "null"
    },
    "commands": {
      "type": "array",
      "maxItems": 10,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "type": "string",
            "description": "Id of the command.",
            "maxLength": 64
          },
          "type": {
            "type": "string",
            "enum": [
              "query",
              "action"
            ],
            "description": "Type of the command",
            "default": "query"
          },
          "samplePrompts": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "text": {
                  "type": "string",
                  "description": "This string will hold the sample prompt",
                  "maxLength": 128
                }
              },
              "required": [
                "text"
              ]
            }
          },
          "apiResponseRenderingTemplateFile": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path for api response rendering template file."
          },
          "context": {
            "type": "array",
            "maxItems": 3,
            "items": {
              "enum": [
                "compose",
                "commandBox",
                "message"
              ]
            },
            "description": "Context where the command would apply",
            "default": [
              "compose",
              "commandBox"
            ]
          },
          "title": {
            "type": "string",
            "description": "Title of the command.",
            "maxLength": 32
          },
          "description": {
            "type": "string",
            "description": "Description of the command.",
            "maxLength": 128
          },
          "initialRun": {
            "type": "boolean",
            "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
            "default": false
          },
          "fetchTask": {
            "type": "boolean",
            "description": "A boolean value that indicates if it should fetch task module dynamically",
            "default": false
          },
          "semanticDescription": {
            "type": "string",
            "description": "Semantic description for the command.",
            "maxLength": 5000
          },
          "parameters": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "name": {
                  "type": "string",
                  "description": "Name of the parameter.",
                  "maxLength": 64
                },
                "inputType": {
                  "type": "string",
                  "enum": [
                    "text",
                    "textarea",
                    "number",
                    "date",
                    "time",
                    "toggle",
                    "choiceset"
                  ],
                  "description": "Type of the parameter",
                  "default": "text"
                },
                "title": {
                  "type": "string",
                  "description": "Title of the parameter.",
                  "maxLength": 32
                },
                "description": {
                  "type": "string",
                  "description": "Description of the parameter.",
                  "maxLength": 128
                },
                "value": {
                  "type": "string",
                  "description": "Initial value for the parameter",
                  "maxLength": 512
                },
                "isRequired": {
                  "type": "boolean",
                  "description": "The value indicates if this parameter is a required field.",
                  "default": false
                },
                "semanticDescription": {
                  "type": "string",
                  "description": "Semantic description for the parameter.",
                  "maxLength": 2000
                },
                "choices": {
                  "type": "array",
                  "maxItems": 10,
                  "description": "The choice options for the parameter",
                  "items": {
                    "type": "object",
                    "properties": {
                      "title": {
                        "type": "string",
                        "description": "Title of the choice",
                        "maxLength": 128
                      },
                      "value": {
                        "type": "string",
                        "description": "Value of the choice",
                        "maxLength": 512
                      }
                    },
                    "additionalProperties": false,
                    "required": [
                      "title",
                      "value"
                    ]
                  }
                }
              },
              "required": [
                "name",
                "title"
              ]
            }
          },
          "taskInfo": {
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
        },
        "required": [
          "id",
          "title"
        ]
      }
    },
    "messageHandlers": {
      "type": "array",
      "maxItems": 5,
      "description": "A list of handlers that allow apps to be invoked when certain conditions are met",
      "items": {
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
    },
    "requirementSet": {
      "$ref": "#/definitions/elementRequirementSet"
    }
  }
}
```

- [Syntax](#tabpanel_8_syntax)
- [Schema](#tabpanel_8_schema)

```json
{
  "botId": "{string}",
  "composeExtensionType": "botBased | apiBased",
  "authorization": {
    "authType": "none | apiSecretServiceAuth | microsoftEntra",
    "microsoftEntraConfiguration": {
      microsoftEntraConfiguration object
    },
    "apiSecretServiceAuthConfiguration": {
      apiSecretServiceAuthConfiguration object
    }
  },
  "apiSpecificationFile": "{string}",
  "canUpdateConfiguration": boolean | null,
  "commands": [
    {
      "id": "{string}",
      "type": "query | action",
      "samplePrompts": [
        {
          samplePrompts object
        }
      ],
      "apiResponseRenderingTemplateFile": "{string}",
      "context": [
        "compose | commandBox | message"
      ],
      "title": "{string}",
      "description": "{string}",
      "initialRun": {boolean},
      "fetchTask": {boolean},
      "semanticDescription": "{string}",
      "parameters": [
        {
          parameters object
        }
      ],
      "taskInfo": {
        taskInfo object
      }
    }
  ],
  "messageHandlers": [
    {
      "type": "link",
      "value": {
        value object
      }
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
      "description": "The Microsoft App ID specified for the bot powering the compose extension in the Bot Framework portal (https://dev.botframework.com/bots)."
    },
    "composeExtensionType": {
      "type": "string",
      "enum": [
        "botBased",
        "apiBased"
      ],
      "description": "Type of the compose extension."
    },
    "authorization": {
      "type": "object",
      "description": "Object capturing authorization information.",
      "properties": {
        "authType": {
          "type": "string",
          "enum": [
            "none",
            "apiSecretServiceAuth",
            "microsoftEntra"
          ],
          "description": "Enum of possible authentication types."
        },
        "microsoftEntraConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do single aad auth flow. It will be only present when auth type is entraId.",
          "properties": {
            "supportsSingleSignOn": {
              "type": "boolean",
              "default": false,
              "description": "Boolean indicating whether single sign on is configured for the app."
            }
          },
          "additionalProperties": false
        },
        "apiSecretServiceAuthConfiguration": {
          "type": "object",
          "description": "Object capturing details needed to do service auth. It will be only present when auth type is apiSecretServiceAuth.",
          "properties": {
            "apiSecretRegistrationId": {
              "type": "string",
              "description": "Registration id returned when developer submits the api key through Developer Portal.",
              "maxLength": 128
            }
          },
          "additionalProperties": false
        }
      },
      "additionalProperties": false
    },
    "apiSpecificationFile": {
      "$ref": "#/definitions/relativePath",
      "description": "A relative file path to the api specification file in the manifest package."
    },
    "canUpdateConfiguration": {
      "type": [
        "boolean",
        "null"
      ],
      "description": "A value indicating whether the configuration of a compose extension can be updated by the user.",
      "default": "null"
    },
    "commands": {
      "type": "array",
      "maxItems": 10,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "id": {
            "type": "string",
            "description": "Id of the command.",
            "maxLength": 64
          },
          "type": {
            "type": "string",
            "enum": [
              "query",
              "action"
            ],
            "description": "Type of the command",
            "default": "query"
          },
          "samplePrompts": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "text": {
                  "type": "string",
                  "description": "This string will hold the sample prompt",
                  "maxLength": 128
                }
              },
              "required": [
                "text"
              ]
            }
          },
          "apiResponseRenderingTemplateFile": {
            "$ref": "#/definitions/relativePath",
            "description": "A relative file path for api response rendering template file."
          },
          "context": {
            "type": "array",
            "maxItems": 3,
            "items": {
              "enum": [
                "compose",
                "commandBox",
                "message"
              ]
            },
            "description": "Context where the command would apply",
            "default": [
              "compose",
              "commandBox"
            ]
          },
          "title": {
            "type": "string",
            "description": "Title of the command.",
            "maxLength": 32
          },
          "description": {
            "type": "string",
            "description": "Description of the command.",
            "maxLength": 128
          },
          "initialRun": {
            "type": "boolean",
            "description": "A boolean value that indicates if the command should be run once initially with no parameter.",
            "default": false
          },
          "fetchTask": {
            "type": "boolean",
            "description": "A boolean value that indicates if it should fetch task module dynamically",
            "default": false
          },
          "semanticDescription": {
            "type": "string",
            "description": "Semantic description for the command.",
            "maxLength": 5000
          },
          "parameters": {
            "type": "array",
            "maxItems": 5,
            "minItems": 1,
            "items": {
              "type": "object",
              "additionalProperties": false,
              "properties": {
                "name": {
                  "type": "string",
                  "description": "Name of the parameter.",
                  "maxLength": 64
                },
                "inputType": {
                  "type": "string",
                  "enum": [
                    "text",
                    "textarea",
                    "number",
                    "date",
                    "time",
                    "toggle",
                    "choiceset"
                  ],
                  "description": "Type of the parameter",
                  "default": "text"
                },
                "title": {
                  "type": "string",
                  "description": "Title of the parameter.",
                  "maxLength": 32
                },
                "description": {
                  "type": "string",
                  "description": "Description of the parameter.",
                  "maxLength": 128
                },
                "value": {
                  "type": "string",
                  "description": "Initial value for the parameter",
                  "maxLength": 512
                },
                "isRequired": {
                  "type": "boolean",
                  "description": "The value indicates if this parameter is a required field.",
                  "default": false
                },
                "semanticDescription": {
                  "type": "string",
                  "description": "Semantic description for the parameter.",
                  "maxLength": 2000
                },
                "choices": {
                  "type": "array",
                  "maxItems": 10,
                  "description": "The choice options for the parameter",
                  "items": {
                    "type": "object",
                    "properties": {
                      "title": {
                        "type": "string",
                        "description": "Title of the choice",
                        "maxLength": 128
                      },
                      "value": {
                        "type": "string",
                        "description": "Value of the choice",
                        "maxLength": 512
                      }
                    },
                    "additionalProperties": false,
                    "required": [
                      "title",
                      "value"
                    ]
                  }
                }
              },
              "required": [
                "name",
                "title"
              ]
            }
          },
          "taskInfo": {
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
        },
        "required": [
          "id",
          "title"
        ]
      }
    },
    "messageHandlers": {
      "type": "array",
      "maxItems": 5,
      "description": "A list of handlers that allow apps to be invoked when certain conditions are met",
      "items": {
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
    }
  }
}
```

## Properties

#### id

A unique identifier for the message extension. Used when defining one-way and mutual app capability dependencies under `elementRelationshipSet`.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### id

A unique identifier for the compose extension.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### botId

The unique Microsoft app ID for the bot that powers the message extension, as registered with the [Bot Framework](https://dev.botframework.com/bots). The ID can be the same as the overall app ID.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
The string value must be a [guid](https://en.wikipedia.org/wiki/Universally_unique_identifier).

#### composeExtensionType

Type of the message extension. Either `botBased` and `apiBased` message extension.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `botBased`, `apiBased`.

#### authorization

Object capturing authorization information for the API-based message extension.

**Type**  
[authorization](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### apiSpecificationFile

A relative file path to the api specification file in the manifest package.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### canUpdateConfiguration

A boolean value indicating whether the configuration of a message extension can be updated by the user.

**Type**  
boolean \| null

**Required**  
—

**Constraints**  


**Supported values**  


#### commands

Array of commands the message extension supports.

**Type**  
Array of [commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 10.

**Supported values**  


#### messageHandlers

A list of handlers that allow apps to be invoked when certain conditions are met. Domains must also be listed in `validDomains`.

**Type**  
Array of [messageHandlers](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-message-handlers?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 5.

**Supported values**  


#### requirementSet

Runtime requirements for the message extension to function properly in the Microsoft 365 host application. If one or more of the requirements aren't supported by the runtime host, the host won't load the message extension.

**Type**  
[elementRequirementSet](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


## Remarks

**Optional** – Array

Note

The name of the feature was changed from "compose extension" to "message extension" in November, 2017, but the app manifest name remains the same so that existing extensions continue to function.

The object is an array \(maximum of 1 element\) with all elements of type `object`. This block is required only for solutions that provide a message extension.

## Examples

```json
{
"composeExtensions": [
        {
            "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
            "id": "composeExtension-id",
            "canUpdateConfiguration": true,
            "commands": [
                {
                    "id": "exampleCmd1",
                    "title": "Example Command",
                    "description": "Command Description; e.g., Search on the web",
                    "initialRun": true,
                    "type": "search",
                    "context": [
                        "compose",
                        "commandBox"
                    ],
                    "parameters": [
                        {
                            "name": "keyword",
                            "title": "Search keywords",
                            "description": "Enter the keywords to search for"
                        }
                    ]
                }
            ],
            "requirementSet": {
                "hostMustSupportFunctionalities": [
                  {"name": "dialogUrl"},
                  {"name": "dialogUrlBot"}
                ]
            }
        }
    ]
}
```
