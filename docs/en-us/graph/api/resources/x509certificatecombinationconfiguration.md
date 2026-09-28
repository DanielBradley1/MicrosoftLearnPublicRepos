<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/x509certificatecombinationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# x509CertificateCombinationConfiguration resource type

Namespace: microsoft.graph

Configuration to require specific certificate properties. You can use this entity to specify the certificate issuer or policy OID that are allowed, as part of certificate-based authentication, in an [authentication strength policy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0).

Inherits from [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedIssuerSkis | String collection | A list of allowed subject key identifier values. |
| allowedPolicyOIDs | String collection | A list of allowed policy OIDs. |
| appliesToCombinations | authenticationMethodModes collection | Which authentication method combinations this configuration applies to. The possible values for x509certificatecombinationconfiguration are `"x509CertificateSingleFactor"` or `"x509CertificateMultiFactor"`. Inherited from [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0). |
| id | String | A system-generated identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.x509CertificateCombinationConfiguration",
  "id": "String (identifier)",
  "appliesToCombinations": [
    "String"
  ],
  "allowedIssuerSkis": [
    "String"
  ],
  "allowedPolicyOIDs": [
    "String"
  ]
}
```
