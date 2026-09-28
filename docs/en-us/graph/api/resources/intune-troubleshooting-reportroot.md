<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-reportroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# reportRoot resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The resource that represents an instance of Enrollment Failure Reports.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get reportRoot](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-reportroot-get?view=graph-rest-1.0) | [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-reportroot?view=graph-rest-1.0) | Read properties and relationships of the [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-reportroot?view=graph-rest-1.0) object. |
| [Update reportRoot](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-reportroot-update?view=graph-rest-1.0) | [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-reportroot?view=graph-rest-1.0) | Update the properties of a [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-reportroot?view=graph-rest-1.0) object. |
| [managedDeviceEnrollmentFailureDetails function](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-reportroot-manageddeviceenrollmentfailuredetails?view=graph-rest-1.0) | [report](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-report?view=graph-rest-1.0) |  |
| [managedDeviceEnrollmentFailureDetails function](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-reportroot-manageddeviceenrollmentfailuredetails?view=graph-rest-1.0) | [report](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-report?view=graph-rest-1.0) |  |
| [managedDeviceEnrollmentTopFailures function](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-reportroot-manageddeviceenrollmenttopfailures?view=graph-rest-1.0) | [report](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-report?view=graph-rest-1.0) |  |
| [managedDeviceEnrollmentTopFailures function](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-reportroot-manageddeviceenrollmenttopfailures?view=graph-rest-1.0) | [report](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-report?view=graph-rest-1.0) |  |

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
