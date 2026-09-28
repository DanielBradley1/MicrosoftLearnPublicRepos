<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosscloudazureactivedirectorytenant?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# crossCloudAzureActiveDirectoryTenant resource type

Namespace: microsoft.graph

Used in the **identitySources** property of a [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) object. The `@odata.type` value `#microsoft.graph.crossCloudAzureActiveDirectoryTenant` indicates that this type identifies another Microsoft Entra tenant in a different cloud as an identity source for a connected organization.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudInstance | String | The ID of the cloud where the tenant is located, one of `microsoftonline.com`, `microsoftonline.us` or `partner.microsoftonline.cn`. Read-only. |
| displayName | String | The name of the Microsoft Entra tenant. Read-only. |
| tenantId | String | The ID of the Microsoft Entra tenant. Read-only. |

## Relationships

None.

## JSON representation

The following is a JSON representation of the type.

```json
{
  "tenantId": "String (identifier)",
  "displayName": "String",
  "cloudInstance": "String"
}
```
