<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-resourceimpactsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-10 -->

# resourceImpactSummary resource type

Namespace: microsoft.graph.healthMonitoring

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represent a summary of the impacted resource type for a Microsoft Entra Health monitoring [alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta).

This resource is an abstract type from which the [directoryObjectImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-directoryobjectimpactsummary?view=graph-rest-beta) resource inherits.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| impactedCount | String | The number of resources impacted. The number could be an exhaustive count or a sampling count. |
| impactedCountLimitExceeded | Boolean | Indicates whether **impactedCount** is exhaustive or a sampling. When this value is `true`, the limit was exceeded and **impactedCount** represents a sampling; otherwise, **impactedCount** represents the true number of impacts. |
| resourceType | String | The type of resource that was impacted. Examples include `user`, `group`, `application`, `servicePrincipal`, `device`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.healthMonitoring.resourceImpactSummary",
  "resourceType": "String",
  "impactedCount": "Integer",
  "impactedCountLimitExceeded": "Boolean"
}
```
