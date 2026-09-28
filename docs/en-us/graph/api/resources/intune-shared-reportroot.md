<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-reportroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# reportRoot resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The resource that represents an instance of a device or troubleshooting report, depending on context.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get reportRoot](https://learn.microsoft.com/en-us/graph/api/intune-shared-reportroot-get?view=graph-rest-beta) | Read properties and relationships of the [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-reportroot?view=graph-rest-beta) object. |  |
| [Update reportRoot](https://learn.microsoft.com/en-us/graph/api/intune-shared-reportroot-update?view=graph-rest-beta) | Update the properties of a [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-reportroot?view=graph-rest-beta) object. |  |
| **Device configuration** |  |  |
| [deviceConfigurationUserActivity function](https://learn.microsoft.com/en-us/graph/api/intune-shared-reportroot-deviceconfigurationuseractivity?view=graph-rest-beta) | Metadata for the device configuration user activity report |  |
| [deviceConfigurationDeviceActivity function](https://learn.microsoft.com/en-us/graph/api/intune-shared-reportroot-deviceconfigurationdeviceactivity?view=graph-rest-beta) | Metadata for the device configuration device activity report |  |
| **Troubleshooting** |  |  |
| [managedDeviceEnrollmentAbandonmentDetails function](https://learn.microsoft.com/en-us/graph/api/intune-shared-reportroot-manageddeviceenrollmentabandonmentdetails?view=graph-rest-beta) | [report](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-report?view=graph-rest-beta) | Metadata for Enrollment abandonment details report |
| [managedDeviceEnrollmentAbandonmentSummary function](https://learn.microsoft.com/en-us/graph/api/intune-shared-reportroot-manageddeviceenrollmentabandonmentsummary?view=graph-rest-beta) | [report](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-report?view=graph-rest-beta) | Metadata for Enrollment abandonment summary report |
| [managedDeviceEnrollmentFailureDetails function](https://learn.microsoft.com/en-us/graph/api/intune-shared-reportroot-manageddeviceenrollmentfailuredetails?view=graph-rest-beta) |  |  |
| [managedDeviceEnrollmentFailureTrends function](https://learn.microsoft.com/en-us/graph/api/intune-shared-reportroot-manageddeviceenrollmentfailuretrends?view=graph-rest-beta) | Metadata for the enrollment failure trends report |  |
| [managedDeviceEnrollmentTopFailures function](https://learn.microsoft.com/en-us/graph/api/intune-shared-reportroot-manageddeviceenrollmenttopfailures?view=graph-rest-beta) |  |  |

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
