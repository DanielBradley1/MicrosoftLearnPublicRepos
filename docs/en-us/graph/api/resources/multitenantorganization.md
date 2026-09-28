<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# multiTenantOrganization resource type

Namespace: microsoft.graph

Defines an organization with more than one instance of Microsoft Entra ID. A multitenant organization enables multiple tenants to collaborate like a single entity.

There can only be one multitenant organization per active tenant. It is not possible to be part of multiple multitenant organizations.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/tenantrelationship-put-multitenantorganization?view=graph-rest-1.0) | [multiTenantOrganization](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganization?view=graph-rest-1.0) | Create a new multitenant organization. |
| [Get](https://learn.microsoft.com/en-us/graph/api/multitenantorganization-get?view=graph-rest-1.0) | [multiTenantOrganization](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganization?view=graph-rest-1.0) | Get properties of the multitenant organization. |
| [Update](https://learn.microsoft.com/en-us/graph/api/multitenantorganization-update?view=graph-rest-1.0) | [multiTenantOrganization](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganization?view=graph-rest-1.0) | Update the properties of a multitenant organization. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Date when multitenant organization was created. Read-only. |
| description | String | Description of the multitenant organization. |
| displayName | String | Display name of the multitenant organization. |
| id | String | Tenant-specific object ID for the multitenant organization object. It is automatically generated when a multitenant organization object is created and stored in the local tenant. This ID is tenant-specific and doesn't match the object IDs of the same multitenant organization in other tenants. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| state | multiTenantOrganizationState | State of the multitenant organization. The possible values are: `active`, `inactive`, `unknownFutureValue`. `active` indicates the multitenant organization is created. `inactive` indicates the multitenant organization isn't created. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| joinRequest | [multiTenantOrganizationJoinRequestRecord](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationjoinrequestrecord?view=graph-rest-1.0) | Defines the status of a tenant joining a multitenant organization. |
| tenants | [multiTenantOrganizationMember](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationmember?view=graph-rest-1.0) collection | Defines tenants added to a multitenant organization. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantOrganization",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "description": "String",
  "state": "String"
}
```
