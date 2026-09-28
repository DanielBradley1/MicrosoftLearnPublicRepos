<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-03 -->

# teamworkDevice resource type

Namespace: microsoft.graph

Note

The Microsoft Graph beta APIs related to device management under the `teamworkDevice` resource type will be deprecated by November 2025 and will no longer be supported after that date.

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents details about a Microsoft Teams-enabled device that is provisioned for the tenant.

Microsoft Teams-enabled devices are Teams-certified collaboration devices. They include Microsoft Teams Rooms \(on Windows and Android\), Microsoft Teams Phones, panels, Surface Hubs, and SIP devices. These categories are the same as those available on the Teams admin center under the section **Teams devices**.

For more information, see [Manage your devices in Microsoft Teams.](https://learn.microsoft.com/en-us/microsoftteams/devices/device-management)

> **Note**: This does not include mobile phones, laptops, computers, tabs, and so on.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List teamworkDevices](https://learn.microsoft.com/en-us/graph/api/teamworkdevice-list?view=graph-rest-beta) | [teamworkDevice](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta) collection | Get a list of all Microsoft Teams-enabled devices provisioned for a tenant. |
| [Get teamworkDevice](https://learn.microsoft.com/en-us/graph/api/teamworkdevice-get?view=graph-rest-beta) | [teamworkDevice](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta) | Get the properties of a Microsoft Teams-enabled device. |
| [restart](https://learn.microsoft.com/en-us/graph/api/teamworkdevice-restart?view=graph-rest-beta) | [teamworkDeviceOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceoperation?view=graph-rest-beta) | Restart the specified Microsoft Teams-enabled device. |
| [runDiagnostics](https://learn.microsoft.com/en-us/graph/api/teamworkdevice-rundiagnostics?view=graph-rest-beta) | [teamworkDeviceOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceoperation?view=graph-rest-beta) | Run and generate diagnostic logs for the specified Microsoft Teams-enabled device. |
| [updateSoftware](https://learn.microsoft.com/en-us/graph/api/teamworkdevice-updatesoftware?view=graph-rest-beta) | [teamworkDeviceOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceoperation?view=graph-rest-beta) | Update the software for a Microsoft Teams-enabled device. |
| [List operations](https://learn.microsoft.com/en-us/graph/api/teamworkdeviceoperation-list?view=graph-rest-beta) | [teamworkDeviceOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceoperation?view=graph-rest-beta) collection | Get a list of operations that are running on a Teams-enabled device. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityState | teamworkDeviceActivityState | The activity state of the device. The possible values are: `unknown`, `busy`, `idle`, `unavailable`, `unknownFutureValue`. |
| companyAssetTag | String | The company asset tag assigned by the admin on the device. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who enrolled the device to the tenant. |
| createdDateTime | DateTimeOffset | The UTC date and time when the device was enrolled to the tenant. |
| currentUser | [teamworkUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-beta) | The signed-in user on the device. |
| deviceType | [teamworkDeviceType](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta#teamworkdevicetype-values) | The type of device. The possible values are: `unknown`, `ipPhone`, `teamsRoom`, `surfaceHub`, `collaborationBar`, `teamsDisplay`, `touchConsole`, `lowCostPhone`, `teamsPanel`, `sip`, `sipAnalog`, `unknownFutureValue`. |
| hardwareDetail | [teamworkHardwareDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamworkhardwaredetail?view=graph-rest-beta) | A collection of hardware-related properties. For example, **oemSerialNumber** and **model**. |
| healthStatus | [teamworkDeviceHealthStatus](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta#teamworkdevicehealthstatus-values) | The health status of the device. The possible values are: `unknown`, `offline`, `critical`, `nonUrgent`, `healthy`, `unknownFutureValue`. |
| id | String | Device identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who last modified the device details. |
| lastModifiedDateTime | DateTimeOffset | The UTC date and time when the device detail was last modified. |
| notes | String | The notes added by the admin to the device. |

### teamworkDeviceType values

| Member | Value | Description |
| :--- | :--- | :--- |
| unknown | 0 | Unknown device. |
| ipPhone | 1 | IP Phone devices are the desk phones for users to make and receive audio calls or join meetings. |
| teamsRoom | 2 | Microsoft Teams Rooms are Windows IoT based devices designed to extend the meeting experience to the conference room. |
| surfaceHub | 3 | Surface Hub devices are wall-mounted or roller-stand-mounted devices with interactive whiteboard. |
| collaborationBar | 4 | Collaboration bars are Microsoft Teams Rooms on Android used for small meeting spaces. |
| teamsDisplay | 5 | Teams display devices are the evolution of Teams phones. These devices are a category of all-in-one dedicated Teams devices that feature an ambient touchscreen and a hands-free experience powered by Cortana. |
| touchConsole | 6 | Touch console devices are the optional peripherals to the Teams Rooms on Android to perform all the device operations. |
| lowCostPhone | 7 | Low-cost phone devices are cost-effective Microsoft Teams phones. |
| teamsPanel | 8 | Microsoft Teams panels are the compact touchscreen devices that display meeting details scheduled via Teams. |
| sip | 9 | Session Initiation Protocol \(SIP\) devices that support Teams calls with the SIP Gateway from Microsoft. |
| sipAnalog | 10 | Legacy analog endpoints such as elevator phones, parking lot phones, or factory floor devices, which are registered with Microsoft Teams through the SIP Gateway. |
| unknownFutureValue | 11 | Evolvable enumeration sentinel value. Don't use. |

### teamworkDeviceHealthStatus values

| Member | Value | Description |
| :--- | :--- | :--- |
| unknown | 0 | Unknown health status. |
| offline | 1 | The device is offline and can't be used. |
| critical | 2 | The state requires urgent attention and action as it might have a significant impact on the performance of the device, or make it unusable for calls or meetings. |
| nonUrgent | 3 | The state requires attention because of issues or notifications that might have a minimal impact on the performance of an online device. |
| healthy | 4 | The device is online and in good condition. |
| unknownFutureValue | 5 | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activity | [teamworkDeviceActivity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceactivity?view=graph-rest-beta) | The activity properties that change based on the device usage. |
| configuration | [teamworkDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceconfiguration?view=graph-rest-beta) | The configuration properties of the device. |
| health | [teamworkDeviceHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevicehealth?view=graph-rest-beta) | The health properties of the device. |
| operations | [teamworkDeviceOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceoperation?view=graph-rest-beta) collection | The async operations on the device. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkDevice",
  "activityState": "String",
  "companyAssetTag": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "currentUser": {
    "@odata.type": "microsoft.graph.teamworkUserIdentity"
  },
  "deviceType": "String",
  "hardwareDetail": {
    "@odata.type": "microsoft.graph.teamworkHardwareDetail"
  },
  "healthStatus": "String",
  "id": "String (identifier)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "notes": "String"
}
```
