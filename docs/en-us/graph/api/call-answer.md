<!-- Source: https://learn.microsoft.com/en-us/graph/api/call-answer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-27 -->

# call: answer

Namespace: microsoft.graph

Enable a bot to answer an incoming [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0). The incoming call request can be an invitation from a participant in a group call or a peer-to-peer call. If an invitation to a group call is received, the notification contains the [chatInfo](https://learn.microsoft.com/en-us/graph/api/resources/chatinfo?view=graph-rest-1.0) and [meetingInfo](https://learn.microsoft.com/en-us/graph/api/resources/meetinginfo?view=graph-rest-1.0) parameters.

The bot is expected to answer, [reject](https://learn.microsoft.com/en-us/graph/api/call-reject?view=graph-rest-1.0), or [redirect](https://learn.microsoft.com/en-us/graph/api/call-redirect?view=graph-rest-1.0) the call before the call times out. The current timeout value is 15 seconds for regular scenarios and 5 seconds for policy-based recording scenarios.

This API supports the following PSTN scenarios:

- Incoming call to bot's PSTN number and then bot invites another PSTN.
- Incoming call to bot's PSTN number and then bot transfer to another PSTN.
- Incoming call to bot's PSTN number and then bot redirects to another PSTN.
- Incoming call to bot's instance identifier and then bot invites another PSTN.
- Incoming call to bot's instance identifier and then bot transfer to another PSTN.
- Incoming call to bot's instance identifier and then bot redirects to another PSTN.
- Incoming call to bot's instance identifier from Scheduled Meeting and then bot invites PSTN.
- Outgoing call from bot \(with instance identifier\) to a PSTN.
- P2P call between bot and another peer \(Teams user, PSTN\), bot invites another PSTN.
- P2P call between bot and another peer \(Teams user, PSTN\), bot invites another Teams user.
- Bot join the scheduled meeting and then invite PSTN.

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
| Application | Calls.JoinGroupCall.All | Calls.JoinGroupCallAsGuest.All |

> **Note:** For a call that uses application-hosted media, you also need the Calls.AccessMedia.All permission. You must have at least one of the following permissions to ensure that the `source` in the incoming call notification is decrypted: Calls.AccessMedia.All, Calls.Initiate.All, Calls.InitiateGroupCall.All, Calls.JoinGroupCall.All, Calls.JoinGroupCallAsGuest.All. The `source` is the caller info in the incoming call notification. Without at least one of these permissions, the `source` will remain encrypted.

## HTTP request

```http
POST /communications/calls/{id}/answer
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| callbackUri | String | Allows bots to provide a specific callback URI for the concurrent call to receive later notifications. If this property isn't set, the bot's global callback URI is used instead. I must be `https`. |
| acceptedModalities | String collection | The list of accepted modalities. The possible values are: `audio`, `video`, `videoBasedScreenSharing`. Required for answering a call. |
| callOptions | [incomingCallOptions](https://learn.microsoft.com/en-us/graph/api/resources/incomingcalloptions?view=graph-rest-1.0) | The call options. |
| mediaConfig | [appHostedMediaConfig](https://learn.microsoft.com/en-us/graph/api/resources/apphostedmediaconfig?view=graph-rest-1.0) or [serviceHostedMediaConfig](https://learn.microsoft.com/en-us/graph/api/resources/servicehostedmediaconfig?view=graph-rest-1.0) | The media configuration. Required. |
| participantCapacity | Int32 | The number of participants that the application can handle for the call, for [Teams policy-based recording](https://learn.microsoft.com/en-us/microsoftteams/teams-recording-policy) scenario. |

## Response

This method returns a `202 Accepted` response code.

## Examples

The following example shows how to call this API.

#### Request

The following example shows the request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls/{id}/answer
Content-Type: application/json
Content-Length: 211

{
  "callbackUri": "callbackUri-value",
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.appHostedMediaConfig",
    "blob": "<Media Session Configuration Blob>"
  },
  "acceptedModalities": [
    "audio"
  ],
  "callOptions": {
    "@odata.type": "#microsoft.graph.incomingCallOptions",
    "isContentSharingNotificationEnabled": true,
    "isDeltaRosterEnabled": true,
    "isInteractiveRosterEnabled": true
  },
  "participantCapacity": 200
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Communications.Calls.Item.Answer;
using Microsoft.Graph.Models;

var requestBody = new AnswerPostRequestBody
{
	CallbackUri = "callbackUri-value",
	MediaConfig = new AppHostedMediaConfig
	{
		OdataType = "#microsoft.graph.appHostedMediaConfig",
		Blob = "<Media Session Configuration Blob>",
	},
	AcceptedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	CallOptions = new IncomingCallOptions
	{
		OdataType = "#microsoft.graph.incomingCallOptions",
		IsContentSharingNotificationEnabled = true,
		IsDeltaRosterEnabled = true,
		IsInteractiveRosterEnabled = true,
	},
	ParticipantCapacity = 200,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Communications.Calls["{call-id}"].Answer.PostAsync(requestBody);
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

requestBody := graphcommunications.NewAnswerPostRequestBody()
callbackUri := "callbackUri-value"
requestBody.SetCallbackUri(&callbackUri) 
mediaConfig := graphmodels.NewAppHostedMediaConfig()
blob := "<Media Session Configuration Blob>"
mediaConfig.SetBlob(&blob) 
requestBody.SetMediaConfig(mediaConfig)
acceptedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetAcceptedModalities(acceptedModalities)
callOptions := graphmodels.NewIncomingCallOptions()
isContentSharingNotificationEnabled := true
callOptions.SetIsContentSharingNotificationEnabled(&isContentSharingNotificationEnabled) 
isDeltaRosterEnabled := true
callOptions.SetIsDeltaRosterEnabled(&isDeltaRosterEnabled) 
isInteractiveRosterEnabled := true
callOptions.SetIsInteractiveRosterEnabled(&isInteractiveRosterEnabled) 
requestBody.SetCallOptions(callOptions)
participantCapacity := int32(200)
requestBody.SetParticipantCapacity(&participantCapacity) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Communications().Calls().ByCallId("call-id").Answer().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.communications.calls.item.answer.AnswerPostRequestBody answerPostRequestBody = new com.microsoft.graph.communications.calls.item.answer.AnswerPostRequestBody();
answerPostRequestBody.setCallbackUri("callbackUri-value");
AppHostedMediaConfig mediaConfig = new AppHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.appHostedMediaConfig");
mediaConfig.setBlob("<Media Session Configuration Blob>");
answerPostRequestBody.setMediaConfig(mediaConfig);
LinkedList<Modality> acceptedModalities = new LinkedList<Modality>();
acceptedModalities.add(Modality.Audio);
answerPostRequestBody.setAcceptedModalities(acceptedModalities);
IncomingCallOptions callOptions = new IncomingCallOptions();
callOptions.setOdataType("#microsoft.graph.incomingCallOptions");
callOptions.setIsContentSharingNotificationEnabled(true);
callOptions.setIsDeltaRosterEnabled(true);
callOptions.setIsInteractiveRosterEnabled(true);
answerPostRequestBody.setCallOptions(callOptions);
answerPostRequestBody.setParticipantCapacity(200);
graphClient.communications().calls().byCallId("{call-id}").answer().post(answerPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const answer = {
  callbackUri: 'callbackUri-value',
  mediaConfig: {
    '@odata.type': '#microsoft.graph.appHostedMediaConfig',
    blob: '<Media Session Configuration Blob>'
  },
  acceptedModalities: [
    'audio'
  ],
  callOptions: {
    '@odata.type': '#microsoft.graph.incomingCallOptions',
    isContentSharingNotificationEnabled: true,
    isDeltaRosterEnabled: true,
    isInteractiveRosterEnabled: true
  },
  participantCapacity: 200
};

await client.api('/communications/calls/{id}/answer')
	.post(answer);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\Calls\Item\Answer\AnswerPostRequestBody;
use Microsoft\Graph\Generated\Models\AppHostedMediaConfig;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\IncomingCallOptions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AnswerPostRequestBody();
$requestBody->setCallbackUri('callbackUri-value');
$mediaConfig = new AppHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.appHostedMediaConfig');
$mediaConfig->setBlob('<Media Session Configuration Blob>');
$requestBody->setMediaConfig($mediaConfig);
$requestBody->setAcceptedModalities([new Modality('audio'),	]);
$callOptions = new IncomingCallOptions();
$callOptions->setOdataType('#microsoft.graph.incomingCallOptions');
$callOptions->setIsContentSharingNotificationEnabled(true);
$callOptions->setIsDeltaRosterEnabled(true);
$callOptions->setIsInteractiveRosterEnabled(true);
$requestBody->setCallOptions($callOptions);
$requestBody->setParticipantCapacity(200);

$graphServiceClient->communications()->calls()->byCallId('call-id')->answer()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	callbackUri = "callbackUri-value"
	mediaConfig = @{
		"@odata.type" = "#microsoft.graph.appHostedMediaConfig"
		blob = "<Media Session Configuration Blob>"
	}
	acceptedModalities = @(
	"audio"
)
callOptions = @{
	"@odata.type" = "#microsoft.graph.incomingCallOptions"
	isContentSharingNotificationEnabled = $true
	isDeltaRosterEnabled = $true
	isInteractiveRosterEnabled = $true
}
participantCapacity = 200
}

Invoke-MgAnswerCommunicationCall -CallId $callId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.calls.item.answer.answer_post_request_body import AnswerPostRequestBody
from msgraph.generated.models.app_hosted_media_config import AppHostedMediaConfig
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.incoming_call_options import IncomingCallOptions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AnswerPostRequestBody(
	callback_uri = "callbackUri-value",
	media_config = AppHostedMediaConfig(
		odata_type = "#microsoft.graph.appHostedMediaConfig",
		blob = "<Media Session Configuration Blob>",
	),
	accepted_modalities = [
		Modality.Audio,
	],
	call_options = IncomingCallOptions(
		odata_type = "#microsoft.graph.incomingCallOptions",
		is_content_sharing_notification_enabled = True,
		is_delta_roster_enabled = True,
		is_interactive_roster_enabled = True,
	),
	participant_capacity = 200,
)

await graph_client.communications.calls.by_call_id('call-id').answer.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```

### Example 1: Answer a Peer-to-Peer VoIP call with service hosted media

#### Notification - incoming

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "created",
      "resourceUrl": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "@odata.id": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
        "@odata.etag": "W/\"5445\"",
        "state": "incoming",
        "direction": "incoming",
        "source": {
          "identity": {
            "user": {
              "displayName": "Test User",
              "id": "8A34A46B-3D17-4ADC-8DCE-DC4E7D572698"
            }
          },
          "region": "westus",
          "languageId": "en-US"
        },
        "targets": [
          {
            "identity": {
              "application": {
                "displayName": "Test BOT",
                "id": "8A34A46B-3D17-4ADC-8DCE-DC4E7D572698"
              }
            }
          }
        ],
        "requestedModalities": [ "audio" ]
      }
    }
  ]
}
```

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls/57DAB8B1894C409AB240BD8BEAE78896/answer
Content-Type: application/json

{
  "callbackUri": "https://bot.contoso.com/api/calls",
  "acceptedModalities": [ "audio" ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.serviceHostedMediaConfig",
    "preFetchMedia": [
      {
        "uri": "https://cdn.contoso.com/beep.wav",
        "resourceId": "1D6DE2D4-CD51-4309-8DAA-70768651088E"
      },
      {
        "uri": "https://cdn.contoso.com/cool.wav",
        "resourceId": "1D6DE2D4-CD51-4309-8DAA-70768651088F"
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Communications.Calls.Item.Answer;
using Microsoft.Graph.Models;

var requestBody = new AnswerPostRequestBody
{
	CallbackUri = "https://bot.contoso.com/api/calls",
	AcceptedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	MediaConfig = new ServiceHostedMediaConfig
	{
		OdataType = "#microsoft.graph.serviceHostedMediaConfig",
		PreFetchMedia = new List<MediaInfo>
		{
			new MediaInfo
			{
				Uri = "https://cdn.contoso.com/beep.wav",
				ResourceId = "1D6DE2D4-CD51-4309-8DAA-70768651088E",
			},
			new MediaInfo
			{
				Uri = "https://cdn.contoso.com/cool.wav",
				ResourceId = "1D6DE2D4-CD51-4309-8DAA-70768651088F",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Communications.Calls["{call-id}"].Answer.PostAsync(requestBody);
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

requestBody := graphcommunications.NewAnswerPostRequestBody()
callbackUri := "https://bot.contoso.com/api/calls"
requestBody.SetCallbackUri(&callbackUri) 
acceptedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetAcceptedModalities(acceptedModalities)
mediaConfig := graphmodels.NewServiceHostedMediaConfig()


mediaInfo := graphmodels.NewMediaInfo()
uri := "https://cdn.contoso.com/beep.wav"
mediaInfo.SetUri(&uri) 
resourceId := "1D6DE2D4-CD51-4309-8DAA-70768651088E"
mediaInfo.SetResourceId(&resourceId) 
mediaInfo1 := graphmodels.NewMediaInfo()
uri := "https://cdn.contoso.com/cool.wav"
mediaInfo1.SetUri(&uri) 
resourceId := "1D6DE2D4-CD51-4309-8DAA-70768651088F"
mediaInfo1.SetResourceId(&resourceId) 

preFetchMedia := []graphmodels.MediaInfoable {
	mediaInfo,
	mediaInfo1,
}
mediaConfig.SetPreFetchMedia(preFetchMedia)
requestBody.SetMediaConfig(mediaConfig)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Communications().Calls().ByCallId("call-id").Answer().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.communications.calls.item.answer.AnswerPostRequestBody answerPostRequestBody = new com.microsoft.graph.communications.calls.item.answer.AnswerPostRequestBody();
answerPostRequestBody.setCallbackUri("https://bot.contoso.com/api/calls");
LinkedList<Modality> acceptedModalities = new LinkedList<Modality>();
acceptedModalities.add(Modality.Audio);
answerPostRequestBody.setAcceptedModalities(acceptedModalities);
ServiceHostedMediaConfig mediaConfig = new ServiceHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.serviceHostedMediaConfig");
LinkedList<MediaInfo> preFetchMedia = new LinkedList<MediaInfo>();
MediaInfo mediaInfo = new MediaInfo();
mediaInfo.setUri("https://cdn.contoso.com/beep.wav");
mediaInfo.setResourceId("1D6DE2D4-CD51-4309-8DAA-70768651088E");
preFetchMedia.add(mediaInfo);
MediaInfo mediaInfo1 = new MediaInfo();
mediaInfo1.setUri("https://cdn.contoso.com/cool.wav");
mediaInfo1.setResourceId("1D6DE2D4-CD51-4309-8DAA-70768651088F");
preFetchMedia.add(mediaInfo1);
mediaConfig.setPreFetchMedia(preFetchMedia);
answerPostRequestBody.setMediaConfig(mediaConfig);
graphClient.communications().calls().byCallId("{call-id}").answer().post(answerPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const answer = {
  callbackUri: 'https://bot.contoso.com/api/calls',
  acceptedModalities: [ 'audio' ],
  mediaConfig: {
    '@odata.type': '#microsoft.graph.serviceHostedMediaConfig',
    preFetchMedia: [
      {
        uri: 'https://cdn.contoso.com/beep.wav',
        resourceId: '1D6DE2D4-CD51-4309-8DAA-70768651088E'
      },
      {
        uri: 'https://cdn.contoso.com/cool.wav',
        resourceId: '1D6DE2D4-CD51-4309-8DAA-70768651088F'
      }
    ]
  }
};

await client.api('/communications/calls/57DAB8B1894C409AB240BD8BEAE78896/answer')
	.post(answer);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\Calls\Item\Answer\AnswerPostRequestBody;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\ServiceHostedMediaConfig;
use Microsoft\Graph\Generated\Models\MediaInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AnswerPostRequestBody();
$requestBody->setCallbackUri('https://bot.contoso.com/api/calls');
$requestBody->setAcceptedModalities([new Modality('audio'),	]);
$mediaConfig = new ServiceHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.serviceHostedMediaConfig');
$preFetchMediaMediaInfo1 = new MediaInfo();
$preFetchMediaMediaInfo1->setUri('https://cdn.contoso.com/beep.wav');
$preFetchMediaMediaInfo1->setResourceId('1D6DE2D4-CD51-4309-8DAA-70768651088E');
$preFetchMediaArray []= $preFetchMediaMediaInfo1;
$preFetchMediaMediaInfo2 = new MediaInfo();
$preFetchMediaMediaInfo2->setUri('https://cdn.contoso.com/cool.wav');
$preFetchMediaMediaInfo2->setResourceId('1D6DE2D4-CD51-4309-8DAA-70768651088F');
$preFetchMediaArray []= $preFetchMediaMediaInfo2;
$mediaConfig->setPreFetchMedia($preFetchMediaArray);

$requestBody->setMediaConfig($mediaConfig);

$graphServiceClient->communications()->calls()->byCallId('call-id')->answer()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	callbackUri = "https://bot.contoso.com/api/calls"
	acceptedModalities = @(
	"audio"
)
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.serviceHostedMediaConfig"
	preFetchMedia = @(
		@{
			uri = "https://cdn.contoso.com/beep.wav"
			resourceId = "1D6DE2D4-CD51-4309-8DAA-70768651088E"
		}
		@{
			uri = "https://cdn.contoso.com/cool.wav"
			resourceId = "1D6DE2D4-CD51-4309-8DAA-70768651088F"
		}
	)
}
}

Invoke-MgAnswerCommunicationCall -CallId $callId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.calls.item.answer.answer_post_request_body import AnswerPostRequestBody
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.service_hosted_media_config import ServiceHostedMediaConfig
from msgraph.generated.models.media_info import MediaInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AnswerPostRequestBody(
	callback_uri = "https://bot.contoso.com/api/calls",
	accepted_modalities = [
		Modality.Audio,
	],
	media_config = ServiceHostedMediaConfig(
		odata_type = "#microsoft.graph.serviceHostedMediaConfig",
		pre_fetch_media = [
			MediaInfo(
				uri = "https://cdn.contoso.com/beep.wav",
				resource_id = "1D6DE2D4-CD51-4309-8DAA-70768651088E",
			),
			MediaInfo(
				uri = "https://cdn.contoso.com/cool.wav",
				resource_id = "1D6DE2D4-CD51-4309-8DAA-70768651088F",
			),
		],
	),
)

await graph_client.communications.calls.by_call_id('call-id').answer.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 202 Accepted
```

