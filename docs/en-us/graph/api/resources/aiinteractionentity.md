<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# aiInteractionEntity resource type

Namespace: microsoft.graph

Represents the base type for interacting with AI entities that provide common properties such as an identifier, name, and version.

Base type of [aiAgentInfo](https://learn.microsoft.com/en-us/graph/api/resources/aiagentinfo?view=graph-rest-1.0) and [aiInteractionPlugin](https://learn.microsoft.com/en-us/graph/api/resources/aiinteractionplugin?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifier | String | The unique identifier of the AI entity. |
| name | String | The display name of the AI entity. |
| version | String | The version of the AI entity used. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.aiInteractionEntity",
  "identifier": "String",
  "name": "String",
  "version": "String"
}
```
