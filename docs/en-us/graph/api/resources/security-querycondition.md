<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-querycondition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# queryCondition resource type

Namespace: microsoft.graph.security

Represents the [advanced hunting](https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-1.0) query that defines the behavior of a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| queryText | String | Contents of the query. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.queryCondition",
  "queryText": "String"
}
```
