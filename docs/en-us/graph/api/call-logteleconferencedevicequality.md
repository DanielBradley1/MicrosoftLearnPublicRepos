<!-- Source: https://learn.microsoft.com/en-us/graph/api/call-logteleconferencedevicequality?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# call: logTeleconferenceDeviceQuality

Namespace: microsoft.graph

Log video teleconferencing device quality data.

The Cloud Video Interop \(CVI\) bot represents video teleconferencing \(VTC\) devices and acts as a back-to-back agent for a VTC device in a conference call. Because a CVI bot is in the middle of the VTC and Microsoft Teams infrastructure as a VTC proxy, it has two media legs. One media leg is between the CVI bot and Teams infrastructure, such as Teams conference server or a Teams client. The other media leg is between the CVI bot and the VTC device.

The third-party partners own the VTC media leg and the Teams infrastructure cannot access the quality data of the third-party call leg. This method is only for the CVI partners to provide their media quality data.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Calls.AccessMedia.All | Not available. |

## HTTP request

```http
POST /communications/calls/logTeleconferenceDeviceQuality
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| User-Agent | Describes the name and version of the calling application. Details will surface in Azure Information Protection Analytics. Suggested format is ApplicationName/Version. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| quality | [teleconferenceDeviceQuality](https://learn.microsoft.com/en-us/graph/api/resources/teleconferencedevicequality?view=graph-rest-1.0) | Quality data of VTC media leg. |

## Response

If successful, this method returns a `200 OK` response code. It doesn't return anything in the response body.

## Examples

The following example shows how to call this API.

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls/logTeleconferenceDeviceQuality
Content-type: application/json

{
  "quality": {
    "@odata.type": "#microsoft.graph.teleconferenceDeviceQuality",
    "callChainId": "0622673d-9f69-49b3-9d4f-5ec64f42ecce",
    "participantId": "ea078406-b5d4-4d3c-b85e-90103dcec7f6",
    "mediaLegId": "bd9ee398-4b9d-42c7-8b8d-4e8efad9435f",
    "deviceName": "TestAgent",
    "deviceDescription": "TestDescription",
    "mediaQualityList": [
      {
        "@odata.type": "#microsoft.graph.teleconferenceDeviceAudioQuality",
        "channelIndex": 1,
        "mediaDuration": "PT20M",
        "networkLinkSpeedInBytes": 13000,
        "localIPAddress": "127.0.0.1",
        "localPort": 6300,
        "remoteIPAddress": "102.1.1.101",
        "remotePort": 6301,
        "inboundPackets": 5500,
        "outboundPackets": 5400,
        "averageInboundPacketLossRateInPercentage": 0.01,
        "averageOutboundPacketLossRateInPercentage": 0.02,
        "maximumInboundPacketLossRateInPercentage": 0.05,
        "maximumOutboundPacketLossRateInPercentage": 0.06,
        "averageInboundRoundTripDelay": "PT0.03S",
        "averageOutboundRoundTripDelay": "PT0.04S",
        "maximumInboundRoundTripDelay": "PT0.13S",
        "maximumOutboundRoundTripDelay": "PT0.14S",
        "averageInboundJitter": "PT0.01S",
        "averageOutboundJitter": "PT0.015S",
        "maximumInboundJitter": "PT0.023S",
        "maximumOutboundJitter": "PT0.024S"
      },
      {
        "@odata.type": "#microsoft.graph.teleconferenceDeviceVideoQuality",
        "channelIndex": 1,
        "mediaDuration": "PT20M",
        "networkLinkSpeedInBytes": 13000,
        "localIPAddress": "127.0.0.1",
        "localPort": 6300,
        "remoteIPAddress": "102.1.1.101",
        "remotePort": 6301,
        "inboundPackets": 5500,
        "outboundPackets": 5400,
        "averageInboundPacketLossRateInPercentage": 0.01,
        "averageOutboundPacketLossRateInPercentage": 0.02,
        "maximumInboundPacketLossRateInPercentage": 0.05,
        "maximumOutboundPacketLossRateInPercentage": 0.06,
        "averageInboundRoundTripDelay": "PT0.03S",
        "averageOutboundRoundTripDelay": "PT0.04S",
        "maximumInboundRoundTripDelay": "PT0.13S",
        "maximumOutboundRoundTripDelay": "PT0.14S",
        "averageInboundJitter": "PT0.01S",
        "averageOutboundJitter": "PT0.015S",
        "maximumInboundJitter": "PT0.023S",
        "maximumOutboundJitter": "PT0.024S"
      },
      {
        "@odata.type": "#microsoft.graph.teleconferenceDeviceScreenSharingQuality",
        "channelIndex": 1,
        "mediaDuration": "PT20M",
        "networkLinkSpeedInBytes": 13000,
        "localIPAddress": "127.0.0.1",
        "localPort": 6300,
        "remoteIPAddress": "102.1.1.101",
        "remotePort": 6301,
        "inboundPackets": 5500,
        "outboundPackets": 5400,
        "averageInboundPacketLossRateInPercentage": 0.01,
        "averageOutboundPacketLossRateInPercentage": 0.02,
        "maximumInboundPacketLossRateInPercentage": 0.05,
        "maximumOutboundPacketLossRateInPercentage": 0.06,
        "averageInboundRoundTripDelay": "PT0.03S",
        "averageOutboundRoundTripDelay": "PT0.04S",
        "maximumInboundRoundTripDelay": "PT0.13S",
        "maximumOutboundRoundTripDelay": "PT0.14S",
        "averageInboundJitter": "PT0.01S",
        "averageOutboundJitter": "PT0.015S",
        "maximumInboundJitter": "PT0.023S",
        "maximumOutboundJitter": "PT0.024S"
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Communications.Calls.LogTeleconferenceDeviceQuality;
using Microsoft.Graph.Models;

var requestBody = new LogTeleconferenceDeviceQualityPostRequestBody
{
	Quality = new TeleconferenceDeviceQuality
	{
		OdataType = "#microsoft.graph.teleconferenceDeviceQuality",
		CallChainId = Guid.Parse("0622673d-9f69-49b3-9d4f-5ec64f42ecce"),
		ParticipantId = Guid.Parse("ea078406-b5d4-4d3c-b85e-90103dcec7f6"),
		MediaLegId = Guid.Parse("bd9ee398-4b9d-42c7-8b8d-4e8efad9435f"),
		DeviceName = "TestAgent",
		DeviceDescription = "TestDescription",
		MediaQualityList = new List<TeleconferenceDeviceMediaQuality>
		{
			new TeleconferenceDeviceAudioQuality
			{
				OdataType = "#microsoft.graph.teleconferenceDeviceAudioQuality",
				ChannelIndex = 1,
				MediaDuration = TimeSpan.Parse("PT20M"),
				NetworkLinkSpeedInBytes = 13000L,
				LocalIPAddress = "127.0.0.1",
				LocalPort = 6300,
				RemoteIPAddress = "102.1.1.101",
				RemotePort = 6301,
				InboundPackets = 5500L,
				OutboundPackets = 5400L,
				AverageInboundPacketLossRateInPercentage = 0.01d,
				AverageOutboundPacketLossRateInPercentage = 0.02d,
				MaximumInboundPacketLossRateInPercentage = 0.05d,
				MaximumOutboundPacketLossRateInPercentage = 0.06d,
				AverageInboundRoundTripDelay = TimeSpan.Parse("PT0.03S"),
				AverageOutboundRoundTripDelay = TimeSpan.Parse("PT0.04S"),
				MaximumInboundRoundTripDelay = TimeSpan.Parse("PT0.13S"),
				MaximumOutboundRoundTripDelay = TimeSpan.Parse("PT0.14S"),
				AverageInboundJitter = TimeSpan.Parse("PT0.01S"),
				AverageOutboundJitter = TimeSpan.Parse("PT0.015S"),
				MaximumInboundJitter = TimeSpan.Parse("PT0.023S"),
				MaximumOutboundJitter = TimeSpan.Parse("PT0.024S"),
			},
			new TeleconferenceDeviceVideoQuality
			{
				OdataType = "#microsoft.graph.teleconferenceDeviceVideoQuality",
				ChannelIndex = 1,
				MediaDuration = TimeSpan.Parse("PT20M"),
				NetworkLinkSpeedInBytes = 13000L,
				LocalIPAddress = "127.0.0.1",
				LocalPort = 6300,
				RemoteIPAddress = "102.1.1.101",
				RemotePort = 6301,
				InboundPackets = 5500L,
				OutboundPackets = 5400L,
				AverageInboundPacketLossRateInPercentage = 0.01d,
				AverageOutboundPacketLossRateInPercentage = 0.02d,
				MaximumInboundPacketLossRateInPercentage = 0.05d,
				MaximumOutboundPacketLossRateInPercentage = 0.06d,
				AverageInboundRoundTripDelay = TimeSpan.Parse("PT0.03S"),
				AverageOutboundRoundTripDelay = TimeSpan.Parse("PT0.04S"),
				MaximumInboundRoundTripDelay = TimeSpan.Parse("PT0.13S"),
				MaximumOutboundRoundTripDelay = TimeSpan.Parse("PT0.14S"),
				AverageInboundJitter = TimeSpan.Parse("PT0.01S"),
				AverageOutboundJitter = TimeSpan.Parse("PT0.015S"),
				MaximumInboundJitter = TimeSpan.Parse("PT0.023S"),
				MaximumOutboundJitter = TimeSpan.Parse("PT0.024S"),
			},
			new TeleconferenceDeviceScreenSharingQuality
			{
				OdataType = "#microsoft.graph.teleconferenceDeviceScreenSharingQuality",
				ChannelIndex = 1,
				MediaDuration = TimeSpan.Parse("PT20M"),
				NetworkLinkSpeedInBytes = 13000L,
				LocalIPAddress = "127.0.0.1",
				LocalPort = 6300,
				RemoteIPAddress = "102.1.1.101",
				RemotePort = 6301,
				InboundPackets = 5500L,
				OutboundPackets = 5400L,
				AverageInboundPacketLossRateInPercentage = 0.01d,
				AverageOutboundPacketLossRateInPercentage = 0.02d,
				MaximumInboundPacketLossRateInPercentage = 0.05d,
				MaximumOutboundPacketLossRateInPercentage = 0.06d,
				AverageInboundRoundTripDelay = TimeSpan.Parse("PT0.03S"),
				AverageOutboundRoundTripDelay = TimeSpan.Parse("PT0.04S"),
				MaximumInboundRoundTripDelay = TimeSpan.Parse("PT0.13S"),
				MaximumOutboundRoundTripDelay = TimeSpan.Parse("PT0.14S"),
				AverageInboundJitter = TimeSpan.Parse("PT0.01S"),
				AverageOutboundJitter = TimeSpan.Parse("PT0.015S"),
				MaximumInboundJitter = TimeSpan.Parse("PT0.023S"),
				MaximumOutboundJitter = TimeSpan.Parse("PT0.024S"),
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Communications.Calls.LogTeleconferenceDeviceQuality.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphcommunications "github.com/microsoftgraph/msgraph-sdk-go/communications"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphcommunications.NewLogTeleconferenceDeviceQualityPostRequestBody()
quality := graphmodels.NewTeleconferenceDeviceQuality()
callChainId := uuid.MustParse("0622673d-9f69-49b3-9d4f-5ec64f42ecce")
quality.SetCallChainId(&callChainId) 
participantId := uuid.MustParse("ea078406-b5d4-4d3c-b85e-90103dcec7f6")
quality.SetParticipantId(&participantId) 
mediaLegId := uuid.MustParse("bd9ee398-4b9d-42c7-8b8d-4e8efad9435f")
quality.SetMediaLegId(&mediaLegId) 
deviceName := "TestAgent"
quality.SetDeviceName(&deviceName) 
deviceDescription := "TestDescription"
quality.SetDeviceDescription(&deviceDescription) 


teleconferenceDeviceMediaQuality := graphmodels.NewTeleconferenceDeviceAudioQuality()
channelIndex := int32(1)
teleconferenceDeviceMediaQuality.SetChannelIndex(&channelIndex) 
mediaDuration , err := abstractions.ParseISODuration("PT20M")
teleconferenceDeviceMediaQuality.SetMediaDuration(&mediaDuration) 
networkLinkSpeedInBytes := int64(13000)
teleconferenceDeviceMediaQuality.SetNetworkLinkSpeedInBytes(&networkLinkSpeedInBytes) 
localIPAddress := "127.0.0.1"
teleconferenceDeviceMediaQuality.SetLocalIPAddress(&localIPAddress) 
localPort := int32(6300)
teleconferenceDeviceMediaQuality.SetLocalPort(&localPort) 
remoteIPAddress := "102.1.1.101"
teleconferenceDeviceMediaQuality.SetRemoteIPAddress(&remoteIPAddress) 
remotePort := int32(6301)
teleconferenceDeviceMediaQuality.SetRemotePort(&remotePort) 
inboundPackets := int64(5500)
teleconferenceDeviceMediaQuality.SetInboundPackets(&inboundPackets) 
outboundPackets := int64(5400)
teleconferenceDeviceMediaQuality.SetOutboundPackets(&outboundPackets) 
averageInboundPacketLossRateInPercentage := float64(0.01)
teleconferenceDeviceMediaQuality.SetAverageInboundPacketLossRateInPercentage(&averageInboundPacketLossRateInPercentage) 
averageOutboundPacketLossRateInPercentage := float64(0.02)
teleconferenceDeviceMediaQuality.SetAverageOutboundPacketLossRateInPercentage(&averageOutboundPacketLossRateInPercentage) 
maximumInboundPacketLossRateInPercentage := float64(0.05)
teleconferenceDeviceMediaQuality.SetMaximumInboundPacketLossRateInPercentage(&maximumInboundPacketLossRateInPercentage) 
maximumOutboundPacketLossRateInPercentage := float64(0.06)
teleconferenceDeviceMediaQuality.SetMaximumOutboundPacketLossRateInPercentage(&maximumOutboundPacketLossRateInPercentage) 
averageInboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.03S")
teleconferenceDeviceMediaQuality.SetAverageInboundRoundTripDelay(&averageInboundRoundTripDelay) 
averageOutboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.04S")
teleconferenceDeviceMediaQuality.SetAverageOutboundRoundTripDelay(&averageOutboundRoundTripDelay) 
maximumInboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.13S")
teleconferenceDeviceMediaQuality.SetMaximumInboundRoundTripDelay(&maximumInboundRoundTripDelay) 
maximumOutboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.14S")
teleconferenceDeviceMediaQuality.SetMaximumOutboundRoundTripDelay(&maximumOutboundRoundTripDelay) 
averageInboundJitter , err := abstractions.ParseISODuration("PT0.01S")
teleconferenceDeviceMediaQuality.SetAverageInboundJitter(&averageInboundJitter) 
averageOutboundJitter , err := abstractions.ParseISODuration("PT0.015S")
teleconferenceDeviceMediaQuality.SetAverageOutboundJitter(&averageOutboundJitter) 
maximumInboundJitter , err := abstractions.ParseISODuration("PT0.023S")
teleconferenceDeviceMediaQuality.SetMaximumInboundJitter(&maximumInboundJitter) 
maximumOutboundJitter , err := abstractions.ParseISODuration("PT0.024S")
teleconferenceDeviceMediaQuality.SetMaximumOutboundJitter(&maximumOutboundJitter) 
teleconferenceDeviceMediaQuality1 := graphmodels.NewTeleconferenceDeviceVideoQuality()
channelIndex := int32(1)
teleconferenceDeviceMediaQuality1.SetChannelIndex(&channelIndex) 
mediaDuration , err := abstractions.ParseISODuration("PT20M")
teleconferenceDeviceMediaQuality1.SetMediaDuration(&mediaDuration) 
networkLinkSpeedInBytes := int64(13000)
teleconferenceDeviceMediaQuality1.SetNetworkLinkSpeedInBytes(&networkLinkSpeedInBytes) 
localIPAddress := "127.0.0.1"
teleconferenceDeviceMediaQuality1.SetLocalIPAddress(&localIPAddress) 
localPort := int32(6300)
teleconferenceDeviceMediaQuality1.SetLocalPort(&localPort) 
remoteIPAddress := "102.1.1.101"
teleconferenceDeviceMediaQuality1.SetRemoteIPAddress(&remoteIPAddress) 
remotePort := int32(6301)
teleconferenceDeviceMediaQuality1.SetRemotePort(&remotePort) 
inboundPackets := int64(5500)
teleconferenceDeviceMediaQuality1.SetInboundPackets(&inboundPackets) 
outboundPackets := int64(5400)
teleconferenceDeviceMediaQuality1.SetOutboundPackets(&outboundPackets) 
averageInboundPacketLossRateInPercentage := float64(0.01)
teleconferenceDeviceMediaQuality1.SetAverageInboundPacketLossRateInPercentage(&averageInboundPacketLossRateInPercentage) 
averageOutboundPacketLossRateInPercentage := float64(0.02)
teleconferenceDeviceMediaQuality1.SetAverageOutboundPacketLossRateInPercentage(&averageOutboundPacketLossRateInPercentage) 
maximumInboundPacketLossRateInPercentage := float64(0.05)
teleconferenceDeviceMediaQuality1.SetMaximumInboundPacketLossRateInPercentage(&maximumInboundPacketLossRateInPercentage) 
maximumOutboundPacketLossRateInPercentage := float64(0.06)
teleconferenceDeviceMediaQuality1.SetMaximumOutboundPacketLossRateInPercentage(&maximumOutboundPacketLossRateInPercentage) 
averageInboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.03S")
teleconferenceDeviceMediaQuality1.SetAverageInboundRoundTripDelay(&averageInboundRoundTripDelay) 
averageOutboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.04S")
teleconferenceDeviceMediaQuality1.SetAverageOutboundRoundTripDelay(&averageOutboundRoundTripDelay) 
maximumInboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.13S")
teleconferenceDeviceMediaQuality1.SetMaximumInboundRoundTripDelay(&maximumInboundRoundTripDelay) 
maximumOutboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.14S")
teleconferenceDeviceMediaQuality1.SetMaximumOutboundRoundTripDelay(&maximumOutboundRoundTripDelay) 
averageInboundJitter , err := abstractions.ParseISODuration("PT0.01S")
teleconferenceDeviceMediaQuality1.SetAverageInboundJitter(&averageInboundJitter) 
averageOutboundJitter , err := abstractions.ParseISODuration("PT0.015S")
teleconferenceDeviceMediaQuality1.SetAverageOutboundJitter(&averageOutboundJitter) 
maximumInboundJitter , err := abstractions.ParseISODuration("PT0.023S")
teleconferenceDeviceMediaQuality1.SetMaximumInboundJitter(&maximumInboundJitter) 
maximumOutboundJitter , err := abstractions.ParseISODuration("PT0.024S")
teleconferenceDeviceMediaQuality1.SetMaximumOutboundJitter(&maximumOutboundJitter) 
teleconferenceDeviceMediaQuality2 := graphmodels.NewTeleconferenceDeviceScreenSharingQuality()
channelIndex := int32(1)
teleconferenceDeviceMediaQuality2.SetChannelIndex(&channelIndex) 
mediaDuration , err := abstractions.ParseISODuration("PT20M")
teleconferenceDeviceMediaQuality2.SetMediaDuration(&mediaDuration) 
networkLinkSpeedInBytes := int64(13000)
teleconferenceDeviceMediaQuality2.SetNetworkLinkSpeedInBytes(&networkLinkSpeedInBytes) 
localIPAddress := "127.0.0.1"
teleconferenceDeviceMediaQuality2.SetLocalIPAddress(&localIPAddress) 
localPort := int32(6300)
teleconferenceDeviceMediaQuality2.SetLocalPort(&localPort) 
remoteIPAddress := "102.1.1.101"
teleconferenceDeviceMediaQuality2.SetRemoteIPAddress(&remoteIPAddress) 
remotePort := int32(6301)
teleconferenceDeviceMediaQuality2.SetRemotePort(&remotePort) 
inboundPackets := int64(5500)
teleconferenceDeviceMediaQuality2.SetInboundPackets(&inboundPackets) 
outboundPackets := int64(5400)
teleconferenceDeviceMediaQuality2.SetOutboundPackets(&outboundPackets) 
averageInboundPacketLossRateInPercentage := float64(0.01)
teleconferenceDeviceMediaQuality2.SetAverageInboundPacketLossRateInPercentage(&averageInboundPacketLossRateInPercentage) 
averageOutboundPacketLossRateInPercentage := float64(0.02)
teleconferenceDeviceMediaQuality2.SetAverageOutboundPacketLossRateInPercentage(&averageOutboundPacketLossRateInPercentage) 
maximumInboundPacketLossRateInPercentage := float64(0.05)
teleconferenceDeviceMediaQuality2.SetMaximumInboundPacketLossRateInPercentage(&maximumInboundPacketLossRateInPercentage) 
maximumOutboundPacketLossRateInPercentage := float64(0.06)
teleconferenceDeviceMediaQuality2.SetMaximumOutboundPacketLossRateInPercentage(&maximumOutboundPacketLossRateInPercentage) 
averageInboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.03S")
teleconferenceDeviceMediaQuality2.SetAverageInboundRoundTripDelay(&averageInboundRoundTripDelay) 
averageOutboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.04S")
teleconferenceDeviceMediaQuality2.SetAverageOutboundRoundTripDelay(&averageOutboundRoundTripDelay) 
maximumInboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.13S")
teleconferenceDeviceMediaQuality2.SetMaximumInboundRoundTripDelay(&maximumInboundRoundTripDelay) 
maximumOutboundRoundTripDelay , err := abstractions.ParseISODuration("PT0.14S")
teleconferenceDeviceMediaQuality2.SetMaximumOutboundRoundTripDelay(&maximumOutboundRoundTripDelay) 
averageInboundJitter , err := abstractions.ParseISODuration("PT0.01S")
teleconferenceDeviceMediaQuality2.SetAverageInboundJitter(&averageInboundJitter) 
averageOutboundJitter , err := abstractions.ParseISODuration("PT0.015S")
teleconferenceDeviceMediaQuality2.SetAverageOutboundJitter(&averageOutboundJitter) 
maximumInboundJitter , err := abstractions.ParseISODuration("PT0.023S")
teleconferenceDeviceMediaQuality2.SetMaximumInboundJitter(&maximumInboundJitter) 
maximumOutboundJitter , err := abstractions.ParseISODuration("PT0.024S")
teleconferenceDeviceMediaQuality2.SetMaximumOutboundJitter(&maximumOutboundJitter) 

mediaQualityList := []graphmodels.TeleconferenceDeviceMediaQualityable {
	teleconferenceDeviceMediaQuality,
	teleconferenceDeviceMediaQuality1,
	teleconferenceDeviceMediaQuality2,
}
quality.SetMediaQualityList(mediaQualityList)
requestBody.SetQuality(quality)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Communications().Calls().LogTeleconferenceDeviceQuality().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.communications.calls.logteleconferencedevicequality.LogTeleconferenceDeviceQualityPostRequestBody logTeleconferenceDeviceQualityPostRequestBody = new com.microsoft.graph.communications.calls.logteleconferencedevicequality.LogTeleconferenceDeviceQualityPostRequestBody();
TeleconferenceDeviceQuality quality = new TeleconferenceDeviceQuality();
quality.setOdataType("#microsoft.graph.teleconferenceDeviceQuality");
quality.setCallChainId(UUID.fromString("0622673d-9f69-49b3-9d4f-5ec64f42ecce"));
quality.setParticipantId(UUID.fromString("ea078406-b5d4-4d3c-b85e-90103dcec7f6"));
quality.setMediaLegId(UUID.fromString("bd9ee398-4b9d-42c7-8b8d-4e8efad9435f"));
quality.setDeviceName("TestAgent");
quality.setDeviceDescription("TestDescription");
LinkedList<TeleconferenceDeviceMediaQuality> mediaQualityList = new LinkedList<TeleconferenceDeviceMediaQuality>();
TeleconferenceDeviceAudioQuality teleconferenceDeviceMediaQuality = new TeleconferenceDeviceAudioQuality();
teleconferenceDeviceMediaQuality.setOdataType("#microsoft.graph.teleconferenceDeviceAudioQuality");
teleconferenceDeviceMediaQuality.setChannelIndex(1);
PeriodAndDuration mediaDuration = PeriodAndDuration.ofDuration(Duration.parse("PT20M"));
teleconferenceDeviceMediaQuality.setMediaDuration(mediaDuration);
teleconferenceDeviceMediaQuality.setNetworkLinkSpeedInBytes(13000L);
teleconferenceDeviceMediaQuality.setLocalIPAddress("127.0.0.1");
teleconferenceDeviceMediaQuality.setLocalPort(6300);
teleconferenceDeviceMediaQuality.setRemoteIPAddress("102.1.1.101");
teleconferenceDeviceMediaQuality.setRemotePort(6301);
teleconferenceDeviceMediaQuality.setInboundPackets(5500L);
teleconferenceDeviceMediaQuality.setOutboundPackets(5400L);
teleconferenceDeviceMediaQuality.setAverageInboundPacketLossRateInPercentage(0.01d);
teleconferenceDeviceMediaQuality.setAverageOutboundPacketLossRateInPercentage(0.02d);
teleconferenceDeviceMediaQuality.setMaximumInboundPacketLossRateInPercentage(0.05d);
teleconferenceDeviceMediaQuality.setMaximumOutboundPacketLossRateInPercentage(0.06d);
PeriodAndDuration averageInboundRoundTripDelay = PeriodAndDuration.ofDuration(Duration.parse("PT0.03S"));
teleconferenceDeviceMediaQuality.setAverageInboundRoundTripDelay(averageInboundRoundTripDelay);
PeriodAndDuration averageOutboundRoundTripDelay = PeriodAndDuration.ofDuration(Duration.parse("PT0.04S"));
teleconferenceDeviceMediaQuality.setAverageOutboundRoundTripDelay(averageOutboundRoundTripDelay);
PeriodAndDuration maximumInboundRoundTripDelay = PeriodAndDuration.ofDuration(Duration.parse("PT0.13S"));
teleconferenceDeviceMediaQuality.setMaximumInboundRoundTripDelay(maximumInboundRoundTripDelay);
PeriodAndDuration maximumOutboundRoundTripDelay = PeriodAndDuration.ofDuration(Duration.parse("PT0.14S"));
teleconferenceDeviceMediaQuality.setMaximumOutboundRoundTripDelay(maximumOutboundRoundTripDelay);
PeriodAndDuration averageInboundJitter = PeriodAndDuration.ofDuration(Duration.parse("PT0.01S"));
teleconferenceDeviceMediaQuality.setAverageInboundJitter(averageInboundJitter);
PeriodAndDuration averageOutboundJitter = PeriodAndDuration.ofDuration(Duration.parse("PT0.015S"));
teleconferenceDeviceMediaQuality.setAverageOutboundJitter(averageOutboundJitter);
PeriodAndDuration maximumInboundJitter = PeriodAndDuration.ofDuration(Duration.parse("PT0.023S"));
teleconferenceDeviceMediaQuality.setMaximumInboundJitter(maximumInboundJitter);
PeriodAndDuration maximumOutboundJitter = PeriodAndDuration.ofDuration(Duration.parse("PT0.024S"));
teleconferenceDeviceMediaQuality.setMaximumOutboundJitter(maximumOutboundJitter);
mediaQualityList.add(teleconferenceDeviceMediaQuality);
TeleconferenceDeviceVideoQuality teleconferenceDeviceMediaQuality1 = new TeleconferenceDeviceVideoQuality();
teleconferenceDeviceMediaQuality1.setOdataType("#microsoft.graph.teleconferenceDeviceVideoQuality");
teleconferenceDeviceMediaQuality1.setChannelIndex(1);
PeriodAndDuration mediaDuration1 = PeriodAndDuration.ofDuration(Duration.parse("PT20M"));
teleconferenceDeviceMediaQuality1.setMediaDuration(mediaDuration1);
teleconferenceDeviceMediaQuality1.setNetworkLinkSpeedInBytes(13000L);
teleconferenceDeviceMediaQuality1.setLocalIPAddress("127.0.0.1");
teleconferenceDeviceMediaQuality1.setLocalPort(6300);
teleconferenceDeviceMediaQuality1.setRemoteIPAddress("102.1.1.101");
teleconferenceDeviceMediaQuality1.setRemotePort(6301);
teleconferenceDeviceMediaQuality1.setInboundPackets(5500L);
teleconferenceDeviceMediaQuality1.setOutboundPackets(5400L);
teleconferenceDeviceMediaQuality1.setAverageInboundPacketLossRateInPercentage(0.01d);
teleconferenceDeviceMediaQuality1.setAverageOutboundPacketLossRateInPercentage(0.02d);
teleconferenceDeviceMediaQuality1.setMaximumInboundPacketLossRateInPercentage(0.05d);
teleconferenceDeviceMediaQuality1.setMaximumOutboundPacketLossRateInPercentage(0.06d);
PeriodAndDuration averageInboundRoundTripDelay1 = PeriodAndDuration.ofDuration(Duration.parse("PT0.03S"));
teleconferenceDeviceMediaQuality1.setAverageInboundRoundTripDelay(averageInboundRoundTripDelay1);
PeriodAndDuration averageOutboundRoundTripDelay1 = PeriodAndDuration.ofDuration(Duration.parse("PT0.04S"));
teleconferenceDeviceMediaQuality1.setAverageOutboundRoundTripDelay(averageOutboundRoundTripDelay1);
PeriodAndDuration maximumInboundRoundTripDelay1 = PeriodAndDuration.ofDuration(Duration.parse("PT0.13S"));
teleconferenceDeviceMediaQuality1.setMaximumInboundRoundTripDelay(maximumInboundRoundTripDelay1);
PeriodAndDuration maximumOutboundRoundTripDelay1 = PeriodAndDuration.ofDuration(Duration.parse("PT0.14S"));
teleconferenceDeviceMediaQuality1.setMaximumOutboundRoundTripDelay(maximumOutboundRoundTripDelay1);
PeriodAndDuration averageInboundJitter1 = PeriodAndDuration.ofDuration(Duration.parse("PT0.01S"));
teleconferenceDeviceMediaQuality1.setAverageInboundJitter(averageInboundJitter1);
PeriodAndDuration averageOutboundJitter1 = PeriodAndDuration.ofDuration(Duration.parse("PT0.015S"));
teleconferenceDeviceMediaQuality1.setAverageOutboundJitter(averageOutboundJitter1);
PeriodAndDuration maximumInboundJitter1 = PeriodAndDuration.ofDuration(Duration.parse("PT0.023S"));
teleconferenceDeviceMediaQuality1.setMaximumInboundJitter(maximumInboundJitter1);
PeriodAndDuration maximumOutboundJitter1 = PeriodAndDuration.ofDuration(Duration.parse("PT0.024S"));
teleconferenceDeviceMediaQuality1.setMaximumOutboundJitter(maximumOutboundJitter1);
mediaQualityList.add(teleconferenceDeviceMediaQuality1);
TeleconferenceDeviceScreenSharingQuality teleconferenceDeviceMediaQuality2 = new TeleconferenceDeviceScreenSharingQuality();
teleconferenceDeviceMediaQuality2.setOdataType("#microsoft.graph.teleconferenceDeviceScreenSharingQuality");
teleconferenceDeviceMediaQuality2.setChannelIndex(1);
PeriodAndDuration mediaDuration2 = PeriodAndDuration.ofDuration(Duration.parse("PT20M"));
teleconferenceDeviceMediaQuality2.setMediaDuration(mediaDuration2);
teleconferenceDeviceMediaQuality2.setNetworkLinkSpeedInBytes(13000L);
teleconferenceDeviceMediaQuality2.setLocalIPAddress("127.0.0.1");
teleconferenceDeviceMediaQuality2.setLocalPort(6300);
teleconferenceDeviceMediaQuality2.setRemoteIPAddress("102.1.1.101");
teleconferenceDeviceMediaQuality2.setRemotePort(6301);
teleconferenceDeviceMediaQuality2.setInboundPackets(5500L);
teleconferenceDeviceMediaQuality2.setOutboundPackets(5400L);
teleconferenceDeviceMediaQuality2.setAverageInboundPacketLossRateInPercentage(0.01d);
teleconferenceDeviceMediaQuality2.setAverageOutboundPacketLossRateInPercentage(0.02d);
teleconferenceDeviceMediaQuality2.setMaximumInboundPacketLossRateInPercentage(0.05d);
teleconferenceDeviceMediaQuality2.setMaximumOutboundPacketLossRateInPercentage(0.06d);
PeriodAndDuration averageInboundRoundTripDelay2 = PeriodAndDuration.ofDuration(Duration.parse("PT0.03S"));
teleconferenceDeviceMediaQuality2.setAverageInboundRoundTripDelay(averageInboundRoundTripDelay2);
PeriodAndDuration averageOutboundRoundTripDelay2 = PeriodAndDuration.ofDuration(Duration.parse("PT0.04S"));
teleconferenceDeviceMediaQuality2.setAverageOutboundRoundTripDelay(averageOutboundRoundTripDelay2);
PeriodAndDuration maximumInboundRoundTripDelay2 = PeriodAndDuration.ofDuration(Duration.parse("PT0.13S"));
teleconferenceDeviceMediaQuality2.setMaximumInboundRoundTripDelay(maximumInboundRoundTripDelay2);
PeriodAndDuration maximumOutboundRoundTripDelay2 = PeriodAndDuration.ofDuration(Duration.parse("PT0.14S"));
teleconferenceDeviceMediaQuality2.setMaximumOutboundRoundTripDelay(maximumOutboundRoundTripDelay2);
PeriodAndDuration averageInboundJitter2 = PeriodAndDuration.ofDuration(Duration.parse("PT0.01S"));
teleconferenceDeviceMediaQuality2.setAverageInboundJitter(averageInboundJitter2);
PeriodAndDuration averageOutboundJitter2 = PeriodAndDuration.ofDuration(Duration.parse("PT0.015S"));
teleconferenceDeviceMediaQuality2.setAverageOutboundJitter(averageOutboundJitter2);
PeriodAndDuration maximumInboundJitter2 = PeriodAndDuration.ofDuration(Duration.parse("PT0.023S"));
teleconferenceDeviceMediaQuality2.setMaximumInboundJitter(maximumInboundJitter2);
PeriodAndDuration maximumOutboundJitter2 = PeriodAndDuration.ofDuration(Duration.parse("PT0.024S"));
teleconferenceDeviceMediaQuality2.setMaximumOutboundJitter(maximumOutboundJitter2);
mediaQualityList.add(teleconferenceDeviceMediaQuality2);
quality.setMediaQualityList(mediaQualityList);
logTeleconferenceDeviceQualityPostRequestBody.setQuality(quality);
graphClient.communications().calls().logTeleconferenceDeviceQuality().post(logTeleconferenceDeviceQualityPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const logTeleconferenceDeviceQuality = {
  quality: {
    '@odata.type': '#microsoft.graph.teleconferenceDeviceQuality',
    callChainId: '0622673d-9f69-49b3-9d4f-5ec64f42ecce',
    participantId: 'ea078406-b5d4-4d3c-b85e-90103dcec7f6',
    mediaLegId: 'bd9ee398-4b9d-42c7-8b8d-4e8efad9435f',
    deviceName: 'TestAgent',
    deviceDescription: 'TestDescription',
    mediaQualityList: [
      {
        '@odata.type': '#microsoft.graph.teleconferenceDeviceAudioQuality',
        channelIndex: 1,
        mediaDuration: 'PT20M',
        networkLinkSpeedInBytes: 13000,
        localIPAddress: '127.0.0.1',
        localPort: 6300,
        remoteIPAddress: '102.1.1.101',
        remotePort: 6301,
        inboundPackets: 5500,
        outboundPackets: 5400,
        averageInboundPacketLossRateInPercentage: 0.01,
        averageOutboundPacketLossRateInPercentage: 0.02,
        maximumInboundPacketLossRateInPercentage: 0.05,
        maximumOutboundPacketLossRateInPercentage: 0.06,
        averageInboundRoundTripDelay: 'PT0.03S',
        averageOutboundRoundTripDelay: 'PT0.04S',
        maximumInboundRoundTripDelay: 'PT0.13S',
        maximumOutboundRoundTripDelay: 'PT0.14S',
        averageInboundJitter: 'PT0.01S',
        averageOutboundJitter: 'PT0.015S',
        maximumInboundJitter: 'PT0.023S',
        maximumOutboundJitter: 'PT0.024S'
      },
      {
        '@odata.type': '#microsoft.graph.teleconferenceDeviceVideoQuality',
        channelIndex: 1,
        mediaDuration: 'PT20M',
        networkLinkSpeedInBytes: 13000,
        localIPAddress: '127.0.0.1',
        localPort: 6300,
        remoteIPAddress: '102.1.1.101',
        remotePort: 6301,
        inboundPackets: 5500,
        outboundPackets: 5400,
        averageInboundPacketLossRateInPercentage: 0.01,
        averageOutboundPacketLossRateInPercentage: 0.02,
        maximumInboundPacketLossRateInPercentage: 0.05,
        maximumOutboundPacketLossRateInPercentage: 0.06,
        averageInboundRoundTripDelay: 'PT0.03S',
        averageOutboundRoundTripDelay: 'PT0.04S',
        maximumInboundRoundTripDelay: 'PT0.13S',
        maximumOutboundRoundTripDelay: 'PT0.14S',
        averageInboundJitter: 'PT0.01S',
        averageOutboundJitter: 'PT0.015S',
        maximumInboundJitter: 'PT0.023S',
        maximumOutboundJitter: 'PT0.024S'
      },
      {
        '@odata.type': '#microsoft.graph.teleconferenceDeviceScreenSharingQuality',
        channelIndex: 1,
        mediaDuration: 'PT20M',
        networkLinkSpeedInBytes: 13000,
        localIPAddress: '127.0.0.1',
        localPort: 6300,
        remoteIPAddress: '102.1.1.101',
        remotePort: 6301,
        inboundPackets: 5500,
        outboundPackets: 5400,
        averageInboundPacketLossRateInPercentage: 0.01,
        averageOutboundPacketLossRateInPercentage: 0.02,
        maximumInboundPacketLossRateInPercentage: 0.05,
        maximumOutboundPacketLossRateInPercentage: 0.06,
        averageInboundRoundTripDelay: 'PT0.03S',
        averageOutboundRoundTripDelay: 'PT0.04S',
        maximumInboundRoundTripDelay: 'PT0.13S',
        maximumOutboundRoundTripDelay: 'PT0.14S',
        averageInboundJitter: 'PT0.01S',
        averageOutboundJitter: 'PT0.015S',
        maximumInboundJitter: 'PT0.023S',
        maximumOutboundJitter: 'PT0.024S'
      }
    ]
  }
};

await client.api('/communications/calls/logTeleconferenceDeviceQuality')
	.post(logTeleconferenceDeviceQuality);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\Calls\LogTeleconferenceDeviceQuality\LogTeleconferenceDeviceQualityPostRequestBody;
use Microsoft\Graph\Generated\Models\TeleconferenceDeviceQuality;
use Microsoft\Graph\Generated\Models\TeleconferenceDeviceMediaQuality;
use Microsoft\Graph\Generated\Models\TeleconferenceDeviceAudioQuality;
use Microsoft\Graph\Generated\Models\TeleconferenceDeviceVideoQuality;
use Microsoft\Graph\Generated\Models\TeleconferenceDeviceScreenSharingQuality;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new LogTeleconferenceDeviceQualityPostRequestBody();
$quality = new TeleconferenceDeviceQuality();
$quality->setOdataType('#microsoft.graph.teleconferenceDeviceQuality');
$quality->setCallChainId('0622673d-9f69-49b3-9d4f-5ec64f42ecce');
$quality->setParticipantId('ea078406-b5d4-4d3c-b85e-90103dcec7f6');
$quality->setMediaLegId('bd9ee398-4b9d-42c7-8b8d-4e8efad9435f');
$quality->setDeviceName('TestAgent');
$quality->setDeviceDescription('TestDescription');
$mediaQualityListTeleconferenceDeviceMediaQuality1 = new TeleconferenceDeviceAudioQuality();
$mediaQualityListTeleconferenceDeviceMediaQuality1->setOdataType('#microsoft.graph.teleconferenceDeviceAudioQuality');
$mediaQualityListTeleconferenceDeviceMediaQuality1->setChannelIndex(1);
$mediaQualityListTeleconferenceDeviceMediaQuality1->setMediaDuration(new \DateInterval('PT20M'));
$mediaQualityListTeleconferenceDeviceMediaQuality1->setNetworkLinkSpeedInBytes(13000);
$mediaQualityListTeleconferenceDeviceMediaQuality1->setLocalIPAddress('127.0.0.1');
$mediaQualityListTeleconferenceDeviceMediaQuality1->setLocalPort(6300);
$mediaQualityListTeleconferenceDeviceMediaQuality1->setRemoteIPAddress('102.1.1.101');
$mediaQualityListTeleconferenceDeviceMediaQuality1->setRemotePort(6301);
$mediaQualityListTeleconferenceDeviceMediaQuality1->setInboundPackets(5500);
$mediaQualityListTeleconferenceDeviceMediaQuality1->setOutboundPackets(5400);
$mediaQualityListTeleconferenceDeviceMediaQuality1->setAverageInboundPacketLossRateInPercentage(0.01);
$mediaQualityListTeleconferenceDeviceMediaQuality1->setAverageOutboundPacketLossRateInPercentage(0.02);
$mediaQualityListTeleconferenceDeviceMediaQuality1->setMaximumInboundPacketLossRateInPercentage(0.05);
$mediaQualityListTeleconferenceDeviceMediaQuality1->setMaximumOutboundPacketLossRateInPercentage(0.06);
$mediaQualityListTeleconferenceDeviceMediaQuality1->setAverageInboundRoundTripDelay(new \DateInterval('PT0.03S'));
$mediaQualityListTeleconferenceDeviceMediaQuality1->setAverageOutboundRoundTripDelay(new \DateInterval('PT0.04S'));
$mediaQualityListTeleconferenceDeviceMediaQuality1->setMaximumInboundRoundTripDelay(new \DateInterval('PT0.13S'));
$mediaQualityListTeleconferenceDeviceMediaQuality1->setMaximumOutboundRoundTripDelay(new \DateInterval('PT0.14S'));
$mediaQualityListTeleconferenceDeviceMediaQuality1->setAverageInboundJitter(new \DateInterval('PT0.01S'));
$mediaQualityListTeleconferenceDeviceMediaQuality1->setAverageOutboundJitter(new \DateInterval('PT0.015S'));
$mediaQualityListTeleconferenceDeviceMediaQuality1->setMaximumInboundJitter(new \DateInterval('PT0.023S'));
$mediaQualityListTeleconferenceDeviceMediaQuality1->setMaximumOutboundJitter(new \DateInterval('PT0.024S'));
$mediaQualityListArray []= $mediaQualityListTeleconferenceDeviceMediaQuality1;
$mediaQualityListTeleconferenceDeviceMediaQuality2 = new TeleconferenceDeviceVideoQuality();
$mediaQualityListTeleconferenceDeviceMediaQuality2->setOdataType('#microsoft.graph.teleconferenceDeviceVideoQuality');
$mediaQualityListTeleconferenceDeviceMediaQuality2->setChannelIndex(1);
$mediaQualityListTeleconferenceDeviceMediaQuality2->setMediaDuration(new \DateInterval('PT20M'));
$mediaQualityListTeleconferenceDeviceMediaQuality2->setNetworkLinkSpeedInBytes(13000);
$mediaQualityListTeleconferenceDeviceMediaQuality2->setLocalIPAddress('127.0.0.1');
$mediaQualityListTeleconferenceDeviceMediaQuality2->setLocalPort(6300);
$mediaQualityListTeleconferenceDeviceMediaQuality2->setRemoteIPAddress('102.1.1.101');
$mediaQualityListTeleconferenceDeviceMediaQuality2->setRemotePort(6301);
$mediaQualityListTeleconferenceDeviceMediaQuality2->setInboundPackets(5500);
$mediaQualityListTeleconferenceDeviceMediaQuality2->setOutboundPackets(5400);
$mediaQualityListTeleconferenceDeviceMediaQuality2->setAverageInboundPacketLossRateInPercentage(0.01);
$mediaQualityListTeleconferenceDeviceMediaQuality2->setAverageOutboundPacketLossRateInPercentage(0.02);
$mediaQualityListTeleconferenceDeviceMediaQuality2->setMaximumInboundPacketLossRateInPercentage(0.05);
$mediaQualityListTeleconferenceDeviceMediaQuality2->setMaximumOutboundPacketLossRateInPercentage(0.06);
$mediaQualityListTeleconferenceDeviceMediaQuality2->setAverageInboundRoundTripDelay(new \DateInterval('PT0.03S'));
$mediaQualityListTeleconferenceDeviceMediaQuality2->setAverageOutboundRoundTripDelay(new \DateInterval('PT0.04S'));
$mediaQualityListTeleconferenceDeviceMediaQuality2->setMaximumInboundRoundTripDelay(new \DateInterval('PT0.13S'));
$mediaQualityListTeleconferenceDeviceMediaQuality2->setMaximumOutboundRoundTripDelay(new \DateInterval('PT0.14S'));
$mediaQualityListTeleconferenceDeviceMediaQuality2->setAverageInboundJitter(new \DateInterval('PT0.01S'));
$mediaQualityListTeleconferenceDeviceMediaQuality2->setAverageOutboundJitter(new \DateInterval('PT0.015S'));
$mediaQualityListTeleconferenceDeviceMediaQuality2->setMaximumInboundJitter(new \DateInterval('PT0.023S'));
$mediaQualityListTeleconferenceDeviceMediaQuality2->setMaximumOutboundJitter(new \DateInterval('PT0.024S'));
$mediaQualityListArray []= $mediaQualityListTeleconferenceDeviceMediaQuality2;
$mediaQualityListTeleconferenceDeviceMediaQuality3 = new TeleconferenceDeviceScreenSharingQuality();
$mediaQualityListTeleconferenceDeviceMediaQuality3->setOdataType('#microsoft.graph.teleconferenceDeviceScreenSharingQuality');
$mediaQualityListTeleconferenceDeviceMediaQuality3->setChannelIndex(1);
$mediaQualityListTeleconferenceDeviceMediaQuality3->setMediaDuration(new \DateInterval('PT20M'));
$mediaQualityListTeleconferenceDeviceMediaQuality3->setNetworkLinkSpeedInBytes(13000);
$mediaQualityListTeleconferenceDeviceMediaQuality3->setLocalIPAddress('127.0.0.1');
$mediaQualityListTeleconferenceDeviceMediaQuality3->setLocalPort(6300);
$mediaQualityListTeleconferenceDeviceMediaQuality3->setRemoteIPAddress('102.1.1.101');
$mediaQualityListTeleconferenceDeviceMediaQuality3->setRemotePort(6301);
$mediaQualityListTeleconferenceDeviceMediaQuality3->setInboundPackets(5500);
$mediaQualityListTeleconferenceDeviceMediaQuality3->setOutboundPackets(5400);
$mediaQualityListTeleconferenceDeviceMediaQuality3->setAverageInboundPacketLossRateInPercentage(0.01);
$mediaQualityListTeleconferenceDeviceMediaQuality3->setAverageOutboundPacketLossRateInPercentage(0.02);
$mediaQualityListTeleconferenceDeviceMediaQuality3->setMaximumInboundPacketLossRateInPercentage(0.05);
$mediaQualityListTeleconferenceDeviceMediaQuality3->setMaximumOutboundPacketLossRateInPercentage(0.06);
$mediaQualityListTeleconferenceDeviceMediaQuality3->setAverageInboundRoundTripDelay(new \DateInterval('PT0.03S'));
$mediaQualityListTeleconferenceDeviceMediaQuality3->setAverageOutboundRoundTripDelay(new \DateInterval('PT0.04S'));
$mediaQualityListTeleconferenceDeviceMediaQuality3->setMaximumInboundRoundTripDelay(new \DateInterval('PT0.13S'));
$mediaQualityListTeleconferenceDeviceMediaQuality3->setMaximumOutboundRoundTripDelay(new \DateInterval('PT0.14S'));
$mediaQualityListTeleconferenceDeviceMediaQuality3->setAverageInboundJitter(new \DateInterval('PT0.01S'));
$mediaQualityListTeleconferenceDeviceMediaQuality3->setAverageOutboundJitter(new \DateInterval('PT0.015S'));
$mediaQualityListTeleconferenceDeviceMediaQuality3->setMaximumInboundJitter(new \DateInterval('PT0.023S'));
$mediaQualityListTeleconferenceDeviceMediaQuality3->setMaximumOutboundJitter(new \DateInterval('PT0.024S'));
$mediaQualityListArray []= $mediaQualityListTeleconferenceDeviceMediaQuality3;
$quality->setMediaQualityList($mediaQualityListArray);

$requestBody->setQuality($quality);

$graphServiceClient->communications()->calls()->logTeleconferenceDeviceQuality()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.calls.log_teleconference_device_quality.log_teleconference_device_quality_post_request_body import LogTeleconferenceDeviceQualityPostRequestBody
from msgraph.generated.models.teleconference_device_quality import TeleconferenceDeviceQuality
from msgraph.generated.models.teleconference_device_media_quality import TeleconferenceDeviceMediaQuality
from msgraph.generated.models.teleconference_device_audio_quality import TeleconferenceDeviceAudioQuality
from msgraph.generated.models.teleconference_device_video_quality import TeleconferenceDeviceVideoQuality
from msgraph.generated.models.teleconference_device_screen_sharing_quality import TeleconferenceDeviceScreenSharingQuality
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = LogTeleconferenceDeviceQualityPostRequestBody(
	quality = TeleconferenceDeviceQuality(
		odata_type = "#microsoft.graph.teleconferenceDeviceQuality",
		call_chain_id = UUID("0622673d-9f69-49b3-9d4f-5ec64f42ecce"),
		participant_id = UUID("ea078406-b5d4-4d3c-b85e-90103dcec7f6"),
		media_leg_id = UUID("bd9ee398-4b9d-42c7-8b8d-4e8efad9435f"),
		device_name = "TestAgent",
		device_description = "TestDescription",
		media_quality_list = [
			TeleconferenceDeviceAudioQuality(
				odata_type = "#microsoft.graph.teleconferenceDeviceAudioQuality",
				channel_index = 1,
				media_duration = "PT20M",
				network_link_speed_in_bytes = 13000,
				local_i_p_address = "127.0.0.1",
				local_port = 6300,
				remote_i_p_address = "102.1.1.101",
				remote_port = 6301,
				inbound_packets = 5500,
				outbound_packets = 5400,
				average_inbound_packet_loss_rate_in_percentage = 0.01,
				average_outbound_packet_loss_rate_in_percentage = 0.02,
				maximum_inbound_packet_loss_rate_in_percentage = 0.05,
				maximum_outbound_packet_loss_rate_in_percentage = 0.06,
				average_inbound_round_trip_delay = "PT0.03S",
				average_outbound_round_trip_delay = "PT0.04S",
				maximum_inbound_round_trip_delay = "PT0.13S",
				maximum_outbound_round_trip_delay = "PT0.14S",
				average_inbound_jitter = "PT0.01S",
				average_outbound_jitter = "PT0.015S",
				maximum_inbound_jitter = "PT0.023S",
				maximum_outbound_jitter = "PT0.024S",
			),
			TeleconferenceDeviceVideoQuality(
				odata_type = "#microsoft.graph.teleconferenceDeviceVideoQuality",
				channel_index = 1,
				media_duration = "PT20M",
				network_link_speed_in_bytes = 13000,
				local_i_p_address = "127.0.0.1",
				local_port = 6300,
				remote_i_p_address = "102.1.1.101",
				remote_port = 6301,
				inbound_packets = 5500,
				outbound_packets = 5400,
				average_inbound_packet_loss_rate_in_percentage = 0.01,
				average_outbound_packet_loss_rate_in_percentage = 0.02,
				maximum_inbound_packet_loss_rate_in_percentage = 0.05,
				maximum_outbound_packet_loss_rate_in_percentage = 0.06,
				average_inbound_round_trip_delay = "PT0.03S",
				average_outbound_round_trip_delay = "PT0.04S",
				maximum_inbound_round_trip_delay = "PT0.13S",
				maximum_outbound_round_trip_delay = "PT0.14S",
				average_inbound_jitter = "PT0.01S",
				average_outbound_jitter = "PT0.015S",
				maximum_inbound_jitter = "PT0.023S",
				maximum_outbound_jitter = "PT0.024S",
			),
			TeleconferenceDeviceScreenSharingQuality(
				odata_type = "#microsoft.graph.teleconferenceDeviceScreenSharingQuality",
				channel_index = 1,
				media_duration = "PT20M",
				network_link_speed_in_bytes = 13000,
				local_i_p_address = "127.0.0.1",
				local_port = 6300,
				remote_i_p_address = "102.1.1.101",
				remote_port = 6301,
				inbound_packets = 5500,
				outbound_packets = 5400,
				average_inbound_packet_loss_rate_in_percentage = 0.01,
				average_outbound_packet_loss_rate_in_percentage = 0.02,
				maximum_inbound_packet_loss_rate_in_percentage = 0.05,
				maximum_outbound_packet_loss_rate_in_percentage = 0.06,
				average_inbound_round_trip_delay = "PT0.03S",
				average_outbound_round_trip_delay = "PT0.04S",
				maximum_inbound_round_trip_delay = "PT0.13S",
				maximum_outbound_round_trip_delay = "PT0.14S",
				average_inbound_jitter = "PT0.01S",
				average_outbound_jitter = "PT0.015S",
				maximum_inbound_jitter = "PT0.023S",
				maximum_outbound_jitter = "PT0.024S",
			),
		],
	),
)

await graph_client.communications.calls.log_teleconference_device_quality.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```
