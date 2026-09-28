<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resellerdelegatedadminrelationship?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# resellerDelegatedAdminRelationship resource type

Namespace: microsoft.graph

Represents the details of the delegated administrative privileges that a Microsoft indirect reseller partner has in a customer tenant that is created by a Microsoft indirect provider partner.

Inherits from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessDetails | [delegatedAdminAccessDetails](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessdetails?view=graph-rest-1.0) | The access details that contain the identifiers of the administrative roles that the partner administrator requests in the customer tenant. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| activatedDateTime | DateTimeOffset | The date and time when the relationship was activated. Read-only. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| autoExtendDuration | Duration | The duration by which the validity of the relationship is automatically extended, denoted in ISO 8601 format. Supported values are: `P0D`, `PT0S`, `P180D`. The default value is `PT0S`. `PT0S` indicates that the relationship expires when the **endDateTime** is reached and it isn't automatically extended. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the relationship was created. Read-only. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| customer | [delegatedAdminRelationshipCustomerParticipant](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshipcustomerparticipant?view=graph-rest-1.0) | The display name and unique identifier of the customer of the relationship. This is configured either by the partner at the time the relationship is created or by the system after the customer approves the relationship. Cannot be changed by the customer. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| displayName | String | The display name of the relationship used for ease of identification. Must be unique across *all* delegated admin relationships of the partner. This is set by the partner only when the relationship is in the `created` **status** and cannot be changed by the customer. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| duration | Duration | The duration of the relationship in ISO 8601 format. Must be a value between `P1D` and `P2Y` inclusive. This is set by the partner only when the relationship is in the `created` **status** and cannot be changed by the customer. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| endDateTime | DateTimeOffset | The date and time when the **status** of the relationship changes to either `terminated` or `expired`. Calculated as `endDateTime = activatedDateTime + duration`. Read-only. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| id | String | The unique identifier of the relationship. Read-only. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| indirectProviderTenantId | String | The tenant ID of the indirect provider partner who created the relationship for the indirect reseller partner. |
| isPartnerConsentPending | Boolean | Indicates the indirect reseller partner consent status. `true` indicates that the partner has yet to review the relationship; `false` indicates that the partner has already provided consent by approving or rejecting the relationship. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the relationship was last modified. Read-only. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| status | delegatedAdminRelationshipStatus | The status of the relationship. Read-only. The possible values are: `activating`, `active`, `approvalPending`, `approved`, `created`, `expired`, `expiring`, `terminated`, `terminating`, `terminationRequested`, `unknownFutureValue`. Supports `$orderBy`. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessAssignments | [delegatedAdminAccessAssignment](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessassignment?view=graph-rest-1.0) collection | The access assignments associated with the delegated admin relationship. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| operations | [delegatedAdminRelationshipOperation](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshipoperation?view=graph-rest-1.0) collection | The long-running operations associated with the delegated admin relationship. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |
| requests | [delegatedAdminRelationshipRequest](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationshiprequest?view=graph-rest-1.0) collection | The requests associated with the delegated admin relationship. Inherited from [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.resellerDelegatedAdminRelationship",
  "accessDetails": {"@odata.type": "microsoft.graph.delegatedAdminAccessDetails"},
  "activatedDateTime": "String (timestamp)",
  "autoExtendDuration": "String (duration)",
  "createdDateTime": "String (timestamp)",
  "customer": {"@odata.type": "microsoft.graph.delegatedAdminRelationshipCustomerParticipant"},
  "displayName": "String",
  "duration": "String (duration)",
  "endDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "indirectProviderTenantId": "String",
  "isPartnerConsentPending": "Boolean",
  "lastModifiedDateTime": "String (timestamp)",
  "status": "String"
}
```
