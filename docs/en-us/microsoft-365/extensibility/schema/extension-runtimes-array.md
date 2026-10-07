<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-array?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# extensionRuntimesArray object

The `extensions.runtimes` array configures the sets of runtimes and actions that an Office add-in or Copilot agent can use. For information about runtimes in Office Add-ins, see [Runtimes in Office Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/runtimes).

Properties that reference this object type:

- [root.extensions.runtimes](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-extensions?view=m365-app-1.30#runtimes-property)

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
  "id": "{string}",
  "type": "general",
  "code": {
    "page": "{string}",
    "script": "{string}"
  },
  "lifetime": "short | long",
  "actions": [
    {
      "id": "{string}",
      "type": "executeFunction | openPage | executeDataFunction",
      "displayName": "{string}",
      "pinnable": {boolean},
      "view": "{string}",
      "multiselect": {boolean},
      "supportsNoItemContext": {boolean},
      "taskpane": {
        taskpane object
      }
    }
  ],
  "customFunctions": {
    "functions": [
      {
        extensionFunction object
      }
    ],
    "namespace": {
      extensionCustomFunctionsNamespace object
    },
    "allowCustomDataForDataTypeAny": {boolean},
    "metadataUrl": "{string}",
    "enums": [
      {
        enum object
      }
    ]
  }
}
```

```json
{
  "type": "object",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "id": {
      "type": "string",
      "description": "A unique identifier for this runtime within the app.  Maximum length is 64 characters.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "general"
      ],
      "default": "general",
      "description": "Supports running functions and launching pages."
    },
    "code": {
      "$ref": "#/definitions/extensionRuntimeCode"
    },
    "lifetime": {
      "type": "string",
      "default": "short",
      "enum": [
        "short",
        "long"
      ],
      "description": "Runtimes with a short lifetime do not preserve state across executions. Runtimes with a long lifetime do."
    },
    "actions": {
      "$ref": "#/definitions/extensionRuntimesActions"
    },
    "customFunctions": {
      "$ref": "#/definitions/extensionCustomFunctions"
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "code"
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
  "id": "{string}",
  "type": "general",
  "code": {
    "page": "{string}",
    "script": "{string}"
  },
  "lifetime": "short | long",
  "actions": [
    {
      "id": "{string}",
      "type": "executeFunction | openPage | executeDataFunction",
      "displayName": "{string}",
      "pinnable": {boolean},
      "view": "{string}",
      "multiselect": {boolean},
      "supportsNoItemContext": {boolean}
    }
  ],
  "customFunctions": {
    "functions": [
      {
        extensionFunction object
      }
    ],
    "namespace": {
      extensionCustomFunctionsNamespace object
    },
    "allowCustomDataForDataTypeAny": {boolean},
    "metadataUrl": "{string}",
    "enums": [
      {
        enum object
      }
    ]
  }
}
```

```json
{
  "type": "object",
  "description": "A runtime environment for a page or script",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "id": {
      "type": "string",
      "description": "A unique identifier for this runtime within the app.  Maximum length is 64 characters.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "general"
      ],
      "default": "general",
      "description": "Supports running functions and launching pages."
    },
    "code": {
      "$ref": "#/definitions/extensionRuntimeCode"
    },
    "lifetime": {
      "type": "string",
      "default": "short",
      "enum": [
        "short",
        "long"
      ],
      "description": "Runtimes with a short lifetime do not preserve state across executions. Runtimes with a long lifetime do."
    },
    "actions": {
      "$ref": "#/definitions/extensionRuntimesActions"
    },
    "customFunctions": {
      "$ref": "#/definitions/extensionCustomFunctions"
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "code"
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
  "id": "{string}",
  "type": "general",
  "code": {
    "page": "{string}",
    "script": "{string}"
  },
  "lifetime": "short | long",
  "actions": [
    {
      "id": "{string}",
      "type": "executeFunction | openPage | executeDataFunction",
      "displayName": "{string}",
      "pinnable": {boolean},
      "view": "{string}",
      "multiselect": {boolean},
      "supportsNoItemContext": {boolean}
    }
  ],
  "customFunctions": {
    "functions": [
      {
        extensionFunction object
      }
    ],
    "namespace": {
      extensionCustomFunctionsNamespace object
    },
    "allowCustomDataForDataTypeAny": {boolean},
    "metadataUrl": "{string}"
  }
}
```

```json
{
  "type": "object",
  "description": "A runtime environment for a page or script",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "id": {
      "type": "string",
      "description": "A unique identifier for this runtime within the app.  Maximum length is 64 characters.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "general"
      ],
      "default": "general",
      "description": "Supports running functions and launching pages."
    },
    "code": {
      "$ref": "#/definitions/extensionRuntimeCode"
    },
    "lifetime": {
      "type": "string",
      "default": "short",
      "enum": [
        "short",
        "long"
      ],
      "description": "Runtimes with a short lifetime do not preserve state across executions. Runtimes with a long lifetime do."
    },
    "actions": {
      "$ref": "#/definitions/extensionRuntimesActions"
    },
    "customFunctions": {
      "$ref": "#/definitions/extensionCustomFunctions"
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "code"
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
  "id": "{string}",
  "type": "general",
  "code": {
    "page": "{string}",
    "script": "{string}"
  },
  "lifetime": "short | long",
  "actions": [
    {
      "id": "{string}",
      "type": "executeFunction | openPage",
      "displayName": "{string}",
      "pinnable": {boolean},
      "view": "{string}",
      "multiselect": {boolean},
      "supportsNoItemContext": {boolean}
    }
  ],
  "customFunctions": {
    "functions": [
      {
        extensionFunction object
      }
    ],
    "namespace": {
      extensionCustomFunctionsNamespace object
    },
    "allowCustomDataForDataTypeAny": {boolean}
  }
}
```

```json
{
  "type": "object",
  "description": "A runtime environment for a page or script",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "id": {
      "type": "string",
      "description": "A unique identifier for this runtime within the app.  Maximum length is 64 characters.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "general"
      ],
      "default": "general",
      "description": "Supports running functions and launching pages."
    },
    "code": {
      "$ref": "#/definitions/extensionRuntimeCode"
    },
    "lifetime": {
      "type": "string",
      "default": "short",
      "enum": [
        "short",
        "long"
      ],
      "description": "Runtimes with a short lifetime do not preserve state across executions. Runtimes with a long lifetime do."
    },
    "actions": {
      "$ref": "#/definitions/extensionRuntimesActions"
    },
    "customFunctions": {
      "$ref": "#/definitions/extensionCustomFunctions"
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "code"
  ]
}
```

- [Syntax](#tabpanel_5_syntax)
- [Schema](#tabpanel_5_schema)

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
  "id": "{string}",
  "type": "general",
  "code": {
    "page": "{string}",
    "script": "{string}"
  },
  "lifetime": "short | long",
  "actions": [
    {
      "id": "{string}",
      "type": "executeFunction | openPage",
      "displayName": "{string}",
      "pinnable": {boolean},
      "view": "{string}",
      "multiselect": {boolean},
      "supportsNoItemContext": {boolean}
    }
  ]
}
```

