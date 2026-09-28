<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webapplication?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# webApplication resource type

Namespace: microsoft.graph

Specifies settings for a web application.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| homePageUrl | String | Home page or landing page of the application. |
| implicitGrantSettings | [implicitGrantSettings](https://learn.microsoft.com/en-us/graph/api/resources/implicitgrantsettings?view=graph-rest-1.0) | Specifies whether this web application can request tokens using the OAuth 2.0 implicit flow. |
| logoutUrl | String | Specifies the URL that is used by Microsoft's authorization service to log out a user using [front-channel](https://openid.net/specs/openid-connect-frontchannel-1_0.html), [back-channel](https://openid.net/specs/openid-connect-backchannel-1_0.html) or SAML logout protocols. |
| redirectUris | String collection | Specifies the URLs where user tokens are sent for sign-in, or the redirect URIs where OAuth 2.0 authorization codes and access tokens are sent. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "homePageUrl": "String",
  "implicitGrantSettings": {"@odata.type": "microsoft.graph.implicitGrantSettings"},
  "logoutUrl": "String",
  "redirectUris": ["String"]
}
```
