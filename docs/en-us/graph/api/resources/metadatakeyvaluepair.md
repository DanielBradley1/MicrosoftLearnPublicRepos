<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/metadatakeyvaluepair?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# metaDataKeyValuePair resource type

Namespace: microsoft.graph

Represents a key-value \(object\) pair of the metadata.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| key | String | Key of the metadata. |
| value | [Json](https://learn.microsoft.com/en-us/graph/api/resources/json?view=graph-rest-1.0) | Value of the metadata. Should be an object. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.metaDataKeyValuePair",
  "key": "String",
  "value": {
    "@odata.type": "microsoft.graph.Json"
  }
}
```
