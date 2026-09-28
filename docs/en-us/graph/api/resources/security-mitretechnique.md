<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-mitretechnique?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# mitreTechnique resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a MITRE Adversarial Tactics, Techniques, and Common Knowledge \(ATT&CK\) technique and optional subtechniques. This resource is configured in the **techniques** property of a [mitreTactic](https://learn.microsoft.com/en-us/graph/api/resources/security-mitretactic?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| subTechniques | String collection | The MITRE ATT&CK subtechnique identifiers that are associated with this technique, for example, `T1059.001`. |
| technique | String | The MITRE ATT&CK technique identifier, for example, `T1059`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.mitreTechnique",
  "subTechniques": [
    "String"
  ],
  "technique": "String"
}
```
