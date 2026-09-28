<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/fido2keyrestrictions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# fido2KeyRestrictions resource type

Namespace: microsoft.graph

Represents the key restrictions that are enforced as part of the [FIDO2 security keys authentication methods policy](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethodconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aaGuids | String collection | A collection of Authenticator Attestation GUIDs. AADGUIDs define key types and manufacturers. |
| enforcementType | fido2RestrictionEnforcementType | Enforcement type. The possible values are: `allow`, `block`. |
| isEnforced | Boolean | Determines if the configured key enforcement is enabled. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fido2KeyRestrictions",
  "aaGuids": [
    "String"
  ],
  "enforcementType": "String",
  "isEnforced": "Boolean"
}
```
