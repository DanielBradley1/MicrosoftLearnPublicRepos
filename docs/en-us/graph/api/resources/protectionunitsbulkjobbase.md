<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/protectionunitsbulkjobbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-02 -->

# protectionUnitsBulkJobBase resource type

Namespace: microsoft.graph

Represents a bulk job associated with one of the protection policies, as specified by the client as part of a protection plan applied to Microsoft 365 data in an organization.

This abstract type is the base type for [siteProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunitsbulkadditionjob?view=graph-rest-1.0), [mailboxProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunitsbulkadditionjob?view=graph-rest-1.0), and [driveProtectionUnitsBulkAdditionJob](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionunitsbulkadditionjob?view=graph-rest-1.0).

Note

The protection units bulk addition job APIs for bulk addition of protection units in the backup policy can accommodate a maximum of 50,000 protection resources in a single job.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of person who created the job. |
| createdDateTime | DateTimeOffset | The time of creation of the job. |
| displayName | String | The name of the protection units bulk addition job. |
| id | String | The unique identifier of the bulk job associated with the policy. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Error details containing resource resolution failures, if any. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who last modified the job. |
| lastModifiedDateTime | DateTimeOffset | Timestamp of the last modification made to the job. |
| status | [protectionUnitsBulkJobStatus](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitsbulkjobbase?view=graph-rest-1.0#protectionunitsbulkjobstatus-values) | The status of the job. The possible values are: `unknown`, `active`, `completed`, `completedWithErrors`, and `unknownFutureValue`. |

### protectionUnitsBulkJobStatus values

| Member | Description |
| :--- | :--- |
| unknown | The job is in an indeterminate state, possibly due to a temporary system issue or error. |
| active | The job is running. |
| completed | The job when was successfully applied to the corresponding policy. |
| completedWithErrors | The job finished running but encountered errors. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.protectionUnitsBulkJobBase",
  "id": "String (identifier)",
  "displayName": "String",
  "status": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  }
}
```
