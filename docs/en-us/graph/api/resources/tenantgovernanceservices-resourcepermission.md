<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-resourcepermission?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# applicationResourcePermission resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a permission required by an application to access a resource. This is used when defining the permissions needed by multi-tenant applications provisioned in governed tenants. This resource is defined in the **permissions** property of [applicationsRequiredResourceAccess](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-applicationsrequiredresourceaccess?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the permission. |
| name | String | The name of the permission. |
| type | [applicationPermissionType](https://learn.microsoft.com/en-us/graph/api/resources/enums-tenantgovernanceservices?view=graph-rest-beta#applicationpermissiontype-values) | The type of permission. The possible values are: `role`, `scope`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.applicationResourcePermission",
  "id": "String",
  "name": "String",
  "type": "String"
}
```
