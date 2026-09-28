<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/optionalclaims?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# optionalClaims resource type

Namespace: microsoft.graph Declares the optional claims requested by an application. An application can configure optional claims to be returned in each of three types of tokens \(ID token, access token, SAML 2 token\) it can receive from the security token service. An application can configure a different set of optional claims to be returned in each token type. The optionalClaims property of the [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) is an **optionalClaims** object.

Application developers can configure optional claims in their Microsoft Entra apps to specify which claims they want in tokens sent to their application by the Microsoft security token service. See [provide optional claims to your Microsoft Entra app](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-optional-claims) for more information.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessToken | [optionalClaim](https://learn.microsoft.com/en-us/graph/api/resources/optionalclaim?view=graph-rest-1.0) collection | The optional claims returned in the JWT access token. |
| idToken | [optionalClaim](https://learn.microsoft.com/en-us/graph/api/resources/optionalclaim?view=graph-rest-1.0) collection | The optional claims returned in the JWT ID token. |
| saml2Token | [optionalClaim](https://learn.microsoft.com/en-us/graph/api/resources/optionalclaim?view=graph-rest-1.0) collection | The optional claims returned in the SAML token. |

## JSON Representation

The following JSON representation shows the resource type.

```json
{
  "idToken": [{"@odata.type": "microsoft.graph.optionalClaim"}],
  "accessToken": [{"@odata.type": "microsoft.graph.optionalClaim"}],
  "saml2Token": [{"@odata.type": "microsoft.graph.optionalClaim"}]
}
```
