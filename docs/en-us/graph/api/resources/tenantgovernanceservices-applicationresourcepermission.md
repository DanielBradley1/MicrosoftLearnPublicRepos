<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-applicationresourcepermission?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# applicationResourcePermission resource type

Namespace: microsoft.graph

Represents a permission required by an application to access a resource. This is used when defining the permissions needed by multi-tenant applications provisioned in governed tenants. This resource is defined in the **permissions** property of [applicationsRequiredResourceAccess](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-applicationsrequiredresourceaccess?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the permission. |
| name | String | The name of the permission. |
| type | [applicationPermissionType](https://learn.microsoft.com/en-us/graph/api/resources/enums-tenantgovernanceservices?view=graph-rest-1.0#applicationpermissiontype-values) | The type of permission. The possible values are: `role`, `scope`, `unknownFutureValue`. |

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
