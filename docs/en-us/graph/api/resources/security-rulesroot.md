<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-rulesroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# rulesRoot resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Container that holds the [custom detection rules](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) configured for the tenant in Microsoft Defender XDR. Accessed as a singleton from the [security](https://learn.microsoft.com/en-us/graph/api/resources/security?view=graph-rest-beta) resource through the `rules` navigation property.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| detectionRules | [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) collection | The custom detection rules configured for the tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.rulesRoot"
}
```
