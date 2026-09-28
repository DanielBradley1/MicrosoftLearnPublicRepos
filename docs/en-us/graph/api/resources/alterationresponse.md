<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/alterationresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# alterationResponse resource type

Namespace: microsoft.graph

Provides information related to spelling corrections in the alteration response.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| originalQueryString | String | Defines the original user query string. |
| queryAlteration | [searchAlteration](https://learn.microsoft.com/en-us/graph/api/resources/searchalteration?view=graph-rest-1.0) | Defines the details of the alteration information for the spelling correction. |
| queryAlterationType | searchAlterationType | Defines the type of the spelling correction. The possible values are: `suggestion`, `modification`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "originalQueryString": "String",
  "queryAlteration": "String",
  "queryAlterationType": "String"
}
```
