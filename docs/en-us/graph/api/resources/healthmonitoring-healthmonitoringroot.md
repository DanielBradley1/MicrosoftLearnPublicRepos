<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-healthmonitoringroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-10 -->

# healthMonitoringRoot resource type

Namespace: microsoft.graph.healthMonitoring

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a container for navigation properties of resources for Microsoft Entra Health monitoring.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| alertConfigurations | [microsoft.graph.healthMonitoring.alertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alertconfiguration?view=graph-rest-beta) collection | The configuration of an alert type, which defines behavior that occurs when an alert is created. |
| alerts | [microsoft.graph.healthMonitoring.alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta) collection | The collection of health monitoring system detected alerts for anomalous usage patterns found in a Microsoft Entra tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.healthMonitoring.healthMonitoringRoot",
  "id": "String (identifier)"
}
```
