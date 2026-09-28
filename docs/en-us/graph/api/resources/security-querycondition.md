<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-querycondition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# queryCondition resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the [advanced hunting](https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-beta) query that defines the behavior of a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| queryText | String | Contents of the query. |
| lastModifiedDateTime \(deprecated\) | DateTimeOffset | Timestamp of when the query in the custom detection rule was last updated. **Deprecated.** This property will be removed from this resource on 2026-10-01. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.queryCondition",
  "queryText": "String",
  "lastModifiedDateTime": "String (timestamp)"
}
```
