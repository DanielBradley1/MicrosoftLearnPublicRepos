<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-03 -->

# teamworkDeviceConfiguration resource type

Namespace: microsoft.graph

Note

The Microsoft Graph beta APIs related to device management under the `teamworkDevice` resource type will be deprecated by November 2025 and will no longer be supported after that date.

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents configuration details for a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta), including software versions, peripheral device configuration \(for example, camera, display, microphone, and speaker\), hardware configuration, and Teams client configuration.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamworkdeviceconfiguration-get?view=graph-rest-beta) | [teamworkDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceconfiguration?view=graph-rest-beta) | Read the properties and relationships of a [teamworkDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cameraConfiguration | [teamworkCameraConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcameraconfiguration?view=graph-rest-beta) | The camera configuration. Applicable only for Microsoft Teams Rooms-enabled devices. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who created the device configuration document. |
| createdDateTime | DateTimeOffset | The UTC date and time when the device configuration document was created. |
| displayConfiguration | [teamworkDisplayConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdisplayconfiguration?view=graph-rest-beta) | The display configuration. |
| hardwareConfiguration | [teamworkHardwareConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkhardwareconfiguration?view=graph-rest-beta) | The hardware configuration. Applicable only for Teams Rooms-enabled devices. |
| id | String | Document identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who last modified the device configuration. |
| lastModifiedDateTime | DateTimeOffset | The UTC date and time when the device configuration was last modified. |
| microphoneConfiguration | [teamworkMicrophoneConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkmicrophoneconfiguration?view=graph-rest-beta) | The microphone configuration. Applicable only for Teams Rooms-enabled devices. |
| softwareVersions | [teamworkDeviceSoftwareVersions](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevicesoftwareversions?view=graph-rest-beta) | Information related to software versions for the device, such as firmware, operating system, Teams client, and admin agent. |
| speakerConfiguration | [teamworkSpeakerConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkspeakerconfiguration?view=graph-rest-beta) | The speaker configuration. Applicable only for Teams Rooms-enabled devices. |
| systemConfiguration | [teamworkSystemConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworksystemconfiguration?view=graph-rest-beta) | The system configuration. Not applicable for Teams Rooms-enabled devices. |
| teamsClientConfiguration | [teamworkTeamsClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkteamsclientconfiguration?view=graph-rest-beta) | The Teams client configuration. Applicable only for Teams Rooms-enabled devices. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkDeviceConfiguration",
  "cameraConfiguration": {
    "@odata.type": "microsoft.graph.teamworkCameraConfiguration"
  },
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "displayConfiguration": {
    "@odata.type": "microsoft.graph.teamworkDisplayConfiguration"
  },
  "hardwareConfiguration": {
    "@odata.type": "microsoft.graph.teamworkHardwareConfiguration"
  },
  "id": "String (identifier)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "microphoneConfiguration": {
    "@odata.type": "microsoft.graph.teamworkMicrophoneConfiguration"
  },
  "softwareVersions": {
    "@odata.type": "microsoft.graph.teamworkDeviceSoftwareVersions"
  },
  "speakerConfiguration": {
    "@odata.type": "microsoft.graph.teamworkSpeakerConfiguration"
  },
  "systemConfiguration": {
    "@odata.type": "microsoft.graph.teamworkSystemConfiguration"
  },
  "teamsClientConfiguration": {
    "@odata.type": "microsoft.graph.teamworkTeamsClientConfiguration"
  }
}
```
