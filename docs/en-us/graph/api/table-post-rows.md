<!-- Source: https://learn.microsoft.com/en-us/graph/api/table-post-rows?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create TableRow

Namespace: microsoft.graph

Adds rows to the end of a table.

Note that this API can accept multiple rows of data. Adding one row at a time can affect performance. The recommended approach is to batch the rows together in a single call rather than inserting single rows. For best results, collect the rows to be inserted on the application side and perform a single row add operation. Experiment with the number of rows to determine the ideal number of rows to use in a single API call.

This request might occasionally result in a `504 HTTP` error. The appropriate response to this error is to repeat the request.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/drive/items/{id}/workbook/tables/{id|name}/rows
POST /me/drive/root:/{item-path}:/workbook/tables/{id|name}/rows
POST /me/drive/items/{id}/workbook/worksheets/{id|name}/tables/{id|name}/rows
POST /me/drive/root:/{item-path}:/workbook/worksheets/{id|name}/tables/{id|name}/rows
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Prefer | respond-async. Indicates that the request is an async request. Optional. |
| Workbook-Session-Id | {Workbook-Session-Id}. Created from the **createSession** request. Optional. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| index | Int32 | Optional. Specifies the relative position of the new row. If null, the addition happens at the end. Any rows below the inserted row are shifted downwards. Zero-indexed. |
| values | [Json](https://learn.microsoft.com/en-us/graph/api/resources/json?view=graph-rest-1.0) | A two-dimensional array of unformatted values of the table rows. |

## Response

If successful, this method returns a `201 Created` response code and a [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Add two rows to a table

In this example, two rows of data are inserted at the end of the table.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/drive/items/01CCETFLK7GVZTZHSQNRD2AEI5XWTCU6FJ/workbook/tables/Table1/rows
Content-type: application/json

{
  "values": [
    [1, 2, 3],
    [4, 5, 6]
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new WorkbookTableRow
{
	Values = new UntypedArray(new List<UntypedNode>
	{
		new UntypedArray(new List<UntypedNode>
		{
			new UntypedDouble(1),
			new UntypedDouble(2),
			new UntypedDouble(3),
		}),
		new UntypedArray(new List<UntypedNode>
		{
			new UntypedDouble(4),
			new UntypedDouble(5),
			new UntypedDouble(6),
		}),
	}),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Workbook.Tables["{workbookTable-id}"].Rows.PostAsync(requestBody);
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

requestBody := graphmodels.NewWorkbookTableRow()
values := []graph.UntypedNodeable {
	 := []graph.UntypedNodeable {
 := float64(1)
requestBody.Set(&) 
 := float64(2)
requestBody.Set(&) 
 := float64(3)
requestBody.Set(&)
	}
	 := []graph.UntypedNodeable {
 := float64(4)
requestBody.Set(&) 
 := float64(5)
requestBody.Set(&) 
 := float64(6)
requestBody.Set(&)
	}
}
requestBody.SetValues(values)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rows, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Workbook().Tables().ByWorkbookTableId("workbookTable-id").Rows().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WorkbookTableRow workbookTableRow = new WorkbookTableRow();
LinkedList<LinkedList<UntypedNode>> values = new LinkedList<LinkedList<UntypedNode>>();
LinkedList<UntypedNode>  = new LinkedList<UntypedNode>();
.add(1d);
.add(2d);
.add(3d);
values.add();
LinkedList<UntypedNode> 4 = new LinkedList<UntypedNode>();
4.add(4d);
4.add(5d);
4.add(6d);
values.add(4);
workbookTableRow.setValues(values);
WorkbookTableRow result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").workbook().tables().byWorkbookTableId("{workbookTable-id}").rows().post(workbookTableRow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workbookTableRow = {
  values: [
    [1, 2, 3],
    [4, 5, 6]
  ]
};

await client.api('/me/drive/items/01CCETFLK7GVZTZHSQNRD2AEI5XWTCU6FJ/workbook/tables/Table1/rows')
	.post(workbookTableRow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\WorkbookTableRow;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new WorkbookTableRow();
$requestBody->setValues([	[1,2,3],	[4,5,6],	]);

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->workbook()->tables()->byWorkbookTableId('workbookTable-id')->rows()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.workbook_table_row import WorkbookTableRow
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = WorkbookTableRow(
	values = [
		[
			1,
			2,
			3,
		],
		[
			4,
			5,
			6,
		],
	],
)

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').workbook.tables.by_workbook_table_id('workbookTable-id').rows.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "index": 99,
  "values": [[1, 2, 3]]
}
```

### Example 2: Add two rows to a table asynchronously

Async requests will be useful if the request takes longer time than expected. Note that the `Workbook-Session-Id` header is required when issuing async requests. The user needs to [Create session](https://learn.microsoft.com/en-us/graph/api/workbook-createsession?view=graph-rest-1.0) before using async rich API features. The header `Prefer:respond-async` is also required in the async requests.

For async features, the user usually needs to issue two or three requests: this request, [Get workbookOperation](https://learn.microsoft.com/en-us/graph/api/workbookoperation-get?view=graph-rest-1.0), and optionally [Get tableRowOperationResult](https://learn.microsoft.com/en-us/graph/api/workbook-tablerowoperationresult?view=graph-rest-1.0).

#### Request

Here is an example of the async request. Note that `202 Accepted` will only happen when the request takes a long time to respond. If the request is completed quickly, it will work like a regular sync request, falling back to [Example 1](#example-1-add-two-rows-to-a-table).

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/me/drive/items/01CCETFLK7GVZTZHSQNRD2AEI5XWTCU6FJ/workbook/tables/Table1/rows
Content-type: application/json
Prefer: respond-async
Workbook-Session-Id: {Workbook-Session-Id}

{
  "values": [
    [1, 2, 3],
    [4, 5, 6]
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new WorkbookTableRow
{
	Values = new UntypedArray(new List<UntypedNode>
	{
		new UntypedArray(new List<UntypedNode>
		{
			new UntypedDouble(1),
			new UntypedDouble(2),
			new UntypedDouble(3),
		}),
		new UntypedArray(new List<UntypedNode>
		{
			new UntypedDouble(4),
			new UntypedDouble(5),
			new UntypedDouble(6),
		}),
	}),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Workbook.Tables["{workbookTable-id}"].Rows.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Prefer", "respond-async");
	requestConfiguration.Headers.Add("Workbook-Session-Id", "{Workbook-Session-Id}");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphdrives "github.com/microsoftgraph/msgraph-sdk-go/drives"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "respond-async")
headers.Add("Workbook-Session-Id", "{Workbook-Session-Id}")

configuration := &graphdrives.ItemItemsItemWorkbookTablesItemRowsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewWorkbookTableRow()
values := []graph.UntypedNodeable {
	 := []graph.UntypedNodeable {
 := float64(1)
requestBody.Set(&) 
 := float64(2)
requestBody.Set(&) 
 := float64(3)
requestBody.Set(&)
	}
	 := []graph.UntypedNodeable {
 := float64(4)
requestBody.Set(&) 
 := float64(5)
requestBody.Set(&) 
 := float64(6)
requestBody.Set(&)
	}
}
requestBody.SetValues(values)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rows, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Workbook().Tables().ByWorkbookTableId("workbookTable-id").Rows().Post(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WorkbookTableRow workbookTableRow = new WorkbookTableRow();
LinkedList<LinkedList<UntypedNode>> values = new LinkedList<LinkedList<UntypedNode>>();
LinkedList<UntypedNode>  = new LinkedList<UntypedNode>();
.add(1d);
.add(2d);
.add(3d);
values.add();
LinkedList<UntypedNode> 4 = new LinkedList<UntypedNode>();
4.add(4d);
4.add(5d);
4.add(6d);
values.add(4);
workbookTableRow.setValues(values);
WorkbookTableRow result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").workbook().tables().byWorkbookTableId("{workbookTable-id}").rows().post(workbookTableRow, requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "respond-async");
	requestConfiguration.headers.add("Workbook-Session-Id", "{Workbook-Session-Id}");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workbookTableRow = {
  values: [
    [1, 2, 3],
    [4, 5, 6]
  ]
};

await client.api('/me/drive/items/01CCETFLK7GVZTZHSQNRD2AEI5XWTCU6FJ/workbook/tables/Table1/rows')
	.post(workbookTableRow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Workbook\Tables\Item\Rows\RowsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Models\WorkbookTableRow;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new WorkbookTableRow();
$requestBody->setValues([	[1,2,3],	[4,5,6],	]);
$requestConfiguration = new RowsRequestBuilderPostRequestConfiguration();
$headers = [
		'Prefer' => 'respond-async',
		'Workbook-Session-Id' => '{Workbook-Session-Id}',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->workbook()->tables()->byWorkbookTableId('workbookTable-id')->rows()->post($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.drives.item.items.item.workbook.tables.item.rows.rows_request_builder import RowsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.workbook_table_row import WorkbookTableRow
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = WorkbookTableRow(
	values = [
		[
			1,
			2,
			3,
		],
		[
			4,
			5,
			6,
		],
	],
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "respond-async")
request_configuration.headers.add("Workbook-Session-Id", "{Workbook-Session-Id}")


result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').workbook.tables.by_workbook_table_id('workbookTable-id').rows.post(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

Here is another example of the response that will lead to an async operation. For details, see [Get workbookOperation](https://learn.microsoft.com/en-us/graph/api/workbookoperation-get?view=graph-rest-1.0) and [Get tableRowOperationResult](https://learn.microsoft.com/en-us/graph/api/workbook-tablerowoperationresult?view=graph-rest-1.0).

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/v1.0/me/drive/items/01CCETFLK7GVZTZHSQNRD2AEI5XWTCU6FJ/workbook/operations/0195cfac-bd22-4f91-b276-dece0aa2378b?sessionId=Y2x1c3Rlcj1QU0c0JnNlc3Npb249MTUuU0cyUEVQRjAwMDI4RjI1MS5BMTE2LjEuVTM2LmM4MGRiNjkwLTQwMTktNGNkNS1hYWJiLTJmYzczM2YxZTQ5ZjE0LjUuZW4tVVM1LmVuLVVTMjQuMTAwM2JmZmRhYzUyMzkzOS1Qcml2YXRlMS5TMjQuJTJmUEI0JTJmWjJqZmt1aXhJZHBjeE8xYmclM2QlM2QxNi4xNi4wLjE0NDEwLjM1MDUwMTQuNS5lbi1VUzUuZW4tVVMxLk0xLk4wLjEuUyZ1c2lkPWExOTMyNTU0LTlhNDAtNzYzNi1mNDU3LWEyNjExMmFkNDg2YQ==
Content-type: application/json

{
}
```
