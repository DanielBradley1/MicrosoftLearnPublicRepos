<!-- Source: https://learn.microsoft.com/en-us/graph/api/participant-reportsyntheticmedia?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# participant: reportSyntheticMedia

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Report synthetic media detections for a [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-beta) in a meeting call. This action is intended for certified third-party audio and video synthetic media detection bots admitted to the meeting call. The detection bot calls this action to flag a participant whose stream it identifies as AI-generated or synthetic media. The detection result is propagated to all participants via roster updates.

After a successful request, the service stores the detection on the participant as a [syntheticMediaDetectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/syntheticmediadetectioninfo?view=graph-rest-beta) object in the participant's [syntheticMediaDetection](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-beta#properties) property and delivers it to all participants in a roster update notification. Each request with a new **id** creates a separate detection record; the service doesn't deduplicate or merge reports. When a participant has multiple detection records, the **syntheticMediaDetection** property reflects the most recent report.

Third-party bots can invoke this action only when the meeting tenant administrator grants the app the `Calls.ReportSyntheticMedia.All` application permission.

The detection bot must be admitted to the call before it can call this action. For more information about registering a calling bot and joining calls, see [Calls and online meetings](https://learn.microsoft.com/en-us/graph/api/resources/communications-api-overview?view=graph-rest-beta). The bot obtains the call ID and participant ID from the call roster and subsequent participant roster update notifications, and uses the [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-beta)'s **id** as `{call-id}` and the [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-beta)'s **id** as `{participant-id}` in the request URL.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Calls.ReportSyntheticMedia.All | Not available. |

## HTTP request

```http
POST /communications/calls/{call-id}/participants/{participant-id}/reportSyntheticMedia
POST /app/calls/{call-id}/participants/{participant-id}/reportSyntheticMedia
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that you can include when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| contentMetadata | [mediaMetadata](https://learn.microsoft.com/en-us/graph/api/resources/mediametadata?view=graph-rest-beta) | Metadata about the content that was analyzed. Required. |
| detectionDateTime | DateTimeOffset | Date and time when the bot performed the detection. This value reflects when the analysis occurred, not when the analyzed media was captured. For media that's recorded and analyzed later, specify the time of analysis. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Required. |
| detections | [syntheticMediaDetectionDetail](https://learn.microsoft.com/en-us/graph/api/resources/syntheticmediadetectiondetail?view=graph-rest-beta) collection | Per-model or per-segment detection results that support the overall finding. Required. |
| id | Guid | Unique identifier for the detection event, in GUID format. The detection bot generates this value, which must be globally unique across reports. Each request that specifies a new **id** creates a separate detection record. Required. |
| isMalicious | Boolean | Indicates whether the detected synthetic media has malicious intent. Set to `true` when the detection bot considers the AI-generated content to have malicious intent; otherwise, `false`. Required. |
| overallConfidence | Double | Aggregated confidence score that the participant's media is synthetic. The value ranges from `0.0` \(low confidence\) to `1.0` \(high confidence\). Each **confidence** value in the **detections** collection represents the score for an individual model or segment, whereas **overallConfidence** represents the aggregated score for the participant. Required. |
| severity | detectionSeverity | Qualitative severity banding of the detection. Because **severity** reflects the same underlying signal as **overallConfidence**, the two values should generally correspond. Optional. Nullable. Omit the value or set it to `null` when the severity can't be determined. The possible values are: `low`, `medium`, `high`, `unknownFutureValue`. |

## Response

If successful, this action returns a `200 OK` response code.

### Error responses

This action can return the following common errors. For more information, see [Errors in Microsoft Graph](https://learn.microsoft.com/en-us/graph/errors).

| Status code | Error condition |
| :--- | :--- |
| `400` | The request is malformed, such as an invalid participant ID format or a missing required parameter. |
| `403` | The app doesn't have the `Calls.ReportSyntheticMedia.All` permission, or the detection bot isn't admitted to the call. |
| `404` | The specified call or participant isn't found. |
| `429` | The app exceeded the request rate limit and is throttled. |

A live detection bot can call this action frequently for the same participant. To avoid throttling, report only meaningful changes in the detection rather than every analyzed frame, and limit the reporting rate to no more than one request per target participant per minute.

## Examples

### Example 1: Report audio synthetic media detection

The following example shows how to report a synthetic media detection for audio content.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/communications/calls/481f3600-983e-4276-9b59-c1b30ec8d125/participants/550fae72-d251-43ec-868c-373732c2704f/reportSyntheticMedia
Content-Type: application/json

{
  "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "detectionDateTime": "2026-03-13T21:00:00Z",
  "severity": "high",
  "overallConfidence": 0.92,
  "isMalicious": true,
  "contentMetadata": {
    "modality": "audio",
    "isRealTime": true,
    "mimeType": "audio/pcm",
    "byteSize": 0,
    "duration": 15,
    "audioMetadata": {
      "sampleRateHz": 16000,
      "bitDepth": 16,
      "channels": 1
    },
    "streamingMetadata": {
      "latencyMs": 50,
      "frameDropRate": 0.0,
      "networkJitterMs": 10
    }
  },
  "detections": [
    {
      "modelName": "DeepfakeDetector-v2",
      "modality": "audio",
      "modelTasks": ["voiceClone"],
      "segment": {
        "startTimeSec": 0,
        "endTimeSec": 15,
        "frameIndices": []
      },
      "confidence": 0.95
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Communications.Calls.Item.Participants.Item.ReportSyntheticMedia;
using Microsoft.Graph.Beta.Models;

var requestBody = new ReportSyntheticMediaPostRequestBody
{
	Id = Guid.Parse("a1b2c3d4-e5f6-7890-abcd-ef1234567890"),
	DetectionDateTime = DateTimeOffset.Parse("2026-03-13T21:00:00Z"),
	Severity = DetectionSeverity.High,
	OverallConfidence = 0.92d,
	IsMalicious = true,
	ContentMetadata = new MediaMetadata
	{
		Modality = ContentModality.Audio,
		IsRealTime = true,
		MimeType = "audio/pcm",
		ByteSize = 0L,
		Duration = 15,
		AudioMetadata = new AudioMetadata
		{
			SampleRateHz = 16000,
			BitDepth = 16,
			Channels = 1,
		},
		StreamingMetadata = new StreamingMetadata
		{
			LatencyMs = 50,
			FrameDropRate = 0d,
			NetworkJitterMs = 10,
		},
	},
	Detections = new List<SyntheticMediaDetectionDetail>
	{
		new SyntheticMediaDetectionDetail
		{
			ModelName = "DeepfakeDetector-v2",
			Modality = ContentModality.Audio,
			ModelTasks = new List<string>
			{
				"voiceClone",
			},
			Segment = new MediaSegment
			{
				StartTimeSec = 0,
				EndTimeSec = 15,
				FrameIndices = new List<Number>
				{
				},
			},
			Confidence = 0.95d,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Communications.Calls["{call-id}"].Participants["{participant-id}"].ReportSyntheticMedia.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  "github.com/google/uuid"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphcommunications "github.com/microsoftgraph/msgraph-beta-sdk-go/communications"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphcommunications.NewReportSyntheticMediaPostRequestBody()
id := uuid.MustParse("a1b2c3d4-e5f6-7890-abcd-ef1234567890")
requestBody.SetId(&id) 
detectionDateTime , err := time.Parse(time.RFC3339, "2026-03-13T21:00:00Z")
requestBody.SetDetectionDateTime(&detectionDateTime) 
severity := graphmodels.HIGH_DETECTIONSEVERITY 
requestBody.SetSeverity(&severity) 
overallConfidence := float64(0.92)
requestBody.SetOverallConfidence(&overallConfidence) 
isMalicious := true
requestBody.SetIsMalicious(&isMalicious) 
contentMetadata := graphmodels.NewMediaMetadata()
modality := graphmodels.AUDIO_CONTENTMODALITY 
contentMetadata.SetModality(&modality) 
isRealTime := true
contentMetadata.SetIsRealTime(&isRealTime) 
mimeType := "audio/pcm"
contentMetadata.SetMimeType(&mimeType) 
byteSize := int64(0)
contentMetadata.SetByteSize(&byteSize) 
duration := int32(15)
contentMetadata.SetDuration(&duration) 
audioMetadata := graphmodels.NewAudioMetadata()
sampleRateHz := int32(16000)
audioMetadata.SetSampleRateHz(&sampleRateHz) 
bitDepth := int32(16)
audioMetadata.SetBitDepth(&bitDepth) 
channels := int32(1)
audioMetadata.SetChannels(&channels) 
contentMetadata.SetAudioMetadata(audioMetadata)
streamingMetadata := graphmodels.NewStreamingMetadata()
latencyMs := int32(50)
streamingMetadata.SetLatencyMs(&latencyMs) 
frameDropRate := float64(0)
streamingMetadata.SetFrameDropRate(&frameDropRate) 
networkJitterMs := int32(10)
streamingMetadata.SetNetworkJitterMs(&networkJitterMs) 
contentMetadata.SetStreamingMetadata(streamingMetadata)
requestBody.SetContentMetadata(contentMetadata)


syntheticMediaDetectionDetail := graphmodels.NewSyntheticMediaDetectionDetail()
modelName := "DeepfakeDetector-v2"
syntheticMediaDetectionDetail.SetModelName(&modelName) 
modality := graphmodels.AUDIO_CONTENTMODALITY 
syntheticMediaDetectionDetail.SetModality(&modality) 
modelTasks := []string {
	"voiceClone",
}
syntheticMediaDetectionDetail.SetModelTasks(modelTasks)
segment := graphmodels.NewMediaSegment()
startTimeSec := int32(0)
segment.SetStartTimeSec(&startTimeSec) 
endTimeSec := int32(15)
segment.SetEndTimeSec(&endTimeSec) 
frameIndices := []graph.numberable {

}
segment.SetFrameIndices(frameIndices)
syntheticMediaDetectionDetail.SetSegment(segment)
confidence := float64(0.95)
syntheticMediaDetectionDetail.SetConfidence(&confidence) 

detections := []graphmodels.SyntheticMediaDetectionDetailable {
	syntheticMediaDetectionDetail,
}
requestBody.SetDetections(detections)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Communications().Calls().ByCallId("call-id").Participants().ByParticipantId("participant-id").ReportSyntheticMedia().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.communications.calls.item.participants.item.reportsyntheticmedia.ReportSyntheticMediaPostRequestBody reportSyntheticMediaPostRequestBody = new com.microsoft.graph.beta.communications.calls.item.participants.item.reportsyntheticmedia.ReportSyntheticMediaPostRequestBody();
reportSyntheticMediaPostRequestBody.setId(UUID.fromString("a1b2c3d4-e5f6-7890-abcd-ef1234567890"));
OffsetDateTime detectionDateTime = OffsetDateTime.parse("2026-03-13T21:00:00Z");
reportSyntheticMediaPostRequestBody.setDetectionDateTime(detectionDateTime);
reportSyntheticMediaPostRequestBody.setSeverity(DetectionSeverity.High);
reportSyntheticMediaPostRequestBody.setOverallConfidence(0.92d);
reportSyntheticMediaPostRequestBody.setIsMalicious(true);
MediaMetadata contentMetadata = new MediaMetadata();
contentMetadata.setModality(ContentModality.Audio);
contentMetadata.setIsRealTime(true);
contentMetadata.setMimeType("audio/pcm");
contentMetadata.setByteSize(0L);
contentMetadata.setDuration(15);
AudioMetadata audioMetadata = new AudioMetadata();
audioMetadata.setSampleRateHz(16000);
audioMetadata.setBitDepth(16);
audioMetadata.setChannels(1);
contentMetadata.setAudioMetadata(audioMetadata);
StreamingMetadata streamingMetadata = new StreamingMetadata();
streamingMetadata.setLatencyMs(50);
streamingMetadata.setFrameDropRate(0d);
streamingMetadata.setNetworkJitterMs(10);
contentMetadata.setStreamingMetadata(streamingMetadata);
reportSyntheticMediaPostRequestBody.setContentMetadata(contentMetadata);
LinkedList<SyntheticMediaDetectionDetail> detections = new LinkedList<SyntheticMediaDetectionDetail>();
SyntheticMediaDetectionDetail syntheticMediaDetectionDetail = new SyntheticMediaDetectionDetail();
syntheticMediaDetectionDetail.setModelName("DeepfakeDetector-v2");
syntheticMediaDetectionDetail.setModality(ContentModality.Audio);
LinkedList<String> modelTasks = new LinkedList<String>();
modelTasks.add("voiceClone");
syntheticMediaDetectionDetail.setModelTasks(modelTasks);
MediaSegment segment = new MediaSegment();
segment.setStartTimeSec(0);
segment.setEndTimeSec(15);
LinkedList<Number> frameIndices = new LinkedList<Number>();
segment.setFrameIndices(frameIndices);
syntheticMediaDetectionDetail.setSegment(segment);
syntheticMediaDetectionDetail.setConfidence(0.95d);
detections.add(syntheticMediaDetectionDetail);
reportSyntheticMediaPostRequestBody.setDetections(detections);
graphClient.communications().calls().byCallId("{call-id}").participants().byParticipantId("{participant-id}").reportSyntheticMedia().post(reportSyntheticMediaPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const reportSyntheticMedia = {
  id: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890',
  detectionDateTime: '2026-03-13T21:00:00Z',
  severity: 'high',
  overallConfidence: 0.92,
  isMalicious: true,
  contentMetadata: {
    modality: 'audio',
    isRealTime: true,
    mimeType: 'audio/pcm',
    byteSize: 0,
    duration: 15,
    audioMetadata: {
      sampleRateHz: 16000,
      bitDepth: 16,
      channels: 1
    },
    streamingMetadata: {
      latencyMs: 50,
      frameDropRate: 0.0,
      networkJitterMs: 10
    }
  },
  detections: [
    {
      modelName: 'DeepfakeDetector-v2',
      modality: 'audio',
      modelTasks: ['voiceClone'],
      segment: {
        startTimeSec: 0,
        endTimeSec: 15,
        frameIndices: []
      },
      confidence: 0.95
    }
  ]
};

await client.api('/communications/calls/481f3600-983e-4276-9b59-c1b30ec8d125/participants/550fae72-d251-43ec-868c-373732c2704f/reportSyntheticMedia')
	.version('beta')
	.post(reportSyntheticMedia);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Communications\Calls\Item\Participants\Item\ReportSyntheticMedia\ReportSyntheticMediaPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\DetectionSeverity;
use Microsoft\Graph\Beta\Generated\Models\MediaMetadata;
use Microsoft\Graph\Beta\Generated\Models\ContentModality;
use Microsoft\Graph\Beta\Generated\Models\AudioMetadata;
use Microsoft\Graph\Beta\Generated\Models\StreamingMetadata;
use Microsoft\Graph\Beta\Generated\Models\SyntheticMediaDetectionDetail;
use Microsoft\Graph\Beta\Generated\Models\MediaSegment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReportSyntheticMediaPostRequestBody();
$requestBody->setId('a1b2c3d4-e5f6-7890-abcd-ef1234567890');
$requestBody->setDetectionDateTime(new \DateTime('2026-03-13T21:00:00Z'));
$requestBody->setSeverity(new DetectionSeverity('high'));
$requestBody->setOverallConfidence(0.92);
$requestBody->setIsMalicious(true);
$contentMetadata = new MediaMetadata();
$contentMetadata->setModality(new ContentModality('audio'));
$contentMetadata->setIsRealTime(true);
$contentMetadata->setMimeType('audio/pcm');
$contentMetadata->setByteSize(0);
$contentMetadata->setDuration(15);
$contentMetadataAudioMetadata = new AudioMetadata();
$contentMetadataAudioMetadata->setSampleRateHz(16000);
$contentMetadataAudioMetadata->setBitDepth(16);
$contentMetadataAudioMetadata->setChannels(1);
$contentMetadata->setAudioMetadata($contentMetadataAudioMetadata);
$contentMetadataStreamingMetadata = new StreamingMetadata();
$contentMetadataStreamingMetadata->setLatencyMs(50);
$contentMetadataStreamingMetadata->setFrameDropRate(0);
$contentMetadataStreamingMetadata->setNetworkJitterMs(10);
$contentMetadata->setStreamingMetadata($contentMetadataStreamingMetadata);
$requestBody->setContentMetadata($contentMetadata);
$detectionsSyntheticMediaDetectionDetail1 = new SyntheticMediaDetectionDetail();
$detectionsSyntheticMediaDetectionDetail1->setModelName('DeepfakeDetector-v2');
$detectionsSyntheticMediaDetectionDetail1->setModality(new ContentModality('audio'));
$detectionsSyntheticMediaDetectionDetail1->setModelTasks(['voiceClone', 	]);
$detectionsSyntheticMediaDetectionDetail1Segment = new MediaSegment();
$detectionsSyntheticMediaDetectionDetail1Segment->setStartTimeSec(0);
$detectionsSyntheticMediaDetectionDetail1Segment->setEndTimeSec(15);
$detectionsSyntheticMediaDetectionDetail1Segment->setFrameIndices([	]);
$detectionsSyntheticMediaDetectionDetail1->setSegment($detectionsSyntheticMediaDetectionDetail1Segment);
$detectionsSyntheticMediaDetectionDetail1->setConfidence(0.95);
$detectionsArray []= $detectionsSyntheticMediaDetectionDetail1;
$requestBody->setDetections($detectionsArray);


$graphServiceClient->communications()->calls()->byCallId('call-id')->participants()->byParticipantId('participant-id')->reportSyntheticMedia()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.communications.calls.item.participants.item.report_synthetic_media.report_synthetic_media_post_request_body import ReportSyntheticMediaPostRequestBody
from msgraph_beta.generated.models.detection_severity import DetectionSeverity
from msgraph_beta.generated.models.media_metadata import MediaMetadata
from msgraph_beta.generated.models.content_modality import ContentModality
from msgraph_beta.generated.models.audio_metadata import AudioMetadata
from msgraph_beta.generated.models.streaming_metadata import StreamingMetadata
from msgraph_beta.generated.models.synthetic_media_detection_detail import SyntheticMediaDetectionDetail
from msgraph_beta.generated.models.media_segment import MediaSegment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReportSyntheticMediaPostRequestBody(
	id = UUID("a1b2c3d4-e5f6-7890-abcd-ef1234567890"),
	detection_date_time = "2026-03-13T21:00:00Z",
	severity = DetectionSeverity.High,
	overall_confidence = 0.92,
	is_malicious = True,
	content_metadata = MediaMetadata(
		modality = ContentModality.Audio,
		is_real_time = True,
		mime_type = "audio/pcm",
		byte_size = 0,
		duration = 15,
		audio_metadata = AudioMetadata(
			sample_rate_hz = 16000,
			bit_depth = 16,
			channels = 1,
		),
		streaming_metadata = StreamingMetadata(
			latency_ms = 50,
			frame_drop_rate = 0,
			network_jitter_ms = 10,
		),
	),
	detections = [
		SyntheticMediaDetectionDetail(
			model_name = "DeepfakeDetector-v2",
			modality = ContentModality.Audio,
			model_tasks = [
				"voiceClone",
			],
			segment = MediaSegment(
				start_time_sec = 0,
				end_time_sec = 15,
				frame_indices = [
				],
			),
			confidence = 0.95,
		),
	],
)

await graph_client.communications.calls.by_call_id('call-id').participants.by_participant_id('participant-id').report_synthetic_media.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```

### Example 2: Report video synthetic media detection

The following example shows how to report a synthetic media detection for video content.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/communications/calls/481f3600-983e-4276-9b59-c1b30ec8d125/participants/550fae72-d251-43ec-868c-373732c2704f/reportSyntheticMedia
Content-Type: application/json

{
  "id": "c3d4e5f6-a7b8-9012-cdef-345678901234",
  "detectionDateTime": "2026-03-13T21:05:00Z",
  "severity": "high",
  "overallConfidence": 0.91,
  "isMalicious": true,
  "contentMetadata": {
    "modality": "video",
    "isRealTime": false,
    "mimeType": "video/mp4",
    "byteSize": 2048000,
    "duration": 30,
    "videoMetadata": {
      "codec": "H.264",
      "frameRate": 30.0,
      "bitrateKbps": 512
    }
  },
  "detections": [
    {
      "modelName": "FaceSwapDetector-v3",
      "modality": "video",
      "modelTasks": ["faceSwap", "lipSync"],
      "segment": {
        "startTimeSec": 0,
        "endTimeSec": 0,
        "frameIndices": [150, 180, 210, 240]
      },
      "confidence": 0.91
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Communications.Calls.Item.Participants.Item.ReportSyntheticMedia;
using Microsoft.Graph.Beta.Models;

var requestBody = new ReportSyntheticMediaPostRequestBody
{
	Id = Guid.Parse("c3d4e5f6-a7b8-9012-cdef-345678901234"),
	DetectionDateTime = DateTimeOffset.Parse("2026-03-13T21:05:00Z"),
	Severity = DetectionSeverity.High,
	OverallConfidence = 0.91d,
	IsMalicious = true,
	ContentMetadata = new MediaMetadata
	{
		Modality = ContentModality.Video,
		IsRealTime = false,
		MimeType = "video/mp4",
		ByteSize = 2048000L,
		Duration = 30,
		VideoMetadata = new VideoMetadata
		{
			Codec = "H.264",
			FrameRate = 30d,
			BitrateKbps = 512,
		},
	},
	Detections = new List<SyntheticMediaDetectionDetail>
	{
		new SyntheticMediaDetectionDetail
		{
			ModelName = "FaceSwapDetector-v3",
			Modality = ContentModality.Video,
			ModelTasks = new List<string>
			{
				"faceSwap",
				"lipSync",
			},
			Segment = new MediaSegment
			{
				StartTimeSec = 0,
				EndTimeSec = 0,
				FrameIndices = new List<Number>
				{
					150,
					180,
					210,
					240,
				},
			},
			Confidence = 0.91d,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Communications.Calls["{call-id}"].Participants["{participant-id}"].ReportSyntheticMedia.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  "github.com/google/uuid"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphcommunications "github.com/microsoftgraph/msgraph-beta-sdk-go/communications"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphcommunications.NewReportSyntheticMediaPostRequestBody()
id := uuid.MustParse("c3d4e5f6-a7b8-9012-cdef-345678901234")
requestBody.SetId(&id) 
detectionDateTime , err := time.Parse(time.RFC3339, "2026-03-13T21:05:00Z")
requestBody.SetDetectionDateTime(&detectionDateTime) 
severity := graphmodels.HIGH_DETECTIONSEVERITY 
requestBody.SetSeverity(&severity) 
overallConfidence := float64(0.91)
requestBody.SetOverallConfidence(&overallConfidence) 
isMalicious := true
requestBody.SetIsMalicious(&isMalicious) 
contentMetadata := graphmodels.NewMediaMetadata()
modality := graphmodels.VIDEO_CONTENTMODALITY 
contentMetadata.SetModality(&modality) 
isRealTime := false
contentMetadata.SetIsRealTime(&isRealTime) 
mimeType := "video/mp4"
contentMetadata.SetMimeType(&mimeType) 
byteSize := int64(2048000)
contentMetadata.SetByteSize(&byteSize) 
duration := int32(30)
contentMetadata.SetDuration(&duration) 
videoMetadata := graphmodels.NewVideoMetadata()
codec := "H.264"
videoMetadata.SetCodec(&codec) 
frameRate := float64(30)
videoMetadata.SetFrameRate(&frameRate) 
bitrateKbps := int32(512)
videoMetadata.SetBitrateKbps(&bitrateKbps) 
contentMetadata.SetVideoMetadata(videoMetadata)
requestBody.SetContentMetadata(contentMetadata)


syntheticMediaDetectionDetail := graphmodels.NewSyntheticMediaDetectionDetail()
modelName := "FaceSwapDetector-v3"
syntheticMediaDetectionDetail.SetModelName(&modelName) 
modality := graphmodels.VIDEO_CONTENTMODALITY 
syntheticMediaDetectionDetail.SetModality(&modality) 
modelTasks := []string {
	"faceSwap",
	"lipSync",
}
syntheticMediaDetectionDetail.SetModelTasks(modelTasks)
segment := graphmodels.NewMediaSegment()
startTimeSec := int32(0)
segment.SetStartTimeSec(&startTimeSec) 
endTimeSec := int32(0)
segment.SetEndTimeSec(&endTimeSec) 
frameIndices := []graph.Numberable {
 := int32(150)
segment.Set(&) 
 := int32(180)
segment.Set(&) 
 := int32(210)
segment.Set(&) 
 := int32(240)
segment.Set(&)
}
segment.SetFrameIndices(frameIndices)
syntheticMediaDetectionDetail.SetSegment(segment)
confidence := float64(0.91)
syntheticMediaDetectionDetail.SetConfidence(&confidence) 

detections := []graphmodels.SyntheticMediaDetectionDetailable {
	syntheticMediaDetectionDetail,
}
requestBody.SetDetections(detections)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Communications().Calls().ByCallId("call-id").Participants().ByParticipantId("participant-id").ReportSyntheticMedia().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.communications.calls.item.participants.item.reportsyntheticmedia.ReportSyntheticMediaPostRequestBody reportSyntheticMediaPostRequestBody = new com.microsoft.graph.beta.communications.calls.item.participants.item.reportsyntheticmedia.ReportSyntheticMediaPostRequestBody();
reportSyntheticMediaPostRequestBody.setId(UUID.fromString("c3d4e5f6-a7b8-9012-cdef-345678901234"));
OffsetDateTime detectionDateTime = OffsetDateTime.parse("2026-03-13T21:05:00Z");
reportSyntheticMediaPostRequestBody.setDetectionDateTime(detectionDateTime);
reportSyntheticMediaPostRequestBody.setSeverity(DetectionSeverity.High);
reportSyntheticMediaPostRequestBody.setOverallConfidence(0.91d);
reportSyntheticMediaPostRequestBody.setIsMalicious(true);
MediaMetadata contentMetadata = new MediaMetadata();
contentMetadata.setModality(ContentModality.Video);
contentMetadata.setIsRealTime(false);
contentMetadata.setMimeType("video/mp4");
contentMetadata.setByteSize(2048000L);
contentMetadata.setDuration(30);
VideoMetadata videoMetadata = new VideoMetadata();
videoMetadata.setCodec("H.264");
videoMetadata.setFrameRate(30d);
videoMetadata.setBitrateKbps(512);
contentMetadata.setVideoMetadata(videoMetadata);
reportSyntheticMediaPostRequestBody.setContentMetadata(contentMetadata);
LinkedList<SyntheticMediaDetectionDetail> detections = new LinkedList<SyntheticMediaDetectionDetail>();
SyntheticMediaDetectionDetail syntheticMediaDetectionDetail = new SyntheticMediaDetectionDetail();
syntheticMediaDetectionDetail.setModelName("FaceSwapDetector-v3");
syntheticMediaDetectionDetail.setModality(ContentModality.Video);
LinkedList<String> modelTasks = new LinkedList<String>();
modelTasks.add("faceSwap");
modelTasks.add("lipSync");
syntheticMediaDetectionDetail.setModelTasks(modelTasks);
MediaSegment segment = new MediaSegment();
segment.setStartTimeSec(0);
segment.setEndTimeSec(0);
LinkedList<Number> frameIndices = new LinkedList<Number>();
frameIndices.add(150);
frameIndices.add(180);
frameIndices.add(210);
frameIndices.add(240);
segment.setFrameIndices(frameIndices);
syntheticMediaDetectionDetail.setSegment(segment);
syntheticMediaDetectionDetail.setConfidence(0.91d);
detections.add(syntheticMediaDetectionDetail);
reportSyntheticMediaPostRequestBody.setDetections(detections);
graphClient.communications().calls().byCallId("{call-id}").participants().byParticipantId("{participant-id}").reportSyntheticMedia().post(reportSyntheticMediaPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const reportSyntheticMedia = {
  id: 'c3d4e5f6-a7b8-9012-cdef-345678901234',
  detectionDateTime: '2026-03-13T21:05:00Z',
  severity: 'high',
  overallConfidence: 0.91,
  isMalicious: true,
  contentMetadata: {
    modality: 'video',
    isRealTime: false,
    mimeType: 'video/mp4',
    byteSize: 2048000,
    duration: 30,
    videoMetadata: {
      codec: 'H.264',
      frameRate: 30.0,
      bitrateKbps: 512
    }
  },
  detections: [
    {
      modelName: 'FaceSwapDetector-v3',
      modality: 'video',
      modelTasks: ['faceSwap', 'lipSync'],
      segment: {
        startTimeSec: 0,
        endTimeSec: 0,
        frameIndices: [150, 180, 210, 240]
      },
      confidence: 0.91
    }
  ]
};

await client.api('/communications/calls/481f3600-983e-4276-9b59-c1b30ec8d125/participants/550fae72-d251-43ec-868c-373732c2704f/reportSyntheticMedia')
	.version('beta')
	.post(reportSyntheticMedia);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Communications\Calls\Item\Participants\Item\ReportSyntheticMedia\ReportSyntheticMediaPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\DetectionSeverity;
use Microsoft\Graph\Beta\Generated\Models\MediaMetadata;
use Microsoft\Graph\Beta\Generated\Models\ContentModality;
use Microsoft\Graph\Beta\Generated\Models\VideoMetadata;
use Microsoft\Graph\Beta\Generated\Models\SyntheticMediaDetectionDetail;
use Microsoft\Graph\Beta\Generated\Models\MediaSegment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReportSyntheticMediaPostRequestBody();
$requestBody->setId('c3d4e5f6-a7b8-9012-cdef-345678901234');
$requestBody->setDetectionDateTime(new \DateTime('2026-03-13T21:05:00Z'));
$requestBody->setSeverity(new DetectionSeverity('high'));
$requestBody->setOverallConfidence(0.91);
$requestBody->setIsMalicious(true);
$contentMetadata = new MediaMetadata();
$contentMetadata->setModality(new ContentModality('video'));
$contentMetadata->setIsRealTime(false);
$contentMetadata->setMimeType('video/mp4');
$contentMetadata->setByteSize(2048000);
$contentMetadata->setDuration(30);
$contentMetadataVideoMetadata = new VideoMetadata();
$contentMetadataVideoMetadata->setCodec('H.264');
$contentMetadataVideoMetadata->setFrameRate(30);
$contentMetadataVideoMetadata->setBitrateKbps(512);
$contentMetadata->setVideoMetadata($contentMetadataVideoMetadata);
$requestBody->setContentMetadata($contentMetadata);
$detectionsSyntheticMediaDetectionDetail1 = new SyntheticMediaDetectionDetail();
$detectionsSyntheticMediaDetectionDetail1->setModelName('FaceSwapDetector-v3');
$detectionsSyntheticMediaDetectionDetail1->setModality(new ContentModality('video'));
$detectionsSyntheticMediaDetectionDetail1->setModelTasks(['faceSwap', 'lipSync', 	]);
$detectionsSyntheticMediaDetectionDetail1Segment = new MediaSegment();
$detectionsSyntheticMediaDetectionDetail1Segment->setStartTimeSec(0);
$detectionsSyntheticMediaDetectionDetail1Segment->setEndTimeSec(0);
$detectionsSyntheticMediaDetectionDetail1Segment->setFrameIndices([150,180,210,240,	]);
$detectionsSyntheticMediaDetectionDetail1->setSegment($detectionsSyntheticMediaDetectionDetail1Segment);
$detectionsSyntheticMediaDetectionDetail1->setConfidence(0.91);
$detectionsArray []= $detectionsSyntheticMediaDetectionDetail1;
$requestBody->setDetections($detectionsArray);


$graphServiceClient->communications()->calls()->byCallId('call-id')->participants()->byParticipantId('participant-id')->reportSyntheticMedia()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.communications.calls.item.participants.item.report_synthetic_media.report_synthetic_media_post_request_body import ReportSyntheticMediaPostRequestBody
from msgraph_beta.generated.models.detection_severity import DetectionSeverity
from msgraph_beta.generated.models.media_metadata import MediaMetadata
from msgraph_beta.generated.models.content_modality import ContentModality
from msgraph_beta.generated.models.video_metadata import VideoMetadata
from msgraph_beta.generated.models.synthetic_media_detection_detail import SyntheticMediaDetectionDetail
from msgraph_beta.generated.models.media_segment import MediaSegment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReportSyntheticMediaPostRequestBody(
	id = UUID("c3d4e5f6-a7b8-9012-cdef-345678901234"),
	detection_date_time = "2026-03-13T21:05:00Z",
	severity = DetectionSeverity.High,
	overall_confidence = 0.91,
	is_malicious = True,
	content_metadata = MediaMetadata(
		modality = ContentModality.Video,
		is_real_time = False,
		mime_type = "video/mp4",
		byte_size = 2048000,
		duration = 30,
		video_metadata = VideoMetadata(
			codec = "H.264",
			frame_rate = 30,
			bitrate_kbps = 512,
		),
	),
	detections = [
		SyntheticMediaDetectionDetail(
			model_name = "FaceSwapDetector-v3",
			modality = ContentModality.Video,
			model_tasks = [
				"faceSwap",
				"lipSync",
			],
			segment = MediaSegment(
				start_time_sec = 0,
				end_time_sec = 0,
				frame_indices = [
					150,
					180,
					210,
					240,
				],
			),
			confidence = 0.91,
		),
	],
)

await graph_client.communications.calls.by_call_id('call-id').participants.by_participant_id('participant-id').report_synthetic_media.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```

### Example 3: Report multimodal synthetic media detection

The following example shows how to report a real-time detection that combines audio and video analysis. The **modality** is `multimodal`, the **contentMetadata** includes both **audioMetadata** and **videoMetadata** \(plus **streamingMetadata** for the live stream\), and the **detections** collection contains one entry per modality.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/communications/calls/481f3600-983e-4276-9b59-c1b30ec8d125/participants/550fae72-d251-43ec-868c-373732c2704f/reportSyntheticMedia
Content-Type: application/json

{
  "id": "b2c3d4e5-f6a7-8901-bcde-f23456789012",
  "detectionDateTime": "2026-03-13T21:10:00Z",
  "severity": "high",
  "overallConfidence": 0.94,
  "isMalicious": true,
  "contentMetadata": {
    "modality": "multimodal",
    "isRealTime": true,
    "mimeType": "video/mp4",
    "byteSize": 0,
    "duration": 20,
    "audioMetadata": {
      "sampleRateHz": 16000,
      "bitDepth": 16,
      "channels": 1
    },
    "videoMetadata": {
      "codec": "H.264",
      "frameRate": 30.0,
      "bitrateKbps": 512
    },
    "streamingMetadata": {
      "latencyMs": 50,
      "frameDropRate": 0.0,
      "networkJitterMs": 10
    }
  },
  "detections": [
    {
      "modelName": "VoiceCloneDetector-v1",
      "modality": "audio",
      "modelTasks": ["voiceClone"],
      "segment": {
        "startTimeSec": 0,
        "endTimeSec": 20,
        "frameIndices": []
      },
      "confidence": 0.93
    },
    {
      "modelName": "FaceSwapDetector-v3",
      "modality": "video",
      "modelTasks": ["faceSwap", "lipSync"],
      "segment": {
        "startTimeSec": 5,
        "endTimeSec": 18,
        "frameIndices": [150, 180, 210, 240]
      },
      "confidence": 0.95
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Communications.Calls.Item.Participants.Item.ReportSyntheticMedia;
using Microsoft.Graph.Beta.Models;

var requestBody = new ReportSyntheticMediaPostRequestBody
{
	Id = Guid.Parse("b2c3d4e5-f6a7-8901-bcde-f23456789012"),
	DetectionDateTime = DateTimeOffset.Parse("2026-03-13T21:10:00Z"),
	Severity = DetectionSeverity.High,
	OverallConfidence = 0.94d,
	IsMalicious = true,
	ContentMetadata = new MediaMetadata
	{
		Modality = ContentModality.Multimodal,
		IsRealTime = true,
		MimeType = "video/mp4",
		ByteSize = 0L,
		Duration = 20,
		AudioMetadata = new AudioMetadata
		{
			SampleRateHz = 16000,
			BitDepth = 16,
			Channels = 1,
		},
		VideoMetadata = new VideoMetadata
		{
			Codec = "H.264",
			FrameRate = 30d,
			BitrateKbps = 512,
		},
		StreamingMetadata = new StreamingMetadata
		{
			LatencyMs = 50,
			FrameDropRate = 0d,
			NetworkJitterMs = 10,
		},
	},
	Detections = new List<SyntheticMediaDetectionDetail>
	{
		new SyntheticMediaDetectionDetail
		{
			ModelName = "VoiceCloneDetector-v1",
			Modality = ContentModality.Audio,
			ModelTasks = new List<string>
			{
				"voiceClone",
			},
			Segment = new MediaSegment
			{
				StartTimeSec = 0,
				EndTimeSec = 20,
				FrameIndices = new List<Number>
				{
				},
			},
			Confidence = 0.93d,
		},
		new SyntheticMediaDetectionDetail
		{
			ModelName = "FaceSwapDetector-v3",
			Modality = ContentModality.Video,
			ModelTasks = new List<string>
			{
				"faceSwap",
				"lipSync",
			},
			Segment = new MediaSegment
			{
				StartTimeSec = 5,
				EndTimeSec = 18,
				FrameIndices = new List<Number>
				{
					150,
					180,
					210,
					240,
				},
			},
			Confidence = 0.95d,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Communications.Calls["{call-id}"].Participants["{participant-id}"].ReportSyntheticMedia.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  "github.com/google/uuid"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphcommunications "github.com/microsoftgraph/msgraph-beta-sdk-go/communications"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphcommunications.NewReportSyntheticMediaPostRequestBody()
id := uuid.MustParse("b2c3d4e5-f6a7-8901-bcde-f23456789012")
requestBody.SetId(&id) 
detectionDateTime , err := time.Parse(time.RFC3339, "2026-03-13T21:10:00Z")
requestBody.SetDetectionDateTime(&detectionDateTime) 
severity := graphmodels.HIGH_DETECTIONSEVERITY 
requestBody.SetSeverity(&severity) 
overallConfidence := float64(0.94)
requestBody.SetOverallConfidence(&overallConfidence) 
isMalicious := true
requestBody.SetIsMalicious(&isMalicious) 
contentMetadata := graphmodels.NewMediaMetadata()
modality := graphmodels.MULTIMODAL_CONTENTMODALITY 
contentMetadata.SetModality(&modality) 
isRealTime := true
contentMetadata.SetIsRealTime(&isRealTime) 
mimeType := "video/mp4"
contentMetadata.SetMimeType(&mimeType) 
byteSize := int64(0)
contentMetadata.SetByteSize(&byteSize) 
duration := int32(20)
contentMetadata.SetDuration(&duration) 
audioMetadata := graphmodels.NewAudioMetadata()
sampleRateHz := int32(16000)
audioMetadata.SetSampleRateHz(&sampleRateHz) 
bitDepth := int32(16)
audioMetadata.SetBitDepth(&bitDepth) 
channels := int32(1)
audioMetadata.SetChannels(&channels) 
contentMetadata.SetAudioMetadata(audioMetadata)
videoMetadata := graphmodels.NewVideoMetadata()
codec := "H.264"
videoMetadata.SetCodec(&codec) 
frameRate := float64(30)
videoMetadata.SetFrameRate(&frameRate) 
bitrateKbps := int32(512)
videoMetadata.SetBitrateKbps(&bitrateKbps) 
contentMetadata.SetVideoMetadata(videoMetadata)
streamingMetadata := graphmodels.NewStreamingMetadata()
latencyMs := int32(50)
streamingMetadata.SetLatencyMs(&latencyMs) 
frameDropRate := float64(0)
streamingMetadata.SetFrameDropRate(&frameDropRate) 
networkJitterMs := int32(10)
streamingMetadata.SetNetworkJitterMs(&networkJitterMs) 
contentMetadata.SetStreamingMetadata(streamingMetadata)
requestBody.SetContentMetadata(contentMetadata)


syntheticMediaDetectionDetail := graphmodels.NewSyntheticMediaDetectionDetail()
modelName := "VoiceCloneDetector-v1"
syntheticMediaDetectionDetail.SetModelName(&modelName) 
modality := graphmodels.AUDIO_CONTENTMODALITY 
syntheticMediaDetectionDetail.SetModality(&modality) 
modelTasks := []string {
	"voiceClone",
}
syntheticMediaDetectionDetail.SetModelTasks(modelTasks)
segment := graphmodels.NewMediaSegment()
startTimeSec := int32(0)
segment.SetStartTimeSec(&startTimeSec) 
endTimeSec := int32(20)
segment.SetEndTimeSec(&endTimeSec) 
frameIndices := []graph.numberable {

}
segment.SetFrameIndices(frameIndices)
syntheticMediaDetectionDetail.SetSegment(segment)
confidence := float64(0.93)
syntheticMediaDetectionDetail.SetConfidence(&confidence) 
syntheticMediaDetectionDetail1 := graphmodels.NewSyntheticMediaDetectionDetail()
modelName := "FaceSwapDetector-v3"
syntheticMediaDetectionDetail1.SetModelName(&modelName) 
modality := graphmodels.VIDEO_CONTENTMODALITY 
syntheticMediaDetectionDetail1.SetModality(&modality) 
modelTasks := []string {
	"faceSwap",
	"lipSync",
}
syntheticMediaDetectionDetail1.SetModelTasks(modelTasks)
segment := graphmodels.NewMediaSegment()
startTimeSec := int32(5)
segment.SetStartTimeSec(&startTimeSec) 
endTimeSec := int32(18)
segment.SetEndTimeSec(&endTimeSec) 
frameIndices := []graph.Numberable {
 := int32(150)
segment.Set(&) 
 := int32(180)
segment.Set(&) 
 := int32(210)
segment.Set(&) 
 := int32(240)
segment.Set(&)
}
segment.SetFrameIndices(frameIndices)
syntheticMediaDetectionDetail1.SetSegment(segment)
confidence := float64(0.95)
syntheticMediaDetectionDetail1.SetConfidence(&confidence) 

detections := []graphmodels.SyntheticMediaDetectionDetailable {
	syntheticMediaDetectionDetail,
	syntheticMediaDetectionDetail1,
}
requestBody.SetDetections(detections)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Communications().Calls().ByCallId("call-id").Participants().ByParticipantId("participant-id").ReportSyntheticMedia().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.communications.calls.item.participants.item.reportsyntheticmedia.ReportSyntheticMediaPostRequestBody reportSyntheticMediaPostRequestBody = new com.microsoft.graph.beta.communications.calls.item.participants.item.reportsyntheticmedia.ReportSyntheticMediaPostRequestBody();
reportSyntheticMediaPostRequestBody.setId(UUID.fromString("b2c3d4e5-f6a7-8901-bcde-f23456789012"));
OffsetDateTime detectionDateTime = OffsetDateTime.parse("2026-03-13T21:10:00Z");
reportSyntheticMediaPostRequestBody.setDetectionDateTime(detectionDateTime);
reportSyntheticMediaPostRequestBody.setSeverity(DetectionSeverity.High);
reportSyntheticMediaPostRequestBody.setOverallConfidence(0.94d);
reportSyntheticMediaPostRequestBody.setIsMalicious(true);
MediaMetadata contentMetadata = new MediaMetadata();
contentMetadata.setModality(ContentModality.Multimodal);
contentMetadata.setIsRealTime(true);
contentMetadata.setMimeType("video/mp4");
contentMetadata.setByteSize(0L);
contentMetadata.setDuration(20);
AudioMetadata audioMetadata = new AudioMetadata();
audioMetadata.setSampleRateHz(16000);
audioMetadata.setBitDepth(16);
audioMetadata.setChannels(1);
contentMetadata.setAudioMetadata(audioMetadata);
VideoMetadata videoMetadata = new VideoMetadata();
videoMetadata.setCodec("H.264");
videoMetadata.setFrameRate(30d);
videoMetadata.setBitrateKbps(512);
contentMetadata.setVideoMetadata(videoMetadata);
StreamingMetadata streamingMetadata = new StreamingMetadata();
streamingMetadata.setLatencyMs(50);
streamingMetadata.setFrameDropRate(0d);
streamingMetadata.setNetworkJitterMs(10);
contentMetadata.setStreamingMetadata(streamingMetadata);
reportSyntheticMediaPostRequestBody.setContentMetadata(contentMetadata);
LinkedList<SyntheticMediaDetectionDetail> detections = new LinkedList<SyntheticMediaDetectionDetail>();
SyntheticMediaDetectionDetail syntheticMediaDetectionDetail = new SyntheticMediaDetectionDetail();
syntheticMediaDetectionDetail.setModelName("VoiceCloneDetector-v1");
syntheticMediaDetectionDetail.setModality(ContentModality.Audio);
LinkedList<String> modelTasks = new LinkedList<String>();
modelTasks.add("voiceClone");
syntheticMediaDetectionDetail.setModelTasks(modelTasks);
MediaSegment segment = new MediaSegment();
segment.setStartTimeSec(0);
segment.setEndTimeSec(20);
LinkedList<Number> frameIndices = new LinkedList<Number>();
segment.setFrameIndices(frameIndices);
syntheticMediaDetectionDetail.setSegment(segment);
syntheticMediaDetectionDetail.setConfidence(0.93d);
detections.add(syntheticMediaDetectionDetail);
SyntheticMediaDetectionDetail syntheticMediaDetectionDetail1 = new SyntheticMediaDetectionDetail();
syntheticMediaDetectionDetail1.setModelName("FaceSwapDetector-v3");
syntheticMediaDetectionDetail1.setModality(ContentModality.Video);
LinkedList<String> modelTasks1 = new LinkedList<String>();
modelTasks1.add("faceSwap");
modelTasks1.add("lipSync");
syntheticMediaDetectionDetail1.setModelTasks(modelTasks1);
MediaSegment segment1 = new MediaSegment();
segment1.setStartTimeSec(5);
segment1.setEndTimeSec(18);
LinkedList<Number> frameIndices1 = new LinkedList<Number>();
frameIndices1.add(150);
frameIndices1.add(180);
frameIndices1.add(210);
frameIndices1.add(240);
segment1.setFrameIndices(frameIndices1);
syntheticMediaDetectionDetail1.setSegment(segment1);
syntheticMediaDetectionDetail1.setConfidence(0.95d);
detections.add(syntheticMediaDetectionDetail1);
reportSyntheticMediaPostRequestBody.setDetections(detections);
graphClient.communications().calls().byCallId("{call-id}").participants().byParticipantId("{participant-id}").reportSyntheticMedia().post(reportSyntheticMediaPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const reportSyntheticMedia = {
  id: 'b2c3d4e5-f6a7-8901-bcde-f23456789012',
  detectionDateTime: '2026-03-13T21:10:00Z',
  severity: 'high',
  overallConfidence: 0.94,
  isMalicious: true,
  contentMetadata: {
    modality: 'multimodal',
    isRealTime: true,
    mimeType: 'video/mp4',
    byteSize: 0,
    duration: 20,
    audioMetadata: {
      sampleRateHz: 16000,
      bitDepth: 16,
      channels: 1
    },
    videoMetadata: {
      codec: 'H.264',
      frameRate: 30.0,
      bitrateKbps: 512
    },
    streamingMetadata: {
      latencyMs: 50,
      frameDropRate: 0.0,
      networkJitterMs: 10
    }
  },
  detections: [
    {
      modelName: 'VoiceCloneDetector-v1',
      modality: 'audio',
      modelTasks: ['voiceClone'],
      segment: {
        startTimeSec: 0,
        endTimeSec: 20,
        frameIndices: []
      },
      confidence: 0.93
    },
    {
      modelName: 'FaceSwapDetector-v3',
      modality: 'video',
      modelTasks: ['faceSwap', 'lipSync'],
      segment: {
        startTimeSec: 5,
        endTimeSec: 18,
        frameIndices: [150, 180, 210, 240]
      },
      confidence: 0.95
    }
  ]
};

await client.api('/communications/calls/481f3600-983e-4276-9b59-c1b30ec8d125/participants/550fae72-d251-43ec-868c-373732c2704f/reportSyntheticMedia')
	.version('beta')
	.post(reportSyntheticMedia);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Communications\Calls\Item\Participants\Item\ReportSyntheticMedia\ReportSyntheticMediaPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\DetectionSeverity;
use Microsoft\Graph\Beta\Generated\Models\MediaMetadata;
use Microsoft\Graph\Beta\Generated\Models\ContentModality;
use Microsoft\Graph\Beta\Generated\Models\AudioMetadata;
use Microsoft\Graph\Beta\Generated\Models\VideoMetadata;
use Microsoft\Graph\Beta\Generated\Models\StreamingMetadata;
use Microsoft\Graph\Beta\Generated\Models\SyntheticMediaDetectionDetail;
use Microsoft\Graph\Beta\Generated\Models\MediaSegment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReportSyntheticMediaPostRequestBody();
$requestBody->setId('b2c3d4e5-f6a7-8901-bcde-f23456789012');
$requestBody->setDetectionDateTime(new \DateTime('2026-03-13T21:10:00Z'));
$requestBody->setSeverity(new DetectionSeverity('high'));
$requestBody->setOverallConfidence(0.94);
$requestBody->setIsMalicious(true);
$contentMetadata = new MediaMetadata();
$contentMetadata->setModality(new ContentModality('multimodal'));
$contentMetadata->setIsRealTime(true);
$contentMetadata->setMimeType('video/mp4');
$contentMetadata->setByteSize(0);
$contentMetadata->setDuration(20);
$contentMetadataAudioMetadata = new AudioMetadata();
$contentMetadataAudioMetadata->setSampleRateHz(16000);
$contentMetadataAudioMetadata->setBitDepth(16);
$contentMetadataAudioMetadata->setChannels(1);
$contentMetadata->setAudioMetadata($contentMetadataAudioMetadata);
$contentMetadataVideoMetadata = new VideoMetadata();
$contentMetadataVideoMetadata->setCodec('H.264');
$contentMetadataVideoMetadata->setFrameRate(30);
$contentMetadataVideoMetadata->setBitrateKbps(512);
$contentMetadata->setVideoMetadata($contentMetadataVideoMetadata);
$contentMetadataStreamingMetadata = new StreamingMetadata();
$contentMetadataStreamingMetadata->setLatencyMs(50);
$contentMetadataStreamingMetadata->setFrameDropRate(0);
$contentMetadataStreamingMetadata->setNetworkJitterMs(10);
$contentMetadata->setStreamingMetadata($contentMetadataStreamingMetadata);
$requestBody->setContentMetadata($contentMetadata);
$detectionsSyntheticMediaDetectionDetail1 = new SyntheticMediaDetectionDetail();
$detectionsSyntheticMediaDetectionDetail1->setModelName('VoiceCloneDetector-v1');
$detectionsSyntheticMediaDetectionDetail1->setModality(new ContentModality('audio'));
$detectionsSyntheticMediaDetectionDetail1->setModelTasks(['voiceClone', 	]);
$detectionsSyntheticMediaDetectionDetail1Segment = new MediaSegment();
$detectionsSyntheticMediaDetectionDetail1Segment->setStartTimeSec(0);
$detectionsSyntheticMediaDetectionDetail1Segment->setEndTimeSec(20);
$detectionsSyntheticMediaDetectionDetail1Segment->setFrameIndices([	]);
$detectionsSyntheticMediaDetectionDetail1->setSegment($detectionsSyntheticMediaDetectionDetail1Segment);
$detectionsSyntheticMediaDetectionDetail1->setConfidence(0.93);
$detectionsArray []= $detectionsSyntheticMediaDetectionDetail1;
$detectionsSyntheticMediaDetectionDetail2 = new SyntheticMediaDetectionDetail();
$detectionsSyntheticMediaDetectionDetail2->setModelName('FaceSwapDetector-v3');
$detectionsSyntheticMediaDetectionDetail2->setModality(new ContentModality('video'));
$detectionsSyntheticMediaDetectionDetail2->setModelTasks(['faceSwap', 'lipSync', 	]);
$detectionsSyntheticMediaDetectionDetail2Segment = new MediaSegment();
$detectionsSyntheticMediaDetectionDetail2Segment->setStartTimeSec(5);
$detectionsSyntheticMediaDetectionDetail2Segment->setEndTimeSec(18);
$detectionsSyntheticMediaDetectionDetail2Segment->setFrameIndices([150,180,210,240,	]);
$detectionsSyntheticMediaDetectionDetail2->setSegment($detectionsSyntheticMediaDetectionDetail2Segment);
$detectionsSyntheticMediaDetectionDetail2->setConfidence(0.95);
$detectionsArray []= $detectionsSyntheticMediaDetectionDetail2;
$requestBody->setDetections($detectionsArray);


$graphServiceClient->communications()->calls()->byCallId('call-id')->participants()->byParticipantId('participant-id')->reportSyntheticMedia()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.communications.calls.item.participants.item.report_synthetic_media.report_synthetic_media_post_request_body import ReportSyntheticMediaPostRequestBody
from msgraph_beta.generated.models.detection_severity import DetectionSeverity
from msgraph_beta.generated.models.media_metadata import MediaMetadata
from msgraph_beta.generated.models.content_modality import ContentModality
from msgraph_beta.generated.models.audio_metadata import AudioMetadata
from msgraph_beta.generated.models.video_metadata import VideoMetadata
from msgraph_beta.generated.models.streaming_metadata import StreamingMetadata
from msgraph_beta.generated.models.synthetic_media_detection_detail import SyntheticMediaDetectionDetail
from msgraph_beta.generated.models.media_segment import MediaSegment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReportSyntheticMediaPostRequestBody(
	id = UUID("b2c3d4e5-f6a7-8901-bcde-f23456789012"),
	detection_date_time = "2026-03-13T21:10:00Z",
	severity = DetectionSeverity.High,
	overall_confidence = 0.94,
	is_malicious = True,
	content_metadata = MediaMetadata(
		modality = ContentModality.Multimodal,
		is_real_time = True,
		mime_type = "video/mp4",
		byte_size = 0,
		duration = 20,
		audio_metadata = AudioMetadata(
			sample_rate_hz = 16000,
			bit_depth = 16,
			channels = 1,
		),
		video_metadata = VideoMetadata(
			codec = "H.264",
			frame_rate = 30,
			bitrate_kbps = 512,
		),
		streaming_metadata = StreamingMetadata(
			latency_ms = 50,
			frame_drop_rate = 0,
			network_jitter_ms = 10,
		),
	),
	detections = [
		SyntheticMediaDetectionDetail(
			model_name = "VoiceCloneDetector-v1",
			modality = ContentModality.Audio,
			model_tasks = [
				"voiceClone",
			],
			segment = MediaSegment(
				start_time_sec = 0,
				end_time_sec = 20,
				frame_indices = [
				],
			),
			confidence = 0.93,
		),
		SyntheticMediaDetectionDetail(
			model_name = "FaceSwapDetector-v3",
			modality = ContentModality.Video,
			model_tasks = [
				"faceSwap",
				"lipSync",
			],
			segment = MediaSegment(
				start_time_sec = 5,
				end_time_sec = 18,
				frame_indices = [
					150,
					180,
					210,
					240,
				],
			),
			confidence = 0.95,
		),
	],
)

await graph_client.communications.calls.by_call_id('call-id').participants.by_participant_id('participant-id').report_synthetic_media.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```
