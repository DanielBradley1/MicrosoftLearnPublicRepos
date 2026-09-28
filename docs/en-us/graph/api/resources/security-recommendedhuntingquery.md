<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-recommendedhuntingquery?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-02-16 -->

# recommendedHuntingQuery resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Kusto Query Language \(KQL\) advanced hunting query.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| kqlText | String | The query string. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.recommendedHuntingQuery",
  "kqlText" : "String"
}
```
