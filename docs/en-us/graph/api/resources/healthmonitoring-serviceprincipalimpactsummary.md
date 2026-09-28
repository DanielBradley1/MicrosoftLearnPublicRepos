<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-serviceprincipalimpactsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-10 -->

# servicePrincipalImpactSummary resource type

Namespace: microsoft.graph.healthMonitoring

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a summary of an impacted service principal resource type for an alert in Microsoft Entra Health monitoring.

Inherits from [directoryObjectImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-directoryobjectimpactsummary?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| impactedCount | String | The number of resources impacted. The number could be an exhaustive count or a sampling count. Inherited from [microsoft.graph.healthMonitoring.resourceImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-resourceimpactsummary?view=graph-rest-beta). |
| impactedCountLimitExceeded | Boolean | Indicates whether **impactedCount** is exhaustive or a sampling. When this value is "true," the limit was exceeded and **impactedCount** represents a sampling. Otherwise, **impactedCount** represents the true number of impacts. Inherited from [microsoft.graph.healthMonitoring.resourceImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-resourceimpactsummary?view=graph-rest-beta). |
| resourceType | String | The type of resource that was impacted, which is `servicePrincipal`. Inherited from [microsoft.graph.healthMonitoring.resourceImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-resourceimpactsummary?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| resourceSampling | [microsoft.graph.directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | The collection of sampling resources that were impacted. Inherited from [microsoft.graph.healthMonitoring.directoryObjectImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-directoryobjectimpactsummary?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.healthMonitoring.servicePrincipalImpactSummary",
  "resourceType": "String",
  "impactedCount": "Integer",
  "impactedCountLimitExceeded": "Boolean"
}
```
