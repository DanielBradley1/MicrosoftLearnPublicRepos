<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementBooleanSettingInstance resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A setting instance representing a boolean value

Inherits from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementBooleanSettingInstances](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementbooleansettinginstance-list?view=graph-rest-beta) | [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta) objects. |
| [Get deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementbooleansettinginstance-get?view=graph-rest-beta) | [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta) object. |
| [Create deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementbooleansettinginstance-create?view=graph-rest-beta) | [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta) | Create a new [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta) object. |
| [Delete deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementbooleansettinginstance-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta). |
| [Update deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementbooleansettinginstance-update?view=graph-rest-beta) | [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta) | Update the properties of a [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The setting instance ID Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| definitionId | String | The ID of the setting definition for this instance Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| valueJson | String | JSON representation of the value Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| value | Boolean | The boolean value |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementBooleanSettingInstance",
  "id": "String (identifier)",
  "definitionId": "String",
  "valueJson": "String",
  "value": true
}
```
