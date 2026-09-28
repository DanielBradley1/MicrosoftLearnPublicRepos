<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-deviceappmanagement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceAppManagement resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device app management singleton entity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| managedAppPolicies | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) collection | Managed app policies. |
| iosManagedAppProtections | [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappprotection?view=graph-rest-1.0) collection | iOS managed app policies. |
| androidManagedAppProtections | [androidManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-androidmanagedappprotection?view=graph-rest-1.0) collection | Android managed app policies. |
| defaultManagedAppProtections | [defaultManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-defaultmanagedappprotection?view=graph-rest-1.0) collection | Default managed app policies. |
| targetedManagedAppConfigurations | [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration?view=graph-rest-1.0) collection | Targeted managed app configurations. |
| mdmWindowsInformationProtectionPolicies | [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-mdmwindowsinformationprotectionpolicy?view=graph-rest-1.0) collection | Windows information protection for apps running on devices which are MDM enrolled. |
| windowsInformationProtectionPolicies | [windowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionpolicy?view=graph-rest-1.0) collection | Windows information protection for apps running on devices which are not MDM enrolled. |
| managedAppRegistrations | [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) collection | The managed app registrations. |
| managedAppStatuses | [managedAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus?view=graph-rest-1.0) collection | The managed app statuses. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAppManagement",
  "id": "String (identifier)"
}
```
