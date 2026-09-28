<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usersignininsight?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# userSignInInsight resource type

Namespace: microsoft.graph

Represents an insight provided to reviewers based on the user's last sign-in date and time.

Inherits from [governanceInsight](https://learn.microsoft.com/en-us/graph/api/resources/governanceinsight?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastSignInDateTime | DateTimeOffset | Indicates when the user last signed in. |
| insightCreatedDateTime | DateTimeOffset | Indicates when the insight was created. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.usersignininsight",
  "lastSignInDateTime": "DateTimeOffset",
  "insightCreatedDateTime": "DateTimeOffset"
}
```
