<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicecleanuprule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedDeviceCleanupRule resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Define the rule when the admin wants the devices to be cleaned up.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedDeviceCleanupRules](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevicecleanuprule-list?view=graph-rest-beta) | [managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicecleanuprule?view=graph-rest-beta) collection | List properties and relationships of the [managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicecleanuprule?view=graph-rest-beta) objects. |
| [Get managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevicecleanuprule-get?view=graph-rest-beta) | [managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicecleanuprule?view=graph-rest-beta) | Read properties and relationships of the [managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicecleanuprule?view=graph-rest-beta) object. |
| [Create managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevicecleanuprule-create?view=graph-rest-beta) | [managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicecleanuprule?view=graph-rest-beta) | Create a new [managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicecleanuprule?view=graph-rest-beta) object. |
| [Delete managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevicecleanuprule-delete?view=graph-rest-beta) | None | Deletes a [managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicecleanuprule?view=graph-rest-beta). |
| [Update managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevicecleanuprule-update?view=graph-rest-beta) | [managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicecleanuprule?view=graph-rest-beta) | Update the properties of a [managedDeviceCleanupRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevicecleanuprule?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Indicates the identifier of the device cleanup rule. This id is assigned at the time when the device cleanup rule is created. Read-only. |
| displayName | String | Indicates the display name of the device cleanup rule. |
| description | String | Indicates the description for the device clean up rule. |
| deviceCleanupRulePlatformType | [deviceCleanupRulePlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecleanupruleplatformtype?view=graph-rest-beta) | Indicates the managed device platform for which the admin wants to create the device clean up rule. Possible values are: `all`, `androidAOSP`, `androidDeviceAdministrator`, `androidDedicatedAndFullyManagedCorporateOwnedWorkProfile`, `chromeOS`, `androidPersonallyOwnedWorkProfile`, `ios`, `macOS`, `windows`, `windowsHolographic`, `unknownFutureValue`, `visionOS`, `tvOS`. |
| lastModifiedDateTime | DateTimeOffset | Indicates the date and time when the device cleanup rule was last modified. This property is read-only. |
| deviceInactivityBeforeRetirementInDays | Int32 | Indicates the number of days when the device has not contacted Intune. Valid values 0 to 2147483647 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDeviceCleanupRule",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "deviceCleanupRulePlatformType": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "deviceInactivityBeforeRetirementInDays": 1024
}
```
