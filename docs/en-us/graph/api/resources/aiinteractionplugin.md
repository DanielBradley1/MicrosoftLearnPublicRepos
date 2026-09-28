<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionplugin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# aiInteractionPlugin resource type

Namespace: microsoft.graph

Represents a plugin or extension invoked during an interaction with an AI or bot service.

Inherits from [aiInteractionEntity](https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionentity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifier | String | The unique identifier of the plugin. Inherited from [aiInteractionEntity](https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionentity?view=graph-rest-1.0). |
| name | String | The display name of the plugin. Inherited from [aiInteractionEntity](https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionentity?view=graph-rest-1.0). |
| version | String | The version of the plugin used. Inherited from [aiInteractionEntity](https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionentity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.aiInteractionPlugin",
  "identifier": "String",
  "name": "String",
  "version": "String"
}
```
