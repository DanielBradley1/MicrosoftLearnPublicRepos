<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workplace?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# workplace resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a workplace in a tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/workplace-list-sensordevices?view=graph-rest-beta) | [workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevice?view=graph-rest-beta) collection | Get a list of all workplace sensor devices created for a tenant. |
| [Create](https://learn.microsoft.com/en-us/graph/api/workplace-post-sensordevices?view=graph-rest-beta) | [workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevice?view=graph-rest-beta) | Create a new sensor device. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sensorDevices | [workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevice?view=graph-rest-beta) collection | A collection of sensor devices. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workplace"
}
```
