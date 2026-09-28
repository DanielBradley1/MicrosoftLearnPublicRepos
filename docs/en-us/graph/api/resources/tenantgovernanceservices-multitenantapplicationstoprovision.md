<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationstoprovision?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# multiTenantApplicationsToProvision resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a multi-tenant application that should be provisioned in the governed tenant when a governance relationship is established. This allows the governing tenant to deploy management or monitoring applications into the governed tenant. This resource is defined in the **multiTenantApplicationsToProvision** property of [governancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The **appId** \(client ID\) of the multi-tenant application. |
| displayName | String | The display name of the application. |
| objectId | String | The object ID of the service principal in the governing tenant. |
| requiredResourceAccesses | [microsoft.graph.applicationsRequiredResourceAccess](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-applicationsrequiredresourceaccess?view=graph-rest-beta) collection | The collection of resource accesses \(permissions\) required by the application. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantApplicationsToProvision",
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
