<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-21 -->

# workplaceSensorDevice resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents hardware capable of hosting multiple sensors that collect and report data on physical or environmental conditions, including occupancy, people count, inferred occupancy, temperature, and more.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/workplace-list-sensordevices?view=graph-rest-beta) | [workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevice?view=graph-rest-beta) collection | Get a list of all workplace sensor devices created for a tenant. |
| [Create](https://learn.microsoft.com/en-us/graph/api/workplace-post-sensordevices?view=graph-rest-beta) | [workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevice?view=graph-rest-beta) | Create a new workplace sensor device. |
| [Get](https://learn.microsoft.com/en-us/graph/api/workplacesensordevice-get?view=graph-rest-beta) | [workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevice?view=graph-rest-beta) | Get the properties of a workplace sensor device, including tags, MAC address, sensors, and more. |
| [Update](https://learn.microsoft.com/en-us/graph/api/workplacesensordevice-update?view=graph-rest-beta) | [workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevice?view=graph-rest-beta) | Update the properties of a workplace sensor device. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/workplacesensordevice-delete?view=graph-rest-beta) | None | Delete a workplace sensor device. |
| [Ingest telemetry](https://learn.microsoft.com/en-us/graph/api/workplacesensordevice-ingesttelemetry?view=graph-rest-beta) | None | Ingest sensor telemetry for a workplace sensor device. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the device. |
| deviceId | String | The user-defined unique identifier of the device provided at the time of creation. |
| displayName | String | The display name of the device. |
| id | String | The unique identifier of the device. It's system generated and a user can't change it. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| ipV4Address | String | The IPv4 address of the device. |
| ipV6Address | String | The IPv6 address of the device. |
| macAddress | String | The MAC address of the device. |
| manufacturer | String | The manufacturer of the device. |
| placeId | String | The unique identifier of the place where the device is located. If the device is installed in a room equipped with a mailbox, this property should match the **ExternalDirectoryObjectId** or Microsoft Entra object ID of the room mailbox. |
| sensors | [workplaceSensor](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensor?view=graph-rest-beta) collection | A list of sensors associated with the device that collect and report data about physical or environmental conditions, such as occupancy, people count, inferred occupancy, temperature, Wi-Fi, and more. |
| tags | String collection | A list of custom tags associated with the device. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workplaceSensorDevice",
  "description": "String",
  "deviceId": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "ipV4Address": "String",
  "ipV6Address": "String",
  "macAddress": "String",
  "manufacturer": "String",
  "placeId": "String",
  "sensors": [{"@odata.type": "microsoft.graph.workplaceSensor"}],
  "tags": ["String"]
}
```
