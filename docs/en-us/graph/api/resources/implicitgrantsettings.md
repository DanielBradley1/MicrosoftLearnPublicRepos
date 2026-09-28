<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/implicitgrantsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# implicitGrantSettings resource type

Namespace: microsoft.graph

Specifies whether this web application can request tokens using the OAuth 2.0 implicit flow. Separate properties are available to request ID and access tokens as part of the implicit flow. To enable implicit flow, at least one of the following properties must be set to true.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enableAccessTokenIssuance | Boolean | Specifies whether this web application can request an access token using the OAuth 2.0 implicit flow. |
| enableIdTokenIssuance | Boolean | Specifies whether this web application can request an ID token using the OAuth 2.0 implicit flow. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "enableIdTokenIssuance": "Boolean",
  "enableAccessTokenIssuance": "Boolean"
}
```
