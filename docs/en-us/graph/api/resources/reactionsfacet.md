<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/reactionsfacet?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# reactionsFacet resource type

Namespace: microsoft.graph

Provides counts of user reactions \(likes, comments, and shares\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| commentCount | Int32 | Count of comments. |
| likeCount | Int32 | Count of likes. |
| shareCount | Int32 | Count of shares. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.reactionsFacet",
  "likeCount": "Integer",
  "commentCount": "Integer",
  "shareCount": "Integer"
}
```
