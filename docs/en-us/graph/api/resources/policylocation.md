<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policylocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# policyLocation resource type

Namespace: microsoft.graph

Abstract base type representing a location \(like a domain or URL\) to which a data protection policy applies. Use [policy location application](https://learn.microsoft.com/en-us/graph/api/resources/policylocationapplication?view=graph-rest-1.0) for application locations, [policy location domain](https://learn.microsoft.com/en-us/graph/api/resources/policylocationdomain?view=graph-rest-1.0) for domain locations, or [policy location URL](https://learn.microsoft.com/en-us/graph/api/resources/policylocationurl?view=graph-rest-1.0) for URL locations.

> **Note** This is an abstract type and isn't instantiated directly.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | String | The actual value representing the location. Location value is specific for concretetype of the policyLocation - policyLocationDomain, policyLocationUrl, or policyLocationApplication \(for example, "contoso.com", "https://partner.contoso.com/upload", "83ef198a-0396-4893-9d4f-d36efbffcaaa"\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource.

```json
{
  "@odata.type": "#microsoft.graph.policyLocation",
  "value": "String"
}
```
