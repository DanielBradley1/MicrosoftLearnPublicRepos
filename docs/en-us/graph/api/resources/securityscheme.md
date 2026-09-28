<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# securityScheme resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines a security scheme that can be used by the operations, as defined in the [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta).

This is an abstract type from which the following types inherit:

- [apiKeySecurityScheme](https://learn.microsoft.com/en-us/graph/api/resources/apikeysecurityscheme?view=graph-rest-beta)
- [httpAuthSecurityScheme](https://learn.microsoft.com/en-us/graph/api/resources/httpauthsecurityscheme?view=graph-rest-beta)
- [mutualTLSSecurityScheme](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlssecurityscheme?view=graph-rest-beta)
- [oAuth2SecurityScheme](https://learn.microsoft.com/en-us/graph/api/resources/oauth2securityscheme?view=graph-rest-beta)
- [openIdConnectSecurityScheme](https://learn.microsoft.com/en-us/graph/api/resources/openidconnectsecurityscheme?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description for security scheme. |
| type | String | The type of the security scheme. Valid values are "apiKey", "http", "mutualTLS", "oauth2", "openIdConnect". |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.securityScheme",
  "type": "String",
  "description": "String"
}
```
