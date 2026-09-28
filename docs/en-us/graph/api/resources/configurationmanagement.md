<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/configurationmanagement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# configurationManagement resource type

Namespace: microsoft.graph

Represents an entity that acts as a container for Tenant Configuration Management functionality.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | identifier for the object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| configurationMonitors | [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) collection | A container for configuration monitor resources. |
| configurationMonitoringResults | [configurationMonitoringResult](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitoringresult?view=graph-rest-1.0) collection | A container for configuration monitoring results resources. |
| configurationDrifts | [configurationDrift](https://learn.microsoft.com/en-us/graph/api/resources/configurationdrift?view=graph-rest-1.0) collection | A container for configuration drift resources. |
| configurationSnapshotJobs | [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) collection | A container for snapshot job resources. |
| configurationSnapshots | [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) collection | A container for configuration snapshot baselines. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.configurationManagement",
  "id": "String (identifier)"
}
```
