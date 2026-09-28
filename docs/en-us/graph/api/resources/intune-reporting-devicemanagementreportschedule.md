<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportschedule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# deviceManagementReportSchedule resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity representing a schedule for which reports are delivered

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementReportSchedules](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreportschedule-list?view=graph-rest-beta) | [deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportschedule?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportschedule?view=graph-rest-beta) objects. |
| [Get deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreportschedule-get?view=graph-rest-beta) | [deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportschedule?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportschedule?view=graph-rest-beta) object. |
| [Create deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreportschedule-create?view=graph-rest-beta) | [deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportschedule?view=graph-rest-beta) | Create a new [deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportschedule?view=graph-rest-beta) object. |
| [Delete deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreportschedule-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportschedule?view=graph-rest-beta). |
| [Update deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/intune-reporting-devicemanagementreportschedule-update?view=graph-rest-beta) | [deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportschedule?view=graph-rest-beta) | Update the properties of a [deviceManagementReportSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportschedule?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for this entity |
| reportScheduleName | String | Name of the schedule |
| subject | String | Subject of the scheduled reports that are delivered |
| emails | String collection | Emails to which the scheduled reports are delivered |
| recurrence | [deviceManagementScheduledReportRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementscheduledreportrecurrence?view=graph-rest-beta) | Frequency of scheduled report delivery. The possible values are: `none`, `daily`, `weekly`, `monthly`. |
| startDateTime | DateTimeOffset | Time that the delivery of the scheduled reports starts |
| endDateTime | DateTimeOffset | Time that the delivery of the scheduled reports ends |
| userId | String | The Id of the User who created the report |
| reportName | String | Name of the report |
| filter | String | Filters applied on the report |
| select | String collection | Columns selected from the report |
| orderBy | String collection | Ordering of columns in the report |
| format | [deviceManagementReportFileFormat](https://learn.microsoft.com/en-us/graph/api/resources/intune-reporting-devicemanagementreportfileformat?view=graph-rest-beta) | Format of the scheduled report. The possible values are: `csv`, `pdf`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementReportSchedule",
  "id": "String (identifier)",
  "reportScheduleName": "String",
  "subject": "String",
  "emails": [
    "String"
  ],
  "recurrence": "String",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "userId": "String",
  "reportName": "String",
  "filter": "String",
  "select": [
    "String"
  ],
  "orderBy": [
    "String"
  ],
  "format": "String"
}
```
