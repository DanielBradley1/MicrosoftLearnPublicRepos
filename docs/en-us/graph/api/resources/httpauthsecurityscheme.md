<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/httpauthsecurityscheme?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# httpAuthSecurityScheme resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an HTTP authentication security scheme used for authenticating API requests. HTTP authentication allows various authentication methods to be used via the HTTP Authorization header, such as Bearer tokens, Basic authentication, and other custom schemes. This resource is configured in the **securitySchemes** property of the [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta).

Inherits from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bearerFormat | String | A hint about the format of the bearer token when using Bearer authentication. For example, `JWT` for JSON Web Tokens. |
| description | String | A description of the security scheme. Inherited from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta). |
| scheme | String | The name of the HTTP authentication scheme to be used in the Authorization header. Common values include `bearer`, `basic`, `digest`, or custom scheme names. |
| type | String | The type of the security scheme. Inherited from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.httpAuthSecurityScheme",
  "type": "String",
  "description": "String",
  "scheme": "String",
  "bearerFormat": "String"
}
```
