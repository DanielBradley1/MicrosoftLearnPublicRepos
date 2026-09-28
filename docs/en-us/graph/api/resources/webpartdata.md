<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webpartdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# webPartData resource type

Namespace: microsoft.graph

Represents the data of a given web part.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| audiences | String collection | Audience information of the web part. By using this property, specific content will be prioritized to specific audiences. |
| dataVersion | String | Data version of the web part. The value is defined by the web part developer. Different dataVersions usually refers to a different property structure. |
| description | String | Description of the web part. |
| properties | [Json](https://learn.microsoft.com/en-us/graph/api/resources/json?view=graph-rest-1.0) | Properties bag of the web part. |
| serverProcessedContent | [serverProcessedContent](https://learn.microsoft.com/en-us/graph/api/resources/serverprocessedcontent?view=graph-rest-1.0) | Contains collections of data that can be processed by server side services like search index and link fixup. |
| title | String | Title of the web part. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webPartData",
  "audiences": ["String"],
  "dataVersion": "String",
  "description": "String",
  "properties": {
    "@odata.type": "microsoft.graph.Json"
  },
  "serverProcessedContent": {
    "@odata.type": "microsoft.graph.serverProcessedContent"
  },
  "title": "String"
}
```
