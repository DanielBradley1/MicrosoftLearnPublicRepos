<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# governanceRequest resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a request from a governing tenant to establish a governance relationship with a governed tenant. The governed tenant can accept or reject the request. When accepted, a [governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-beta) is created.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-list-governancerequests?view=graph-rest-beta) | [microsoft.graph.governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-beta) collection | Get a list of the [governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-post-governancerequests?view=graph-rest-beta) | [microsoft.graph.governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-beta) | Create a new governance request to establish a relationship with a governed tenant. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governancerequest-get?view=graph-rest-beta) | [microsoft.graph.governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-beta) | Read the properties of a [governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governancerequest-update?view=graph-rest-beta) | [microsoft.graph.governanceRequest](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-beta) | Update the **status** property to accept or reject the governance request. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expirationDateTime | DateTimeOffset | The date and time when the request expires if not accepted or rejected. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |
| governedTenantId | String | The Microsoft Entra tenant ID of the governed tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governedTenantName | String | The display name of the governed tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governingTenantId | String | The Microsoft Entra tenant ID of the governing tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governingTenantName | String | The display name of the governing tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| id | String | The unique identifier for the governance request. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| policySnapshot | [microsoft.graph.relationshipPolicy](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relationshippolicy?view=graph-rest-beta) | A snapshot of the governance policy to be applied if the request is accepted, including delegated administration role assignments and multi-tenant applications to provision. |
| requestDateTime | DateTimeOffset | The date and time when the request was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |
| status | microsoft.graph.requestStatus | The current status of the governance request. The possible values are: `pending`, `accepted`, `rejected`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| governancePolicyTemplate | [microsoft.graph.tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-beta) | The governance policy template associated with this request. |

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
