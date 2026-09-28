<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-urlentitymapping?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# urlEntityMapping resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a mapping from columns in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) query result to a URL entity that is attached to the resulting alert.

Base type: [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addressColumn | String | Name of the detection query column that maps to the URL address of the alert entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.urlEntityMapping",
  "addressColumn": "String"
}
```
