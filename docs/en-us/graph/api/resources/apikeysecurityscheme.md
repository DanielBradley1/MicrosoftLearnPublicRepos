<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/apikeysecurityscheme?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# apiKeySecurityScheme resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an API key security scheme used for authenticating API requests. API key authentication is a simple authentication method where a unique key is passed in the request to identify and authenticate the caller. This resource is configured in the **securitySchemes** property of the [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta).

Inherits from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description of the security scheme. Inherited from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta). |
| in | String | The location of the API key. The possible values are: `query`, `header`, or `cookie`. |
| name | String | The name of the API key parameter \(for example, `api_key` or `X-API-Key`\). |
| type | String | The type of the security scheme. Inherited from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.apiKeySecurityScheme",
  "type": "String",
  "description": "String",
  "name": "String",
  "in": "String"
}
```
