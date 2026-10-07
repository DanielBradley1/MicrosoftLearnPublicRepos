<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationstoprovisionsnapshot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# multiTenantApplicationsToProvisionSnapshot resource type

Namespace: microsoft.graph

Represents a snapshot of a multi-tenant application configuration that was captured when a [governance relationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-1.0) or [request](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0) was created. This preserves the application configuration as it was defined at that point in time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The **appId** \(client ID\) of the multi-tenant application. |
| displayName | String | The display name of the application. |
| objectId | String | The object ID of the service principal in the governing tenant. |
| requiredResourceAccesses | [microsoft.graph.applicationsRequiredResourceAccess](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-applicationsrequiredresourceaccess?view=graph-rest-1.0) collection | The collection of resource accesses \(permissions\) required by the application. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantApplicationsToProvisionSnapshot",
  "appId": "String",
  "objectId": "String",
  "displayName": "String",
  "requiredResourceAccesses": [
    {
      "@odata.type": "microsoft.graph.applicationsRequiredResourceAccess"
    }
  ]
}
```