```json
{
  "type": "object",
  "description": "A runtime environment for a page or script",
  "properties": {
    "requirements": {
      "$ref": "#/definitions/requirementsExtensionElement"
    },
    "id": {
      "type": "string",
      "description": "A unique identifier for this runtime within the app.  Maximum length is 64 characters.",
      "maxLength": 64
    },
    "type": {
      "type": "string",
      "enum": [
        "general"
      ],
      "default": "general",
      "description": "Supports running functions and launching pages."
    },
    "code": {
      "$ref": "#/definitions/extensionRuntimeCode"
    },
    "lifetime": {
      "type": "string",
      "default": "short",
      "enum": [
        "short",
        "long"
      ],
      "description": "Runtimes with a short lifetime do not preserve state across executions. Runtimes with a long lifetime do."
    },
    "actions": {
      "$ref": "#/definitions/extensionRuntimesActions"
    }
  },
  "additionalProperties": false,
  "required": [
    "id",
    "code"
  ]
}
```

## Properties

#### requirements

Specifies the scopes, formFactors, and Office JavaScript library requirement sets that must be supported on the Office client in order for the runtime to be included in the add-in. For more information, see [Specify Office Add-in requirements in the unified manifest for Microsoft 365](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requirements-property-unified-manifest).

**Type**  
[requirementsExtensionElement](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### id

Specifies the ID for runtime.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### type

Specifies the type of runtime. The supported enum value for [browser-based runtime](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/runtimes#browser-runtime) is `general`.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `general`.

#### code

Specifies the location of code for the runtime. Based on `runtime.type`, add-ins can use either a JavaScript file or an HTML page with an embedded `script` tag that specifies the URL of a JavaScript file. Both URLs are necessary in situations where the `runtime.type` is uncertain.

**Type**  
[extensionRuntimeCode](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtime-code?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### lifetime

Specifies the lifetime of the runtime. The possible values are the following:

`short` \(default\): Doesn't preserve state across executions. It enables an [Outlook add-in to process unsolicited messages](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30).

`long` : Preserves the state across executions, allowing the add-in to run indefinitely. For example, task pane code will continue running even when the user closes the task pane. It can also be shared across different features of your add-in. See [Configure your Office Add-in to use a shared JavaScript runtime](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/configure-your-add-in-to-use-a-shared-runtime) for details.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `short`, `long`.

#### actions

Specifies the set of actions supported by the runtime. An action is either running a JavaScript function or opening a view such as a task pane.

**Type**  
Array of [extensionRuntimesActionsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 150.

**Supported values**  


#### actions

Specifies the set of actions supported by the runtime. An action is either running a JavaScript function or opening a view such as a task pane.

**Type**  
Array of [extensionRuntimesActionsItem](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-runtimes-actions-item?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1. Maximum array items: 20.

**Supported values**  


#### customFunctions

**Type**  
[extensionCustomFunctions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-custom-functions?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


## Remarks

To use `extensions.runtimes`, see [create add-in commands](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/create-addin-commands-unified-manifest), [configure the runtime for a task pane](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/create-addin-commands-unified-manifest#configure-the-runtime-for-the-task-pane-command), and [configure the runtime for the function command](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/create-addin-commands-unified-manifest#configure-the-runtime-for-the-function-command).

Note

An object in the `extensions` array may not have both a `runtimes` and a `contentRuntimes` property.

## Examples

```json
{
    "extensions": [
        {
          "runtimes": [
            {
              "requirements": {
                "capabilities": [
                  {
                    "name": "MailBox",
                    "minVersion": "1.10"
                  }
                ]
              },
              "id": "eventsRuntime",
              "type": "general",
              "code": {
                "page": "https://contoso.com/events.html",
                "script": "https://contoso.com/events.js"
              },
              "lifetime": "short",
              "actions": [
                {
                  "id": "onMessageSending",
                  "type": "executeFunction"
                },
                {
                  "id": "onNewMessageComposeCreated",
                  "type": "executeFunction"
                }
              ]
            },
            {
              "requirements": {
                "capabilities": [
                  {
                    "name": "MailBox", "minVersion": "1.1"
                  }
                ]
              },
              "id": "commandsRuntime",
              "type": "general",
              "code": {
                "page": "https://contoso.com/commands.html",
                "script": "https://contoso.com/commands.js"
              },
              "lifetime": "short",
              "actions": [
                {
                  "id": "action1",
                  "type": "executeFunction"
                },
                {
                  "id": "action2",
                  "type": "executeFunction"
                },
                {
                  "id": "action3",
                  "type": "executeFunction"
                }
              ]
            }
          ],
        }
    ]
}
```

## See also

- [Runtimes in Office Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/runtimes)
