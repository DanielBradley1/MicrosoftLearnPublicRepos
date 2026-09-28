<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-15 -->

# recoveryJobBase resource type

Namespace: microsoft.graph.entraRecoveryServices

Abstract base type for recovery jobs. Defines common properties shared by [recoveryPreviewJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoverypreviewjob?view=graph-rest-1.0) and [recoveryJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjob?view=graph-rest-1.0). Cannot be instantiated directly. Jobs follow the resource-based long running operation \(RELO\) pattern.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-recovery-list-jobs?view=graph-rest-1.0) | [microsoft.graph.entraRecoveryServices.recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0) collection | Get a list of the recoveryJobBase objects and their properties. |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-recoveryjobbase-cancel?view=graph-rest-1.0) | None | Cancel a running recovery or preview job. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| filteringCriteria | [microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobfilteringcriteriabase?view=graph-rest-1.0) | Optional filtering criteria used to scope the job to specific entity types or entity IDs. |
| id | String | The unique identifier for the job. Supports `$filter` \(`eq`, `ne`\). |
| jobCompletionDateTime | DateTimeOffset | The date and time when the job completed. Null if the job is still running. |
| jobStartDateTime | DateTimeOffset | The date and time when the job started. |
| status | [microsoft.graph.entraRecoveryServices.recoveryStatus](#recoverystatus-values) | The current status of the job. Supports `$filter` \(`eq`, `ne`\). |
| targetStateDateTime | DateTimeOffset | The target snapshot timestamp to which the tenant is being restored. Supports `$filter` \(`eq`, `ne`\). |
| totalChangedLinksCalculated | Int32 | The total count of changed directory object links \(relationships\) calculated by the job. `null` until the job completes calculation. Not all calculated link changes may be successfully applied; see **totalLinksModified** on derived types for the count of links that were actually modified. |
| totalChangedObjectsCalculated | Int32 | The total count of changed directory objects calculated by the job. `null` until the job completes calculation. Not all calculated object changes may be successfully applied; see **totalObjectsModified** on derived types for the count of objects that were actually modified. |

### recoveryStatus values

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Use the `Prefer: include-unknown-enum-members` request header to get the following members: `calculating`, `loadingData`.

| Member | Description |
| :--- | :--- |
| initialized | The job is initialized but hasn't started. |
| running | The job is in progress. |
| successful | The job completed successfully. |
| failed | The job didn't complete successfully. |
| abandoned | The job was abandoned by the user. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| calculating | The job is calculating the recovery preview. |
| loadingData | The job is loading snapshot data. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJobBase",
  "id": "String (identifier)",
  "status": "String",
  "targetStateDateTime": "String (timestamp)",
  "jobStartDateTime": "String (timestamp)",
  "jobCompletionDateTime": "String (timestamp)",
  "filteringCriteria": {
    "@odata.type": "microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase"
  },
  "totalChangedObjectsCalculated": "Integer",
  "totalChangedLinksCalculated": "Integer"
}
```
