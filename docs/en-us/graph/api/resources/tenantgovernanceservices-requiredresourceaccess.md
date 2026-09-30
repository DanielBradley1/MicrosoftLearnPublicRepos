<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-requiredresourceaccess?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# applicationsRequiredResourceAccess resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the permissions required by an application to access a specific resource. This is used when [defining multi-tenant applications to provision in governed tenants](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationstoprovisionsnapshot?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| permissions | [microsoft.graph.applicationResourcePermission](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-applicationresourcepermission?view=graph-rest-beta) collection | The collection of resource permissions required by the application. |
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
