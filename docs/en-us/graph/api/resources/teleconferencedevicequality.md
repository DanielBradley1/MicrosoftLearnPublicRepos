<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teleconferencedevicequality?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# teleconferenceDeviceQuality resource type

Namespace: microsoft.graph

Represents video teleconferencing device session-level quality data.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callChainId | Guid | A unique identifier for all the participant calls in a conference or a unique identifier for two participant calls in P2P call. This needs to be copied over from `Microsoft.Graph.Call.CallChainId`. |
| cloudServiceDeploymentEnvironment | String | A geo-region where the service is deployed, such as `ProdNoam`. |
| cloudServiceDeploymentId | String | A unique deployment identifier assigned by Azure. |
| cloudServiceInstanceName | String | The Azure deployed cloud service instance name, such as `FrontEnd_IN_3`. |
| cloudServiceName | String | The Azure deployed cloud service name, such as `contoso.cloudapp.net`. |
| deviceDescription | String | Any additional description, such as `VTC Bldg 30/21`. |
| deviceName | String | The user media agent name, such as `Cisco SX80`. |
| mediaLegId | Guid | A unique identifier for a specific media leg of a participant in a conference. One participant can have multiple media leg identifiers if retargeting happens. CVI partner assigns this value. |
| mediaQualityList | [teleconferenceDeviceMediaQuality](https://learn.microsoft.com/en-us/graph/api/resources/teleconferencedevicemediaquality?view=graph-rest-1.0) collection | The list of media qualities in a media session \(call\), such as audio quality, video quality, and/or screen sharing quality. |
| participantId | Guid | A unique identifier for a specific participant in a conference. The CVI partner needs to copy over `Call.MyParticipantId` to this property. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "callChainId": "Guid",
  "cloudServiceDeploymentEnvironment": "String",
  "cloudServiceDeploymentId": "String",
  "cloudServiceInstanceName": "String",
  "cloudServiceName": "String",
  "deviceDescription": "String",
  "deviceName": "String",
  "mediaLegId": "Guid",
  "mediaQualityList": [{"@odata.type": "microsoft.graph.teleconferenceDeviceMediaQuality"}],
  "participantId": "Guid"
}
```
