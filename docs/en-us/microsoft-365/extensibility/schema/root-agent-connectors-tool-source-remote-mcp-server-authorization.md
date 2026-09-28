<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-authorization?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.agentConnectors.toolSource.remoteMcpServer.authorization object

Authorization configuration for connecting to the local MCP server. The design mirrors that of [API plugin manifests](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api-plugin-manifest-2.3). For details, see [Register MCP servers as agent connectors for Microsoft 365](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors).

Properties that reference this object type:

- [root.agentConnectors.toolSource.remoteMcpServer.authorization](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30#authorization-property)

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
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "type": "None | OAuthPluginVault | ApiKeyPluginVault | DynamicClientRegistration | AzureKeyVault",
  "referenceId": "{string}"
}
```

```json
{
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
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "type": "None | OAuthPluginVault | ApiKeyPluginVault | DynamicClientRegistration",
  "referenceId": "{string}"
}
```

```json
{
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
```

## Properties

#### type

The type of authorization required to invoke the MCP server. Supported values include:

- `None`: No authentication required \(anonymous access\).
- `OAuthPluginVault`: OAuth 2.0 tokens stored inside Microsoft's secure vault.
- `ApiKeyPluginVault`: API key stored in a vault and referenced by ID.
- `DynamicClientRegistration`: Dynamic OAuth client creation.
- `AzureKeyVault`: Secrets stored in your own Azure Key Vault instance.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `None`, `OAuthPluginVault`, `ApiKeyPluginVault`, `DynamicClientRegistration`, `AzureKeyVault`.

#### type

The type of authorization required to invoke the MCP server. Supported values include:

- `None`: No authentication required \(anonymous access\).
- `OAuthPluginVault`: OAuth 2.0 tokens stored inside Microsoft's secure vault.
- `ApiKeyPluginVault`: API key stored in a vault and referenced by ID.
- `DynamicClientRegistration`: Dynamic OAuth client creation.
- `AzureKeyVault`: Secrets stored in your own Azure Key Vault instance.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `None`, `OAuthPluginVault`, `ApiKeyPluginVault`, `DynamicClientRegistration`.

#### referenceId

A reference identifier used when type is OAuthPluginVault, ApiKeyPluginVault, or DynamicClientRegistration. The referenceId value is acquired independently when providing the necessary authorization configuration values. This mechanism exists to prevent the need for storing secret values in the plugin manifest.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 128.

**Supported values**
