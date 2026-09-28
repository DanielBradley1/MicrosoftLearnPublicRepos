<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-directoryobjectimpactsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-10 -->

# directoryObjectImpactSummary resource type

Namespace: microsoft.graph.healthMonitoring

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a summary of an impacted resource in the directory \(Microsoft Entra ID\) object type. This type is an abstract type from which the following resources inherit:

- [applicationImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-applicationimpactsummary?view=graph-rest-beta)
- [deviceImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-deviceimpactsummary?view=graph-rest-beta)
- [groupImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-groupimpactsummary?view=graph-rest-beta)
- [servicePrincipalImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-serviceprincipalimpactsummary?view=graph-rest-beta)
- [userImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-userimpactsummary?view=graph-rest-beta)

Inherits from [resourceImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-resourceimpactsummary?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| impactedCount | String | The number of resources impacted. The number could be an exhaustive count or a sampling count. Inherited from [microsoft.graph.healthMonitoring.resourceImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-resourceimpactsummary?view=graph-rest-beta). |
| impactedCountLimitExceeded | Boolean | Indicates whether **impactedCount** is exhaustive or a sampling. When this value is "true," the limit was exceeded and **impactedCount** represents a sampling. Otherwise, **impactedCount** represents the true number of impacts. Inherited from [microsoft.graph.healthMonitoring.resourceImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-resourceimpactsummary?view=graph-rest-beta). |
| resourceType | String | The type of resource that was impacted. Examples include `user`, `group`, `application`, `servicePrincipal`, `device`. Inherited from [microsoft.graph.healthMonitoring.resourceImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-resourceimpactsummary?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| resourceSampling | [microsoft.graph.directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | The collection of sampling resources that were impacted. Supports $expand. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.healthMonitoring.directoryObjectImpactSummary",
  "resourceType": "String",
  "impactedCount": "Integer",
  "impactedCountLimitExceeded": "Boolean"
}
```
