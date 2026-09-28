<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsManagementAppHealthState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows management app health state entity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsManagementAppHealthStates](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanagementapphealthstate-list?view=graph-rest-beta) | [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta) collection | List properties and relationships of the [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta) objects. |
| [Get windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanagementapphealthstate-get?view=graph-rest-beta) | [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta) | Read properties and relationships of the [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta) object. |
| [Create windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanagementapphealthstate-create?view=graph-rest-beta) | [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta) | Create a new [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta) object. |
| [Delete windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanagementapphealthstate-delete?view=graph-rest-beta) | None | Deletes a [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta). |
| [Update windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/intune-devices-windowsmanagementapphealthstate-update?view=graph-rest-beta) | [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta) | Update the properties of a [windowsManagementAppHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapphealthstate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the Windows management app health state. This property is read-only. |
| healthState | [healthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-healthstate?view=graph-rest-beta) | Windows management app health state. Possible values are: `unknown`, `healthy`, `unhealthy`. |
| installedVersion | String | Windows management app installed version. |
| lastCheckInDateTime | DateTimeOffset | Windows management app last check-in time. |
| deviceName | String | Name of the device on which Windows management app is installed. |
| deviceOSVersion | String | Windows 10 OS version of the device on which Windows management app is installed. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsManagementAppHealthState",
  "id": "String (identifier)",
  "healthState": "String",
  "installedVersion": "String",
  "lastCheckInDateTime": "String (timestamp)",
  "deviceName": "String",
  "deviceOSVersion": "String"
}
```
