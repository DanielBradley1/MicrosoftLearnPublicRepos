<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/spaapplication?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# spaApplication resource type

Namespace: microsoft.graph

Specifies settings for a single-page application.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| redirectUris | String collection | Specifies the URLs where user tokens are sent for sign-in, or the redirect URIs where OAuth 2.0 authorization codes and access tokens are sent. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "redirectUris": ["String"]
}
```
