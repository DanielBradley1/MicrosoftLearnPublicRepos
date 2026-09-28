<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementstringsettinginstance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementStringSettingInstance resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A setting instance representing a string value

Inherits from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementStringSettingInstances](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementstringsettinginstance-list?view=graph-rest-beta) | [deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementstringsettinginstance?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementstringsettinginstance?view=graph-rest-beta) objects. |
| [Get deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementstringsettinginstance-get?view=graph-rest-beta) | [deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementstringsettinginstance?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementstringsettinginstance?view=graph-rest-beta) object. |
| [Create deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementstringsettinginstance-create?view=graph-rest-beta) | [deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementstringsettinginstance?view=graph-rest-beta) | Create a new [deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementstringsettinginstance?view=graph-rest-beta) object. |
| [Delete deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementstringsettinginstance-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementstringsettinginstance?view=graph-rest-beta). |
| [Update deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementstringsettinginstance-update?view=graph-rest-beta) | [deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementstringsettinginstance?view=graph-rest-beta) | Update the properties of a [deviceManagementStringSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementstringsettinginstance?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The setting instance ID Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| definitionId | String | The ID of the setting definition for this instance Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| valueJson | String | JSON representation of the value Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| value | String | The string value |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementStringSettingInstance",
  "id": "String (identifier)",
  "definitionId": "String",
  "valueJson": "String",
  "value": "String"
}
```
