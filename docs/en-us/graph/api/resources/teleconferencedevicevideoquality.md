<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teleconferencedevicevideoquality?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teleconferenceDeviceVideoQuality resource type

Namespace: microsoft.graph

Represents video teleconferencing device video quality data.

## Properties

The **teleconferenceDeviceVideoQuality** resource inherits the properties from [teleconferenceDeviceMediaQuality](https://learn.microsoft.com/en-us/graph/api/resources/teleconferencedevicemediaquality?view=graph-rest-1.0), and includes the following additional properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| averageInboundBitRate | Double | The average inbound stream video bit rate per second. |
| averageInboundFrameRate | Double | The average inbound stream video frame rate per second. |
| averageOutboundBitRate | Double | The average outbound stream video bit rate per second. |
| averageOutboundFrameRate | Double | The average outbound stream video frame rate per second. |

### Derived types

| Type | Description |
| :--- | :--- |
| [teleconferenceDeviceScreenSharingQuality](https://learn.microsoft.com/en-us/graph/api/resources/teleconferencedevicescreensharingquality?view=graph-rest-1.0) | Video teleconferencing device screen-sharing quality data. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "averageInboundBitRate": 1024,
  "averageInboundFrameRate": 1024,
  "averageInboundJitter": "String (ISO 8601 duration)",
  "averageInboundPacketLossRateInPercentage": 10,
  "averageInboundRoundTripDelay": "String (ISO 8601 duration)",
  "averageOutboundBitRate": 1024,
  "averageOutboundFrameRate": 1024,
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
