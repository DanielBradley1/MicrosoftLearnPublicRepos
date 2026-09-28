<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettinginstance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementAbstractComplexSettingInstance resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A setting instance representing a complex value for an abstract setting

Inherits from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementAbstractComplexSettingInstances](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementabstractcomplexsettinginstance-list?view=graph-rest-beta) | [deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettinginstance?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettinginstance?view=graph-rest-beta) objects. |
| [Get deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementabstractcomplexsettinginstance-get?view=graph-rest-beta) | [deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettinginstance?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettinginstance?view=graph-rest-beta) object. |
| [Create deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementabstractcomplexsettinginstance-create?view=graph-rest-beta) | [deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettinginstance?view=graph-rest-beta) | Create a new [deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettinginstance?view=graph-rest-beta) object. |
| [Delete deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementabstractcomplexsettinginstance-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettinginstance?view=graph-rest-beta). |
| [Update deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementabstractcomplexsettinginstance-update?view=graph-rest-beta) | [deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettinginstance?view=graph-rest-beta) | Update the properties of a [deviceManagementAbstractComplexSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementabstractcomplexsettinginstance?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The setting instance ID Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| definitionId | String | The ID of the setting definition for this instance Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| valueJson | String | JSON representation of the value Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| implementationId | String | The definition ID for the chosen implementation of this complex setting |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| value | [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) collection | The values that make up the complex setting |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementAbstractComplexSettingInstance",
  "id": "String (identifier)",
  "definitionId": "String",
  "valueJson": "String",
  "implementationId": "String"
}
```
