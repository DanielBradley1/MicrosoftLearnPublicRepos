<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/oauth2securityscheme?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# oAuth2SecurityScheme resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an OAuth 2.0 security scheme used for authenticating API requests. This resource is configured in the **securitySchemes** property of the [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta).

Inherits from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description of the security scheme. Inherited from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta). |
| flows | [oAuthFlows](https://learn.microsoft.com/en-us/graph/api/resources/oauthflows?view=graph-rest-beta) | The OAuth 2.0 flows \(grant types\) supported by this security scheme, such as authorization code, client credentials, implicit, and password flows. |
| type | String | The type of the security scheme. Inherited from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.oAuth2SecurityScheme",
  "type": "String",
  "description": "String",
  "flows": {
    "@odata.type": "microsoft.graph.oAuthFlows"
  }
}
```
