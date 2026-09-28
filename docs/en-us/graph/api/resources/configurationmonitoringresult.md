<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitoringresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# configurationMonitoringResult resource type

Namespace: microsoft.graph

Represents the information and properties of a [configurationMonitoringResult](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitoringresult?view=graph-rest-1.0) object. This resource allows administrators to view monitor run details. They can determine whether the monitor is running successfully. If it isn't, they can identify the reasons for the failure. The resource also reports the number of drifts found in each monitor run.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/configurationmanagement-list-configurationmonitoringresults?view=graph-rest-1.0) | [configurationMonitoringResult](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitoringresult?view=graph-rest-1.0) collection | Get a list of the [configurationMonitoringResult](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitoringresult?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/configurationmonitoringresult-get?view=graph-rest-1.0) | [configurationMonitoringResult](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitoringresult?view=graph-rest-1.0) | Read the properties and relationships of a [configurationMonitoringResult](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitoringresult?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| driftsCount | Int32 | Number of drifts observed during a monitor run.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `ge`, `le`\) and `$orderby`. |
| errorDetails | [errorDetail](https://learn.microsoft.com/en-us/graph/api/resources/errordetail?view=graph-rest-1.0) collection | All the error details that prevent the monitor from running successfully. The error details are a contained entity.  <br>  <br>Requires `$select` to retrieve. |
| id | String | Globally unique identifier \(GUID\) of the monitor run. System-generated. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderby`. |
| monitorId | String | Globally unique identifier \(GUID\) of the monitor. System-generated.  <br>  <br>Supports `$filter` \(`eq`, `ne`\). |
| runCompletionDateTime | DateTimeOffset | Date and time at which the monitor run completed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `ge`, `le`\) and `$orderby`. |
| runInitiationDateTime | DateTimeOffset | Date and time at which the monitor run initiated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `ge`, `le`\) and `$orderby`. |
| runStatus | monitorRunStatus | Status of the monitor run. The possible values are: `successful`, `partiallySuccessful`, `failed`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`, `ne`\) and `$orderby`. |
| tenantId | String | Globally unique identifier \(GUID\) of the tenant for which the monitor runs. Fetched automatically by the system.  <br>  <br>Supports `$filter` \(`eq`, `ne`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.configurationMonitoringResult",
  "driftsCount": "Int32",
  "errorDetails": [{"@odata.type": "microsoft.graph.errorDetail"}],
  "id": "String (identifier)",
  "monitorId": "String",
  "runCompletionDateTime": "String (timestamp)",
  "runInitiationDateTime": "String (timestamp)",
  "runStatus": "String",
  "tenantId": "String"
}
```
