<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-mitretactic?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# mitreTactic resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a MITRE ATT&CK tactic and the techniques used within it. This resource is configured in the **tactics** property of an [alertTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-alerttemplate?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| tactic | String | The MITRE tactic identifier, for example, `Exploit`. |
| techniques | [microsoft.graph.security.mitreTechnique](https://learn.microsoft.com/en-us/graph/api/resources/security-mitretechnique?view=graph-rest-beta) collection | The techniques observed within this tactic. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.mitreTactic",
  "tactic": "String",
  "techniques": [
    {
      "@odata.type": "microsoft.graph.security.mitreTechnique"
    }
  ]
}
```
