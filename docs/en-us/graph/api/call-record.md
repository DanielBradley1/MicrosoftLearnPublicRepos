<!-- Source: https://learn.microsoft.com/en-us/graph/api/call-record?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# call: recordResponse

Namespace: microsoft.graph

Records a short audio response from the caller. A bot can utilize this to capture a voice response from a caller after they are prompted for a response.

For further information on how to handle operations, please review [commsOperation](https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0)

> **Note:** This is only supported for [calls](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) which are initiated with [serviceHostedMediaConfig](https://learn.microsoft.com/en-us/graph/api/resources/servicehostedmediaconfig?view=graph-rest-1.0).

This action is not intended to record the entire call. The maximum length of recording is 2 minutes. The recording is not saved permanently by the Cloud Communications Platform and is discarded shortly after the call ends. The bot must download the recording promptly after the recording operation finishes by using the recordingLocation value that's given in the completed notification.

> **Note:** Any media collected may **not** be persisted. Make sure you are compliant with the laws and regulations of your area when it comes to call recording. Please consult with a legal counsel for more information.

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
POST /communications/calls/{id}/recordResponse
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| prompts | [mediaPrompt](https://learn.microsoft.com/en-us/graph/api/resources/mediaprompt?view=graph-rest-1.0) collection | The prompts to be played. The maximum supported mediaPrompt collection size is 1. |
| bargeInAllowed | Boolean | If true, the recordResponse request will barge into other existing queued-up/currently-processing record/playprompt requests. Default = false. |
| initialSilenceTimeoutInSeconds | Int32 | Maximum initial silence \(user silence\) allowed from the time we start the record response operation before we timeout and fail the operation. If we are playing a prompt, then this timer starts after prompt finishes. Default = 5 seconds, Min = 1 second, Max = 120 seconds |
| maxSilenceTimeoutInSeconds | Int32 | Maximum silence \(pause\) time allowed after a user has started speaking. Default = 5 seconds, Min = 1 second, Max = 120 seconds. |
| maxRecordDurationInSeconds | Int32 | Max duration for the recordResponse operation before stopping recording. Default = 5 seconds, Min = 1 second, Max = 120 seconds. |
| playBeep | Boolean | If true, plays a beep to indicate to the user that they can start recording their message. Default = true. |
| stopTones | String collection | Stop tones specified to end recording. |
| clientContext | String | Unique Client Context string. Max limit is 256 chars. |

## Response

This method returns a `200 OK` response code and a Location header with a URI to the [recordOperation](https://learn.microsoft.com/en-us/graph/api/resources/recordoperation?view=graph-rest-1.0) created for this request.

## Example

The following example shows how to call this API.

### Example 1: Records a short audio response from the caller

##### Request

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
POST https://graph.microsoft.com/v1.0/communications/calls/{id}/recordResponse
Content-Type: application/json
Content-Length: 394

{
  "bargeInAllowed": true,
  "clientContext": "d45324c1-fcb5-430a-902c-f20af696537c",
  "prompts": [
    {
      "@odata.type": "#microsoft.graph.mediaPrompt",
      "mediaInfo": {
        "uri": "https://cdn.contoso.com/beep.wav",
        "resourceId": "1D6DE2D4-CD51-4309-8DAA-70768651088E"
      }
    }
  ],
  "maxRecordDurationInSeconds": 10,
  "initialSilenceTimeoutInSeconds": 5,
  "maxSilenceTimeoutInSeconds": 2,
  "playBeep": true,
  "stopTones": [ "#", "1", "*" ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Communications.Calls.Item.RecordResponse;
using Microsoft.Graph.Models;

var requestBody = new RecordResponsePostRequestBody
{
	BargeInAllowed = true,
	ClientContext = "d45324c1-fcb5-430a-902c-f20af696537c",
	Prompts = new List<Prompt>
	{
		new MediaPrompt
		{
			OdataType = "#microsoft.graph.mediaPrompt",
			MediaInfo = new MediaInfo
			{
				Uri = "https://cdn.contoso.com/beep.wav",
				ResourceId = "1D6DE2D4-CD51-4309-8DAA-70768651088E",
			},
		},
	},
	MaxRecordDurationInSeconds = 10,
	InitialSilenceTimeoutInSeconds = 5,
	MaxSilenceTimeoutInSeconds = 2,
	PlayBeep = true,
	StopTones = new List<string>
	{
		"#",
		"1",
		"*",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls["{call-id}"].RecordResponse.PostAsync(requestBody);
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

requestBody := graphcommunications.NewRecordResponsePostRequestBody()
bargeInAllowed := true
requestBody.SetBargeInAllowed(&bargeInAllowed) 
clientContext := "d45324c1-fcb5-430a-902c-f20af696537c"
requestBody.SetClientContext(&clientContext) 


prompt := graphmodels.NewMediaPrompt()
mediaInfo := graphmodels.NewMediaInfo()
uri := "https://cdn.contoso.com/beep.wav"
mediaInfo.SetUri(&uri) 
resourceId := "1D6DE2D4-CD51-4309-8DAA-70768651088E"
mediaInfo.SetResourceId(&resourceId) 
prompt.SetMediaInfo(mediaInfo)

prompts := []graphmodels.Promptable {
	prompt,
}
requestBody.SetPrompts(prompts)
maxRecordDurationInSeconds := int32(10)
requestBody.SetMaxRecordDurationInSeconds(&maxRecordDurationInSeconds) 
initialSilenceTimeoutInSeconds := int32(5)
requestBody.SetInitialSilenceTimeoutInSeconds(&initialSilenceTimeoutInSeconds) 
maxSilenceTimeoutInSeconds := int32(2)
requestBody.SetMaxSilenceTimeoutInSeconds(&maxSilenceTimeoutInSeconds) 
playBeep := true
requestBody.SetPlayBeep(&playBeep) 
stopTones := []string {
	"#",
	"1",
	"*",
}
requestBody.SetStopTones(stopTones)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
recordResponse, err := graphClient.Communications().Calls().ByCallId("call-id").RecordResponse().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.communications.calls.item.recordresponse.RecordResponsePostRequestBody recordResponsePostRequestBody = new com.microsoft.graph.communications.calls.item.recordresponse.RecordResponsePostRequestBody();
recordResponsePostRequestBody.setBargeInAllowed(true);
recordResponsePostRequestBody.setClientContext("d45324c1-fcb5-430a-902c-f20af696537c");
LinkedList<Prompt> prompts = new LinkedList<Prompt>();
MediaPrompt prompt = new MediaPrompt();
prompt.setOdataType("#microsoft.graph.mediaPrompt");
MediaInfo mediaInfo = new MediaInfo();
mediaInfo.setUri("https://cdn.contoso.com/beep.wav");
mediaInfo.setResourceId("1D6DE2D4-CD51-4309-8DAA-70768651088E");
prompt.setMediaInfo(mediaInfo);
prompts.add(prompt);
recordResponsePostRequestBody.setPrompts(prompts);
recordResponsePostRequestBody.setMaxRecordDurationInSeconds(10);
recordResponsePostRequestBody.setInitialSilenceTimeoutInSeconds(5);
recordResponsePostRequestBody.setMaxSilenceTimeoutInSeconds(2);
recordResponsePostRequestBody.setPlayBeep(true);
LinkedList<String> stopTones = new LinkedList<String>();
stopTones.add("#");
stopTones.add("1");
stopTones.add("*");
recordResponsePostRequestBody.setStopTones(stopTones);
var result = graphClient.communications().calls().byCallId("{call-id}").recordResponse().post(recordResponsePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const recordOperation = {
  bargeInAllowed: true,
  clientContext: 'd45324c1-fcb5-430a-902c-f20af696537c',
  prompts: [
    {
      '@odata.type': '#microsoft.graph.mediaPrompt',
      mediaInfo: {
        uri: 'https://cdn.contoso.com/beep.wav',
        resourceId: '1D6DE2D4-CD51-4309-8DAA-70768651088E'
      }
    }
  ],
  maxRecordDurationInSeconds: 10,
  initialSilenceTimeoutInSeconds: 5,
  maxSilenceTimeoutInSeconds: 2,
  playBeep: true,
  stopTones: [ '#', '1', '*' ]
};

await client.api('/communications/calls/{id}/recordResponse')
	.post(recordOperation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\Calls\Item\RecordResponse\RecordResponsePostRequestBody;
use Microsoft\Graph\Generated\Models\Prompt;
use Microsoft\Graph\Generated\Models\MediaPrompt;
use Microsoft\Graph\Generated\Models\MediaInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RecordResponsePostRequestBody();
$requestBody->setBargeInAllowed(true);
$requestBody->setClientContext('d45324c1-fcb5-430a-902c-f20af696537c');
$promptsPrompt1 = new MediaPrompt();
$promptsPrompt1->setOdataType('#microsoft.graph.mediaPrompt');
$promptsPrompt1MediaInfo = new MediaInfo();
$promptsPrompt1MediaInfo->setUri('https://cdn.contoso.com/beep.wav');
$promptsPrompt1MediaInfo->setResourceId('1D6DE2D4-CD51-4309-8DAA-70768651088E');
$promptsPrompt1->setMediaInfo($promptsPrompt1MediaInfo);
$promptsArray []= $promptsPrompt1;
$requestBody->setPrompts($promptsArray);

$requestBody->setMaxRecordDurationInSeconds(10);
$requestBody->setInitialSilenceTimeoutInSeconds(5);
$requestBody->setMaxSilenceTimeoutInSeconds(2);
$requestBody->setPlayBeep(true);
$requestBody->setStopTones(['#', '1', '*', ]);

$result = $graphServiceClient->communications()->calls()->byCallId('call-id')->recordResponse()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	bargeInAllowed = $true
	clientContext = "d45324c1-fcb5-430a-902c-f20af696537c"
	prompts = @(
		@{
			"@odata.type" = "#microsoft.graph.mediaPrompt"
			mediaInfo = @{
				uri = "https://cdn.contoso.com/beep.wav"
				resourceId = "1D6DE2D4-CD51-4309-8DAA-70768651088E"
			}
		}
	)
	maxRecordDurationInSeconds = 10
	initialSilenceTimeoutInSeconds = 5
	maxSilenceTimeoutInSeconds = 2
	playBeep = $true
	stopTones = @(
	"#"
"1"
"*"
)
}

Invoke-MgRecordCommunicationCallResponse -CallId $callId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.calls.item.record_response.record_response_post_request_body import RecordResponsePostRequestBody
from msgraph.generated.models.prompt import Prompt
from msgraph.generated.models.media_prompt import MediaPrompt
from msgraph.generated.models.media_info import MediaInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RecordResponsePostRequestBody(
	barge_in_allowed = True,
	client_context = "d45324c1-fcb5-430a-902c-f20af696537c",
	prompts = [
		MediaPrompt(
			odata_type = "#microsoft.graph.mediaPrompt",
			media_info = MediaInfo(
				uri = "https://cdn.contoso.com/beep.wav",
				resource_id = "1D6DE2D4-CD51-4309-8DAA-70768651088E",
			),
		),
	],
	max_record_duration_in_seconds = 10,
	initial_silence_timeout_in_seconds = 5,
	max_silence_timeout_in_seconds = 2,
	play_beep = True,
	stop_tones = [
		"#",
		"1",
		"*",
	],
)

result = await graph_client.communications.calls.by_call_id('call-id').record_response.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

##### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Location: https://graph.microsoft.com/v1.0/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896/operations/0fe0623f-d628-42ed-b4bd-8ac290072cc5

{
  "@odata.type": "#microsoft.graph.recordOperation",
  "id": "0fe0623f-d628-42ed-b4bd-8ac290072cc5",
  "status": "running",
  "resultInfo": null,
  "recordingLocation": null,
  "clientContext": "d45324c1-fcb5-430a-902c-f20af696537c"
}
```

##### Notification - operation completed

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
      "resourceUrl": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896/operations/0FE0623FD62842EDB4BD8AC290072CC5",
      "resourceData": {
        "@odata.type": "#microsoft.graph.recordOperation",
        "@odata.id": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896/operations/0FE0623FD62842EDB4BD8AC290072CC5",
        "@odata.etag": "W/\"54451\"",
        "id": "0fe0623f-d628-42ed-b4bd-8ac290072cc5",
        "clientContext": "d45324c1-fcb5-430a-902c-f20af696537c",
        "status": "completed",
        "resultInfo": {
          "@odata.type": "#microsoft.graph.resultInfo",
          "code": 200,
          "subcode": 8515,
          "message": "Action completed, max record duration reached."
        },
        "recordingLocation": "https://file.location/17e3b46c-f61d-4f4d-9635-c626ef18e6ad",
        "recordingAccessToken": "<access-token>"
      }
    }
  ]
}
```

### Example 2: Retrieving the recording file

> **Note:** You may NOT record or otherwise persist media content from calls or meetings that your application accesses, or data derived from that media content. Make sure you are compliant with the laws and regulations of your area regarding data protection and confidentiality of communications. Please see the [Terms of Use](https://learn.microsoft.com/en-us/legal/microsoft-apis/terms-of-use) and consult with your legal counsel for more information.

##### Request

```http
GET https://file.location/17e3b46c-f61d-4f4d-9635-c626ef18e6ad
Authorization: Bearer <recordingAccessToken>
```

##### Response

```http
HTTP/1.1 200 OK
Transfer-Encoding: chunked
Date: Thu, 17 Jan 2019 01:46:37 GMT
Content-Type: application/octet-stream

(application/octet-stream of size 160696 bytes)
```
