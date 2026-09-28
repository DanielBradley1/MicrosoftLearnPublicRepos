<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-devicemanagementreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementReports resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Singleton entity that acts as a container for all reports functionality.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-devicemanagementreports-get?view=graph-rest-beta) | [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-devicemanagementreports?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-devicemanagementreports?view=graph-rest-beta) object. |
| [Update deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-devicemanagementreports-update?view=graph-rest-beta) | [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-devicemanagementreports?view=graph-rest-beta) | Update the properties of a [deviceManagementReports](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-devicemanagementreports?view=graph-rest-beta) object. |
| [getGroupPolicySettingsDeviceSettingsReport action](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-devicemanagementreports-getgrouppolicysettingsdevicesettingsreport?view=graph-rest-beta) | Stream |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for this entity |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementReports",
  "id": "String (identifier)"
}
```
