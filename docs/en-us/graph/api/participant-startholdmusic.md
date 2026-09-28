<!-- Source: https://learn.microsoft.com/en-us/graph/api/participant-startholdmusic?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# participant: startHoldMusic

Namespace: microsoft.graph

Put a [participant](https://learn.microsoft.com/en-us/graph/api/resources/participant?view=graph-rest-1.0) on hold and play music in the background.

> **Note:** Only one participant can be placed on hold at any given time.

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
| Application | Calls.JoinGroupCallasGuest.All | Calls.JoinGroupCall.All |

## HTTP request

```http
POST /communications/calls/{id}/participants/{id}/startHoldMusic
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
| clientContext | String | Optional. Unique client context string. Can have a maximum of 256 characters. |
| customPrompt | microsoft.graph.mediaPrompt | Optional. The audio prompt that the participant hears when placed on hold. |

## Response

If successful, this method returns a `202 Accepted` response code and a [startHoldMusicOperation](https://learn.microsoft.com/en-us/graph/api/resources/startholdmusicoperation?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls/e141b67c-90fd-455d-858b-b48a40b9cc8d/participants/fa1e9582-7145-4ca3-bcd8-577f561fcb6e/startHoldMusic
Content-type: application/json

{
  "customPrompt": {
    "@odata.type": "#microsoft.graph.mediaPrompt",
    "mediaInfo": {
      "@odata.type": "#microsoft.graph.mediaInfo",
      "uri": "https://bot.contoso.com/onHold.wav",
    },
  },
  "clientContext": "d45324c1-fcb5-430a-902c-f20af696537c",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Communications.Calls.Item.Participants.Item.StartHoldMusic;
using Microsoft.Graph.Models;

var requestBody = new StartHoldMusicPostRequestBody
{
	CustomPrompt = new MediaPrompt
	{
		OdataType = "#microsoft.graph.mediaPrompt",
		MediaInfo = new MediaInfo
		{
			OdataType = "#microsoft.graph.mediaInfo",
			Uri = "https://bot.contoso.com/onHold.wav",
		},
	},
	ClientContext = "d45324c1-fcb5-430a-902c-f20af696537c",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls["{call-id}"].Participants["{participant-id}"].StartHoldMusic.PostAsync(requestBody);
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

requestBody := graphcommunications.NewStartHoldMusicPostRequestBody()
customPrompt := graphmodels.NewMediaPrompt()
mediaInfo := graphmodels.NewMediaInfo()
uri := "https://bot.contoso.com/onHold.wav"
mediaInfo.SetUri(&uri) 
customPrompt.SetMediaInfo(mediaInfo)
requestBody.SetCustomPrompt(customPrompt)
clientContext := "d45324c1-fcb5-430a-902c-f20af696537c"
requestBody.SetClientContext(&clientContext) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
startHoldMusic, err := graphClient.Communications().Calls().ByCallId("call-id").Participants().ByParticipantId("participant-id").StartHoldMusic().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.communications.calls.item.participants.item.startholdmusic.StartHoldMusicPostRequestBody startHoldMusicPostRequestBody = new com.microsoft.graph.communications.calls.item.participants.item.startholdmusic.StartHoldMusicPostRequestBody();
MediaPrompt customPrompt = new MediaPrompt();
customPrompt.setOdataType("#microsoft.graph.mediaPrompt");
MediaInfo mediaInfo = new MediaInfo();
mediaInfo.setOdataType("#microsoft.graph.mediaInfo");
mediaInfo.setUri("https://bot.contoso.com/onHold.wav");
customPrompt.setMediaInfo(mediaInfo);
startHoldMusicPostRequestBody.setCustomPrompt(customPrompt);
startHoldMusicPostRequestBody.setClientContext("d45324c1-fcb5-430a-902c-f20af696537c");
var result = graphClient.communications().calls().byCallId("{call-id}").participants().byParticipantId("{participant-id}").startHoldMusic().post(startHoldMusicPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const startHoldMusicOperation = {
  customPrompt: {
    '@odata.type': '#microsoft.graph.mediaPrompt',
    mediaInfo: {
      '@odata.type': '#microsoft.graph.mediaInfo',
      uri: 'https://bot.contoso.com/onHold.wav',
    },
  },
  clientContext: 'd45324c1-fcb5-430a-902c-f20af696537c',
};

await client.api('/communications/calls/e141b67c-90fd-455d-858b-b48a40b9cc8d/participants/fa1e9582-7145-4ca3-bcd8-577f561fcb6e/startHoldMusic')
	.post(startHoldMusicOperation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\Calls\Item\Participants\Item\StartHoldMusic\StartHoldMusicPostRequestBody;
use Microsoft\Graph\Generated\Models\MediaPrompt;
use Microsoft\Graph\Generated\Models\MediaInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new StartHoldMusicPostRequestBody();
$customPrompt = new MediaPrompt();
$customPrompt->setOdataType('#microsoft.graph.mediaPrompt');
$customPromptMediaInfo = new MediaInfo();
$customPromptMediaInfo->setOdataType('#microsoft.graph.mediaInfo');
$customPromptMediaInfo->setUri('https://bot.contoso.com/onHold.wav');
$customPrompt->setMediaInfo($customPromptMediaInfo);
$requestBody->setCustomPrompt($customPrompt);
$requestBody->setClientContext('d45324c1-fcb5-430a-902c-f20af696537c');

$result = $graphServiceClient->communications()->calls()->byCallId('call-id')->participants()->byParticipantId('participant-id')->startHoldMusic()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	customPrompt = @{
		"@odata.type" = "#microsoft.graph.mediaPrompt"
		mediaInfo = @{
			"@odata.type" = "#microsoft.graph.mediaInfo"
			uri = "https://bot.contoso.com/onHold.wav"
		}
	}
	clientContext = "d45324c1-fcb5-430a-902c-f20af696537c"
}

Start-MgCommunicationCallParticipantHoldMusic -CallId $callId -ParticipantId $participantId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.calls.item.participants.item.start_hold_music.start_hold_music_post_request_body import StartHoldMusicPostRequestBody
from msgraph.generated.models.media_prompt import MediaPrompt
from msgraph.generated.models.media_info import MediaInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = StartHoldMusicPostRequestBody(
	custom_prompt = MediaPrompt(
		odata_type = "#microsoft.graph.mediaPrompt",
		media_info = MediaInfo(
			odata_type = "#microsoft.graph.mediaInfo",
			uri = "https://bot.contoso.com/onHold.wav",
		),
	),
	client_context = "d45324c1-fcb5-430a-902c-f20af696537c",
)

result = await graph_client.communications.calls.by_call_id('call-id').participants.by_participant_id('participant-id').start_hold_music.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/v1.0/communications/calls/e141b67c-90fd-455d-858b-b48a40b9cc8d/operations/0fe0623f-d628-42ed-b4bd-8ac290072cc5

{
  "@odata.type": "#microsoft.graph.startHoldMusicOperation",
  "id": "0fe0623f-d628-42ed-b4bd-8ac290072cc5",
  "status": "running",
  "clientContext": "d45324c1-fcb5-430a-902c-f20af696537c"
}
```

### Notification sent to the application after the startHoldMusicOperation finishes

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
      "resourceUrl": "communications/calls/e141b67c-90fd-455d-858b-b48a40b9cc8d/operations/0fe0623f-d628-42ed-b4bd-8ac290072cc5",
      "resourceData": {
        "@odata.type": "#microsoft.graph.startHoldMusicOperation",
        "@odata.id": "communications/calls/e141b67c-90fd-455d-858b-b48a40b9cc8d/operations/0fe0623f-d628-42ed-b4bd-8ac290072cc5",
        "@odata.etag": "W/\"54451\"",
        "clientContext": "d45324c1-fcb5-430a-902c-f20af696537c",
        "status": "completed"
      }
    }
  ]
}
```
