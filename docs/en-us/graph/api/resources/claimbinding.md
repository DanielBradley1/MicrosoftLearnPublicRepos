<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/claimbinding?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# claimBinding resource type

Namespace: microsoft.graph

Defines the mapping between a source attribute and a Verifiable ID claim in a [verifiedIdProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofileconfiguration?view=graph-rest-1.0) object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| matchConfidenceLevel | matchConfidenceLevel | The confidence level for matching the claim to the source attribute. The possible values are: `exact`, `relaxed`, `unknownFutureValue`. |
| sourceAttribute | String | Source attribute name from the source system, for example a directory attribute. |
| verifiedIdClaim | String | Verified ID claim name or path, for example `vc.credentialSubject.firstName`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.claimBinding",
  "matchConfidenceLevel": "String",
  "sourceAttribute": "String",
  "verifiedIdClaim": "String"
}
```
