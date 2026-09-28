<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/inboundoutboundpolicyconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# inboundOutboundPolicyConfiguration resource type

Namespace: microsoft.graph

Defines the inbound and outbound rulesets for particular configurations within cross-tenant access settings.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inboundAllowed | Boolean | Defines whether external users coming inbound are allowed. |
| outboundAllowed | Boolean | Defines whether internal users are allowed to go outbound. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.inboundOutboundPolicyConfiguration",
  "inboundAllowed": {"@odata.type": "Boolean"},
  "outboundAllowed": {"@odata.type": "Boolean"}
}
```
