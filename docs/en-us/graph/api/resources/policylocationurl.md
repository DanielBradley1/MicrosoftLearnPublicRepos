<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policylocationurl?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# policyLocationUrl resource type

Namespace: microsoft.graph

Represents a specific URL as a location for data protection policy scoping.

Inherits from [policyLocation](https://learn.microsoft.com/en-us/graph/api/resources/policylocation?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | String | The actual value representing the location \(for example, "https://partner.contoso.com/upload"\). Inherited from [policyLocation](https://learn.microsoft.com/en-us/graph/api/resources/policylocation?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.policyLocationUrl",
  "value": "String" 
}
```
