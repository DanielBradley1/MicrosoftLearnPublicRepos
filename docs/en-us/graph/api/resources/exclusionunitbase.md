<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# exclusionUnitBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the abstract base entity for an exclusion unit that specifies artifacts to be excluded from full workload backup.

Full workload backup policies use an exclusion unit pattern. After creating a protection policy with [backupPolicyProtectionMode](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#backuppolicyprotectionmode-values) set to `fullServiceBackup`, you can manage the exclusion list using a delta pattern on the policy update endpoint \(**siteExclusionUnits@delta**, **driveExclusionUnits@delta**, or **mailboxExclusionUnits@delta**\). For bulk operations, use the dedicated [bulk addition job](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbulkadditionjob?view=graph-rest-beta) APIs.

This resource is the base type for [siteExclusionUnit](https://learn.microsoft.com/en-us/graph/api/resources/siteexclusionunit?view=graph-rest-beta), [driveExclusionUnit](https://learn.microsoft.com/en-us/graph/api/resources/driveexclusionunit?view=graph-rest-beta), and [mailboxExclusionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxexclusionunit?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the person who created the exclusion unit. |
| createdDateTime | DateTimeOffset | The date and time when the exclusion unit was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | Contains error details if the exclusion unit is in a failed state. |
| id | String | The unique identifier of the exclusion unit. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the person who last modified the exclusion unit. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the exclusion unit was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| policyId | String | The unique identifier of the protection policy that contains this exclusion unit. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.exclusionUnitBase",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "policyId": "String"
}
```
