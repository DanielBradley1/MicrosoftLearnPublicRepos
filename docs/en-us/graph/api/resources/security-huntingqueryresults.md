<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-huntingqueryresults?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-29 -->

# huntingQueryResults resource type

Namespace: microsoft.graph.security

The results of running a [query for advanced hunting](https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| schema | [microsoft.graph.security.singlePropertySchema](https://learn.microsoft.com/en-us/graph/api/resources/security-singlepropertyschema?view=graph-rest-1.0) collection | The schema for the response. |
| results | [microsoft.graph.security.huntingRowResult](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingrowresult?view=graph-rest-1.0) collection | The results of the hunting query. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "schema": [{"@odata.type": "microsoft.graph.security.singlePropertySchema"}],
    "results": [{"@odata.type": "microsoft.graph.security.huntingRowResult"}]
}
```
