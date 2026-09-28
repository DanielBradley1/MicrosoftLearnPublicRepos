<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjob?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-15 -->

# recoveryJob resource type

Namespace: microsoft.graph.entraRecoveryServices

Represents a recovery job that applies changes to restore a tenant's directory objects to a specific snapshot state. Inherits from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). After the job completes, use the `getFailedChanges` function to review any changes that could not be applied.

Inherits from [microsoft.graph.entraRecoveryServices.recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-snapshot-list-recoveryjobs?view=graph-rest-1.0) | [microsoft.graph.entraRecoveryServices.recoveryJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjob?view=graph-rest-1.0) collection | Get a list of the recoveryJob objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-snapshot-post-recoveryjobs?view=graph-rest-1.0) | [microsoft.graph.entraRecoveryServices.recoveryJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjob?view=graph-rest-1.0) | Create a new recoveryJob object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-recoveryjob-get?view=graph-rest-1.0) | [microsoft.graph.entraRecoveryServices.recoveryJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjob?view=graph-rest-1.0) | Read the properties and relationships of a recoveryJob object. |
| [Get failed changes](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-recoveryjob-getfailedchanges?view=graph-rest-1.0) | [microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoverychangeobjectbase?view=graph-rest-1.0) collection | Retrieve changes that failed to apply during recovery. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| filteringCriteria | [microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobfilteringcriteriabase?view=graph-rest-1.0) | Optional filtering criteria used to scope the job to specific entity types or entity IDs. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). |
| id | String | The unique identifier for the job. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| jobCompletionDateTime | DateTimeOffset | The date and time when the job completed. Null if the job is still running. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). |
| jobStartDateTime | DateTimeOffset | The date and time when the job started. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). |
| status | [microsoft.graph.entraRecoveryServices.recoveryStatus](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0#recoverystatus-values) | The current status of the job. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| targetStateDateTime | DateTimeOffset | The target snapshot timestamp to which the tenant is being restored. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). Supports `$filter` \(`eq`, `ne`\). |
| totalChangedLinksCalculated | Int32 | The total count of changed directory object links \(relationships\) calculated by the job. `null` until the job completes calculation. This value can differ from **totalLinksModified** because some link changes may fail to apply during recovery. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). |
| totalChangedObjectsCalculated | Int32 | The total count of changed directory objects calculated by the job. `null` until the job completes calculation. This value can differ from **totalObjectsModified** because some object changes may fail to apply during recovery. Inherited from [recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0). |
| totalFailedChanges | Int32 | The count of changes \(including both objects and links\) that failed to apply during recovery. |
| totalLinksModified | Int32 | The count of directory object links \(relationships\) that were successfully modified during recovery. This value may be less than **totalChangedLinksCalculated** if some link changes failed. |
| totalObjectsModified | Int32 | The count of directory objects that were successfully modified during recovery. This value may be less than **totalChangedObjectsCalculated** if some object changes failed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryJob",
  "id": "String (identifier)",
  "status": "String",
  "targetStateDateTime": "String (timestamp)",
  "jobStartDateTime": "String (timestamp)",
  "jobCompletionDateTime": "String (timestamp)",
  "filteringCriteria": {
    "@odata.type": "microsoft.graph.entraRecoveryServices.recoveryJobFilteringCriteriaBase"
  },
  "totalChangedObjectsCalculated": "Integer",
  "totalChangedLinksCalculated": "Integer",
  "totalObjectsModified": "Integer",
  "totalLinksModified": "Integer",
  "totalFailedChanges": "Integer"
}
```
