<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# user resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an Azure Active Directory user object.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List users](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-list?view=graph-rest-beta) objects. | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) collection | List properties and relationships of the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) objects. |
| [Get user](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-get?view=graph-rest-beta) object. | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) | Read properties and relationships of the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) object. |
| [Create user](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-create?view=graph-rest-beta) object. | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) | Create a new [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) object. |
| [Delete user](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-delete?view=graph-rest-beta). | None | Deletes a [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta). |
| [Update user](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-update?view=graph-rest-beta) object. | [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) | Update the properties of a [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) object. |
| **Device management** |  |  |
| [getLoggedOnManagedDevices function](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-getloggedonmanageddevices?view=graph-rest-beta) | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) collection |  |
| [removeAllDevicesFromManagement action](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-removealldevicesfrommanagement?view=graph-rest-beta) | None | Retire all devices from management for this user |
| **Mobile application management \(MAM\)** |  |  |
| [getManagedAppDiagnosticStatuses function](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-getmanagedappdiagnosticstatuses?view=graph-rest-beta) | [managedAppDiagnosticStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdiagnosticstatus?view=graph-rest-beta) collection | Gets diagnostics validation status for a given user. |
| [getManagedAppPolicies function](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-getmanagedapppolicies?view=graph-rest-beta) | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) collection | Gets app restrictions for a given user. |
| [wipeManagedAppRegistrationByDeviceTag action](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-wipemanagedappregistrationbydevicetag?view=graph-rest-beta) | None | Issues a wipe operation on an app registration with specified device tag. |
| [wipeManagedAppRegistrationsByDeviceTag action](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-wipemanagedappregistrationsbydevicetag?view=graph-rest-beta) | None | Issues a wipe operation on an app registration with specified device tag. |
| **Onboarding** |  |  |
| [exportDeviceAndAppManagementData function](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-exportdeviceandappmanagementdata?view=graph-rest-beta) | [deviceAndAppManagementData](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-deviceandappmanagementdata?view=graph-rest-beta) |  |
| [getEffectiveDeviceEnrollmentConfigurations function](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-geteffectivedeviceenrollmentconfigurations?view=graph-rest-beta) | [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) collection |  |
| **Troubleshooting** |  |  |
| [getManagedDevicesWithAppFailures function](https://learn.microsoft.com/en-us/graph/api/intune-shared-user-getmanageddeviceswithappfailures?view=graph-rest-beta) | String collection | Retrieves the list of devices with failed apps. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the user. |
| **Onboarding** |  |  |
| deviceEnrollmentLimit | Int32 | The limit on the maximum number of devices that the user is permitted to enroll. Allowed values are 5 or 1000. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| **Device management** |  |  |
| managedDevices | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) collection | The managed devices associated with the user. |
| **Mobile application management \(MAM\)** |  |  |
| managedAppRegistrations | [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) collection | Zero or more managed app registrations that belong to the user. |
| **Onboarding** |  |  |
| deviceEnrollmentConfigurations | [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) collection | Get enrollment configurations targeted to the user |
| **Troubleshooting** |  |  |
| deviceManagementTroubleshootingEvents | [deviceManagementTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementtroubleshootingevent?view=graph-rest-beta) collection | The list of troubleshooting events for this user. |
| mobileAppIntentAndStates | [mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate?view=graph-rest-beta) collection | The list of troubleshooting events for this user. |
| mobileAppTroubleshootingEvents | [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapptroubleshootingevent?view=graph-rest-beta) collection | The list of mobile app troubleshooting events for this user. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.user",
  "id": "String (identifier)"
}
```
