<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-snapshot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-15 -->

# snapshot resource type

Namespace: microsoft.graph.entraRecoveryServices

Represents a backup snapshot of the tenant's directory data at a specific point in time. Each snapshot defines a timestamp to which a tenant's state can be recovered. The **id** property is a base64-encoded representation of the snapshot timestamp.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List snapshots](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-recovery-list-snapshots?view=graph-rest-1.0) | [microsoft.graph.entraRecoveryServices.snapshot](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-snapshot?view=graph-rest-1.0) collection | Get a list of the snapshot objects and their properties. |
| [Get snapshot](https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-snapshot-get?view=graph-rest-1.0) | [microsoft.graph.entraRecoveryServices.snapshot](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-snapshot?view=graph-rest-1.0) | Read the properties and relationships of a snapshot object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the snapshot was created. |
| id | String | The unique identifier for the snapshot. This ID is the base64-encoded representation of the snapshot timestamp. |
| totalChangedObjects | Int32 | The total number of changed objects identified in this snapshot. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| recoveryJobs | [microsoft.graph.entraRecoveryServices.recoveryJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjob?view=graph-rest-1.0) collection | Collection of recovery jobs created for this snapshot. |
| recoveryPreviewJobs | [microsoft.graph.entraRecoveryServices.recoveryPreviewJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoverypreviewjob?view=graph-rest-1.0) collection | Collection of preview jobs created for this snapshot. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.snapshot",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "totalChangedObjects": "Integer"
}
```
