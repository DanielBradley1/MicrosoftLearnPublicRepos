<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualevent-post-presenters?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Create virtualEventPresenter

Namespace: microsoft.graph

Create a new [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) object on a virtual event.

Currently, the following types of virtual events are supported:

- [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0)
- [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | VirtualEvent.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /solutions/virtualEvents/townhalls/{townhallId}/presenters
POST /solutions/virtualEvents/webinars/{webinarId}/presenters
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) object.

You can specify the following properties when you create a presenter on a **virtualEventTownhall**:

| Property | Type | Description |
| :--- | :--- | :--- |
| identity | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Identity information of the presenter. The following are the supported identities: [communicationsGuestIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsguestidentity?view=graph-rest-1.0) and [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0). |

You can specify the following properties when you create a presenter on a **virtualEventWebinar**:

| Property | Type | Description |
| :--- | :--- | :--- |
| identity | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Identity information of the presenter. The following are the supported identities: [communicationsGuestIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsguestidentity?view=graph-rest-1.0) and [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0). |
| presenterDetails | [virtualEventPresenterDetails](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenterdetails?view=graph-rest-1.0) | Other details about the presenter. |

## Response

If successful, this method returns a `201 Created` response code and a [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create an in-tenant presenter on a **virtualEventWebinar**

The following example shows how to create an internal user as a presenter on a **virtualEventWebinar**.

#### Request

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
POST https://graph.microsoft.com/v1.0/solutions/virtualEvents/webinars/6b48b5dd-e3a0-428c-b7ad-90896b87a047@09a21d49-f0f3-4b3f-96b6-f381e9430742/presenters
Content-Type: application/json

{
  "identity": {
    "@odata.type": "#microsoft.graph.communicationsUserIdentity",
    "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new VirtualEventPresenter
{
	Identity = new CommunicationsUserIdentity
	{
		OdataType = "#microsoft.graph.communicationsUserIdentity",
		Id = "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Webinars["{virtualEventWebinar-id}"].Presenters.PostAsync(requestBody);
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

requestBody := graphmodels.NewVirtualEventPresenter()
identity := graphmodels.NewCommunicationsUserIdentity()
id := "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b"
identity.SetId(&id) 
requestBody.SetIdentity(identity)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
presenters, err := graphClient.Solutions().VirtualEvents().Webinars().ByVirtualEventWebinarId("virtualEventWebinar-id").Presenters().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VirtualEventPresenter virtualEventPresenter = new VirtualEventPresenter();
CommunicationsUserIdentity identity = new CommunicationsUserIdentity();
identity.setOdataType("#microsoft.graph.communicationsUserIdentity");
identity.setId("7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b");
virtualEventPresenter.setIdentity(identity);
VirtualEventPresenter result = graphClient.solutions().virtualEvents().webinars().byVirtualEventWebinarId("{virtualEventWebinar-id}").presenters().post(virtualEventPresenter);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualEventPresenter = {
  identity: {
    '@odata.type': '#microsoft.graph.communicationsUserIdentity',
    id: '7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b'
  }
};

await client.api('/solutions/virtualEvents/webinars/6b48b5dd-e3a0-428c-b7ad-90896b87a047@09a21d49-f0f3-4b3f-96b6-f381e9430742/presenters')
	.post(virtualEventPresenter);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\VirtualEventPresenter;
use Microsoft\Graph\Generated\Models\CommunicationsUserIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VirtualEventPresenter();
$identity = new CommunicationsUserIdentity();
$identity->setOdataType('#microsoft.graph.communicationsUserIdentity');
$identity->setId('7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b');
$requestBody->setIdentity($identity);

$result = $graphServiceClient->solutions()->virtualEvents()->webinars()->byVirtualEventWebinarId('virtualEventWebinar-id')->presenters()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	identity = @{
		"@odata.type" = "#microsoft.graph.communicationsUserIdentity"
		id = "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b"
	}
}

New-MgVirtualEventWebinarPresenter -VirtualEventWebinarId $virtualEventWebinarId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.virtual_event_presenter import VirtualEventPresenter
from msgraph.generated.models.communications_user_identity import CommunicationsUserIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VirtualEventPresenter(
	identity = CommunicationsUserIdentity(
		odata_type = "#microsoft.graph.communicationsUserIdentity",
		id = "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
	),
)

result = await graph_client.solutions.virtual_events.webinars.by_virtual_event_webinar_id('virtualEventWebinar-id').presenters.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
  "email": "kenneth.brown@contoso.com",
  "identity": {
    "@odata.type": "#microsoft.graph.communicationsUserIdentity",
    "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
    "displayName": "Kennth Brown",
    "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
  },
  "presenterDetails": null
}
```

### Example 2: Create an out-of-tenant presenter on a **virtualEventWebinar**

The following example shows how to create a guest user as a presenter on a **virtualEventWebinar**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/solutions/virtualEvents/webinars/6b48b5dd-e3a0-428c-b7ad-90896b87a047@09a21d49-f0f3-4b3f-96b6-f381e9430742/presenters
Content-Type: application/json

{
  "identity": {
    "@odata.type": "#microsoft.graph.communicationsGuestIdentity",
    "displayName": "Guest Speaker",
    "email": "guest.speaker@fabrikam.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new VirtualEventPresenter
{
	Identity = new CommunicationsGuestIdentity
	{
		OdataType = "#microsoft.graph.communicationsGuestIdentity",
		DisplayName = "Guest Speaker",
		Email = "guest.speaker@fabrikam.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Webinars["{virtualEventWebinar-id}"].Presenters.PostAsync(requestBody);
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

requestBody := graphmodels.NewVirtualEventPresenter()
identity := graphmodels.NewCommunicationsGuestIdentity()
displayName := "Guest Speaker"
identity.SetDisplayName(&displayName) 
email := "guest.speaker@fabrikam.com"
identity.SetEmail(&email) 
requestBody.SetIdentity(identity)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
presenters, err := graphClient.Solutions().VirtualEvents().Webinars().ByVirtualEventWebinarId("virtualEventWebinar-id").Presenters().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VirtualEventPresenter virtualEventPresenter = new VirtualEventPresenter();
CommunicationsGuestIdentity identity = new CommunicationsGuestIdentity();
identity.setOdataType("#microsoft.graph.communicationsGuestIdentity");
identity.setDisplayName("Guest Speaker");
identity.setEmail("guest.speaker@fabrikam.com");
virtualEventPresenter.setIdentity(identity);
VirtualEventPresenter result = graphClient.solutions().virtualEvents().webinars().byVirtualEventWebinarId("{virtualEventWebinar-id}").presenters().post(virtualEventPresenter);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualEventPresenter = {
  identity: {
    '@odata.type': '#microsoft.graph.communicationsGuestIdentity',
    displayName: 'Guest Speaker',
    email: 'guest.speaker@fabrikam.com'
  }
};

await client.api('/solutions/virtualEvents/webinars/6b48b5dd-e3a0-428c-b7ad-90896b87a047@09a21d49-f0f3-4b3f-96b6-f381e9430742/presenters')
	.post(virtualEventPresenter);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\VirtualEventPresenter;
use Microsoft\Graph\Generated\Models\CommunicationsGuestIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VirtualEventPresenter();
$identity = new CommunicationsGuestIdentity();
$identity->setOdataType('#microsoft.graph.communicationsGuestIdentity');
$identity->setDisplayName('Guest Speaker');
$identity->setEmail('guest.speaker@fabrikam.com');
$requestBody->setIdentity($identity);

$result = $graphServiceClient->solutions()->virtualEvents()->webinars()->byVirtualEventWebinarId('virtualEventWebinar-id')->presenters()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	identity = @{
		"@odata.type" = "#microsoft.graph.communicationsGuestIdentity"
		displayName = "Guest Speaker"
		email = "guest.speaker@fabrikam.com"
	}
}

New-MgVirtualEventWebinarPresenter -VirtualEventWebinarId $virtualEventWebinarId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.virtual_event_presenter import VirtualEventPresenter
from msgraph.generated.models.communications_guest_identity import CommunicationsGuestIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VirtualEventPresenter(
	identity = CommunicationsGuestIdentity(
		odata_type = "#microsoft.graph.communicationsGuestIdentity",
		display_name = "Guest Speaker",
		email = "guest.speaker@fabrikam.com",
	),
)

result = await graph_client.solutions.virtual_events.webinars.by_virtual_event_webinar_id('virtualEventWebinar-id').presenters.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "184975c0-4096-4a02-b251-c48546691c42",
  "email": "guest.speaker@fabrikam.com",
  "presenterDetails": null,
  "identity": {
    "@odata.type": "#microsoft.graph.communicationsGuestIdentity",
    "id": "184975c0-4096-4a02-b251-c48546691c42",
    "displayName": "Guest Speaker",
    "email": "guest.speaker@fabrikam.com"
  }
}
```

### Example 3: Create an in-tenant presenter on a **virtualEventTownhall**

The following example shows how to create an internal user as a presenter on a **virtualEventTownhall**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/solutions/virtualEvents/townhalls/502dadea-b5d8-44aa-a851-a0ac496a36bf@09a21d49-f0f3-4b3f-96b6-f381e9430742/presenters
Content-Type: application/json

{
  "identity": {
    "@odata.type": "#microsoft.graph.communicationsUserIdentity",
    "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new VirtualEventPresenter
{
	Identity = new CommunicationsUserIdentity
	{
		OdataType = "#microsoft.graph.communicationsUserIdentity",
		Id = "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Townhalls["{virtualEventTownhall-id}"].Presenters.PostAsync(requestBody);
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

requestBody := graphmodels.NewVirtualEventPresenter()
identity := graphmodels.NewCommunicationsUserIdentity()
id := "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b"
identity.SetId(&id) 
requestBody.SetIdentity(identity)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
presenters, err := graphClient.Solutions().VirtualEvents().Townhalls().ByVirtualEventTownhallId("virtualEventTownhall-id").Presenters().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VirtualEventPresenter virtualEventPresenter = new VirtualEventPresenter();
CommunicationsUserIdentity identity = new CommunicationsUserIdentity();
identity.setOdataType("#microsoft.graph.communicationsUserIdentity");
identity.setId("7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b");
virtualEventPresenter.setIdentity(identity);
VirtualEventPresenter result = graphClient.solutions().virtualEvents().townhalls().byVirtualEventTownhallId("{virtualEventTownhall-id}").presenters().post(virtualEventPresenter);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualEventPresenter = {
  identity: {
    '@odata.type': '#microsoft.graph.communicationsUserIdentity',
    id: '7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b'
  }
};

await client.api('/solutions/virtualEvents/townhalls/502dadea-b5d8-44aa-a851-a0ac496a36bf@09a21d49-f0f3-4b3f-96b6-f381e9430742/presenters')
	.post(virtualEventPresenter);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\VirtualEventPresenter;
use Microsoft\Graph\Generated\Models\CommunicationsUserIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VirtualEventPresenter();
$identity = new CommunicationsUserIdentity();
$identity->setOdataType('#microsoft.graph.communicationsUserIdentity');
$identity->setId('7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b');
$requestBody->setIdentity($identity);

$result = $graphServiceClient->solutions()->virtualEvents()->townhalls()->byVirtualEventTownhallId('virtualEventTownhall-id')->presenters()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	identity = @{
		"@odata.type" = "#microsoft.graph.communicationsUserIdentity"
		id = "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b"
	}
}

New-MgVirtualEventTownhallPresenter -VirtualEventTownhallId $virtualEventTownhallId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.virtual_event_presenter import VirtualEventPresenter
from msgraph.generated.models.communications_user_identity import CommunicationsUserIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VirtualEventPresenter(
	identity = CommunicationsUserIdentity(
		odata_type = "#microsoft.graph.communicationsUserIdentity",
		id = "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
	),
)

result = await graph_client.solutions.virtual_events.townhalls.by_virtual_event_townhall_id('virtualEventTownhall-id').presenters.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
  "email": "kenneth.brown@contoso.com",
  "identity": {
    "@odata.type": "#microsoft.graph.communicationsUserIdentity",
    "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
    "displayName": "Kennth Brown",
    "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
  },
  "presenterDetails": null
}
```

### Example 4: Create an out-of-tenant presenter on a **virtualEventTownhall**

The following example shows how to create a guest user as a presenter on a **virtualEventTownhall**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/solutions/virtualEvents/townhalls/502dadea-b5d8-44aa-a851-a0ac496a36bf@09a21d49-f0f3-4b3f-96b6-f381e9430742/presenters
Content-Type: application/json

{
  "identity": {
    "@odata.type": "#microsoft.graph.communicationsGuestIdentity",
    "displayName": "Guest Speaker",
    "email": "guest.speaker@fabrikam.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new VirtualEventPresenter
{
	Identity = new CommunicationsGuestIdentity
	{
		OdataType = "#microsoft.graph.communicationsGuestIdentity",
		DisplayName = "Guest Speaker",
		Email = "guest.speaker@fabrikam.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Townhalls["{virtualEventTownhall-id}"].Presenters.PostAsync(requestBody);
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

requestBody := graphmodels.NewVirtualEventPresenter()
identity := graphmodels.NewCommunicationsGuestIdentity()
displayName := "Guest Speaker"
identity.SetDisplayName(&displayName) 
email := "guest.speaker@fabrikam.com"
identity.SetEmail(&email) 
requestBody.SetIdentity(identity)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
presenters, err := graphClient.Solutions().VirtualEvents().Townhalls().ByVirtualEventTownhallId("virtualEventTownhall-id").Presenters().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VirtualEventPresenter virtualEventPresenter = new VirtualEventPresenter();
CommunicationsGuestIdentity identity = new CommunicationsGuestIdentity();
identity.setOdataType("#microsoft.graph.communicationsGuestIdentity");
identity.setDisplayName("Guest Speaker");
identity.setEmail("guest.speaker@fabrikam.com");
virtualEventPresenter.setIdentity(identity);
VirtualEventPresenter result = graphClient.solutions().virtualEvents().townhalls().byVirtualEventTownhallId("{virtualEventTownhall-id}").presenters().post(virtualEventPresenter);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualEventPresenter = {
  identity: {
    '@odata.type': '#microsoft.graph.communicationsGuestIdentity',
    displayName: 'Guest Speaker',
    email: 'guest.speaker@fabrikam.com'
  }
};

await client.api('/solutions/virtualEvents/townhalls/502dadea-b5d8-44aa-a851-a0ac496a36bf@09a21d49-f0f3-4b3f-96b6-f381e9430742/presenters')
	.post(virtualEventPresenter);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\VirtualEventPresenter;
use Microsoft\Graph\Generated\Models\CommunicationsGuestIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VirtualEventPresenter();
$identity = new CommunicationsGuestIdentity();
$identity->setOdataType('#microsoft.graph.communicationsGuestIdentity');
$identity->setDisplayName('Guest Speaker');
$identity->setEmail('guest.speaker@fabrikam.com');
$requestBody->setIdentity($identity);

$result = $graphServiceClient->solutions()->virtualEvents()->townhalls()->byVirtualEventTownhallId('virtualEventTownhall-id')->presenters()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	identity = @{
		"@odata.type" = "#microsoft.graph.communicationsGuestIdentity"
		displayName = "Guest Speaker"
		email = "guest.speaker@fabrikam.com"
	}
}

New-MgVirtualEventTownhallPresenter -VirtualEventTownhallId $virtualEventTownhallId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.virtual_event_presenter import VirtualEventPresenter
from msgraph.generated.models.communications_guest_identity import CommunicationsGuestIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VirtualEventPresenter(
	identity = CommunicationsGuestIdentity(
		odata_type = "#microsoft.graph.communicationsGuestIdentity",
		display_name = "Guest Speaker",
		email = "guest.speaker@fabrikam.com",
	),
)

result = await graph_client.solutions.virtual_events.townhalls.by_virtual_event_townhall_id('virtualEventTownhall-id').presenters.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "184975c0-4096-4a02-b251-c48546691c42",
  "email": "guest.speaker@fabrikam.com",
  "presenterDetails": null,
  "identity": {
    "@odata.type": "#microsoft.graph.communicationsGuestIdentity",
    "id": "184975c0-4096-4a02-b251-c48546691c42",
    "displayName": "Guest Speaker",
    "email": "guest.speaker@fabrikam.com"
  }
}
```
