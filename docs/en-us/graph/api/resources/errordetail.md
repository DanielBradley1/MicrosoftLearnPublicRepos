<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/errordetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# errorDetail resource type

Namespace: microsoft.graph

Represents details of errors found during a [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) run or a [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0). When the administrator resolves the issues, the monitor and snapshot jobs run successfully.

Administrators can use the `$select` query parameter to get **errorDetails** from the [configurationMonitoringResult](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitoringresult?view=graph-rest-1.0) and [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) APIs.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errorMessage | String | The message that describes the error to help the admin take action. |
| resourceInstanceName | String | The resource type identifier. |
| resourceType | String | Name of the resource type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.errorDetail",
  "errorMessage": "String",
  "resourceInstanceName": "String",
  "resourceType": "String"
}
```
