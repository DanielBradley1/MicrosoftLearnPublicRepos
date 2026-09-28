<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.agentConnectors.toolSource.remoteMcpServer object

Adds support for connectors that leverage a Remote MCP Server as the source of data.

Properties that reference this object type:

- [root.agentConnectors.toolSource.remoteMcpServer](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source?view=m365-app-1.30#remoteMcpServer-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "mcpServerUrl": "{string}",
  "mcpToolDescription": {
    "file": "{string}"
  },
  "authorization": {
    "type": "None | OAuthPluginVault | ApiKeyPluginVault | DynamicClientRegistration | AzureKeyVault",
    "referenceId": "{string}"
  }
}
```

```json
{
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
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "mcpServerUrl": "{string}",
  "mcpToolDescription": {
    "file": "{string}"
  },
  "authorization": {
    "type": "None | OAuthPluginVault | ApiKeyPluginVault | DynamicClientRegistration | AzureKeyVault",
    "referenceId": "{string}"
  }
}
```

```json
{
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
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "mcpServerUrl": "{string}",
  "mcpToolDescription": {
    "file": "{string}"
  },
  "authorization": {
    "type": "None | OAuthPluginVault | ApiKeyPluginVault | DynamicClientRegistration",
    "referenceId": "{string}"
  }
}
```

```json
{
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
```

- [Syntax](#tabpanel_4_syntax)
- [Schema](#tabpanel_4_schema)

```json
{
  "mcpServerUrl": "{string}",
  "mcpToolDescription": {
    "file": "{string}"
  },
  "authorization": {
    "type": "None | OAuthPluginVault | ApiKeyPluginVault | DynamicClientRegistration",
    "referenceId": "{string}"
  }
}
```

```json
{
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
```

## Properties

#### mcpServerUrl

The URL of the remote MCP Server.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `https://`.

#### mcpToolDescription

Configuration for MCP tool descriptions, either by file reference or inline content \(but not both\). When this property is present it indicates that dynamic discovery will not be used.

To enable dynamic tool discovery, omit the [mcpToolDescription](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-mcp-tool-description) property from your `remoteMcpServer` configuration.

**Type**  
[mcpToolDescription](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-mcp-tool-description?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### mcpToolDescription

Configuration for MCP tool descriptions, either by file reference or inline content \(but not both\). When this property is present it indicates that dynamic discovery will not be used.

To enable dynamic tool discovery, omit the [mcpToolDescription](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-mcp-tool-description) property from your `remoteMcpServer` configuration.

**Type**  
[mcpToolDescription](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-mcp-tool-description?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**  


#### mcpToolDescription

Configuration for MCP tool descriptions, either by file reference or inline content \(but not both\). When this property is present it indicates that dynamic discovery will not be used.

**Type**  
[mcpToolDescription](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-mcp-tool-description?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### authorization

Authorization configuration for connecting to the local MCP server. The design mirrors that of [API plugin manifests](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api-plugin-manifest-2.3).

**Type**  
[authorization](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**
