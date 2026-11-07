<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-mitretactic?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# mitreTactic resource type

Namespace: microsoft.graph.security

Represents a MITRE ATT&CK tactic and the techniques used within it. This resource is configured in the **tactics** property of an [alertTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-alerttemplate?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| tactic | String | The MITRE tactic identifier, for example, `Exploit`. |
| techniques | [microsoft.graph.security.mitreTechnique](https://learn.microsoft.com/en-us/graph/api/resources/security-mitretechnique?view=graph-rest-1.0) collection | The techniques observed within this tactic. |

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
