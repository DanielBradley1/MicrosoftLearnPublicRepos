<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureactivedirectorytenant?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# azureActiveDirectoryTenant resource type

Namespace: microsoft.graph

Used in the **identitySources** property of a [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0). The `@odata.type` value `#microsoft.graph.azureActiveDirectoryTenant` indicates that this type identifies another Microsoft Entra tenant as an identity source for a connected organization.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the Microsoft Entra tenant. Read-only. |
| tenantId | String | The ID of the Microsoft Entra tenant. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureActiveDirectoryTenant",
  "displayName": "String",
  "tenantId": "String"
}
```
