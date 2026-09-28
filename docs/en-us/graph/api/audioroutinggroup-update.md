<!-- Source: https://learn.microsoft.com/en-us/graph/api/audioroutinggroup-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Update audioRoutingGroup

Namespace: microsoft.graph

Modify sources and receivers of an [audioRoutingGroup](https://learn.microsoft.com/en-us/graph/api/resources/audioroutinggroup?view=graph-rest-1.0).

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
| Application | Calls.JoinGroupCall.All | Calls.InitiateGroupCall.All |

## HTTP request

```http
PATCH /app/calls/{id}/audioRoutingGroups/{id}
PATCH /communications/calls/{id}/audioRoutingGroups/{id}
```

> **Note:** The `/app` path is deprecated. Going forward, use the `/communications` path.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| receivers | String collection | The target participants in the audioRoutingGroup. |
| routingMode | String | The possible values are: `oneToOne`, `multicast`. |
| sources | String collection | The source participant in the audioRoutingGroup. |

## Response

If successful, this method returns a `200 OK` response code and an updated [audioRoutingGroup](https://learn.microsoft.com/en-us/graph/api/resources/audioroutinggroup?view=graph-rest-1.0) object in the response body.

## Example

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
PATCH https://graph.microsoft.com/v1.0/communications/calls/{id}/audioRoutingGroups/{id}
Content-Type: application/json

{
  "id": "oneToOne",
  "routingMode": "oneToOne",
  "sources": [
    "632899f8-2ea1-4604-8413-27bd2892079f"
  ],
  "receivers": [
    "550fae72-d251-43ec-868c-373732c2704f",
    "72f988bf-86f1-41af-91ab-2d7cd011db47"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AudioRoutingGroup
{
	Id = "oneToOne",
	RoutingMode = RoutingMode.OneToOne,
	Sources = new List<string>
	{
		"632899f8-2ea1-4604-8413-27bd2892079f",
	},
	Receivers = new List<string>
	{
		"550fae72-d251-43ec-868c-373732c2704f",
		"72f988bf-86f1-41af-91ab-2d7cd011db47",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls["{call-id}"].AudioRoutingGroups["{audioRoutingGroup-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAudioRoutingGroup()
id := "oneToOne"
requestBody.SetId(&id) 
routingMode := graphmodels.ONETOONE_ROUTINGMODE 
requestBody.SetRoutingMode(&routingMode) 
sources := []string {
	"632899f8-2ea1-4604-8413-27bd2892079f",
}
requestBody.SetSources(sources)
receivers := []string {
	"550fae72-d251-43ec-868c-373732c2704f",
	"72f988bf-86f1-41af-91ab-2d7cd011db47",
}
requestBody.SetReceivers(receivers)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
audioRoutingGroups, err := graphClient.Communications().Calls().ByCallId("call-id").AudioRoutingGroups().ByAudioRoutingGroupId("audioRoutingGroup-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AudioRoutingGroup audioRoutingGroup = new AudioRoutingGroup();
audioRoutingGroup.setId("oneToOne");
audioRoutingGroup.setRoutingMode(RoutingMode.OneToOne);
LinkedList<String> sources = new LinkedList<String>();
sources.add("632899f8-2ea1-4604-8413-27bd2892079f");
audioRoutingGroup.setSources(sources);
LinkedList<String> receivers = new LinkedList<String>();
receivers.add("550fae72-d251-43ec-868c-373732c2704f");
receivers.add("72f988bf-86f1-41af-91ab-2d7cd011db47");
audioRoutingGroup.setReceivers(receivers);
AudioRoutingGroup result = graphClient.communications().calls().byCallId("{call-id}").audioRoutingGroups().byAudioRoutingGroupId("{audioRoutingGroup-id}").patch(audioRoutingGroup);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const audioRoutingGroup = {
  id: 'oneToOne',
  routingMode: 'oneToOne',
  sources: [
    '632899f8-2ea1-4604-8413-27bd2892079f'
  ],
  receivers: [
    '550fae72-d251-43ec-868c-373732c2704f',
    '72f988bf-86f1-41af-91ab-2d7cd011db47'
  ]
};

await client.api('/communications/calls/{id}/audioRoutingGroups/{id}')
	.update(audioRoutingGroup);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AudioRoutingGroup;
use Microsoft\Graph\Generated\Models\RoutingMode;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AudioRoutingGroup();
$requestBody->setId('oneToOne');
$requestBody->setRoutingMode(new RoutingMode('oneToOne'));
$requestBody->setSources(['632899f8-2ea1-4604-8413-27bd2892079f', 	]);
$requestBody->setReceivers(['550fae72-d251-43ec-868c-373732c2704f', '72f988bf-86f1-41af-91ab-2d7cd011db47', 	]);

$result = $graphServiceClient->communications()->calls()->byCallId('call-id')->audioRoutingGroups()->byAudioRoutingGroupId('audioRoutingGroup-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	id = "oneToOne"
	routingMode = "oneToOne"
	sources = @(
	"632899f8-2ea1-4604-8413-27bd2892079f"
)
receivers = @(
"550fae72-d251-43ec-868c-373732c2704f"
"72f988bf-86f1-41af-91ab-2d7cd011db47"
)
}

Update-MgCommunicationCallAudioRoutingGroup -CallId $callId -AudioRoutingGroupId $audioRoutingGroupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.audio_routing_group import AudioRoutingGroup
from msgraph.generated.models.routing_mode import RoutingMode
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AudioRoutingGroup(
	id = "oneToOne",
	routing_mode = RoutingMode.OneToOne,
	sources = [
		"632899f8-2ea1-4604-8413-27bd2892079f",
	],
	receivers = [
		"550fae72-d251-43ec-868c-373732c2704f",
		"72f988bf-86f1-41af-91ab-2d7cd011db47",
	],
)

result = await graph_client.communications.calls.by_call_id('call-id').audio_routing_groups.by_audio_routing_group_id('audioRoutingGroup-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "oneToOne",
  "routingMode": "oneToOne",
  "sources": [
    "632899f8-2ea1-4604-8413-27bd2892079f"
  ],
  "receivers": [
    "550fae72-d251-43ec-868c-373732c2704f",
    "72f988bf-86f1-41af-91ab-2d7cd011db47"
  ]
}
```