#### Notification - establishing

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "updated",
      "resourceUrl": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "@odata.id": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
        "@odata.etag": "W/\"5445\"",
        "state": "establishing"
      }
    }
  ]
}
```

> **Note:** Call establishing/established notifications may arrive out of order.

#### Notification - established

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "updated",
      "resourceUrl": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "@odata.id": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
        "@odata.etag": "W/\"5445\"",
        "state": "established"
      }
    }
  ]
}
```

> **Note:** Call establishing/established notifications may arrive out of order.

### Example 2: Answer VOIP call with application hosted media

#### Notification - incoming

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "created",
      "resourceUrl": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "@odata.id": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
        "@odata.etag": "W/\"5445\"",
        "state": "incoming",
        "direction": "incoming",
        "source": {
          "@odata.type": "#microsoft.graph.participantInfo",
          "identity": {
            "user": {
              "displayName": "Test User",
              "id": "8A34A46B-3D17-4ADC-8DCE-DC4E7D572698"
            }
          },
          "region": "westus",
          "languageId": "en-US"
        },
        "targets": [
          {
            "@odata.type": "#microsoft.graph.invitationParticipantInfo",
            "identity": {
              "application": {
                "displayName": "Test BOT",
                "id": "8A34A46B-3D17-4ADC-8DCE-DC4E7D572698"
              }
            }
          }
        ],
        "requestedModalities": [ "audio" ]
      }
    }
  ]
}
```

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls/57DAB8B1894C409AB240BD8BEAE78896/answer
Content-Type: application/json

{
  "callbackUri": "https://bot.contoso.com/api/calls",
  "acceptedModalities": [ "audio" ],
  "mediaConfig": {
    "@odata.type": "#microsoft.graph.appHostedMediaConfig",
    "blob": "<Media Session Configuration Blob>"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Communications.Calls.Item.Answer;
using Microsoft.Graph.Models;

var requestBody = new AnswerPostRequestBody
{
	CallbackUri = "https://bot.contoso.com/api/calls",
	AcceptedModalities = new List<Modality?>
	{
		Modality.Audio,
	},
	MediaConfig = new AppHostedMediaConfig
	{
		OdataType = "#microsoft.graph.appHostedMediaConfig",
		Blob = "<Media Session Configuration Blob>",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Communications.Calls["{call-id}"].Answer.PostAsync(requestBody);
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

requestBody := graphcommunications.NewAnswerPostRequestBody()
callbackUri := "https://bot.contoso.com/api/calls"
requestBody.SetCallbackUri(&callbackUri) 
acceptedModalities := []graphmodels.Modalityable {
	modality := graphmodels.AUDIO_MODALITY 
	requestBody.SetModality(&modality)
}
requestBody.SetAcceptedModalities(acceptedModalities)
mediaConfig := graphmodels.NewAppHostedMediaConfig()
blob := "<Media Session Configuration Blob>"
mediaConfig.SetBlob(&blob) 
requestBody.SetMediaConfig(mediaConfig)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Communications().Calls().ByCallId("call-id").Answer().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.communications.calls.item.answer.AnswerPostRequestBody answerPostRequestBody = new com.microsoft.graph.communications.calls.item.answer.AnswerPostRequestBody();
answerPostRequestBody.setCallbackUri("https://bot.contoso.com/api/calls");
LinkedList<Modality> acceptedModalities = new LinkedList<Modality>();
acceptedModalities.add(Modality.Audio);
answerPostRequestBody.setAcceptedModalities(acceptedModalities);
AppHostedMediaConfig mediaConfig = new AppHostedMediaConfig();
mediaConfig.setOdataType("#microsoft.graph.appHostedMediaConfig");
mediaConfig.setBlob("<Media Session Configuration Blob>");
answerPostRequestBody.setMediaConfig(mediaConfig);
graphClient.communications().calls().byCallId("{call-id}").answer().post(answerPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const answer = {
  callbackUri: 'https://bot.contoso.com/api/calls',
  acceptedModalities: [ 'audio' ],
  mediaConfig: {
    '@odata.type': '#microsoft.graph.appHostedMediaConfig',
    blob: '<Media Session Configuration Blob>'
  }
};

await client.api('/communications/calls/57DAB8B1894C409AB240BD8BEAE78896/answer')
	.post(answer);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\Calls\Item\Answer\AnswerPostRequestBody;
use Microsoft\Graph\Generated\Models\Modality;
use Microsoft\Graph\Generated\Models\AppHostedMediaConfig;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AnswerPostRequestBody();
$requestBody->setCallbackUri('https://bot.contoso.com/api/calls');
$requestBody->setAcceptedModalities([new Modality('audio'),	]);
$mediaConfig = new AppHostedMediaConfig();
$mediaConfig->setOdataType('#microsoft.graph.appHostedMediaConfig');
$mediaConfig->setBlob('<Media Session Configuration Blob>');
$requestBody->setMediaConfig($mediaConfig);

$graphServiceClient->communications()->calls()->byCallId('call-id')->answer()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	callbackUri = "https://bot.contoso.com/api/calls"
	acceptedModalities = @(
	"audio"
)
mediaConfig = @{
	"@odata.type" = "#microsoft.graph.appHostedMediaConfig"
	blob = "<Media Session Configuration Blob>"
}
}

Invoke-MgAnswerCommunicationCall -CallId $callId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.calls.item.answer.answer_post_request_body import AnswerPostRequestBody
from msgraph.generated.models.modality import Modality
from msgraph.generated.models.app_hosted_media_config import AppHostedMediaConfig
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AnswerPostRequestBody(
	callback_uri = "https://bot.contoso.com/api/calls",
	accepted_modalities = [
		Modality.Audio,
	],
	media_config = AppHostedMediaConfig(
		odata_type = "#microsoft.graph.appHostedMediaConfig",
		blob = "<Media Session Configuration Blob>",
	),
)

await graph_client.communications.calls.by_call_id('call-id').answer.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 202 Accepted
```

