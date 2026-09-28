<!-- Source: https://learn.microsoft.com/en-us/graph/api/place-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create place

Namespace: microsoft.graph

Create a new [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) object.

You can also use this method to create the following child object types: [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0), [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0), [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0), [room](https://learn.microsoft.com/en-us/graph/api/resources/room?view=graph-rest-1.0), [workspace](https://learn.microsoft.com/en-us/graph/api/resources/workspace?view=graph-rest-1.0), or [desk](https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Place.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Place.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Exchange Administrator* is the least privileged role supported for this operation.

When using application permissions, you must configure the required `TenantPlacesManagement` role \(to manage Places\) and the `MailRecipient` role \(to manage users and mailboxes\). For more information on how to configure these roles, see [Role Based Access Control for Applications in Exchange Online](https://learn.microsoft.com/en-us/exchange/permissions-exo/application-rbac).

## HTTP request

```http
POST /places
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) object.

For a list of all properties that are available when you create a **place** object, see the [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) resource.

## Response

If successful, this method returns a `201 Created` response code and a [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a building

The following example shows how to create a new **building** object.

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
POST https://graph.microsoft.com/v1.0/places
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.building",
  "displayName": "B001"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Building
{
	OdataType = "microsoft.graph.building",
	DisplayName = "B001",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places.PostAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
displayName := "B001"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Building place = new Building();
place.setOdataType("microsoft.graph.building");
place.setDisplayName("B001");
Place result = graphClient.places().post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.building',
  displayName: 'B001'
};

await client.api('/places')
	.post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Building;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Building();
$requestBody->setOdataType('microsoft.graph.building');
$requestBody->setDisplayName('B001');

$result = $graphServiceClient->places()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.building"
	displayName = "B001"
}

New-MgPlace -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.building import Building
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Building(
	odata_type = "microsoft.graph.building",
	display_name = "B001",
)

result = await graph_client.places.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.building",
  "id": "767a31a7-6987-41c9-b829-ab351b8aab53",
  "placeId": "767a31a7-6987-41c9-b829-ab351b8aab53",
  "displayName": "B001"
}
```

### Example 2: Create a floor

The following example shows how to create a new **floor** object.

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
POST https://graph.microsoft.com/v1.0/places
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.floor",
  "displayName": "F1",
  "parentId": "767a31a7-6987-41c9-b829-ab351b8aab53"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Floor
{
	OdataType = "microsoft.graph.floor",
	DisplayName = "F1",
	ParentId = "767a31a7-6987-41c9-b829-ab351b8aab53",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places.PostAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
displayName := "F1"
requestBody.SetDisplayName(&displayName) 
parentId := "767a31a7-6987-41c9-b829-ab351b8aab53"
requestBody.SetParentId(&parentId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Floor place = new Floor();
place.setOdataType("microsoft.graph.floor");
place.setDisplayName("F1");
place.setParentId("767a31a7-6987-41c9-b829-ab351b8aab53");
Place result = graphClient.places().post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.floor',
  displayName: 'F1',
  parentId: '767a31a7-6987-41c9-b829-ab351b8aab53'
};

await client.api('/places')
	.post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Floor;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Floor();
$requestBody->setOdataType('microsoft.graph.floor');
$requestBody->setDisplayName('F1');
$requestBody->setParentId('767a31a7-6987-41c9-b829-ab351b8aab53');

$result = $graphServiceClient->places()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.floor"
	displayName = "F1"
	parentId = "767a31a7-6987-41c9-b829-ab351b8aab53"
}

New-MgPlace -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.floor import Floor
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Floor(
	odata_type = "microsoft.graph.floor",
	display_name = "F1",
	parent_id = "767a31a7-6987-41c9-b829-ab351b8aab53",
)

result = await graph_client.places.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.floor",
  "id": "46ef7aed-5d94-4fd4-ae03-b333bc7a6955",
  "placeId": "46ef7aed-5d94-4fd4-ae03-b333bc7a6955",
  "displayName": "F1",
  "parentId": "767a31a7-6987-41c9-b829-ab351b8aab53",
  "tags": [],
  "isWheelChairAccessible": false
}
```

### Example 3: Create a section

The following example shows how to create a new **section** object.

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
POST https://graph.microsoft.com/v1.0/places
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.section",
  "displayName": "S1",
  "parentId": "46ef7aed-5d94-4fd4-ae03-b333bc7a6955"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Section
{
	OdataType = "microsoft.graph.section",
	DisplayName = "S1",
	ParentId = "46ef7aed-5d94-4fd4-ae03-b333bc7a6955",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places.PostAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
displayName := "S1"
requestBody.SetDisplayName(&displayName) 
parentId := "46ef7aed-5d94-4fd4-ae03-b333bc7a6955"
requestBody.SetParentId(&parentId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Section place = new Section();
place.setOdataType("microsoft.graph.section");
place.setDisplayName("S1");
place.setParentId("46ef7aed-5d94-4fd4-ae03-b333bc7a6955");
Place result = graphClient.places().post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.section',
  displayName: 'S1',
  parentId: '46ef7aed-5d94-4fd4-ae03-b333bc7a6955'
};

await client.api('/places')
	.post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Section;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Section();
$requestBody->setOdataType('microsoft.graph.section');
$requestBody->setDisplayName('S1');
$requestBody->setParentId('46ef7aed-5d94-4fd4-ae03-b333bc7a6955');

$result = $graphServiceClient->places()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.section"
	displayName = "S1"
	parentId = "46ef7aed-5d94-4fd4-ae03-b333bc7a6955"
}

New-MgPlace -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.section import Section
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Section(
	odata_type = "microsoft.graph.section",
	display_name = "S1",
	parent_id = "46ef7aed-5d94-4fd4-ae03-b333bc7a6955",
)

result = await graph_client.places.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.section",
  "id": "1ad0f725-6885-49c5-9a47-3b22a1f9409d",
  "placeId": "1ad0f725-6885-49c5-9a47-3b22a1f9409d",
  "displayName": "S1",
  "parentId": "46ef7aed-5d94-4fd4-ae03-b333bc7a6955",
  "tags": [],
  "isWheelChairAccessible": false
}
```

### Example 4: Create a desk

The following example shows how to create a new **desk** object.

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
POST https://graph.microsoft.com/v1.0/places
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.desk",
  "displayName": "D1",
  "parentId": "1ad0f725-6885-49c5-9a47-3b22a1f9409d"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Desk
{
	OdataType = "microsoft.graph.desk",
	DisplayName = "D1",
	ParentId = "1ad0f725-6885-49c5-9a47-3b22a1f9409d",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places.PostAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
displayName := "D1"
requestBody.SetDisplayName(&displayName) 
parentId := "1ad0f725-6885-49c5-9a47-3b22a1f9409d"
requestBody.SetParentId(&parentId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Desk place = new Desk();
place.setOdataType("microsoft.graph.desk");
place.setDisplayName("D1");
place.setParentId("1ad0f725-6885-49c5-9a47-3b22a1f9409d");
Place result = graphClient.places().post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.desk',
  displayName: 'D1',
  parentId: '1ad0f725-6885-49c5-9a47-3b22a1f9409d'
};

await client.api('/places')
	.post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Desk;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Desk();
$requestBody->setOdataType('microsoft.graph.desk');
$requestBody->setDisplayName('D1');
$requestBody->setParentId('1ad0f725-6885-49c5-9a47-3b22a1f9409d');

$result = $graphServiceClient->places()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.desk"
	displayName = "D1"
	parentId = "1ad0f725-6885-49c5-9a47-3b22a1f9409d"
}

New-MgPlace -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.desk import Desk
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Desk(
	odata_type = "microsoft.graph.desk",
	display_name = "D1",
	parent_id = "1ad0f725-6885-49c5-9a47-3b22a1f9409d",
)

result = await graph_client.places.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.desk",
  "id": "fc25d4dc-817a-45bc-a72d-2616cd7566ac",
  "placeId": "fc25d4dc-817a-45bc-a72d-2616cd7566ac",
  "displayName": "D1",
  "parentId": "1ad0f725-6885-49c5-9a47-3b22a1f9409d",
  "tags": [],
  "isWheelChairAccessible": false,
  "mode": { "@odata.type": "#microsoft.graph.dropInPlaceMode" }
}
```

### Example 5: Create a room

The following example shows how to create a new **room** object.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/places
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.room",
  "displayName": "Conf Room 4/3.3G11",
  "parentId": "46ef7aed-5d94-4fd4-ae03-b333bc7a6955",
  "bookingType": "standard"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Room
{
	OdataType = "microsoft.graph.room",
	DisplayName = "Conf Room 4/3.3G11",
	ParentId = "46ef7aed-5d94-4fd4-ae03-b333bc7a6955",
	BookingType = BookingType.Standard,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places.PostAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
displayName := "Conf Room 4/3.3G11"
requestBody.SetDisplayName(&displayName) 
parentId := "46ef7aed-5d94-4fd4-ae03-b333bc7a6955"
requestBody.SetParentId(&parentId) 
bookingType := graphmodels.STANDARD_BOOKINGTYPE 
requestBody.SetBookingType(&bookingType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Room place = new Room();
place.setOdataType("microsoft.graph.room");
place.setDisplayName("Conf Room 4/3.3G11");
place.setParentId("46ef7aed-5d94-4fd4-ae03-b333bc7a6955");
place.setBookingType(BookingType.Standard);
Place result = graphClient.places().post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.room',
  displayName: 'Conf Room 4/3.3G11',
  parentId: '46ef7aed-5d94-4fd4-ae03-b333bc7a6955',
  bookingType: 'standard'
};

await client.api('/places')
	.post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Room;
use Microsoft\Graph\Generated\Models\BookingType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Room();
$requestBody->setOdataType('microsoft.graph.room');
$requestBody->setDisplayName('Conf Room 4/3.3G11');
$requestBody->setParentId('46ef7aed-5d94-4fd4-ae03-b333bc7a6955');
$requestBody->setBookingType(new BookingType('standard'));

$result = $graphServiceClient->places()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.room"
	displayName = "Conf Room 4/3.3G11"
	parentId = "46ef7aed-5d94-4fd4-ae03-b333bc7a6955"
	bookingType = "standard"
}

New-MgPlace -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.room import Room
from msgraph.generated.models.booking_type import BookingType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Room(
	odata_type = "microsoft.graph.room",
	display_name = "Conf Room 4/3.3G11",
	parent_id = "46ef7aed-5d94-4fd4-ae03-b333bc7a6955",
	booking_type = BookingType.Standard,
)

result = await graph_client.places.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.room",
  "id": "0be387a4-d53b-410f-9daf-f4fa07e5b05a",
  "placeId": "4923e5a8-453e-4edf-b272-9c33757d4fb3",
  "displayName": "Conf Room 4/3.3G11",
  "parentId": "46ef7aed-5d94-4fd4-ae03-b333bc7a6955",
  "isWheelChairAccessible": false,
  "emailAddress": "confroom433G115497308f1755150217899@contoso.com",
  "bookingType": "standard"
}
```

