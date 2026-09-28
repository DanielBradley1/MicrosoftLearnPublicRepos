<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitemcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# externalItemContent resource type

Namespace: microsoft.graph.externalConnectors

The content of an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0) indexed via a Microsoft Search [connection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| type | microsoft.graph.externalConnectors.externalItemContentType | The type of content in the value property. The possible values are: `text`, `html`, `unknownFutureValue`. These are the content types that the indexer supports, and not the file extension types allowed. |
| value | String | The content for the externalItem. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "type": "String",
  "value": "String"
}
```
