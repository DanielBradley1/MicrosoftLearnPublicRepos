<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server-mcp-tool-description?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.agentConnectors.toolSource.remoteMcpServer.mcpToolDescription object

Configuration for MCP tool descriptions, either by file reference or inline content \(but not both\). When this property is present it indicates that dynamic discovery will not be used.

Properties that reference this object type:

- [root.agentConnectors.toolSource.remoteMcpServer.mcpToolDescription](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-remote-mcp-server?view=m365-app-1.30#mcpToolDescription-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "file": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Configuration for MCP tool descriptions by file reference. When this property is present it indicates that dynamic discovery will not be used.",
  "properties": {
    "file": {
      "$ref": "#/definitions/relativePath",
      "description": "The relative path to the MCP tool description file within the app package."
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "file": "{string}"
}
```

```json
{
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
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "file": "{string}"
}
```

```json
{
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
}
```

## Properties

#### file

The relative path to the MCP tool description file within the app package.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### file

The relative path to the MCP tool description file within the app package.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**
