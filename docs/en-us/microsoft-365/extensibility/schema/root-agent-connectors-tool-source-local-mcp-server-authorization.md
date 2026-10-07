<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-local-mcp-server-authorization?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-06-29 -->

# root.agentConnectors.toolSource.localMcpServer.authorization object

Authorization configuration for connecting to the local MCP server. The design mirrors that of [API plugin manifests](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api-plugin-manifest-2.3).

Properties that reference this object type:

- [root.agentConnectors.toolSource.localMcpServer.authorization](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-local-mcp-server?view=m365-app-prev#authorization-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "type": "None | OAuthPluginVault | ApiKeyPluginVault | DynamicClientRegistration | AzureKeyVault",
  "referenceId": "{string}"
}
```

```json
{
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
```

## Properties

#### type

The type of authorization required to invoke the MCP server. Supported values are: 'None' \(anonymous access\), 'OAuthPluginVault' \(OAuth flow with referenceId\), 'ApiKeyPluginVault' \(API Key with referenceId\), 'DynamicClientRegistration' \(dynamic client registration with referenceId\), and 'AzureKeyVault'.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `None`, `OAuthPluginVault`, `ApiKeyPluginVault`, `DynamicClientRegistration`, `AzureKeyVault`.

#### referenceId

\(maxLength: 128\) A reference identifier used when type is OAuthPluginVault, ApiKeyPluginVault, or DynamicClientRegistration. The referenceId value is acquired independently when providing the necessary authorization configuration values. This mechanism exists to prevent the need for storing secret values in the plugin manifest.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**
