<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevicehealth?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-03 -->

# teamworkDeviceHealth resource type

Namespace: microsoft.graph

Note

The Microsoft Graph beta APIs related to device management under the `teamworkDevice` resource type will be deprecated by November 2025 and will no longer be supported after that date.

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the health details of a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta). The device health is calculated based on the device configuration and other device parameters.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamworkdevicehealth-get?view=graph-rest-beta) | [teamworkDeviceHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevicehealth?view=graph-rest-beta) | Read the properties and relationships of a [teamworkDeviceHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevicehealth?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| connection | [teamworkConnection](https://learn.microsoft.com/en-us/graph/api/resources/teamworkconnection?view=graph-rest-beta) | Information about the connection status. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who created the device health document. |
| createdDateTime | DateTimeOffset | The UTC date and time when the device health document was created. |
| hardwareHealth | [teamworkHardwareHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkhardwarehealth?view=graph-rest-beta) | Health details about the device hardware. |
| id | String | Doucument identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who last modified the device health details. |
| lastModifiedDateTime | DateTimeOffset | The UTC date and time when the device health detail was last modified. |
| loginStatus | [teamworkLoginStatus](https://learn.microsoft.com/en-us/graph/api/resources/teamworkloginstatus?view=graph-rest-beta) | The login status of Microsoft Teams, Skype for Business, and Exchange. |
| peripheralsHealth | [teamworkPeripheralsHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheralshealth?view=graph-rest-beta) | Health details about all peripherals \(for example, speaker and microphone\) attached to a device. |
| softwareUpdateHealth | [teamworkSoftwareUpdateHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworksoftwareupdatehealth?view=graph-rest-beta) | Software updates available for the device. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkDeviceHealth",
  "connection": {
    "@odata.type": "microsoft.graph.teamworkConnection"
  },
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "hardwareHealth": {
    "@odata.type": "microsoft.graph.teamworkHardwareHealth"
  },
  "id": "String (identifier)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "loginStatus": {
    "@odata.type": "microsoft.graph.teamworkLoginStatus"
  },
  "peripheralsHealth": {
    "@odata.type": "microsoft.graph.teamworkPeripheralsHealth"
  },
  "softwareUpdateHealth": {
    "@odata.type": "microsoft.graph.teamworkSoftwareUpdateHealth"
  }
}
```
