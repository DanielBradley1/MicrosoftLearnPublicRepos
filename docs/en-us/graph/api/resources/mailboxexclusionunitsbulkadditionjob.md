<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailboxexclusionunitsbulkadditionjob?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# mailboxExclusionUnitsBulkAdditionJob resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an async job for bulk-adding mailbox exclusion units to an [Exchange protection policy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-beta) configured for full workload backup.

The initial status upon creation of the job is `active`. When all the mailboxes are added to the corresponding Exchange protection policy as exclusion units, the status of the job is `completed`. If any failures occur, the status of the job is `completedWithErrors`.

Inherits from [exclusionUnitBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbulkadditionjob?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/exchangeprotectionpolicy-list-mailboxexclusionunitsbulkadditionjobs?view=graph-rest-beta) | [mailboxExclusionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/mailboxexclusionunitsbulkadditionjob?view=graph-rest-beta) collection | Get a list of [mailbox exclusion units bulk addition jobs](https://learn.microsoft.com/en-us/graph/api/resources/mailboxexclusionunitsbulkadditionjob?view=graph-rest-beta) associated with an [Exchange protection policy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-beta). |
| [Create](https://learn.microsoft.com/en-us/graph/api/exchangeprotectionpolicy-post-mailboxexclusionunitsbulkadditionjobs?view=graph-rest-beta) | [mailboxExclusionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/mailboxexclusionunitsbulkadditionjob?view=graph-rest-beta) | Create a [mailbox exclusion units bulk addition job](https://learn.microsoft.com/en-us/graph/api/resources/mailboxexclusionunitsbulkadditionjob?view=graph-rest-beta) for an [Exchange protection policy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-beta). |
| [Get](https://learn.microsoft.com/en-us/graph/api/mailboxexclusionunitsbulkadditionjob-get?view=graph-rest-beta) | [mailboxExclusionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/mailboxexclusionunitsbulkadditionjob?view=graph-rest-beta) | Get a [mailbox exclusion units bulk addition job](https://learn.microsoft.com/en-us/graph/api/resources/mailboxexclusionunitsbulkadditionjob?view=graph-rest-beta) associated with an [Exchange protection policy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the person who created the bulk addition job. Inherited from [exclusionUnitBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbulkadditionjob?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the bulk addition job was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [exclusionUnitBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbulkadditionjob?view=graph-rest-beta). |
| displayName | String | The display name of the bulk addition job. Inherited from [exclusionUnitBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbulkadditionjob?view=graph-rest-beta). |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | Contains error details if the bulk addition job failed. Inherited from [exclusionUnitBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbulkadditionjob?view=graph-rest-beta). |
| id | String | The unique identifier of the bulk addition job. Inherited from [exclusionUnitBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbulkadditionjob?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the person who last modified the bulk addition job. Inherited from [exclusionUnitBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbulkadditionjob?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the bulk addition job was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [exclusionUnitBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbulkadditionjob?view=graph-rest-beta). |
| mailboxes | String collection | The email addresses of the mailboxes to be added as exclusion units to the protection policy. |
| status | [exclusionUnitBulkJobStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#exclusionunitbulkjobstatus-values) | The status of the bulk addition job. The possible values are: `created`, `active`, `completed`, `completedWithErrors`, `unknownFutureValue`. Inherited from [exclusionUnitBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbulkadditionjob?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mailboxExclusionUnitsBulkAdditionJob",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "mailboxes": ["String"],
  "status": "String"
}
```
