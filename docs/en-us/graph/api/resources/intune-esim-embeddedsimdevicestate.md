<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# embeddedSIMDeviceState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Describes the embedded SIM activation code deployment state in relation to a device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List embeddedSIMDeviceStates](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimdevicestate-list?view=graph-rest-beta) | [embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate?view=graph-rest-beta) collection | List properties and relationships of the [embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate?view=graph-rest-beta) objects. |
| [Get embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimdevicestate-get?view=graph-rest-beta) | [embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate?view=graph-rest-beta) | Read properties and relationships of the [embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate?view=graph-rest-beta) object. |
| [Create embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimdevicestate-create?view=graph-rest-beta) | [embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate?view=graph-rest-beta) | Create a new [embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate?view=graph-rest-beta) object. |
| [Delete embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimdevicestate-delete?view=graph-rest-beta) | None | Deletes a [embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate?view=graph-rest-beta). |
| [Update embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimdevicestate-update?view=graph-rest-beta) | [embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate?view=graph-rest-beta) | Update the properties of a [embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the embedded SIM device status. System generated value assigned when created. |
| createdDateTime | DateTimeOffset | The time the embedded SIM device status was created. Generated service side. |
| modifiedDateTime | DateTimeOffset | The time the embedded SIM device status was last modified. Updated service side. |
| lastSyncDateTime | DateTimeOffset | The time the embedded SIM device last checked in. Updated service side. |
| universalIntegratedCircuitCardIdentifier | String | The Universal Integrated Circuit Card Identifier \(UICCID\) identifying the hardware onto which a profile is to be deployed. |
| deviceName | String | Device name to which the subscription was provisioned e.g. DESKTOP-JOE |
| userName | String | Username which the subscription was provisioned to e.g. joe@contoso.com |
| state | [embeddedSIMDeviceStateValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestatevalue?view=graph-rest-beta) | The state of the profile operation applied to the device. Possible values are: `notEvaluated`, `failed`, `installing`, `installed`, `deleting`, `error`, `deleted`, `removedByUser`. |
| stateDetails | String | String description of the provisioning state. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.embeddedSIMDeviceState",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "lastSyncDateTime": "String (timestamp)",
  "universalIntegratedCircuitCardIdentifier": "String",
  "deviceName": "String",
  "userName": "String",
  "state": "String",
  "stateDetails": "String"
}
```
