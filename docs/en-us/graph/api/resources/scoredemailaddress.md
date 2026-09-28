<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/scoredemailaddress?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# scoredEmailAddress resource type

Namespace: microsoft.graph

Represents a scored email address.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | string | The email address. |
| relevanceScore | double | The relevance score of the email address. A relevance score is used as a sort key, in relation to the other returned results. A higher relevance score value corresponds to a more relevant result. Relevance is determined by the user’s communication and collaboration patterns and business relationships. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "address": "string",
  "relevanceScore": 1024.0
}
```
