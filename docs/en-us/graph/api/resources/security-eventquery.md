<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-eventquery?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# eventQuery resource type

Namespace: microsoft.graph.security Represents the workload \(SharePoint Online, OneDrive for Business, Exchange Online\) and identification information associated with a retention event.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| queryType | microsoft.graph.security.queryType | Represents the type of query associated with an event. 'files' for SPO and ODB and 'messages' for EXO.The possible values are: `files`, `messages`, `unknownFutureValue`. |
| query | String | Represents unique identification for the query. 'Asset ID' for SharePoint Online and OneDrive for Business, 'keywords' for Exchange Online. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.eventQuery",
  "queryType": "String",
  "query": "String"
}
```
