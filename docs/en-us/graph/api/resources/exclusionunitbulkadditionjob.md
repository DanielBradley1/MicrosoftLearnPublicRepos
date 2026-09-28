<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbulkadditionjob?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# exclusionUnitBulkAdditionJob resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the abstract base entity for an async job that bulk-adds exclusion units to a protection policy.

This resource is the base type for [siteExclusionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteexclusionunitsbulkadditionjob?view=graph-rest-beta), [driveExclusionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/driveexclusionunitsbulkadditionjob?view=graph-rest-beta), and [mailboxExclusionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/mailboxexclusionunitsbulkadditionjob?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the person who created the bulk addition job. |
| createdDateTime | DateTimeOffset | The date and time when the bulk addition job was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | The display name of the bulk addition job. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | Contains error details if the bulk addition job failed. |
| id | String | The unique identifier of the bulk addition job. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the person who last modified the bulk addition job. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the bulk addition job was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| status | [exclusionUnitBulkJobStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#exclusionunitbulkjobstatus-values) | The status of the bulk addition job. The possible values are: `created`, `active`, `completed`, `completedWithErrors`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.exclusionUnitBulkAdditionJob",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "status": "String"
}
```
