<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkmicrophoneconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkMicrophoneConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the microphone configuration for a Microsoft Teams Rooms [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isMicrophoneOptional | Boolean | `True` if the configured microphone is optional. `False` if the microphone is not optional and the health state of the device should be computed. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| defaultMicrophone | [teamworkPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta) | Information about the default microphone. |
| microphones | [teamworkPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta) collection | A collection of microphones. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkMicrophoneConfiguration",
  "isMicrophoneOptional": "Boolean"
}
```
