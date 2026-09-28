<!-- Source: https://learn.microsoft.com/en-us/graph/api/call-playprompt?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# call: playPrompt

Namespace: microsoft.graph

Play a prompt in the call.

For more information about how to handle operations, see [commsOperation](https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0)

Note

The **playPrompt** action is supported only for [calls](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) that are initiated with [serviceHostedMediaConfig](https://learn.microsoft.com/en-us/graph/api/resources/servicehostedmediaconfig?view=graph-rest-1.0).

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
| Application | Calls.Initiate.All | Calls.AccessMedia.All |

> **Note:** Permissions are checked when the call is created; no additional permission check is made when calling this API. Calls.AccessMedia.All is only necessary for calls that use app-hosted media.

## HTTP request

```http
POST /communications/calls/{id}/playPrompt
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| prompts | [MediaPrompt](https://learn.microsoft.com/en-us/graph/api/resources/mediaprompt?view=graph-rest-1.0) collection | The prompts to be played. The maximum supported MediaPrompt collection size is 20. |
| clientContext | String | Unique client context string. Can have a maximum of 256 characters. |

## Response

If successful, this method returns a `200 OK` response code and a [playPromptOperation](https://learn.microsoft.com/en-us/graph/api/resources/playpromptoperation?view=graph-rest-1.0) object in the response body.

## Example

The following example shows how to call this API.

### Request

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
POST https://graph.microsoft.com/v1.0/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896/playPrompt
Content-Type: application/json
Content-Length: 166

{
  "clientContext": "d45324c1-fcb5-430a-902c-f20af696537c",
  "prompts": [
    {
      "@odata.type": "#microsoft.graph.mediaPrompt",
      "mediaInfo": {
        "@odata.type": "#microsoft.graph.mediaInfo",
        "uri": "https://cdn.contoso.com/beep.wav",
        "resourceId": "1D6DE2D4-CD51-4309-8DAA-70768651088E"
      }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Communications.Calls.Item.PlayPrompt;
using Microsoft.Graph.Models;

var requestBody = new PlayPromptPostRequestBody
{
	ClientContext = "d45324c1-fcb5-430a-902c-f20af696537c",
	Prompts = new List<Prompt>
	{
		new MediaPrompt
		{
			OdataType = "#microsoft.graph.mediaPrompt",
			MediaInfo = new MediaInfo
			{
				OdataType = "#microsoft.graph.mediaInfo",
				Uri = "https://cdn.contoso.com/beep.wav",
				ResourceId = "1D6DE2D4-CD51-4309-8DAA-70768651088E",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls["{call-id}"].PlayPrompt.PostAsync(requestBody);
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

requestBody := graphcommunications.NewPlayPromptPostRequestBody()
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

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
playPrompt, err := graphClient.Communications().Calls().ByCallId("call-id").PlayPrompt().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.communications.calls.item.playprompt.PlayPromptPostRequestBody playPromptPostRequestBody = new com.microsoft.graph.communications.calls.item.playprompt.PlayPromptPostRequestBody();
playPromptPostRequestBody.setClientContext("d45324c1-fcb5-430a-902c-f20af696537c");
LinkedList<Prompt> prompts = new LinkedList<Prompt>();
MediaPrompt prompt = new MediaPrompt();
prompt.setOdataType("#microsoft.graph.mediaPrompt");
MediaInfo mediaInfo = new MediaInfo();
mediaInfo.setOdataType("#microsoft.graph.mediaInfo");
mediaInfo.setUri("https://cdn.contoso.com/beep.wav");
mediaInfo.setResourceId("1D6DE2D4-CD51-4309-8DAA-70768651088E");
prompt.setMediaInfo(mediaInfo);
prompts.add(prompt);
playPromptPostRequestBody.setPrompts(prompts);
var result = graphClient.communications().calls().byCallId("{call-id}").playPrompt().post(playPromptPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const playPromptOperation = {
  clientContext: 'd45324c1-fcb5-430a-902c-f20af696537c',
  prompts: [
    {
      '@odata.type': '#microsoft.graph.mediaPrompt',
      mediaInfo: {
        '@odata.type': '#microsoft.graph.mediaInfo',
        uri: 'https://cdn.contoso.com/beep.wav',
        resourceId: '1D6DE2D4-CD51-4309-8DAA-70768651088E'
      }
    }
  ]
};

await client.api('/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896/playPrompt')
	.post(playPromptOperation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\Calls\Item\PlayPrompt\PlayPromptPostRequestBody;
use Microsoft\Graph\Generated\Models\Prompt;
use Microsoft\Graph\Generated\Models\MediaPrompt;
use Microsoft\Graph\Generated\Models\MediaInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PlayPromptPostRequestBody();
$requestBody->setClientContext('d45324c1-fcb5-430a-902c-f20af696537c');
$promptsPrompt1 = new MediaPrompt();
$promptsPrompt1->setOdataType('#microsoft.graph.mediaPrompt');
$promptsPrompt1MediaInfo = new MediaInfo();
$promptsPrompt1MediaInfo->setOdataType('#microsoft.graph.mediaInfo');
$promptsPrompt1MediaInfo->setUri('https://cdn.contoso.com/beep.wav');
$promptsPrompt1MediaInfo->setResourceId('1D6DE2D4-CD51-4309-8DAA-70768651088E');
$promptsPrompt1->setMediaInfo($promptsPrompt1MediaInfo);
$promptsArray []= $promptsPrompt1;
$requestBody->setPrompts($promptsArray);


$result = $graphServiceClient->communications()->calls()->byCallId('call-id')->playPrompt()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	clientContext = "d45324c1-fcb5-430a-902c-f20af696537c"
	prompts = @(
		@{
			"@odata.type" = "#microsoft.graph.mediaPrompt"
			mediaInfo = @{
				"@odata.type" = "#microsoft.graph.mediaInfo"
				uri = "https://cdn.contoso.com/beep.wav"
				resourceId = "1D6DE2D4-CD51-4309-8DAA-70768651088E"
			}
		}
	)
}

Invoke-MgPlayCommunicationCallPrompt -CallId $callId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.calls.item.play_prompt.play_prompt_post_request_body import PlayPromptPostRequestBody
from msgraph.generated.models.prompt import Prompt
from msgraph.generated.models.media_prompt import MediaPrompt
from msgraph.generated.models.media_info import MediaInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PlayPromptPostRequestBody(
	client_context = "d45324c1-fcb5-430a-902c-f20af696537c",
	prompts = [
		MediaPrompt(
			odata_type = "#microsoft.graph.mediaPrompt",
			media_info = MediaInfo(
				odata_type = "#microsoft.graph.mediaInfo",
				uri = "https://cdn.contoso.com/beep.wav",
				resource_id = "1D6DE2D4-CD51-4309-8DAA-70768651088E",
			),
		),
	],
)

result = await graph_client.communications.calls.by_call_id('call-id').play_prompt.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Location: https://graph.microsoft.com/v1.0/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896/operations/0fe0623f-d628-42ed-b4bd-8ac290072cc5
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.playPromptOperation",
  "id": "0fe0623f-d628-42ed-b4bd-8ac290072cc5",
  "status": "running",
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
        "@odata.type": "#microsoft.graph.playPromptOperation",
        "@odata.id": "/communications/calls/57DAB8B1894C409AB240BD8BEAE78896/operations/0FE0623FD62842EDB4BD8AC290072CC5",
        "@odata.etag": "W/\"54451\"",
        "resultInfo": {
          "@odata.type": "#microsoft.graph.resultInfo",
          "code": 200,
          "subcode": 0,
          "message": "Action completed successfully."
        },
        "clientContext": "d45324c1-fcb5-430a-902c-f20af696537c",
        "status": "completed"
      }
    }
  ]
}
```
