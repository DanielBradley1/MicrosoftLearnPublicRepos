<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/oauthflows?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# oAuthFlows resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Allows configuration of the supported OAuth Flows for an [OAuth 2.0 security scheme](https://learn.microsoft.com/en-us/graph/api/resources/oauth2securityscheme?view=graph-rest-beta) used for authenticating API requests.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authorizationCode | [oAuthFlow](https://learn.microsoft.com/en-us/graph/api/resources/oauthflow?view=graph-rest-beta) | Configuration for the OAuth Authorization Code flow. |
| clientCredentials | [oAuthFlow](https://learn.microsoft.com/en-us/graph/api/resources/oauthflow?view=graph-rest-beta) | Configuration for the OAuth Client Credentials flow. |
| implicit | [oAuthFlow](https://learn.microsoft.com/en-us/graph/api/resources/oauthflow?view=graph-rest-beta) | Configuration for the OAuth Implicit flow |
| password | [oAuthFlow](https://learn.microsoft.com/en-us/graph/api/resources/oauthflow?view=graph-rest-beta) | Configuration for the OAuth Resource Owner Password flow |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.oAuthFlows",
  "implicit": {
    "@odata.type": "microsoft.graph.oAuthFlow"
  },
  "password": {
    "@odata.type": "microsoft.graph.oAuthFlow"
  },
  "clientCredentials": {
    "@odata.type": "microsoft.graph.oAuthFlow"
  },
  "authorizationCode": {
    "@odata.type": "microsoft.graph.oAuthFlow"
  }
}
```
