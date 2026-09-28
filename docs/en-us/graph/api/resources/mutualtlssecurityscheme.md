<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mutualtlssecurityscheme?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# mutualTLSSecurityScheme resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a mutual TLS security scheme used for authenticating API requests. This resource is configured in the **securitySchemes** property of the [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta).

Inherits from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description of the security scheme. Inherited from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta). |
| type | String | The type of the security scheme. Inherited from [securityScheme](https://learn.microsoft.com/en-us/graph/api/resources/securityscheme?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mutualTLSSecurityScheme",
  "type": "String",
  "description": "String"
}
```
