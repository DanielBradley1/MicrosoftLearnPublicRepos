<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-sensorsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-05 -->

# sensorSettings resource type

Namespace: microsoft.graph.security

Provides settings information for a sensor.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description of the sensor. |
| domainControllerDnsNames | String collection | DNS names for the domain controller |
| isDelayedDeploymentEnabled | Boolean | Indicates whether to delay updates for the sensor. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| networkAdapters | [microsoft.graph.security.networkAdapter](https://learn.microsoft.com/en-us/graph/api/resources/security-networkadapter?view=graph-rest-1.0) collection | Sensor network adapters. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.sensorSettings",
  "description": "String",
  "domainControllerDnsNames": [
    "String"
  ],
  "isDelayedDeploymentEnabled": "Boolean"
}
```
