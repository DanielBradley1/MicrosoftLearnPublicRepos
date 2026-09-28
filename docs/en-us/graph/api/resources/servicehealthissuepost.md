<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/servicehealthissuepost?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# serviceHealthIssuePost resource type

Namespace: microsoft.graph

Represents a historical post in a [service health issue](https://learn.microsoft.com/en-us/graph/api/resources/servicehealthissue?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The published time of the post. |
| description | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The content of the service issue post. The supported value for the contentType property is `html`. |
| postType | postType | The post type of the service issue historical post. The possible values are: `regular`, `quick`, `strategic`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceHealthIssuePost",
  "createdDateTime": "String (timestamp)",
  "postType": "String",
  "description": {
    "@odata.type": "microsoft.graph.itemBody"
  }
}
```
