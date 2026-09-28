<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/publickeyinfrastructureroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-27 -->

# publicKeyInfrastructureRoot resource type

Namespace: microsoft.graph

The collection of public key infrastructure instances over different Microsoft Entra features.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the PublicKeyInfrastructure entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| certificateBasedAuthConfigurations | [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) collection | The collection of public key infrastructure instances for the certificate-based authentication feature for users. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.publicKeyInfrastructureRoot",
  "id": "String (identifier)"
}
```
