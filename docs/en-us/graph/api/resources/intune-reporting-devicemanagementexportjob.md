<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjob?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# deviceManagementExportJob resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity representing a job to export a report.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementExportJobs](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementexportjob-list?view=graph-rest-1.0) | [deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjob?view=graph-rest-1.0) collection | List properties and relationships of the [deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjob?view=graph-rest-1.0) objects. |
| [Get deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementexportjob-get?view=graph-rest-1.0) | [deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjob?view=graph-rest-1.0) | Read properties and relationships of the [deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjob?view=graph-rest-1.0) object. |
| [Create deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementexportjob-create?view=graph-rest-1.0) | [deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjob?view=graph-rest-1.0) | Create a new [deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjob?view=graph-rest-1.0) object. |
| [Delete deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementexportjob-delete?view=graph-rest-1.0) | None | Deletes a [deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjob?view=graph-rest-1.0). |
| [Update deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementexportjob-update?view=graph-rest-1.0) | [deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjob?view=graph-rest-1.0) | Update the properties of a [deviceManagementExportJob](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjob?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for this entity. |
| reportName | String | Name of the report. The maximum length allowed for this property is 2000 characters. |
| filter | String | Filters applied on the report. The maximum length allowed for this property is 2000 characters. |
| select | String collection | Columns selected from the report. The maximum number of allowed columns names is 256. The maximum length allowed for each column name in this property is 1000 characters. |
| format | [deviceManagementReportFileFormat](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportfileformat?view=graph-rest-1.0) | Format of the exported report. Possible values are `csv` and `json`. The possible values are: `csv`, `pdf`, `json`, `unknownFutureValue`. |
| snapshotId | String | A snapshot is an identifiable subset of the dataset represented by the ReportName. A sessionId or CachedReportConfiguration id can be used here. If a sessionId is specified, Filter, Select, and OrderBy are applied to the data represented by the sessionId. Filter, Select, and OrderBy cannot be specified together with a CachedReportConfiguration id. The maximum length allowed for this property is 128 characters. |
| localizationType | [deviceManagementExportJobLocalizationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementexportjoblocalizationtype?view=graph-rest-1.0) | Configures how the requested export job is localized. Possible values are `replaceLocalizableValues` and `localizedValuesAsAdditionalColumn`. The possible values are: `localizedValuesAsAdditionalColumn`, `replaceLocalizableValues`. |
| status | [deviceManagementReportStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportstatus?view=graph-rest-1.0) | Status of the export job. Possible values are `unknown`, `notStarted`, `inProgress`, `completed` and `failed`. The possible values are: `unknown`, `notStarted`, `inProgress`, `completed`, `failed`. |
| url | String | Temporary location of the exported report. |
| requestDateTime | DateTimeOffset | Time that the exported report was requested. |
| expirationDateTime | DateTimeOffset | Time that the exported report expires. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementExportJob",
  "id": "String (identifier)",
  "reportName": "String",
  "filter": "String",
  "select": [
    "String"
  ],
  "format": "String",
  "snapshotId": "String",
  "localizationType": "String",
  "status": "String",
  "url": "String",
  "requestDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)"
}
```
