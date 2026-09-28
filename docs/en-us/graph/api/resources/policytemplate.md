<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policytemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-25 -->

# policyTemplate resource type

Namespace: microsoft.graph

Represents the base policy in the directory for multitenant organization settings.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ID of the template. Key. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| multiTenantOrganizationIdentitySynchronization | [multiTenantOrganizationIdentitySyncPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationidentitysyncpolicytemplate?view=graph-rest-1.0) | Defines an optional cross-tenant access policy template with user synchronization settings for a multitenant organization. |
| multiTenantOrganizationPartnerConfiguration | [multiTenantOrganizationPartnerConfigurationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationpartnerconfigurationtemplate?view=graph-rest-1.0) | Defines an optional cross-tenant access policy template with inbound and outbound partner configuration settings for a multitenant organization. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.policyTemplate"
}
```
