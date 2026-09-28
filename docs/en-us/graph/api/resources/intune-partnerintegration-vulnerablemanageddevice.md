<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# vulnerableManagedDevice resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This entity represents a device associated with a task.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List vulnerableManagedDevices](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-vulnerablemanageddevice-list?view=graph-rest-beta) | [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) collection | List properties and relationships of the [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) objects. |
| [Get vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-vulnerablemanageddevice-get?view=graph-rest-beta) | [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) | Read properties and relationships of the [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) object. |
| [Create vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-vulnerablemanageddevice-create?view=graph-rest-beta) | [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) | Create a new [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) object. |
| [Delete vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-vulnerablemanageddevice-delete?view=graph-rest-beta) | None | Deletes a [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta). |
| [Update vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-vulnerablemanageddevice-update?view=graph-rest-beta) | [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) | Update the properties of a [vulnerableManagedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-vulnerablemanageddevice?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The entity key, and AAD device ID. |
| managedDeviceId | String | The Intune managed device ID. |
| displayName | String | The device name. |
| lastSyncDateTime | DateTimeOffset | The last sync date. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.vulnerableManagedDevice",
  "id": "String (identifier)",
  "managedDeviceId": "String",
  "displayName": "String",
  "lastSyncDateTime": "String (timestamp)"
}
```
