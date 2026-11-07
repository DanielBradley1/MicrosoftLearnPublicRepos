<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-rulesroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# rulesRoot resource type

Namespace: microsoft.graph.security

Container that holds the [custom detection rules](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) configured for the tenant in Microsoft Defender XDR. Accessed as a singleton from the [security](https://learn.microsoft.com/en-us/graph/api/resources/security?view=graph-rest-1.0) resource through the `rules` navigation property.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| detectionRules | [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) collection | The custom detection rules configured for the tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.rulesRoot"
}
```
