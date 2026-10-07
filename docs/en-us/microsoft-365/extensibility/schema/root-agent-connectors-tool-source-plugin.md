<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source-plugin?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# root.agentConnectors.toolSource.plugin object

Configuration details for connectors that leverage a Plugin Manifest. Either both id and file properties must be provided \(for external plugin reference\), or only the description property must be provided \(for inline plugin manifest\).

Properties that reference this object type:

- [root.agentConnectors.toolSource.plugin](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-agent-connectors-tool-source?view=m365-app-prev#plugin-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}",
  "file": "{string}"
}
```

```json
{
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
}
```

## Properties

#### id

The unique identifier of the plugin that provides the tools.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### file

The relative path to the plugin manifest file within the app package.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**
