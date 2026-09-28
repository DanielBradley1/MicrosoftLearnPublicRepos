<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoverypreviewjob?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-15 -->

# recoveryPreviewJob resource type

Namespace: microsoft.graph.entraRecoveryServices

Represents a preview job that calculates and enumerates the changes required to recover a tenant to a specific snapshot state. Inherits from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). Use the [getChanges](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-recoverypreviewjob-getchanges?view=graph-rest-1.0) function to retrieve the calculated changes after the job completes.

Inherits from [microsoft.graph.entraRecoveryServices.recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-snapshot-list-recoverypreviewjobs?view=graph-rest-1.0) | [microsoft.graph.entraRecoveryServices.recoveryPreviewJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoverypreviewjob?view=graph-rest-1.0) collection | Get a list of the recoveryPreviewJob objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-snapshot-post-recoverypreviewjobs?view=graph-rest-1.0) | [microsoft.graph.entraRecoveryServices.recoveryPreviewJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoverypreviewjob?view=graph-rest-1.0) | Create a new recoveryPreviewJob object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-recoverypreviewjob-get?view=graph-rest-1.0) | [microsoft.graph.entraRecoveryServices.recoveryPreviewJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoverypreviewjob?view=graph-rest-1.0) | Read the properties and relationships of a recoveryPreviewJob object. |
| [Get changes](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-recoverypreviewjob-getchanges?view=graph-rest-1.0) | [microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoverychangeobjectbase?view=graph-rest-1.0) collection | Retrieve the collection of changes calculated by the preview job. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| filteringCriteria | [microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobfilteringcriteriabase?view=graph-rest-1.0) | Optional filtering criteria used to scope the job to specific entity types or entity IDs. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). |
| id | String | The unique identifier for the job. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| jobCompletionDateTime | DateTimeOffset | The date and time when the job completed. `null` if the job is still running. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). |
| jobStartDateTime | DateTimeOffset | The date and time when the job started. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). |
| status | [microsoft.graph.entraRecoveryServices.recoveryStatus](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0#recoverystatus-values) | The current status of the job. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| targetStateDateTime | DateTimeOffset | The target snapshot timestamp to which the tenant is being restored. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| totalChangedLinksCalculated | Int32 | The total count of changed directory object links \(relationships\) calculated by the job. `null` until the job completes calculation. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). |
| totalChangedObjectsCalculated | Int32 | The total count of changed directory objects calculated by the job. `null` until the job completes calculation. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryPreviewJob",
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
