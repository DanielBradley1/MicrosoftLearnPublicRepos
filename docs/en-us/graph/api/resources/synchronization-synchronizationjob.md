<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# synchronizationJob resource type

Namespace: microsoft.graph

Performs synchronization by periodically running in the background, polling for changes in one directory, and pushing them to another directory. The synchronization job is always specific to a particular instance of an application in your tenant. As part of the synchronization job setup, you need to give authorization to read and write objects in your target directory, and customize the job's synchronization schema.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronization-list-jobs?view=graph-rest-1.0) | [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0) collection | List existing jobs for a given application instance \(service principal\). |
| [Get](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-get?view=graph-rest-1.0) | [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0) | Read properties and relationships of a synchronizationJob object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronization-post-jobs?view=graph-rest-1.0) | [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0) | Create new job for a given application. |
| [Start](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-start?view=graph-rest-1.0) | None | Start synchronization. If the job is in a paused state, it continues from the point where the job was paused. If the job is in quarantine, the quarantine status is cleared. |
| [Pause](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-pause?view=graph-rest-1.0) | None | Temporarily stop synchronization. All the progress, including job state, is persisted, and the job will continue from where it left off when a [Start](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-start?view=graph-rest-1.0) call is made. |
| [Restart](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-restart?view=graph-rest-1.0) | None | Force the job to start over and re-process all the objects in the directory. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-delete?view=graph-rest-1.0) | None | Stop synchronization, and permanently delete all the state associated with the job. |
| [Provision on demand](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-provisionondemand?view=graph-rest-1.0) | [synchronizationJobApplicationParameters](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjobapplicationparameters?view=graph-rest-1.0) collection | Represents the objects that will be provisioned and the synchronization rules executed. The resource is primarily used for on-demand provisioning. |
| [Validate credentials](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-validatecredentials?view=graph-rest-1.0) | None | Test provided credentials against target directory. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique synchronization job identifier. Read-only. |
| schedule | [synchronizationSchedule](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschedule?view=graph-rest-1.0) | Schedule used to run the job. Read-only. |
| status | [synchronizationStatus](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationstatus?view=graph-rest-1.0) | Status of the job, which includes when the job was last run, current job state, and errors. |
| synchronizationJobSettings | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-1.0) | Settings associated with the job. Some settings are inherited from the template. |
| templateId | String | Identifier of the [synchronization template](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtemplate?view=graph-rest-1.0) this job is based on. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| bulkUpload | [bulkUpload](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-bulkupload?view=graph-rest-1.0) | The bulk upload operation for the job. |
| schema | [synchronizationSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0) | The synchronization schema configured for the job. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "schedule": {
    "@odata.type": "microsoft.graph.synchronizationSchedule"
  },
  "status": {
    "@odata.type": "microsoft.graph.synchronizationStatus"
  },
  "synchronizationJobSettings": {
    "@odata.type": "microsoft.graph.keyValuePair"
  },
  "templateId": "String"
}
```