#### Notification - establishing

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "updated",
      "resourceUrl": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "@odata.id": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
        "@odata.etag": "W/\"5445\"",
        "state": "establishing"
      }
    }
  ]
}
```

> **Note:** Call establishing/established notifications may arrive out of order.

#### Notification - established

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "updated",
      "resourceUrl": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "@odata.id": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896",
        "@odata.etag": "W/\"5445\"",
        "state": "established"
      }
    }
  ]
}
```

> **Note:** Call establishing/established notifications may arrive out of order.

#### Notification - content sharing started

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "created",
      "resourceUrl": "/communications/calls/421f4c00-4436-4c3a-9d9a-c4924cf98e67/contentsharingsessions/2765eb15-01f8-47c6-b12b-c32111a4a86f"
    }
  ]
}
```

#### Notification - content sharing ended

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "deleted",
      "resourceUrl": "/communications/calls/421f4c00-4436-4c3a-9d9a-c4924cf98e67/contentsharingsessions/2765eb15-01f8-47c6-b12b-c32111a4a86f"
    }
  ]
}
```

### Example 3: Answer a policy-based recording call

Under the [Policy-based recording scenario](https://learn.microsoft.com/en-us/microsoftteams/teams-recording-policy), before a participant under policy joins a call, an incoming call notification is sent to the bot associated with the policy. The join information can be found under the **botData** property. The bot can then choose to answer the call and [update the recording status](https://learn.microsoft.com/en-us/graph/api/call-updaterecordingstatus?view=graph-rest-1.0) accordingly.

When `participantCapacity` is specified in the `Answer` request for a policy-based recording notification, subsequent participant joining events belonging to the same policy group is sent out as [participantJoiningNotification](https://learn.microsoft.com/en-us/graph/api/resources/participantjoiningnotification?view=graph-rest-1.0) instead of new incoming call notification, until a number of participants that the current call instance is handling has reached the number specified in `participantCapacity`.

The following is an example of the incoming call notification that a bot would receive in this case.

```json
{
   "@odata.type":"#microsoft.graph.commsNotifications",
   "value":[
      {
         "@odata.type":"#microsoft.graph.commsNotification",
         "changeType":"created",
         "resource":"/app/calls/e71f0300-9c1f-4d99-b5f4-2722e877d497",
         "resourceUrl":"/communications/calls/e71f0300-9c1f-4d99-b5f4-2722e877d497",
         "resourceData":{
            "@odata.type":"#microsoft.graph.call",
            "state":"incoming",
            "direction":"incoming",
            "source":{
               "@odata.type":"#microsoft.graph.participantInfo",
               "id":"90fad2ce-8989-41a1-8a66-f6636e629a2a",
               "identity":{
                  "@odata.type":"#microsoft.graph.identitySet",
                  "user":{
                     "@odata.type":"#microsoft.graph.identity",
                     "id":"8A34A46B-3D17-4ADC-8DCE-DC4E7D572698",
                     "identityProvider":"AAD"
                  }
               },
               "endpointType":"default",
               "region":"amer"
            },
            "targets":[
               {
                  "@odata.type":"#microsoft.graph.invitationParticipantInfo",
                  "identity":{
                     "@odata.type":"#microsoft.graph.identitySet",
                     "applicationInstance":{
                        "@odata.type":"#microsoft.graph.identity",
                        "id":"832899f8-2ea1-4604-8413-27bd2892079f",
                        "identityProvider":"AAD"
                     }
                  },
                  "endpointType":"default",
                  "id":"4520a1a5-5394-5a41-aa12-9ee6fa18cfc8",
                  "region":null,
                  "languageId":null
               }
            ],
            "meetingInfo":{
               "@odata.type":"#microsoft.graph.tokenMeetingInfo",
               "token":"join token"
            },
            "tenantId":"932899f8-2ea1-4604-8413-27bd2892079f",
            "myParticipantId":"1520a1a5-5394-4a41-aa72-9ee6fa18cfc8",
            "callChainId":"05f2f70f-3a9c-47c1-80a9-cc79e91d8cec",
            "incomingContext":{
               "@odata.type":"#microsoft.graph.incomingContext",
               "sourceParticipantId":"30fad2ce-8989-41a1-8a66-f6636e629a2a",
               "observedParticipantId":"30fad2ce-8989-41a1-8a66-f6636e629a2a"
            },
            "id":"e71f0300-9c1f-4d99-b5f4-2722e877d497",
            "applicationMetadata":{
               "botData":{
                  "mediaHostedRegion":"USEA",
                  "user":{
                     "participationMethod":"callee",
                     "clientLocation":"US"
                  },
                  "otherSideUser":{
                     "id":"971f0300-9c1f-4d99-b5f4-2722e877d490",
                     "participantId":"3520a1a5-5394-4a41-aa72-9ee6fa18cfc8",
                     "tenantId":"1540a1a5-2394-4a41-aa72-9ee6fa18cfc8",
                     "onBehalfOf":{
                        "id":"871f0300-9c1f-4d99-b5f4-2722e877d490"
                     },
                     "participationMethod":"caller",
                     "clientLocation":"EUNO"
                  },
                  "inviteReasons":[
                     "PolicyBasedRecording"
                  ],
                  "policyIdentifier":"Test Policy",
                  "pairedRecorders":[
                     {
                        "id":"471f0300-5c1f-4d99-b5f4-2722e877d490",
                        "participantId":"371f0300-2c1f-4d99-b5f4-2722e877d490"
                     }
                  ],
                  "otherRecorders":[
                     {
                        "id":"671f0300-9c1f-4d99-b5f4-2722e877d490",
                        "participantId":"a71f0300-ec1f-4d99-b5f4-2722e877d490"
                     }
                  ]
               }
            }
         }
      }
   ]
}
```
