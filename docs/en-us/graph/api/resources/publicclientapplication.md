<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/publicclientapplication?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# publicClientApplication resource type

Namespace: microsoft.graph

Specifies settings for nonweb app or nonweb API \(for example, mobile or other public clients such as an installed application running on a desktop device\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| redirectUris | String collection | Specifies the URLs where user tokens are sent for sign-in, or the redirect URIs where OAuth 2.0 authorization codes and access tokens are sent. For iOS and macOS apps, specify the value following the syntax `msauth.{BUNDLEID}://auth`, replacing "{BUNDLEID}". For example, if the bundle ID is `com.microsoft.identitysample.MSALiOS`, the URI is `msauth.com.microsoft.identitysample.MSALiOS://auth`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "redirectUris": ["String"]
}
```
