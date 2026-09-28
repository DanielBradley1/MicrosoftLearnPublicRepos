<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofileconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# verifiedIdProfileConfiguration resource type

Namespace: microsoft.graph

Verified ID profile configuration defining set of properties of a specific [Verified ID credential](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| acceptedIssuer | String | Trusted Verified ID issuer. |
| claimBindings | [claimBinding](https://learn.microsoft.com/en-us/graph/api/resources/claimbinding?view=graph-rest-1.0) collection | Claim bindings from Verified ID to source attributes. |
| claimBindingSource | claimBindingSource | Source to validate against Verified ID claims. The possible values are: `directory`, `unknownFutureValue`. |
| claimValidation | [claimValidation](https://learn.microsoft.com/en-us/graph/api/resources/claimvalidation?view=graph-rest-1.0) | Validation settings for claim processing. |
| type | String | Verified ID type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiedIdProfileConfiguration",
  "type": "String",
  "acceptedIssuer": "String",
  "claimBindingSource": "String",
  "claimBindings": [
    {
      "@odata.type": "microsoft.graph.claimBinding"
    }
  ],
  "claimValidation": {
    "@odata.type": "microsoft.graph.claimValidation"
  }
}
```
