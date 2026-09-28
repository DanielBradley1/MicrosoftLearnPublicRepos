<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-20 -->

# printJob resource type

Namespace: microsoft.graph

Represents a print job that has been queued for a printer.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/printjob-get?view=graph-rest-1.0) | [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) | Read properties and relationships of printJob object. |
| [Create print job](https://learn.microsoft.com/en-us/graph/api/printer-post-jobs?view=graph-rest-1.0) | [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) | Create a new print job object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/printjob-update?view=graph-rest-1.0) | [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) | Update a print job object. |
| [Start](https://learn.microsoft.com/en-us/graph/api/printjob-start?view=graph-rest-1.0) | None | Start the print job. |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/printjob-cancel?view=graph-rest-1.0) | None | Cancel the print job. |
| [Abort](https://learn.microsoft.com/en-us/graph/api/printjob-abort?view=graph-rest-1.0) | None | Abort the print job. |
| [Redirect](https://learn.microsoft.com/en-us/graph/api/printjob-redirect?view=graph-rest-1.0) | [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) | A print job that is queued for the destination printer. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuration | [printJobConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/printjobconfiguration?view=graph-rest-1.0) | A group of settings that a printer should use to print a job. |
| createdBy | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-1.0) | Read-only. Nullable. |
| createdDateTime | DateTimeOffset | The DateTimeOffset when the job was created. Read-only. |
| id | String | The ID of the print job. Read-only. |
| isFetchable | Edm.Boolean | If true, document can be fetched by printer. |
| redirectedFrom | Edm.String | Contains the source job URL, if the job has been redirected from another printer. |
| redirectedTo | Edm.String | Contains the destination job URL, if the job has been redirected to another printer. |
| status | [printJobStatus](https://learn.microsoft.com/en-us/graph/api/resources/printjobstatus?view=graph-rest-1.0) | The status of the print job. Read-only. |
| errorCode | Int32 | The error code of the print job. Read-only. |
| acknowledgedDateTime | DateTimeOffset | The dateTimeOffset when the job was acknowledged. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| documents | [printDocument](https://learn.microsoft.com/en-us/graph/api/resources/printdocument?view=graph-rest-1.0) collection | Read-only. |
| tasks | [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) collection | A list of [printTasks](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) that were triggered by this print job. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printJob",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "status": {
    "@odata.type": "microsoft.graph.printJobStatus"
  },
  "createdBy": {
    "@odata.type": "microsoft.graph.userIdentity"
  },
  "configuration": {
    "@odata.type": "microsoft.graph.printJobConfiguration"
  },
  "redirectedTo": "String",
  "redirectedFrom": "String",
  "isFetchable": "Boolean"
}
```
