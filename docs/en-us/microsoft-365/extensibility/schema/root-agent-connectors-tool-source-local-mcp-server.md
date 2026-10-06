<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-local-mcp-server?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# root.agentConnectors.toolSource.localMcpServer object

Adds support for connectors that leverage a local MCP Server as the source of data.

Properties that reference this object type:

- [root.agentConnectors.toolSource.localMcpServer](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source?view=m365-app-prev#localMcpServer-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "mcpServerIdentifier": "{string}",
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
```

## Properties

#### mcpServerIdentifier

The unique identifier of the local MCP Server deployed via some secure mechanism to the user's desktop.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### mcpToolDescription

Configuration for MCP tool descriptions, either by file reference or inline content \(but not both\). When this property is present it indicates that dynamic discovery will not be used.

**Type**  
[mcpToolDescription](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-local-mcp-server-mcp-tool-description?view=m365-app-prev)

**Required**  
—

**Constraints**  


**Supported values**  


#### authorization

Authorization configuration for connecting to the local MCP server. The design mirrors that of [API plugin manifests](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api-plugin-manifest-2.3).

**Type**  
[authorization](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-local-mcp-server-authorization?view=m365-app-prev)

**Required**  
—

**Constraints**  


**Supported values**
