<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementSettingInstance resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Base type for a setting instance

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementSettingInstances](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettinginstance-list?view=graph-rest-beta) | [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) objects. |
| [Get deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettinginstance-get?view=graph-rest-beta) | [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The setting instance ID |
| definitionId | String | The ID of the setting definition for this instance |
| valueJson | String | JSON representation of the value |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementSettingInstance",
  "id": "String (identifier)",
  "definitionId": "String",
  "valueJson": "String"
}
```
