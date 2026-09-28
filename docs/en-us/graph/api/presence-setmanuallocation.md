<!-- Source: https://learn.microsoft.com/en-us/graph/api/presence-setmanuallocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# presence: setManualLocation

Namespace: microsoft.graph

Set the manual work location signal for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). The explicit value chosen by a user or an authorized client overrides any automatically detected or scheduled working hours and location.

- Precedence: manual > automatic > scheduled
- Precision \(within the same layer\): more precise wins \(for example, office + building > office\)
- If a manual location is set, it overrides both automatic and scheduled settings.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Presence.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/presence/setManualLocation
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| placeId | String | Identifier of the place, if applicable. |
| workLocationType | workLocationType | Semantic type of the location. Supports a subset of the values for **workLocationType**. The possible values are: `office`, `remote`, `timeOff`. |

## Response

If successful, this action returns a `200 OK` response code.

## Examples

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
POST https://graph.microsoft.com/v1.0/me/presence/setManualLocation
Content-Type: application/json

{
  "workLocationType": "office",
  "placeId": "eb706f15-137e-4722-b4d1-b601481d9251"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.Presence.SetManualLocation;
using Microsoft.Graph.Models;

var requestBody = new SetManualLocationPostRequestBody
{
	WorkLocationType = WorkLocationType.Office,
	PlaceId = "eb706f15-137e-4722-b4d1-b601481d9251",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Me.Presence.SetManualLocation.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewItemSetManualLocationPostRequestBody()
workLocationType := graphmodels.OFFICE_WORKLOCATIONTYPE 
requestBody.SetWorkLocationType(&workLocationType) 
placeId := "eb706f15-137e-4722-b4d1-b601481d9251"
requestBody.SetPlaceId(&placeId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Me().Presence().SetManualLocation().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.presence.setmanuallocation.SetManualLocationPostRequestBody setManualLocationPostRequestBody = new com.microsoft.graph.users.item.presence.setmanuallocation.SetManualLocationPostRequestBody();
setManualLocationPostRequestBody.setWorkLocationType(WorkLocationType.Office);
setManualLocationPostRequestBody.setPlaceId("eb706f15-137e-4722-b4d1-b601481d9251");
graphClient.me().presence().setManualLocation().post(setManualLocationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const setManualLocation = {
  workLocationType: 'office',
  placeId: 'eb706f15-137e-4722-b4d1-b601481d9251'
};

await client.api('/me/presence/setManualLocation')
	.post(setManualLocation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Presence\SetManualLocation\SetManualLocationPostRequestBody;
use Microsoft\Graph\Generated\Models\WorkLocationType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SetManualLocationPostRequestBody();
$requestBody->setWorkLocationType(new WorkLocationType('office'));
$requestBody->setPlaceId('eb706f15-137e-4722-b4d1-b601481d9251');

$graphServiceClient->me()->presence()->setManualLocation()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	workLocationType = "office"
	placeId = "eb706f15-137e-4722-b4d1-b601481d9251"
}

# A UPN can also be used as -UserId.
Set-MgUserPresenceManualLocation -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.presence.set_manual_location.set_manual_location_post_request_body import SetManualLocationPostRequestBody
from msgraph.generated.models.work_location_type import WorkLocationType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SetManualLocationPostRequestBody(
	work_location_type = WorkLocationType.Office,
	place_id = "eb706f15-137e-4722-b4d1-b601481d9251",
)

await graph_client.me.presence.set_manual_location.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```
