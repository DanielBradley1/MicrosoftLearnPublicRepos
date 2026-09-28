<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantrelationship?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# tenantRelationship resource type

Namespace: microsoft.graph

Represent the various type of tenant relationships.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| delegatedAdminCustomers | [delegatedAdminCustomer](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadmincustomer?view=graph-rest-1.0) collection | The customer who has a delegated admin relationship with a Microsoft partner. |
| delegatedAdminRelationships | [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0) collection | The details of the delegated administrative privileges that a Microsoft partner has in a customer tenant. |
| multiTenantOrganization | [multiTenantOrganization](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganization?view=graph-rest-1.0) | Defines an organization with more than one instance of Microsoft Entra ID. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tenantRelationship"
}
```
