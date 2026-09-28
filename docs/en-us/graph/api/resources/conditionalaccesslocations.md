<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesslocations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-23 -->

# conditionalAccessLocations resource type

Namespace: microsoft.graph

Represents locations included in and excluded from the scope of a [conditional access policy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0). Locations can be [countries and regions](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-1.0) or [IP addresses](https://learn.microsoft.com/en-us/graph/api/resources/ipnamedlocation?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeLocations | String collection | Location IDs excluded from scope of policy. |
| includeLocations | String collection | Location IDs in scope of policy unless explicitly excluded, `All`, or `AllTrusted`. |

## JSON representation

The following JSON representation shows the resource type.

## Relationships

None.

```json
{
  "excludeLocations": ["String"],
  "includeLocations": ["String"]
}
```
