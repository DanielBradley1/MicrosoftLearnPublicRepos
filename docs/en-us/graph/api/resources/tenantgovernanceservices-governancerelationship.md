<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# governanceRelationship resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an established governance relationship between a governing tenant and a governed tenant. A governance relationship is created when a [governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-beta) is accepted by the governed tenant.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-list-governancerelationships?view=graph-rest-beta) | [microsoft.graph.governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-beta) collection | Get a list of the [governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governancerelationship-get?view=graph-rest-beta) | [microsoft.graph.governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-beta) | Read the properties of a [governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governancerelationship-update?view=graph-rest-beta) | [microsoft.graph.governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-beta) | Update the **status** property to initiate termination of the governance relationship. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdType | microsoft.graph.relationshipCreationType | Indicates how the relationship was created. The possible values are: `approvedByAdmin`, `addOnTenant`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| creationDateTime | DateTimeOffset | The date and time when the relationship was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2026 is `2026-01-01T00:00:00Z`.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |
| governedTenantId | String | The Microsoft Entra tenant ID of the governed tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governedTenantName | String | The display name of the governed tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governingTenantId | String | The Microsoft Entra tenant ID of the governing tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governingTenantName | String | The display name of the governing tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| id | String | The unique identifier for the governance relationship. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| policySnapshot | [microsoft.graph.relationshipPolicy](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relationshippolicy?view=graph-rest-beta) | A snapshot of the governance policy applied to this relationship, including delegated administration role assignments and multi-tenant applications to provision. |
| status | microsoft.graph.relationshipStatus | The current status of the governance relationship. The possible values are: `active`, `terminated`, `terminationRequestedByGoverningTenant`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.governanceRelationship",
  "createdType": "String",
  "creationDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "status": "String",
  "governingTenantId": "String",
  "governedTenantId": "String",
  "governingTenantName": "String",
  "governedTenantName": "String",
  "policySnapshot": {
    "@odata.type": "microsoft.graph.relationshipPolicy"
  }
}
```
