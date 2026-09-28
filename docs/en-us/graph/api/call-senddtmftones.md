<!-- Source: https://learn.microsoft.com/en-us/graph/api/call-senddtmftones?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# call: sendDtmfTones

Namespace: microsoft.graph

Send DTMF tones in a call.

For more information about how to handle operations, see [commsOperation](https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0)

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
| Application | Calls.Initiate.All | Calls.AccessMedia.All |

> **Note:** Permissions are checked when a call is created; no additional permission check is made when calling this API. Calls.AccessMedia.All is only necessary for calls that use app-hosted media.

## HTTP request

```http
POST /app/calls/{id}/sendDtmfTones
POST /communications/calls/{id}/sendDtmfTones
```

> **Note:** The `/app` path is deprecated. Going forward, use the `/communications` path.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| tones | [ToneInfo](https://learn.microsoft.com/en-us/graph/api/resources/toneinfo?view=graph-rest-1.0) collection | The tones to be sent. |
| delayBetweenTonesMs | Int32 | The milliseconds delay between tones. |
| clientContext | String | Unique client context string. Can have a maximum of 256 characters. |

## Response

If successful, this method returns a `200 OK` response code and a [sendDtmfTonesOperation](https://learn.microsoft.com/en-us/graph/api/resources/senddtmftonesoperation?view=graph-rest-1.0) object in the response body.

## Examples

The following example shows how to send DTMF tones in a call.

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
POST https://graph.microsoft.com/v1.0/communications/calls/481f3600-983e-4276-9b59-c1b30ec8d125/microsoft.graph.sendDtmfTones
Content-Type: application/json
Content-Length: 166

{
  "tones": [
    "tone1",
    "tone2",
    "tone3",
    "tone4",
    "tone5",
    "tone6",
    "tone7",
    "tone8",
    "tone9",
    "tone0",
    "star",
    "pound"
  ],
  "delayBetweenTonesMs": 1000,
  "clientContext": "e0be71f1-a14f-4cec-b65a-e7aba5db7c53"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Communications.Calls.Item.SendDtmfTones;
using Microsoft.Graph.Models;

var requestBody = new SendDtmfTonesPostRequestBody
{
	Tones = new List<Tone?>
	{
		Tone.Tone1,
		Tone.Tone2,
		Tone.Tone3,
		Tone.Tone4,
		Tone.Tone5,
		Tone.Tone6,
		Tone.Tone7,
		Tone.Tone8,
		Tone.Tone9,
		Tone.Tone0,
		Tone.Star,
		Tone.Pound,
	},
	DelayBetweenTonesMs = 1000,
	ClientContext = "e0be71f1-a14f-4cec-b65a-e7aba5db7c53",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls["{call-id}"].SendDtmfTones.PostAsync(requestBody);
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

requestBody := graphcommunications.NewSendDtmfTonesPostRequestBody()
tones := []graphmodels.Toneable {
	tone := graphmodels.TONE1_TONE 
	requestBody.SetTone(&tone) 
	tone := graphmodels.TONE2_TONE 
	requestBody.SetTone(&tone) 
	tone := graphmodels.TONE3_TONE 
	requestBody.SetTone(&tone) 
	tone := graphmodels.TONE4_TONE 
	requestBody.SetTone(&tone) 
	tone := graphmodels.TONE5_TONE 
	requestBody.SetTone(&tone) 
	tone := graphmodels.TONE6_TONE 
	requestBody.SetTone(&tone) 
	tone := graphmodels.TONE7_TONE 
	requestBody.SetTone(&tone) 
	tone := graphmodels.TONE8_TONE 
	requestBody.SetTone(&tone) 
	tone := graphmodels.TONE9_TONE 
	requestBody.SetTone(&tone) 
	tone := graphmodels.TONE0_TONE 
	requestBody.SetTone(&tone) 
	tone := graphmodels.STAR_TONE 
	requestBody.SetTone(&tone) 
	tone := graphmodels.POUND_TONE 
	requestBody.SetTone(&tone)
}
requestBody.SetTones(tones)
delayBetweenTonesMs := int32(1000)
requestBody.SetDelayBetweenTonesMs(&delayBetweenTonesMs) 
clientContext := "e0be71f1-a14f-4cec-b65a-e7aba5db7c53"
requestBody.SetClientContext(&clientContext) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sendDtmfTones, err := graphClient.Communications().Calls().ByCallId("call-id").SendDtmfTones().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.communications.calls.item.senddtmftones.SendDtmfTonesPostRequestBody sendDtmfTonesPostRequestBody = new com.microsoft.graph.communications.calls.item.senddtmftones.SendDtmfTonesPostRequestBody();
LinkedList<Tone> tones = new LinkedList<Tone>();
tones.add(Tone.Tone1);
tones.add(Tone.Tone2);
tones.add(Tone.Tone3);
tones.add(Tone.Tone4);
tones.add(Tone.Tone5);
tones.add(Tone.Tone6);
tones.add(Tone.Tone7);
tones.add(Tone.Tone8);
tones.add(Tone.Tone9);
tones.add(Tone.Tone0);
tones.add(Tone.Star);
tones.add(Tone.Pound);
sendDtmfTonesPostRequestBody.setTones(tones);
sendDtmfTonesPostRequestBody.setDelayBetweenTonesMs(1000);
sendDtmfTonesPostRequestBody.setClientContext("e0be71f1-a14f-4cec-b65a-e7aba5db7c53");
var result = graphClient.communications().calls().byCallId("{call-id}").sendDtmfTones().post(sendDtmfTonesPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendDtmfTonesOperation = {
  tones: [
    'tone1',
    'tone2',
    'tone3',
    'tone4',
    'tone5',
    'tone6',
    'tone7',
    'tone8',
    'tone9',
    'tone0',
    'star',
    'pound'
  ],
  delayBetweenTonesMs: 1000,
  clientContext: 'e0be71f1-a14f-4cec-b65a-e7aba5db7c53'
};

await client.api('/communications/calls/481f3600-983e-4276-9b59-c1b30ec8d125/microsoft.graph.sendDtmfTones')
	.post(sendDtmfTonesOperation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\Calls\Item\SendDtmfTones\SendDtmfTonesPostRequestBody;
use Microsoft\Graph\Generated\Models\Tone;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendDtmfTonesPostRequestBody();
$requestBody->setTones([new Tone('tone1'),new Tone('tone2'),new Tone('tone3'),new Tone('tone4'),new Tone('tone5'),new Tone('tone6'),new Tone('tone7'),new Tone('tone8'),new Tone('tone9'),new Tone('tone0'),new Tone('star'),new Tone('pound'),	]);
$requestBody->setDelayBetweenTonesMs(1000);
$requestBody->setClientContext('e0be71f1-a14f-4cec-b65a-e7aba5db7c53');

$result = $graphServiceClient->communications()->calls()->byCallId('call-id')->sendDtmfTones()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	tones = @(
	"tone1"
"tone2"
"tone3"
"tone4"
"tone5"
"tone6"
"tone7"
"tone8"
"tone9"
"tone0"
"star"
"pound"
)
delayBetweenTonesMs = 1000
clientContext = "e0be71f1-a14f-4cec-b65a-e7aba5db7c53"
}

Send-MgCommunicationCallDtmfTone -CallId $callId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.calls.item.send_dtmf_tones.send_dtmf_tones_post_request_body import SendDtmfTonesPostRequestBody
from msgraph.generated.models.tone import Tone
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendDtmfTonesPostRequestBody(
	tones = [
		Tone.Tone1,
		Tone.Tone2,
		Tone.Tone3,
		Tone.Tone4,
		Tone.Tone5,
		Tone.Tone6,
		Tone.Tone7,
		Tone.Tone8,
		Tone.Tone9,
		Tone.Tone0,
		Tone.Star,
		Tone.Pound,
	],
	delay_between_tones_ms = 1000,
	client_context = "e0be71f1-a14f-4cec-b65a-e7aba5db7c53",
)

result = await graph_client.communications.calls.by_call_id('call-id').send_dtmf_tones.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Location: https://graph.microsoft.com/v1.0/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896/operations/d36fe651-9f50-484d-bd4b-1e6415eae448

{
  "@odata.type": "#microsoft.graph.sendDtmfTonesOperation",
  "status": "running",
  "clientContext": "e0be71f1-a14f-4cec-b65a-e7aba5db7c53",
  "id": "d36fe651-9f50-484d-bd4b-1e6415eae448"
}
```

### Notification - operation completed

#### Successful case

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
      "resourceUrl": "/communications/calls/481f3600-983e-4276-9b59-c1b30ec8d125/operations/d36fe651-9f50-484d-bd4b-1e6415eae448",
      "resourceData": {
        "@odata.type": "#microsoft.graph.sendDtmfTonesOperation",
        "status": "completed",
        "completionReason": "completedSuccessfully",
        "clientContext": "e0be71f1-a14f-4cec-b65a-e7aba5db7c53",
        "id": "d36fe651-9f50-484d-bd4b-1e6415eae448"
      }
    }
  ]
}
```

#### Error case 1

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
      "resourceUrl": "/communications/calls/481f3600-983e-4276-9b59-c1b30ec8d125/operations/d36fe651-9f50-484d-bd4b-1e6415eae448",
      "resourceData": {
        "@odata.type": "#microsoft.graph.sendDtmfTonesOperation",
        "status": "completed",
        "completionReason": "mediaOperationCanceled",
        "clientContext": "e0be71f1-a14f-4cec-b65a-e7aba5db7c53",
        "id": "d36fe651-9f50-484d-bd4b-1e6415eae448"
      }
    }
  ]
}
```

#### Error case 2

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
      "resourceUrl": "/communications/calls/481f3600-983e-4276-9b59-c1b30ec8d125/operations/d36fe651-9f50-484d-bd4b-1e6415eae448",
      "resourceData": {
        "@odata.type": "#microsoft.graph.sendDtmfTonesOperation",
        "status": "completed",
        "completionReason": "unknown",
        "clientContext": "e0be71f1-a14f-4cec-b65a-e7aba5db7c53",
        "id": "d36fe651-9f50-484d-bd4b-1e6415eae448"
      }
    }
  ]
}
```
