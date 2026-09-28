<!-- Source: https://learn.microsoft.com/en-us/graph/api/call-updaterecordingstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# call: updateRecordingStatus

Namespace: microsoft.graph

Update the application's recording status associated with a call. This requires the use of the [Teams policy-based recording](https://learn.microsoft.com/en-us/MicrosoftTeams/teams-recording-policy) solution.

> **Additional Restriction**: You may NOT use the Media Access API to record or otherwise persist media content from calls or meetings that your application accesses, or data derived from that media content \("record" or "recording"\), without first calling the **updateRecordingStatus** API to indicate that recording has begun, and receiving a success reply from that API. If your application begins recording any meeting, it must end the recording prior to calling the **updateRecordingStatus** API to indicate that the recording has ended.

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
| Application | Calls.AccessMedia.All | Calls.JoinGroupCall.All |

## HTTP request

```http
POST /communications/calls/{id}/updateRecordingStatus
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
| clientContext | String | Unique client context string. Max limit is 256 chars. |
| status | String | The recording status. The possible values are: `notRecording`, `recording`, or `failed`. |

## Response

This method returns a `200 OK` response code and a Location header with a URI to the [updateRecordingStatusOperation](https://learn.microsoft.com/en-us/graph/api/resources/updaterecordingstatusoperation?view=graph-rest-1.0) object created for this request.

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
POST https://graph.microsoft.com/v1.0/communications/calls/{id}/updateRecordingStatus
Content-Type: application/json
Content-Length: 79

{
  "clientContext": "clientContext-value",
  "status": "notRecording | recording | failed"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Communications.Calls.Item.UpdateRecordingStatus;
using Microsoft.Graph.Models;

var requestBody = new UpdateRecordingStatusPostRequestBody
{
	ClientContext = "clientContext-value",
	Status = RecordingStatus.NotRecording | RecordingStatus.Recording | RecordingStatus.Failed,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls["{call-id}"].UpdateRecordingStatus.PostAsync(requestBody);
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

requestBody := graphcommunications.NewUpdateRecordingStatusPostRequestBody()
clientContext := "clientContext-value"
requestBody.SetClientContext(&clientContext) 
status := graphmodels.NOTRECORDING | RECORDING | FAILED_RECORDINGSTATUS 
requestBody.SetStatus(&status) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
updateRecordingStatus, err := graphClient.Communications().Calls().ByCallId("call-id").UpdateRecordingStatus().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.communications.calls.item.updaterecordingstatus.UpdateRecordingStatusPostRequestBody updateRecordingStatusPostRequestBody = new com.microsoft.graph.communications.calls.item.updaterecordingstatus.UpdateRecordingStatusPostRequestBody();
updateRecordingStatusPostRequestBody.setClientContext("clientContext-value");
updateRecordingStatusPostRequestBody.setStatus(RecordingStatus.NotRecording);
var result = graphClient.communications().calls().byCallId("{call-id}").updateRecordingStatus().post(updateRecordingStatusPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const updateRecordingStatusOperation = {
  clientContext: 'clientContext-value',
  status: 'notRecording | recording | failed'
};

await client.api('/communications/calls/{id}/updateRecordingStatus')
	.post(updateRecordingStatusOperation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\Calls\Item\UpdateRecordingStatus\UpdateRecordingStatusPostRequestBody;
use Microsoft\Graph\Generated\Models\RecordingStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpdateRecordingStatusPostRequestBody();
$requestBody->setClientContext('clientContext-value');
$requestBody->setStatus(new RecordingStatus('notRecording | recording | failed'));

$result = $graphServiceClient->communications()->calls()->byCallId('call-id')->updateRecordingStatus()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	clientContext = "clientContext-value"
	status = "notRecording | recording | failed"
}

Update-MgCommunicationCallRecordingStatus -CallId $callId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.calls.item.update_recording_status.update_recording_status_post_request_body import UpdateRecordingStatusPostRequestBody
from msgraph.generated.models.recording_status import RecordingStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpdateRecordingStatusPostRequestBody(
	client_context = "clientContext-value",
	status = RecordingStatus.NotRecording | RecordingStatus.Recording | RecordingStatus.Failed,
)

result = await graph_client.communications.calls.by_call_id('call-id').update_recording_status.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Location: https://graph.microsoft.com/v1.0/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896/operations/0fe0623f-d628-42ed-b4bd-8ac290072cc5

{
  "@odata.type": "#microsoft.graph.updateRecordingStatusOperation",
  "clientContext": "clientContext-value",
  "id": "0fe0623f-d628-42ed-b4bd-8ac290072cc5",
  "resultInfo": null,
  "status": "completed"
}
```
