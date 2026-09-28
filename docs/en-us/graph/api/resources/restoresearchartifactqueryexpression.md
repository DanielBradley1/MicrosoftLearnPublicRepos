<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restoresearchartifactqueryexpression?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# restoreSearchArtifactQueryExpression resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a structured query expression for searching artifacts in restore operations. This resource provides a type-safe way to construct search queries for backup artifacts.

All properties are optional and can be combined to create more specific search queries.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hasAttachment | Boolean | Indicates whether the artifact has an attachment. Optional. |
| items | [granularRestoreItems](https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreitems?view=graph-rest-beta) collection | The types of items to include in the search. Optional. |
| recipients | String collection | The recipient email addresses to filter by. Optional. |
| senders | String collection | The sender email addresses to filter by. Optional. |
| subjects | String collection | The subject lines to filter by. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restoreSearchArtifactQueryExpression",
  "recipients": [
    "String"
  ],
  "senders": [
    "String"
  ],
  "subjects": [
    "String"
  ],
  "items": [
    "String"
  ],
  "hasAttachment": "Boolean"
}
```
