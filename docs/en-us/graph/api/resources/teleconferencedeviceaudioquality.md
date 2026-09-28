<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teleconferencedeviceaudioquality?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teleconferenceDeviceAudioQuality resource type

Namespace: microsoft.graph

Represents video teleconferencing device audio quality data.

## Properties

**teleconferenceDeviceAudioQuality** inherits all the properties of the [teleconferenceDeviceMediaQuality](https://learn.microsoft.com/en-us/graph/api/resources/teleconferencedevicemediaquality?view=graph-rest-1.0) resource.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "averageInboundJitter": "String (ISO 8601 duration)",
  "averageInboundPacketLossRateInPercentage": 10,
  "averageInboundRoundTripDelay": "String (ISO 8601 duration)",
  "averageOutboundJitter": "String (ISO 8601 duration)",
  "averageOutboundPacketLossRateInPercentage": 10,
  "averageOutboundRoundTripDelay": "String (ISO 8601 duration)",
  "channelIndex": 1,
  "inboundPackets": 1024,
  "localIPAddress": "String",
  "localPort": 2000,
  "maximumInboundJitter": "String (ISO 8601 duration)",
  "maximumInboundPacketLossRateInPercentage": 12,
  "maximumInboundRoundTripDelay": "String (ISO 8601 duration)",
  "maximumOutboundJitter": "String (ISO 8601 duration)",
  "maximumOutboundPacketLossRateInPercentage": 12,
  "maximumOutboundRoundTripDelay": "String (ISO 8601 duration)",
  "mediaDuration": "String (ISO 8601 duration)",
  "networkLinkSpeedInBytes": 1000000,
  "outboundPackets": 1024,
  "remoteIPAddress": "String",
  "remotePort": 3000
}
```
