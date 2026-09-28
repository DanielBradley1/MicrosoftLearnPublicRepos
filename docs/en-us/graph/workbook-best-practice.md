<!-- Source: https://learn.microsoft.com/en-us/graph/workbook-best-practice -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Best practices for working with the Excel API

This article provides recommendations for working with the [Excel APIs](https://learn.microsoft.com/en-us/graph/api/resources/excel) in Microsoft Graph.

## Manage sessions in the most efficient way

If you have more than one call to make within a certain period of time, we recommend that you create a session and pass the session ID with each request. To represent the session in the API, use the `workbook-session-id: {session-id}` header. By doing so, you can use the Excel APIs in the most efficient way.

The following example shows you how to add a new number to a table and then find one record in a workbook using this approach.

### Step 1: Create a session

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/drive/items/{id}/workbook/createSession
Content-type: application/json

{
  "persistChanges": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Drives.Item.Items.Item.Workbook.CreateSession;

var requestBody = new CreateSessionPostRequestBody
{
	PersistChanges = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Workbook.CreateSession.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdrives "github.com/microsoftgraph/msgraph-sdk-go/drives"
	  //other-imports
)

requestBody := graphdrives.NewCreateSessionPostRequestBody()
persistChanges := true
requestBody.SetPersistChanges(&persistChanges) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
createSession, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Workbook().CreateSession().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.drives.item.items.item.workbook.createsession.CreateSessionPostRequestBody createSessionPostRequestBody = new com.microsoft.graph.drives.item.items.item.workbook.createsession.CreateSessionPostRequestBody();
createSessionPostRequestBody.setPersistChanges(true);
var result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").workbook().createSession().post(createSessionPostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workbookSessionInfo = {
  persistChanges: true
};

await client.api('/me/drive/items/{id}/workbook/createSession')
	.post(workbookSessionInfo);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Workbook\CreateSession\CreateSessionPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateSessionPostRequestBody();
$requestBody->setPersistChanges(true);

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->workbook()->createSession()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.drives.item.items.item.workbook.create_session.create_session_post_request_body import CreateSessionPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateSessionPostRequestBody(
	persist_changes = True,
)

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').workbook.create_session.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

The following is a successful response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "id-value",
  "persistChanges": true
}
```

### Step 2: Add a new row to the table

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/me/drive/items/{id}/workbook/tables/{id|name}/rows/add
Content-type: application/json
workbook-session-id: {session-id}

{
  "values": [[“east”, “pear”, 4]]
}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workbookTableRow = {
  values: [[“east”, “pear”, 4]]
};

await client.api('/me/drive/items/{id}/workbook/tables/{id|name}/rows/add')
	.post(workbookTableRow);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "index": 6,
  "values": [[“east”, “pear”, 4]]
}
```

### Step 3: Look up a value in the updated table

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/me/drive/items/{id}/workbook/functions/vlookup
Content-type: application/json
workbook-session-id: {session-id}

