<!-- Source: https://learn.microsoft.com/en-us/graph/api/tablesort-apply?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# TableSort: apply

Namespace: microsoft.graph

Perform a sort operation.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Files.ReadWrite | Not available. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/drive/items/{id}/workbook/tables/{id|name}/sort/apply
POST /me/drive/root:/{item-path}:/workbook/tables/{id|name}/sort/apply
POST /me/drive/items/{id}/workbook/worksheets/{id|name}/tables/{id|name}/sort/apply
POST /me/drive/root:/{item-path}:/workbook/worksheets/{id|name}/tables/{id|name}/sort/apply
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Workbook-Session-Id | Workbook session Id that determines if changes are persisted or not. Optional. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| fields | WorkbookSortField collection | The list of conditions to sort on. |
| matchCase | Boolean | Optional. Whether to have the casing impact string ordering. |
| method | string | Optional. The ordering method used for Chinese characters. The possible values are: `PinYin`, `StrokeCount`. |

## Response

If successful, this method returns `200 OK` response code. It doesn't return anything in the response body.

## Example

Here is an example of how to call this API.

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/drive/items/{id}/workbook/tables/{id|name}/sort/apply
Content-type: application/json

{
  "fields": [
    {
      "key": 99,
      "sortOn": "sortOn-value",
      "ascending": true,
      "color": "color-value",
      "dataOption": "dataOption-value",
      "icon": {
        "set": "set-value",
        "index": 99
      }
    }
  ],
  "matchCase": true,
  "method": "method-value"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Drives.Item.Items.Item.Workbook.Tables.Item.Sort.Apply;
using Microsoft.Graph.Models;

var requestBody = new ApplyPostRequestBody
{
	Fields = new List<WorkbookSortField>
	{
		new WorkbookSortField
		{
			Key = 99,
			SortOn = "sortOn-value",
			Ascending = true,
			Color = "color-value",
			DataOption = "dataOption-value",
			Icon = new WorkbookIcon
			{
				Set = "set-value",
				Index = 99,
			},
		},
	},
	MatchCase = true,
	Method = "method-value",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Workbook.Tables["{workbookTable-id}"].Sort.Apply.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdrives "github.com/microsoftgraph/msgraph-sdk-go/drives"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphdrives.NewApplyPostRequestBody()


workbookSortField := graphmodels.NewWorkbookSortField()
key := int32(99)
workbookSortField.SetKey(&key) 
sortOn := "sortOn-value"
workbookSortField.SetSortOn(&sortOn) 
ascending := true
workbookSortField.SetAscending(&ascending) 
color := "color-value"
workbookSortField.SetColor(&color) 
dataOption := "dataOption-value"
workbookSortField.SetDataOption(&dataOption) 
icon := graphmodels.NewWorkbookIcon()
set := "set-value"
icon.SetSet(&set) 
index := int32(99)
icon.SetIndex(&index) 
workbookSortField.SetIcon(icon)

fields := []graphmodels.WorkbookSortFieldable {
	workbookSortField,
}
requestBody.SetFields(fields)
matchCase := true
requestBody.SetMatchCase(&matchCase) 
method := "method-value"
requestBody.SetMethod(&method) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Workbook().Tables().ByWorkbookTableId("workbookTable-id").Sort().Apply().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.drives.item.items.item.workbook.tables.item.sort.apply.ApplyPostRequestBody applyPostRequestBody = new com.microsoft.graph.drives.item.items.item.workbook.tables.item.sort.apply.ApplyPostRequestBody();
LinkedList<WorkbookSortField> fields = new LinkedList<WorkbookSortField>();
WorkbookSortField workbookSortField = new WorkbookSortField();
workbookSortField.setKey(99);
workbookSortField.setSortOn("sortOn-value");
workbookSortField.setAscending(true);
workbookSortField.setColor("color-value");
workbookSortField.setDataOption("dataOption-value");
WorkbookIcon icon = new WorkbookIcon();
icon.setSet("set-value");
icon.setIndex(99);
workbookSortField.setIcon(icon);
fields.add(workbookSortField);
applyPostRequestBody.setFields(fields);
applyPostRequestBody.setMatchCase(true);
applyPostRequestBody.setMethod("method-value");
graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").workbook().tables().byWorkbookTableId("{workbookTable-id}").sort().apply().post(applyPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const apply = {
  fields: [
    {
      key: 99,
      sortOn: 'sortOn-value',
      ascending: true,
      color: 'color-value',
      dataOption: 'dataOption-value',
      icon: {
        set: 'set-value',
        index: 99
      }
    }
  ],
  matchCase: true,
  method: 'method-value'
};

await client.api('/me/drive/items/{id}/workbook/tables/{id|name}/sort/apply')
	.post(apply);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Workbook\Tables\Item\Sort\Apply\ApplyPostRequestBody;
use Microsoft\Graph\Generated\Models\WorkbookSortField;
use Microsoft\Graph\Generated\Models\WorkbookIcon;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ApplyPostRequestBody();
$fieldsWorkbookSortField1 = new WorkbookSortField();
$fieldsWorkbookSortField1->setKey(99);
$fieldsWorkbookSortField1->setSortOn('sortOn-value');
$fieldsWorkbookSortField1->setAscending(true);
$fieldsWorkbookSortField1->setColor('color-value');
$fieldsWorkbookSortField1->setDataOption('dataOption-value');
$fieldsWorkbookSortField1Icon = new WorkbookIcon();
$fieldsWorkbookSortField1Icon->setSet('set-value');
$fieldsWorkbookSortField1Icon->setIndex(99);
$fieldsWorkbookSortField1->setIcon($fieldsWorkbookSortField1Icon);
$fieldsArray []= $fieldsWorkbookSortField1;
$requestBody->setFields($fieldsArray);

$requestBody->setMatchCase(true);
$requestBody->setMethod('method-value');

$graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->workbook()->tables()->byWorkbookTableId('workbookTable-id')->sort()->apply()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.drives.item.items.item.workbook.tables.item.sort.apply.apply_post_request_body import ApplyPostRequestBody
from msgraph.generated.models.workbook_sort_field import WorkbookSortField
from msgraph.generated.models.workbook_icon import WorkbookIcon
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ApplyPostRequestBody(
	fields = [
		WorkbookSortField(
			key = 99,
			sort_on = "sortOn-value",
			ascending = True,
			color = "color-value",
			data_option = "dataOption-value",
			icon = WorkbookIcon(
				set = "set-value",
				index = 99,
			),
		),
	],
	match_case = True,
	method = "method-value",
)

await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').workbook.tables.by_workbook_table_id('workbookTable-id').sort.apply.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```
