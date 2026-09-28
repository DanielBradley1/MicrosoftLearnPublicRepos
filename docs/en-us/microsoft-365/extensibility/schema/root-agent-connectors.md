<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.agentConnectors object

An agent connector represents a mechanism to enable agents to access information from systems outside of Microsoft 365, often via an MCP Server. Other mechanisms include using OpenAPI descriptions for calling external HTTP APIs. The role of the agent connector is to provide the necessary configuration information to agents or other Microsoft 365 applications to connect to these external systems. An agent connector can be provided for use by other elements described within the same app manifest, or as a standalone resource that can be referenced in the app manifest by other Microsoft 365 applications.

For more information, see [Register MCP servers as agent connectors for Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors).

Properties that reference this object type:

- [root.agentConnectors](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#agentConnectors-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "displayName": "{string}",
  "description": "{string}",
  "toolSource": {
    "plugin": {
      plugin object
    },
    "remoteMcpServer": {
      remoteMcpServer object
    },
    "localMcpServer": {
      localMcpServer object
    }
  }
}
```

```json
{
  "type": "object",
  "description": "An agent connector represents a mechanism to enable agents to access information from systems outside of Microsoft 365, often via an MCP Server. Other mechanisms include using OpenAPI descriptions for calling external HTTP APIs. The role of the agent connector is to provide the necessary configuration information to agents or other M365 applications to connect to these external systems. An agent connector can be provided for use by other elements described within the same Unified App Manifest, or as a standalone resource that can be referenced in the Unified App Manifest of other M365 applications.",
  "properties": {
    "id": {
      "type": "string",
      "description": "Unique identifier for the agent connector",
      "maxLength": 64
    },
    "displayName": {
      "type": "string",
      "description": "A user-friendly name for the connector, which can be displayed in UIs.",
      "maxLength": 128
    },
    "description": {
      "type": "string",
      "description": "A brief description of the connector\u0027s purpose and functionality.",
      "maxLength": 4000
    },
    "toolSource": {
      "type": "object",
      "description": "Configuration details for connectors that provide tools for agents, either via a plugin, a remote MCP server or a local MCP server. One and only one of the above properties MUST be defined within a tool source object.",
      "properties": {
        "plugin": {
          "type": "object",
          "description": "Configuration details for connectors that leverage a Plugin Manifest. Both the id and file properties must be provided.",
          "properties": {
            "id": {
              "type": "string",
              "description": "The unique identifier of the plugin that provides the tools.",
              "maxLength": 64
            },
            "file": {
              "$ref": "#/definitions/relativePath",
              "description": "The relative path to the plugin manifest file within the app package."
            }
          },
          "required": [
            "id",
            "file"
          ],
          "additionalProperties": false
        },
        "remoteMcpServer": {
          "type": "object",
          "description": "Adds support for connectors that leverage a Remote MCP Server as the source of data.",
          "additionalProperties": false,
          "properties": {
            "mcpServerUrl": {
              "$ref": "#/definitions/secureHttpUrl",
              "description": "The URL of the remote MCP Server."
            },
            "mcpToolDescription": {
              "type": "object",
              "description": "Configuration for MCP tool descriptions by file reference. When this property is present it indicates that dynamic discovery will not be used.",
              "properties": {
                "file": {
                  "$ref": "#/definitions/relativePath",
                  "description": "The relative path to the MCP tool description file within the app package."
                }
              },
              "additionalProperties": false
            },
            "authorization": {
              "type": "object",
              "description": "Authorization configuration for connecting to the remote MCP server. The design mirrors that of Plugin Manifests https://learn.microsoft.com/microsoft-365-copilot/extensibility/api-plugin-manifest-2.3",
              "additionalProperties": false,
              "properties": {
                "type": {
                  "type": "string",
                  "enum": [
                    "None",
                    "OAuthPluginVault",
                    "ApiKeyPluginVault",
                    "DynamicClientRegistration",
                    "AzureKeyVault"
                  ],
                  "description": "The type of authorization required to invoke the MCP server. Supported values are: \u0027None\u0027 (anonymous access), \u0027OAuthPluginVault\u0027 (OAuth flow with referenceId), \u0027ApiKeyPluginVault\u0027 (API Key with referenceId), \u0027DynamicClientRegistration\u0027 (dynamic client registration with referenceId), \u0027AzureKeyVault\u0027 (Azure Key Vault integration)."
                },
                "referenceId": {
                  "type": "string",
                  "maxLength": 128,
                  "description": "A reference identifier used when type is OAuthPluginVault, ApiKeyPluginVault, DynamicClientRegistration, or AzureKeyVault. The referenceId value is acquired independently when providing the necessary authorization configuration values. This mechanism exists to prevent the need for storing secret values in the plugin manifest."
                }
              },
              "required": [
                "type"
              ],
              "if": {
                "properties": {
                  "type": {
                    "enum": [
                      "OAuthPluginVault",
                      "ApiKeyPluginVault",
                      "DynamicClientRegistration",
                      "AzureKeyVault"
                    ]
                  }
                }
              },
              "then": {
                "required": [
                  "referenceId"
                ]
              }
            }
          },
          "required": [
            "mcpServerUrl"
          ]
        },
        "localMcpServer": {
          "type": "object",
          "description": "Adds support for connectors that leverage a local MCP Server as the source of data.",
          "additionalProperties": false,
          "properties": {
            "mcpServerIdentifier": {
              "type": "string",
              "maxLength": 128,
              "description": "The unique identifier of the local MCP Server deployed via some secure mechanism to the user\u0027s desktop."
            },
            "mcpToolDescription": {
              "type": "object",
              "additionalProperties": false,
              "description": "Configuration for MCP tool descriptions by file reference. When this property is present it indicates that dynamic discovery will not be used.",
              "properties": {
                "file": {
                  "$ref": "#/definitions/relativePath",
                  "description": "The relative path to the MCP tool description file within the app package."
                }
              }
            },
            "authorization": {
              "type": "object",
              "description": "Authorization configuration for connecting to the local MCP server. The design mirrors that of Plugin Manifests https://learn.microsoft.com/microsoft-365-copilot/extensibility/api-plugin-manifest-2.3",
              "properties": {
                "type": {
                  "type": "string",
                  "enum": [
                    "None",
                    "OAuthPluginVault",
                    "ApiKeyPluginVault",
                    "DynamicClientRegistration",
                    "AzureKeyVault"
                  ],
                  "description": "The type of authorization required to invoke the MCP server. Supported values are: \u0027None\u0027 (anonymous access), \u0027OAuthPluginVault\u0027 (OAuth flow with referenceId), \u0027ApiKeyPluginVault\u0027 (API Key with referenceId), \u0027DynamicClientRegistration\u0027 (dynamic client registration with referenceId), \u0027AzureKeyVault\u0027 (Azure Key Vault integration)."
                },
                "referenceId": {
                  "type": "string",
                  "maxLength": 128,
                  "description": " (maxLength: 128)\tA reference identifier used when type is OAuthPluginVault, ApiKeyPluginVault, DynamicClientRegistration, or AzureKeyVault. The referenceId value is acquired independently when providing the necessary authorization configuration values. This mechanism exists to prevent the need for storing secret values in the plugin manifest."
                }
              },
              "additionalProperties": false,
              "required": [
                "type"
              ],
              "if": {
                "properties": {
                  "type": {
                    "enum": [
                      "OAuthPluginVault",
                      "ApiKeyPluginVault",
                      "DynamicClientRegistration",
                      "AzureKeyVault"
                    ]
                  }
                }
              },
              "then": {
                "required": [
                  "referenceId"
                ]
              }
            }
          },
          "required": [
            "mcpServerIdentifier"
          ]
        }
      },
      "additionalProperties": false
    }
  },
  "required": [
    "id",
    "displayName"
  ],
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "id": "{string}",
  "displayName": "{string}",
  "description": "{string}",
  "toolSource": {
    "remoteMcpServer": {
      remoteMcpServer object
    }
  }
}
```

```json
{
  "type": "object",
  "description": "An agent connector represents a mechanism to enable agents to access information from systems outside of Microsoft 365, often via an MCP Server. Other mechanisms include using OpenAPI descriptions for calling external HTTP APIs. The role of the agent connector is to provide the necessary configuration information to agents or other M365 applications to connect to these external systems. An agent connector can be provided for use by other elements described within the same Unified App Manifest, or as a standalone resource that can be referenced in the Unified App Manifest of other M365 applications.",
  "properties": {
    "id": {
      "type": "string",
      "description": "Unique identifier for the agent connector",
      "maxLength": 64
    },
    "displayName": {
      "type": "string",
      "description": "A user-friendly name for the connector, which can be displayed in UIs.",
      "maxLength": 128
    },
    "description": {
      "type": "string",
      "description": "A brief description of the connector\u0027s purpose and functionality.",
      "maxLength": 4000
    },
    "toolSource": {
      "type": "object",
      "description": "Configuration details for connectors that provide tools for agents via a remote MCP server.",
      "properties": {
        "remoteMcpServer": {
          "type": "object",
          "description": "Configuration details for a connector that provides tools via a remote MCP server.",
          "additionalProperties": false,
          "properties": {
            "mcpServerUrl": {
              "$ref": "#/definitions/secureHttpUrl",
              "description": "The URL of the remote MCP Server."
            },
            "mcpToolDescription": {
              "type": "object",
              "description": "Configuration for MCP tool descriptions by file reference.",
              "properties": {
                "file": {
                  "$ref": "#/definitions/relativePath",
                  "description": "The relative path to the MCP tool description file within the app package."
                }
              },
              "required": [
                "file"
              ],
              "additionalProperties": false
            },
            "authorization": {
              "type": "object",
              "description": "Authorization configuration for connecting to the local MCP server. The design mirrors that of Plugin Manifests https://spec-hub.azurewebsites.net/specifications/PluginManifest-2.3.html",
              "additionalProperties": false,
              "properties": {
                "type": {
                  "type": "string",
                  "enum": [
                    "None",
                    "OAuthPluginVault",
                    "ApiKeyPluginVault",
                    "DynamicClientRegistration",
                    "AzureKeyVault"
                  ],
                  "description": "The type of authorization required to invoke the MCP server. Supported values are: \u0027None\u0027 (anonymous access), \u0027OAuthPluginVault\u0027 (OAuth flow with referenceId), \u0027ApiKeyPluginVault\u0027 (API Key with referenceId), \u0027DynamicClientRegistration\u0027 (dynamic client registration with referenceId)."
                },
                "referenceId": {
                  "type": "string",
                  "maxLength": 128,
                  "description": "A reference identifier used when type is OAuthPluginVault, ApiKeyPluginVault, or DynamicClientRegistration. The referenceId value is acquired independently when providing the necessary authorization configuration values. This mechanism exists to prevent the need for storing secret values in the plugin manifest."
                }
              },
              "required": [
                "type"
              ],
              "if": {
                "properties": {
                  "type": {
                    "enum": [
                      "OAuthPluginVault",
                      "ApiKeyPluginVault",
                      "DynamicClientRegistration",
                      "AzureKeyVault"
                    ]
                  }
                }
              },
              "then": {
                "required": [
                  "referenceId"
                ]
              }
            }
          },
          "required": [
            "mcpServerUrl"
          ]
        }
      },
      "additionalProperties": false
    }
  },
  "required": [
    "id",
    "displayName"
  ],
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "id": "{string}",
  "displayName": "{string}",
  "description": "{string}",
  "toolSource": {
    "remoteMcpServer": {
      remoteMcpServer object
    }
  }
}
```

```json
{
  "type": "object",
  "description": "An agent connector represents a mechanism to enable agents to access information from systems outside of Microsoft 365, often via an MCP Server. Other mechanisms include using OpenAPI descriptions for calling external HTTP APIs. The role of the agent connector is to provide the necessary configuration information to agents or other M365 applications to connect to these external systems. An agent connector can be provided for use by other elements described within the same Unified App Manifest, or as a standalone resource that can be referenced in the Unified App Manifest of other M365 applications.",
  "properties": {
    "id": {
      "type": "string",
      "description": "Unique identifier for the agent connector",
      "maxLength": 64
    },
    "displayName": {
      "type": "string",
      "description": "A user-friendly name for the connector, which can be displayed in UIs.",
      "maxLength": 128
    },
    "description": {
      "type": "string",
      "description": "A brief description of the connector\u0027s purpose and functionality.",
      "maxLength": 4000
    },
    "toolSource": {
      "type": "object",
      "description": "Configuration details for connectors that provide tools for agents via a remote MCP server.",
      "properties": {
        "remoteMcpServer": {
          "type": "object",
          "description": "Configuration details for a connector that provides tools via a remote MCP server.",
          "additionalProperties": false,
          "properties": {
            "mcpServerUrl": {
              "$ref": "#/definitions/secureHttpUrl",
              "description": "The URL of the remote MCP Server."
            },
            "mcpToolDescription": {
              "type": "object",
              "description": "Configuration for MCP tool descriptions by file reference.",
              "properties": {
                "file": {
                  "$ref": "#/definitions/relativePath",
                  "description": "The relative path to the MCP tool description file within the app package."
                }
              },
              "required": [
                "file"
              ],
              "additionalProperties": false
            },
            "authorization": {
              "type": "object",
              "description": "Authorization configuration for connecting to the local MCP server. The design mirrors that of Plugin Manifests https://spec-hub.azurewebsites.net/specifications/PluginManifest-2.3.html",
              "additionalProperties": false,
              "properties": {
                "type": {
                  "type": "string",
                  "enum": [
                    "None",
                    "OAuthPluginVault",
                    "ApiKeyPluginVault",
                    "DynamicClientRegistration"
                  ],
                  "description": "The type of authorization required to invoke the MCP server. Supported values are: \u0027None\u0027 (anonymous access), \u0027OAuthPluginVault\u0027 (OAuth flow with referenceId), \u0027ApiKeyPluginVault\u0027 (API Key with referenceId), \u0027DynamicClientRegistration\u0027 (dynamic client registration with referenceId)."
                },
                "referenceId": {
                  "type": "string",
                  "maxLength": 128,
                  "description": "A reference identifier used when type is OAuthPluginVault, ApiKeyPluginVault, or DynamicClientRegistration. The referenceId value is acquired independently when providing the necessary authorization configuration values. This mechanism exists to prevent the need for storing secret values in the plugin manifest."
                }
              },
              "required": [
                "type"
              ],
              "if": {
                "properties": {
                  "type": {
                    "enum": [
                      "OAuthPluginVault",
                      "ApiKeyPluginVault",
                      "DynamicClientRegistration"
                    ]
                  }
                }
              },
              "then": {
                "required": [
                  "referenceId"
                ]
              }
            }
          },
          "required": [
            "mcpServerUrl",
            "mcpToolDescription"
          ]
        }
      },
      "additionalProperties": false
    }
  },
  "required": [
    "id",
    "displayName"
  ],
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "id": "{string}",
  "displayName": "{string}",
  "description": "{string}",
  "toolSource": {
    "remoteMcpServer": {
      remoteMcpServer object
    }
  }
}
```

```json
{
  "type": "object",
  "description": "An agent connector represents a mechanism to enable agents to access information from systems outside of Microsoft 365, often via an MCP Server. Other mechanisms include using OpenAPI descriptions for calling external HTTP APIs. The role of the agent connector is to provide the necessary configuration information to agents or other M365 applications to connect to these external systems. An agent connector can be provided for use by other elements described within the same Unified App Manifest, or as a standalone resource that can be referenced in the Unified App Manifest of other M365 applications.",
  "properties": {
    "id": {
      "type": "string",
      "description": "Unique identifier for the agent connector",
      "maxLength": 64
    },
    "displayName": {
      "type": "string",
      "description": "A user-friendly name for the connector, which can be displayed in UIs.",
      "maxLength": 128
    },
    "description": {
      "type": "string",
      "description": "A brief description of the connector\u0027s purpose and functionality.",
      "maxLength": 4000
    },
    "toolSource": {
      "type": "object",
      "description": "Configuration details for connectors that provide tools for agents via a remote MCP server.",
      "properties": {
        "remoteMcpServer": {
          "type": "object",
          "description": "Configuration details for a connector that provides tools via a remote MCP server.",
          "additionalProperties": false,
          "properties": {
            "mcpServerUrl": {
              "$ref": "#/definitions/secureHttpUrl",
              "description": "The URL of the remote MCP Server."
            },
            "mcpToolDescription": {
              "type": "object",
              "description": "Configuration for MCP tool descriptions, either by file reference or inline content (but not both). When this property is present it indicates that dynamic discovery will not be used.",
              "properties": {
                "file": {
                  "$ref": "#/definitions/relativePath",
                  "description": "The relative path to the MCP tool description file within the app package."
                }
              },
              "required": [
                "file"
              ],
              "additionalProperties": false
            },
            "authorization": {
              "type": "object",
              "description": "Authorization configuration for connecting to the local MCP server. The design mirrors that of Plugin Manifests https://spec-hub.azurewebsites.net/specifications/PluginManifest-2.3.html",
              "additionalProperties": false,
              "properties": {
                "type": {
                  "type": "string",
                  "enum": [
                    "None",
                    "OAuthPluginVault",
                    "ApiKeyPluginVault",
                    "DynamicClientRegistration"
                  ],
                  "description": "The type of authorization required to invoke the MCP server. Supported values are: \u0027None\u0027 (anonymous access), \u0027OAuthPluginVault\u0027 (OAuth flow with referenceId), \u0027ApiKeyPluginVault\u0027 (API Key with referenceId), \u0027DynamicClientRegistration\u0027 (dynamic client registration with referenceId)."
                },
                "referenceId": {
                  "type": "string",
                  "maxLength": 128,
                  "description": "A reference identifier used when type is OAuthPluginVault, ApiKeyPluginVault, or DynamicClientRegistration. The referenceId value is acquired independently when providing the necessary authorization configuration values. This mechanism exists to prevent the need for storing secret values in the plugin manifest."
                }
              },
              "required": [
                "type"
              ],
              "if": {
                "properties": {
                  "type": {
                    "enum": [
                      "OAuthPluginVault",
                      "ApiKeyPluginVault",
                      "DynamicClientRegistration"
                    ]
                  }
                }
              },
              "then": {
                "required": [
                  "referenceId"
                ]
              }
            }
          },
          "required": [
            "mcpServerUrl",
            "mcpToolDescription"
          ]
        }
      },
      "additionalProperties": false
    }
  },
  "required": [
    "id",
    "displayName"
  ],
  "additionalProperties": false
}
```

## Properties

#### id

Unique identifier for the agent connector

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### displayName

A user-friendly name for the connector, which can be displayed in UIs.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### displayName

A user-friendly name for the connector, which can be displayed in UIs.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### description

A brief description of the connector's purpose and functionality.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 4000.

**Supported values**  


#### description

A brief description of the connector's purpose and functionality.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 4000.

**Supported values**  


#### toolSource

Configuration details for connectors that provide tools for agents, either via a plugin, a remote MCP server or a local MCP server. One and only one of the above properties MUST be defined within a tool source object.

**Type**  
[toolSource](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**
