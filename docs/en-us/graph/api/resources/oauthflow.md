<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/oauthflow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# oAuthFlow resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An object containing configuration information for a supported [OAuth flow](https://learn.microsoft.com/en-us/graph/api/resources/oauthflows?view=graph-rest-beta) in an [oAuth2SecurityScheme](https://learn.microsoft.com/en-us/graph/api/resources/oauth2securityscheme?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authorizationUrl | String | The authorization URL to be used for this flow. This MUST be in the form of a URL. The OAuth2 standard requires the use of TLS. |
| refreshUrl | String | The URL to be used for obtaining refresh tokens. This MUST be in the form of a URL. The OAuth2 standard requires the use of TLS. |
| scopes | [oAuthScopeDictionary](https://learn.microsoft.com/en-us/graph/api/resources/oauthscopedictionary?view=graph-rest-beta) | The available scopes for the OAuth2 security scheme. A map between the scope name and a short description for it. The map MAY be empty. |
| tokenUrl | String | The token URL to be used for this flow. This MUST be in the form of a URL. The OAuth2 standard requires the use of TLS. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.oAuthFlow",
  "authorizationUrl": "String",
  "tokenUrl": "String",
  "refreshUrl": "String",
  "scopes": {
    "@odata.type": "microsoft.graph.oAuthScopeDictionary"
  }
}
```
