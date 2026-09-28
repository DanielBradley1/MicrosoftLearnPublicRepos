<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkspeakerconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkSpeakerConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the speaker configuration for a Microsoft Teams Rooms [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isCommunicationSpeakerOptional | Boolean | `True` if the communication speaker is optional. Used to compute the health state if the communication speaker is not optional. |
| isSpeakerOptional | Boolean | `True` if the configured speaker is optional. Used to compute the health state if the speaker is not optional. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| defaultCommunicationSpeaker | [teamworkPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta) | The default communication speaker used for conference meetings. |
| defaultSpeaker | [teamworkPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta) | The default speaker used for all media and notification sounds. |
| speakers | [teamworkPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta) collection | The list of connected speakers. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkSpeakerConfiguration",
  "isCommunicationSpeakerOptional": "Boolean",
  "isSpeakerOptional": "Boolean"
}
```
