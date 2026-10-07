<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# governanceInvitation resource type

Namespace: microsoft.graph

Represents an invitation sent by a future governed tenant to a future governing tenant. This invitation authorizes the governing tenant to send a [governance request](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerequest?view=graph-rest-1.0) to the governed tenant to establish a [governance relationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0). The invitation expires after 30 days.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-list-governanceinvitations?view=graph-rest-1.0) | [microsoft.graph.governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0) collection | Get a list of the [governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-post-governanceinvitations?view=graph-rest-1.0) | [microsoft.graph.governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0) | Create a new governance invitation. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governanceinvitation-get?view=graph-rest-1.0) | [microsoft.graph.governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0) | Read the properties of a [governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governanceinvitation-delete?view=graph-rest-1.0) | None | Delete a governance invitation. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the invitation was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |
| expirationDateTime | DateTimeOffset | The date and time when the invitation expires. The timestamp type represents date and time information using ISO 8601 format and is always in UTC.  <br>  <br>Supports `$filter` \(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderBy`. |
| governedTenantId | String | The Microsoft Entra tenant ID of the governed tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governedTenantName | String | The display name of the governed tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governingTenantId | String | The Microsoft Entra tenant ID of the governing tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| governingTenantName | String | The display name of the governing tenant.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |
| id | String | The unique identifier for the governance invitation.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderBy`. |

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
