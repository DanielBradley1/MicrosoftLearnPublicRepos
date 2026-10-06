<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-local-mcp-server-mcp-tool-description?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# root.agentConnectors.toolSource.localMcpServer.mcpToolDescription object

Configuration for MCP tool descriptions, either by file reference or inline content \(but not both\). When this property is present it indicates that dynamic discovery will not be used.

Properties that reference this object type:

- [root.agentConnectors.toolSource.localMcpServer.mcpToolDescription](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-local-mcp-server?view=m365-app-prev#mcpToolDescription-property)

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
  "additionalProperties": false,
  "description": "Configuration for MCP tool descriptions by file reference. When this property is present it indicates that dynamic discovery will not be used.",
  "properties": {
    "file": {
      "$ref": "#/definitions/relativePath",
      "description": "The relative path to the MCP tool description file within the app package."
    }
  }
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
