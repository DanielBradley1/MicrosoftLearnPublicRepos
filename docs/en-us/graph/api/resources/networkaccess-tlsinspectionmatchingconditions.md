<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionmatchingconditions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# tlsInspectionMatchingConditions resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the conditions used to match network traffic in [TLS inspection rules](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| destinations | [microsoft.graph.networkaccess.tlsInspectionDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectiondestination?view=graph-rest-beta) collection | A collection of destinations to match against. Can include FQDN destinations or web category destinations. An empty collection means no destination matching is performed. At least one destination must have non-null properties to allow for matching. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionMatchingConditions",
  "destinations": [
    {
      "@odata.type": "microsoft.graph.networkaccess.tlsInspectionFqdnDestination"
    }
  ]
}
```
