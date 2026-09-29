<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-applicationsrequiredresourceaccess?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# applicationsRequiredResourceAccess resource type

Namespace: microsoft.graph

Represents the permissions required by an application to access a specific resource. This is used when [defining multi-tenant applications to provision in governed tenants](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationstoprovisionsnapshot?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| permissions | [microsoft.graph.applicationResourcePermission](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-applicationresourcepermission?view=graph-rest-1.0) collection | The collection of resource permissions required by the application. |
| resourceAppId | String | The **appId** \(client ID\) of the resource that the application needs to access. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.applicationsRequiredResourceAccess",
  "resourceAppId": "String",
  "permissions": [
    {
      "@odata.type": "microsoft.graph.applicationResourcePermission"
    }
  ]
}
```
