<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheralshealth?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkPeripheralsHealth resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents health details for all peripheral devices attached to a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| communicationSpeakerHealth | [teamworkPeripheralHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheralhealth?view=graph-rest-beta) | The health details about the communication speaker. |
| contentCameraHealth | [teamworkPeripheralHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheralhealth?view=graph-rest-beta) | The health details about the content camera. |
| displayHealthCollection | [teamworkPeripheralHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheralhealth?view=graph-rest-beta) collection | The health details about displays. |
| microphoneHealth | [teamworkPeripheralHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheralhealth?view=graph-rest-beta) | The health details about the microphone. |
| roomCameraHealth | [teamworkPeripheralHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheralhealth?view=graph-rest-beta) | The health details about the room camera. |
| speakerHealth | [teamworkPeripheralHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheralhealth?view=graph-rest-beta) | The health details about the speaker. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkPeripheralsHealth",
  "communicationSpeakerHealth": {
    "@odata.type": "microsoft.graph.teamworkPeripheralHealth"
  },
  "contentCameraHealth": {
    "@odata.type": "microsoft.graph.teamworkPeripheralHealth"
  },
  "displayHealthCollection": [
    {
      "@odata.type": "microsoft.graph.teamworkPeripheralHealth"
    }
  ],
  "microphoneHealth": {
    "@odata.type": "microsoft.graph.teamworkPeripheralHealth"
  },
  "roomCameraHealth": {
    "@odata.type": "microsoft.graph.teamworkPeripheralHealth"
  },
  "speakerHealth": {
    "@odata.type": "microsoft.graph.teamworkPeripheralHealth"
  }
}
```
