<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentextension?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# agentExtension resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A declaration of a protocol extension supported by an agent, as defined in the **extensions** property of [agentCapabilities](https://learn.microsoft.com/en-us/graph/api/resources/agentcapabilities?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A human-readable description of how this agent uses the extension. |
| params | [agentExtensionParams](https://learn.microsoft.com/en-us/graph/api/resources/agentextensionparams?view=graph-rest-beta) | Extension-specific configuration parameters. |
| required | Boolean | If true, the client must understand and comply with the extension's requirements to interact with the agent. |
| uri | String | The unique URI identifying the extension. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentExtension",
  "uri": "String",
  "description": "String",
  "required": "Boolean",
  "params": {
    "@odata.type": "microsoft.graph.agentExtensionParams"
  }
}
```
