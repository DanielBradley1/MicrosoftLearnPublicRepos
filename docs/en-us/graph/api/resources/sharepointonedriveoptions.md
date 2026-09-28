<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointonedriveoptions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-19 -->

# sharePointOneDriveOptions resource type

Namespace: microsoft.graph

Provides the search content options when a search is performed using application permissions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| includeContent | searchContent | The type of search content. The possible values are: `sharedContent`, `privateContent`, `unknownFutureValue`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "includeContent": "String"
}
```
