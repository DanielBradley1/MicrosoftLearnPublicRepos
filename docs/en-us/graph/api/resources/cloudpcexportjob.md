<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexportjob?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-21 -->

# cloudPcExportJob resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the export job for downloading a specified Cloud PC report.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create export job](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-post-exportjobs?view=graph-rest-beta) | [cloudPcExportJob](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexportjob?view=graph-rest-beta) | Create a new [cloudPcExportJob](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexportjob?view=graph-rest-beta) object to initiate downloading the entire or a specified portion of a report. |
| [Get export job](https://learn.microsoft.com/en-us/graph/api/cloudpcexportjob-get?view=graph-rest-beta) | [cloudPcExportJob](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexportjob?view=graph-rest-beta) | Read the properties and relationships of a [cloudPcExportJob](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexportjob?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expirationDateTime | DateTimeOffset | The date and time when the export job expires. |
| exportJobStatus | [cloudPcExportJobStatus](#cloudpcexportjobstatus-values) | The status of the export job. The possible values are: `notStarted`, `inProgress`, `completed`, `unknownFutureValue`. Read-only. |
| exportUrl | String | The storage account URL of the exported report. It can be used to download the file. |
| filter | String | The filter applied on the report. |
| format | String | The format of the exported report. |
| id | String | The unique identifier for the report. Read-only. |
| reportName | [cloudPcReportName](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreportname?view=graph-rest-beta) | The report name. |
| requestDateTime | DateTimeOffset | The date and time when the export job was requested. |
| select | String collection | The selected columns of the report. |

### cloudPcExportJobStatus values

| Member | Description |
| :--- | :--- |
| notStarted | The export job doesn't start yet. |
| inProgress | The export job is in progress. |
| completed | The export job is completed with the export URL returned. |
| failed | The export job has failed. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcExportJob",
  "expirationDateTime": "String (timestamp)",
  "exportJobStatus": "String",
  "exportUrl": "String",
  "filter": "String",
  "format": "String",
  "id": "String (identifier)",
  "reportName": "String",
  "requestDateTime": "String (timestamp)",
  "select": [
    "String"
  ]
}
```
