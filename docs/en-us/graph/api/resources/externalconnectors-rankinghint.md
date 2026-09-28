<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-rankinghint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# rankingHint resource type

Namespace: microsoft.graph.externalConnectors

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies the schema property's ranking hint.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| importanceScore | microsoft.graph.externalConnectors.importanceScore | Specifies the schema property importance. The possible values are: `low`, `medium`, `high`, `veryHigh`, `unknownFutureValue`. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "importanceScore": "string"
}
```
