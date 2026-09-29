<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# governanceRequest resource type

Namespace: microsoft.graph

Represents a request from a governing tenant to establish a governance relationship with a governed tenant. The governed tenant can accept or reject the request. When accepted, a [governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-1.0) is created.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-list-governancerequests?view=graph-rest-1.0) | [microsoft.graph.governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0) collection | Get a list of the [governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-post-governancerequests?view=graph-rest-1.0) | [microsoft.graph.governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0) | Create a new governance request to establish a relationship with a governed tenant. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governancerequest-get?view=graph-rest-1.0) | [microsoft.graph.governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0) | Read the properties of a [governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governancerequest-update?view=graph-rest-1.0) | [microsoft.graph.governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0) | Update the **status** property to accept or reject the governance request. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expirationDateTime | DateTimeOffset | The date and time when the request expires if not accepted or rejected. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |
| governedTenantId | String | The Microsoft Entra tenant ID of the governed tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governedTenantName | String | The display name of the governed tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governingTenantId | String | The Microsoft Entra tenant ID of the governing tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governingTenantName | String | The display name of the governing tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| id | String | The unique identifier for the governance request.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| policySnapshot | [microsoft.graph.relationshipPolicy](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relationshippolicy?view=graph-rest-1.0) | A snapshot of the governance policy to be applied if the request is accepted, including delegated administration role assignments and multi-tenant applications to provision. |
| requestDateTime | DateTimeOffset | The date and time when the request was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |
| status | microsoft.graph.requestStatus | The current status of the governance request. The possible values are: `pending`, `accepted`, `rejected`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| governancePolicyTemplate | [microsoft.graph.tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-1.0) | The governance policy template associated with this request. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.governanceRequest",
  "id": "String (identifier)",
  "governingTenantId": "String",
  "governingTenantName": "String",
  "governedTenantId": "String",
  "governedTenantName": "String",
  "expirationDateTime": "String (timestamp)",
  "requestDateTime": "String (timestamp)",
  "status": "String",
  "policySnapshot": {
    "@odata.type": "microsoft.graph.relationshipPolicy"
  }
}
```