{
    "lookupValue":"pear",
    "tableArray":{"Address":"Sheet1!B2:C7"},
    "colIndexNum":2,
    "rangeLookup":false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Drives.Item.Items.Item.Workbook.Functions.Vlookup;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new VlookupPostRequestBody
{
	LookupValue = new UntypedString("pear"),
	TableArray = new UntypedObject(new Dictionary<string, UntypedNode>
	{
		{
			"Address", new UntypedString("Sheet1!B2:C7")
		},
	}),
	ColIndexNum = new UntypedDouble(2),
	RangeLookup = new UntypedBoolean(false),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Workbook.Functions.Vlookup.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("workbook-session-id", "{session-id}");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdrives "github.com/microsoftgraph/msgraph-sdk-go/drives"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("workbook-session-id", "{session-id}")

configuration := &graphdrives.ItemItemsItemWorkbookFunctionsVlookupRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphdrives.NewVlookupPostRequestBody()
lookupValue := "pear"
requestBody.SetLookupValue(&lookupValue) 
tableArray := graph.NewUntypedNode()
address := "Sheet1!B2:C7"
tableArray.SetAddress(&address) 
requestBody.SetTableArray(tableArray)
colIndexNum := float64(2)
requestBody.SetColIndexNum(&colIndexNum) 
rangeLookup := false
requestBody.SetRangeLookup(&rangeLookup) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
vlookup, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Workbook().Functions().Vlookup().Post(context.Background(), requestBody, configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.drives.item.items.item.workbook.functions.vlookup.VlookupPostRequestBody vlookupPostRequestBody = new com.microsoft.graph.drives.item.items.item.workbook.functions.vlookup.VlookupPostRequestBody();
vlookupPostRequestBody.setLookupValue("pear");
UntypedNode tableArray = new UntypedNode();
tableArray.setAddress("Sheet1!B2:C7");
vlookupPostRequestBody.setTableArray(tableArray);
vlookupPostRequestBody.setColIndexNum(2d);
vlookupPostRequestBody.setRangeLookup(false);
var result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").workbook().functions().vlookup().post(vlookupPostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("workbook-session-id", "{session-id}");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workbookFunctionResult = {
    lookupValue: 'pear',
    tableArray: {Address: 'Sheet1!B2:C7'},
    colIndexNum: 2,
    rangeLookup: false
};

await client.api('/me/drive/items/{id}/workbook/functions/vlookup')
	.post(workbookFunctionResult);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Workbook\Functions\Vlookup\VlookupRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Workbook\Functions\Vlookup\VlookupPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VlookupPostRequestBody();
$requestBody->setLookupValue('pear');
$tableArray = new UntypedNode();
$tableArray->setAddress('Sheet1!B2:C7');
$requestBody->setTableArray($tableArray);
$requestBody->setColIndexNum(2);
$requestBody->setRangeLookup(false);
$requestConfiguration = new VlookupRequestBuilderPostRequestConfiguration();
$headers = [
		'workbook-session-id' => '{session-id}',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->workbook()->functions()->vlookup()->post($requestBody, $requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.drives.item.items.item.workbook.functions.vlookup.vlookup_request_builder import VlookupRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.drives.item.items.item.workbook.functions.vlookup.vlookup_post_request_body import VlookupPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VlookupPostRequestBody(
	lookup_value = "pear",
	table_array = UntypedNode(
		address = "Sheet1!B2:C7",
	),
	col_index_num = 2,
	range_lookup = False,
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("workbook-session-id", "{session-id}")


result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').workbook.functions.vlookup.post(request_body, request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP code: 200 OK
content-type: application/json

{
    "value": 5
}
```

### Step 4: Close the session after all the requests are completed

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/me/drive/items/{id}/workbook/closeSession
Content-type: application/json
workbook-session-id: {session-id}

{
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Drives.Item.Items.Item.Workbook.CloseSession;

var requestBody = new CloseSessionPostRequestBody
{
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Workbook.CloseSession.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("workbook-session-id", "{session-id}");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdrives "github.com/microsoftgraph/msgraph-sdk-go/drives"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("workbook-session-id", "{session-id}")

configuration := &graphdrives.ItemItemsItemWorkbookCloseSessionRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphdrives.NewCloseSessionPostRequestBody()

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Workbook().CloseSession().Post(context.Background(), requestBody, configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.drives.item.items.item.workbook.closesession.CloseSessionPostRequestBody closeSessionPostRequestBody = new com.microsoft.graph.drives.item.items.item.workbook.closesession.CloseSessionPostRequestBody();
graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").workbook().closeSession().post(closeSessionPostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("workbook-session-id", "{session-id}");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const closeSession = {
};

await client.api('/me/drive/items/{id}/workbook/closeSession')
	.post(closeSession);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Workbook\CloseSession\CloseSessionRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Workbook\CloseSession\CloseSessionPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloseSessionPostRequestBody();
$requestConfiguration = new CloseSessionRequestBuilderPostRequestConfiguration();
$headers = [
		'workbook-session-id' => '{session-id}',
	];
$requestConfiguration->headers = $headers;


$graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->workbook()->closeSession()->post($requestBody, $requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.drives.item.items.item.workbook.close_session.close_session_request_builder import CloseSessionRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.drives.item.items.item.workbook.close_session.close_session_post_request_body import CloseSessionPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloseSessionPostRequestBody(
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("workbook-session-id", "{session-id}")


await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').workbook.close_session.post(request_body, request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

For more information, see [Create session](https://learn.microsoft.com/en-us/graph/api/workbook-createsession) and [Close session](https://learn.microsoft.com/en-us/graph/api/workbook-closesession).

## Work with APIs that take a long time to complete

You might notice that some operations take an indeterminate amount time to complete; for example, opening a large workbook. It is easy to hit timeout while waiting for the response to these requests. To resolve this issue, we provide the long-running operation pattern. When you use this pattern, you don't need to worry about the timeout for the request.

Currently, the session creation Excel API in Microsoft Graph has the long-running operation pattern enabled. This pattern involves the following steps:

1. Add a `Prefer: respond-async` header to the request to indicate that it is a long-running operation when you create a session.
2. A long-running operation returns a `202 Accepted` response along with a Location header to retrieve the operation status. If the session creation completes in several seconds, it returns a regular create session response instead of using the long-running operation pattern.
3. With the `202 Accepted` response, you can retrieve the operation status at the specified location. Operation status values include `notStarted`, `running`, `succeeded`, and `failed`.
4. After the operation completes, you can get the session creation result through the specified URL in the succeeded response.

The following example creates a session using the long-running operation pattern.

### Initial request to create session

#### Request

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/me/drive/items/{drive-item-id}/workbook/createSession
Prefer: respond-async
Content-type: application/json
{
    "persistChanges": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Drives.Item.Items.Item.Workbook.CreateSession;

var requestBody = new CreateSessionPostRequestBody
{
	PersistChanges = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Workbook.CreateSession.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Prefer", "respond-async");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdrives "github.com/microsoftgraph/msgraph-sdk-go/drives"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "respond-async")

configuration := &graphdrives.ItemItemsItemWorkbookCreateSessionRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphdrives.NewCreateSessionPostRequestBody()
persistChanges := true
requestBody.SetPersistChanges(&persistChanges) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
createSession, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Workbook().CreateSession().Post(context.Background(), requestBody, configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.drives.item.items.item.workbook.createsession.CreateSessionPostRequestBody createSessionPostRequestBody = new com.microsoft.graph.drives.item.items.item.workbook.createsession.CreateSessionPostRequestBody();
createSessionPostRequestBody.setPersistChanges(true);
var result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").workbook().createSession().post(createSessionPostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "respond-async");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workbookSessionInfo = {
    persistChanges: true
};

await client.api('/me/drive/items/{drive-item-id}/workbook/createSession')
	.post(workbookSessionInfo);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Workbook\CreateSession\CreateSessionRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Workbook\CreateSession\CreateSessionPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateSessionPostRequestBody();
$requestBody->setPersistChanges(true);
$requestConfiguration = new CreateSessionRequestBuilderPostRequestConfiguration();
$headers = [
		'Prefer' => 'respond-async',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->workbook()->createSession()->post($requestBody, $requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.drives.item.items.item.workbook.create_session.create_session_request_builder import CreateSessionRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.drives.item.items.item.workbook.create_session.create_session_post_request_body import CreateSessionPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateSessionPostRequestBody(
	persist_changes = True,
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "respond-async")


result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').workbook.create_session.post(request_body, request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

The long-running operation pattern returns a `202 Accepted` response similar to the following.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/v1.0/me/drive/items/{drive-item-id}/workbook/operations/{operation-id}
Content-type: application/json

{
}
```

In some cases, if the creation succeeds within seconds, it won't enter the long-running operation pattern; instead, it returns as a regular create session and the successful request will return a `201 Created` response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "id-value",
  "persistChanges": true
}
```

The following example shows the response when the request fails.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 500 Internal Server Error
Content-type: application/json

{
  "error":{
    "code": "internalServerError",
    "message": "An internal server error occurred while processing the request.",
    "innerError": {
      "code": "internalServerErrorUncategorized",
      "message": "An unspecified error has occurred.",
      "innerError": {
        "code": "GenericFileOpenError",
        "message": "The workbook cannot be opened."
      }
    }
  }
}
```

### Poll status of the long-running create session

With the long-running operation pattern, you can get the creation status at specified location by using the following request. The suggested interval to poll status is around 30 seconds. The maximum interval should be no more than 4 minutes.

#### Request

```http
GET https://graph.microsoft.com/v1.0/me/drive/items/{drive-item-id}/workbook/operations/{operation-id}
{
}
```

#### Response

The following is the response when the operation has a status of `running`.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": {operation-id},
    "status": "running"
}
```

The following is the response when the operation status is `succeeded`.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": {operation-id},
    "status": "succeeded",
    "resourceLocation": "https://graph.microsoft.com/v1.0/me/drive/items/{drive-item-id}/workbook/sessionInfoResource(key='{key}')
}
```

The following is the response when the operation status is `failed`.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": {operation-id},
  "status": "failed",
  "error":{
    "code": "internalServerError",
    "message": "An internal server error occurred while processing the request.",
    "innerError": {
      "code": ""internalServerErrorUncategorized",
      "message": "An unspecified error has occurred.",
      "innerError": {
        "code": "GenericFileOpenError",
        "message": "The workbook cannot be opened."
      }
    }
  }
}
```

For more information about errors, see [Error codes and messages](https://learn.microsoft.com/en-us/graph/workbook-error-codes#error-codes-and-messages).

### Acquire session information

#### Request

With a status of `succeeded`, you can get the created session information through `resourceLocation` with a request similar to the following.

```http
GET https://graph.microsoft.com/v1.0/me/drive/items/{drive-item-id}/workbook/sessionInfoResource(key='{key}')
{
}
```

#### Response

The following is the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "id-value",
    "persistChanges": true
}
```

Note

Acquire session information depends on the initial request. You don't need to acquire the result if the initial request doesn't return a response body.

## Reduce throttling errors

Excel APIs in Microsoft Graph affect the resource usage of multiple dependency services. The impact can vary between different requests: for example, you might expect that updating a short string in a single cell of a small workbook would consume fewer resources than adding a big table with complex formulas to a large workbook.

Even with the same API, parameters and target workbooks can introduce significant differences. Therefore Excel API throttling isn't defined with simple and universal limit numbers, as they would result in more restrictive limits. The following best practices will help you complete tasks more quickly with fewer throttling errors.

### Retry-After header

In many cases, a throttling response includes a `Retry-After` header. Respecting the value of the header and delaying similar requests would help the client recover from throttling. For details about handling error responses from Excel APIs in Microsoft Graph, see [Error handling for Excel APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/workbook-error-handling).

### Throttling and concurrency

Another factor related to throttling is request concurrency. We don't recommend increasing concurrency when using Excel APIs \(for example, parallelizing the requests to the same workbook\), especially for write requests. Instead, unless there is a specific concern, such as significant networking overhead compared to very short request execution time, we recommend sequential usage in the most common case: for each workbook, only send the next request after receiving a successful response to the current request.

Concurrent write requests to the same workbook don’t usually run in parallel \(although in some cases they do\); rather, they are often the cause of throttling, timeout \(when requests are queued on servers\), merge conflict \(when concurrent sessions are involved\) and other types of failures. They also complicate error handling; for example, when you receive a failure response, there is no way to confirm the status of other pending requests, which makes it difficult to determine or to recover the state of the workbook.

## Related content

- [Use the Excel REST API](https://learn.microsoft.com/en-us/graph/api/resources/excel)
