<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# governanceInvitation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an invitation sent by a future governed tenant to a future governing tenant. This invitation authorizes the governing tenant to send a [governance request](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-beta) to the governed tenant to establish a [governance relationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-beta). The invitation expires after 30 days.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-list-governanceinvitations?view=graph-rest-beta) | [microsoft.graph.governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-beta) collection | Get a list of the [governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-post-governanceinvitations?view=graph-rest-beta) | [microsoft.graph.governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-beta) | Create a new governance invitation. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governanceinvitation-get?view=graph-rest-beta) | [microsoft.graph.governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-beta) | Read the properties of a [governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governanceinvitation-delete?view=graph-rest-beta) | None | Delete a governance invitation. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the invitation was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |
| expirationDateTime | DateTimeOffset | The date and time when the invitation expires. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |
| governedTenantId | String | The Microsoft Entra tenant ID of the governed tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governedTenantName | String | The display name of the governed tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governingTenantId | String | The Microsoft Entra tenant ID of the governing tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governingTenantName | String | The display name of the governing tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| id | String | The unique identifier for the governance invitation. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.governanceInvitation",
  "id": "String (identifier)",
  "governingTenantId": "String",
  "governedTenantId": "String",
  "governingTenantName": "String",
  "governedTenantName": "String",
  "createdDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)"
}
```