### Example 6: Create a workspace

The following example shows how to create a new **workspace** object.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/v1.0/places
Content-Type: application/json

{
  "@odata.type": "microsoft.graph.workspace",
  "parentId": "f7de7265-e420-47b4-9d49-28d728716241",
  "displayName": "testSpace001",
  "tags": ["test"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Workspace
{
	OdataType = "microsoft.graph.workspace",
	ParentId = "f7de7265-e420-47b4-9d49-28d728716241",
	DisplayName = "testSpace001",
	Tags = new List<string>
	{
		"test",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places.PostAsync(requestBody);
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

requestBody := graphmodels.NewPlace()
parentId := "f7de7265-e420-47b4-9d49-28d728716241"
requestBody.SetParentId(&parentId) 
displayName := "testSpace001"
requestBody.SetDisplayName(&displayName) 
tags := []string {
	"test",
}
requestBody.SetTags(tags)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
places, err := graphClient.Places().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Workspace place = new Workspace();
place.setOdataType("microsoft.graph.workspace");
place.setParentId("f7de7265-e420-47b4-9d49-28d728716241");
place.setDisplayName("testSpace001");
LinkedList<String> tags = new LinkedList<String>();
tags.add("test");
place.setTags(tags);
Place result = graphClient.places().post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const place = {
  '@odata.type': 'microsoft.graph.workspace',
  parentId: 'f7de7265-e420-47b4-9d49-28d728716241',
  displayName: 'testSpace001',
  tags: ['test']
};

await client.api('/places')
	.post(place);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Workspace;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Workspace();
$requestBody->setOdataType('microsoft.graph.workspace');
$requestBody->setParentId('f7de7265-e420-47b4-9d49-28d728716241');
$requestBody->setDisplayName('testSpace001');
$requestBody->setTags(['test', 	]);

$result = $graphServiceClient->places()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "microsoft.graph.workspace"
	parentId = "f7de7265-e420-47b4-9d49-28d728716241"
	displayName = "testSpace001"
	tags = @(
	"test"
)
}

New-MgPlace -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.workspace import Workspace
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Workspace(
	odata_type = "microsoft.graph.workspace",
	parent_id = "f7de7265-e420-47b4-9d49-28d728716241",
	display_name = "testSpace001",
	tags = [
		"test",
	],
)

result = await graph_client.places.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note**: The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.workspace",
  "id": "49c2fcfb-163a-4e00-a42b-0615d6789e72",
  "placeId": "d90144aa-8cc4-4d49-97f2-9c365e38ed7e",
  "displayName": "testSpace001",
  "parentId": "f7de7265-e420-47b4-9d49-28d728716241",
  "tags": [
    "test"
  ],
  "emailAddress": "testSpace0015d9988631755150528582@contoso.com",
  "nickname": "testSpace001",
  "mode": { }
}
```
