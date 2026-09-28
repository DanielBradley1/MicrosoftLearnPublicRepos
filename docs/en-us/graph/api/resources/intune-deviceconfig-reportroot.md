<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-reportroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# reportRoot resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The resource that represents an instance of History Reports.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get reportRoot](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-reportroot-get?view=graph-rest-1.0) | [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-reportroot?view=graph-rest-1.0) | Read properties and relationships of the [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-reportroot?view=graph-rest-1.0) object. |
| [Update reportRoot](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-reportroot-update?view=graph-rest-1.0) | [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-reportroot?view=graph-rest-1.0) | Update the properties of a [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-reportroot?view=graph-rest-1.0) object. |
| [deviceConfigurationUserActivity function](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-reportroot-deviceconfigurationuseractivity?view=graph-rest-1.0) | [report](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-report?view=graph-rest-1.0) | Metadata for the device configuration user activity report |
| [deviceConfigurationDeviceActivity function](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-reportroot-deviceconfigurationdeviceactivity?view=graph-rest-1.0) | [report](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-report?view=graph-rest-1.0) | Metadata for the device configuration device activity report |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for this entity. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.reportRoot",
  "id": "String (identifier)"
}
```
