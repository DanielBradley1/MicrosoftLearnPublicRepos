<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-singlepropertyschema?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# singlePropertySchema resource type

Namespace: microsoft.graph.security

The schema of one property in the results of running an [advanced hunting query](https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the property. |
| type | String | The type of the property. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "name": "Timestamp",
    "type": "DateTime"
}
```
