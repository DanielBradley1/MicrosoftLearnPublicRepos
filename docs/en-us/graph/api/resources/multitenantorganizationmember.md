<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationmember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# multiTenantOrganizationMember resource type

Namespace: microsoft.graph

Defines a tenant added to a multitenant organization.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/multitenantorganization-list-tenants?view=graph-rest-1.0) | [multiTenantOrganizationMember](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationmember?view=graph-rest-1.0) collection | List the tenants and their properties in the multitenant organization. |
| [Add](https://learn.microsoft.com/en-us/graph/api/multitenantorganization-post-tenants?view=graph-rest-1.0) | [multiTenantOrganizationMember](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationmember?view=graph-rest-1.0) | Add a tenant to a multitenant organization. |
| [Get](https://learn.microsoft.com/en-us/graph/api/multitenantorganizationmember-get?view=graph-rest-1.0) | [multiTenantOrganizationMember](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationmember?view=graph-rest-1.0) | Get a tenant and its properties in the multitenant organization. |
| [Update](https://learn.microsoft.com/en-us/graph/api/multitenantorganizationmember-update?view=graph-rest-1.0) | [multiTenantOrganizationMember](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationmember?view=graph-rest-1.0) | Update the properties of a tenant in a multitenant organization. |
| [Remove](https://learn.microsoft.com/en-us/graph/api/multitenantorganization-delete-tenants?view=graph-rest-1.0) | None | Remove a tenant from a multitenant organization. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addedByTenantId | String | Tenant ID of the tenant that added the tenant to the multitenant organization. Read-only. |
| addedDateTime | DateTimeOffset | Date and time when the tenant was added to the multitenant organization. Read-only. |
| displayName | String | Display name of the tenant added to the multitenant organization. |
| joinedDateTime | DateTimeOffset | Date and time when the tenant joined the multitenant organization. Read-only. |
| role | multiTenantOrganizationMemberRole | Role of the tenant in the multitenant organization. The possible values are: `owner`, `member` \(default\), `unknownFutureValue`. Tenants with the owner role can manage the multitenant organization but tenants with the member role can only participate in a multitenant organization. There can be multiple tenants with the owner role in a multitenant organization. |
| state | multiTenantOrganizationMemberState | State of the tenant in the multitenant organization. The possible values are: `pending`, `active`, `removed`, `unknownFutureValue`. Tenants in the pending state must [join the multitenant organization](https://learn.microsoft.com/en-us/graph/api/multitenantorganizationjoinrequestrecord-update?view=graph-rest-1.0) to participate in the multitenant organization. Tenants in the active state can participate in the multitenant organization. Tenants in the removed state are in the process of being removed from the multitenant organization. Read-only. |
| tenantId | String | Tenant ID of the Microsoft Entra tenant added to the multitenant organization. Set at the time tenant is added.  <br>  <br>Supports `$filter`. Key. |
| transitionDetails | [multiTenantOrganizationMemberTransitionDetails](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationmembertransitiondetails?view=graph-rest-1.0) | Details of the processing status for a tenant in a multitenant organization. Read-only. Nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantOrganizationMember",
  "tenantId": "String (identifier)",
  "displayName": "String",
  "addedDateTime": "String (timestamp)",
  "joinedDateTime": "String (timestamp)",
  "addedByTenantId": "String",
  "role": "String",
  "state": "String",
  "transitionDetails": {
    "@odata.type": "microsoft.graph.multiTenantOrganizationMemberTransitionDetails"
  }
}
```
