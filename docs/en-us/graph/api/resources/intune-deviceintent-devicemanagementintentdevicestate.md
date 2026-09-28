<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementIntentDeviceState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that represents device state for an intent

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementIntentDeviceStates](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicestate-list?view=graph-rest-beta) | [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) objects. |
| [Get deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicestate-get?view=graph-rest-beta) | [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) object. |
| [Create deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicestate-create?view=graph-rest-beta) | [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) | Create a new [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) object. |
| [Delete deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicestate-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta). |
| [Update deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentdevicestate-update?view=graph-rest-beta) | [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) | Update the properties of a [deviceManagementIntentDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentdevicestate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID |
| userPrincipalName | String | The user principal name that is being reported on a device |
| userName | String | The user name that is being reported on a device |
| deviceDisplayName | String | Device name that is being reported |
| lastReportedDateTime | DateTimeOffset | Last modified date time of an intent report |
| state | [complianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-compliancestatus?view=graph-rest-beta) | Device state for an intent. Possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`. |
| deviceId | String | Device id that is being reported |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementIntentDeviceState",
  "id": "String (identifier)",
  "userPrincipalName": "String",
  "userName": "String",
  "deviceDisplayName": "String",
  "lastReportedDateTime": "String (timestamp)",
  "state": "String",
  "deviceId": "String"
}
```
