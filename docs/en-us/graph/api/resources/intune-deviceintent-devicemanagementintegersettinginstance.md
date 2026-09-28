<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintegersettinginstance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementIntegerSettingInstance resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A setting instance representing an integer value

Inherits from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementIntegerSettingInstances](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintegersettinginstance-list?view=graph-rest-beta) | [deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintegersettinginstance?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintegersettinginstance?view=graph-rest-beta) objects. |
| [Get deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintegersettinginstance-get?view=graph-rest-beta) | [deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintegersettinginstance?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintegersettinginstance?view=graph-rest-beta) object. |
| [Create deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintegersettinginstance-create?view=graph-rest-beta) | [deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintegersettinginstance?view=graph-rest-beta) | Create a new [deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintegersettinginstance?view=graph-rest-beta) object. |
| [Delete deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintegersettinginstance-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintegersettinginstance?view=graph-rest-beta). |
| [Update deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintegersettinginstance-update?view=graph-rest-beta) | [deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintegersettinginstance?view=graph-rest-beta) | Update the properties of a [deviceManagementIntegerSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintegersettinginstance?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The setting instance ID Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| definitionId | String | The ID of the setting definition for this instance Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| valueJson | String | JSON representation of the value Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| value | Int32 | The integer value |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementIntegerSettingInstance",
  "id": "String (identifier)",
  "definitionId": "String",
  "valueJson": "String",
  "value": 1024
}
```
