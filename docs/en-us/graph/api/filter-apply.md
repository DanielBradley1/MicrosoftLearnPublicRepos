<!-- Source: https://learn.microsoft.com/en-us/graph/api/filter-apply?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# filter: apply

Namespace: microsoft.graph

Apply the given filter criteria on the given column.

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
POST /me/drive/items/{id}/workbook/tables/{id|name}/columns/{id|name}/filter/apply
POST /me/drive/root:/{item-path}:/workbook/tables/{id|name}/columns/{id|name}/filter/apply
POST /me/drive/items/{id}/workbook/worksheets/{id|name}/tables/{id|name}/columns/{id|name}/filter/apply
POST /me/drive/root:/{item-path}:/workbook/worksheets/{id|name}/tables/{id|name}/columns/{id|name}/filter/apply
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| criteria | workbookFilterCriteria | The criteria to apply. |

## Response

If successful, this method returns a `200 OK` response code. It doesn't return anything in the response body.

## Example

The following example shows how to call this API.

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
POST https://graph.microsoft.com/v1.0/me/drive/items/{id}/workbook/tables/{id|name}/columns/{id|name}/filter/apply
Content-type: application/json

{
  "criteria": {
    "criterion1": "criterion1-value",
    "criterion2": "criterion2-value",
    "color": "color-value",
    "operator": {
    },
    "icon": {
      "set": "set-value",
      "index": 99
    },
    "dynamicCriteria": "dynamicCriteria-value",
    "values": {
    },
    "filterOn": "filterOn-value"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Drives.Item.Items.Item.Workbook.Tables.Item.Columns.Item.Filter.Apply;
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ApplyPostRequestBody
{
	Criteria = new WorkbookFilterCriteria
	{
		Criterion1 = "criterion1-value",
		Criterion2 = "criterion2-value",
		Color = "color-value",
		Operator = new Operator
		{
		},
		Icon = new WorkbookIcon
		{
			Set = "set-value",
			Index = 99,
		},
		DynamicCriteria = "dynamicCriteria-value",
		Values = new UntypedObject(new Dictionary<string, UntypedNode>
		{
		}),
		FilterOn = "filterOn-value",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Workbook.Tables["{workbookTable-id}"].Columns["{workbookTableColumn-id}"].Filter.Apply.PostAsync(requestBody);
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
criteria := graphmodels.NewWorkbookFilterCriteria()
criterion1 := "criterion1-value"
criteria.SetCriterion1(&criterion1) 
criterion2 := "criterion2-value"
criteria.SetCriterion2(&criterion2) 
color := "color-value"
criteria.SetColor(&color) 
operator := graph.Newoperator()
criteria.SetOperator(operator)
icon := graphmodels.NewWorkbookIcon()
set := "set-value"
icon.SetSet(&set) 
index := int32(99)
icon.SetIndex(&index) 
criteria.SetIcon(icon)
dynamicCriteria := "dynamicCriteria-value"
criteria.SetDynamicCriteria(&dynamicCriteria) 
values := graph.NewUntypedNode()
criteria.SetValues(values)
filterOn := "filterOn-value"
criteria.SetFilterOn(&filterOn) 
requestBody.SetCriteria(criteria)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Workbook().Tables().ByWorkbookTableId("workbookTable-id").Columns().ByWorkbookTableColumnId("workbookTableColumn-id").Filter().Apply().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.drives.item.items.item.workbook.tables.item.columns.item.filter.apply.ApplyPostRequestBody applyPostRequestBody = new com.microsoft.graph.drives.item.items.item.workbook.tables.item.columns.item.filter.apply.ApplyPostRequestBody();
WorkbookFilterCriteria criteria = new WorkbookFilterCriteria();
criteria.setCriterion1("criterion1-value");
criteria.setCriterion2("criterion2-value");
criteria.setColor("color-value");
Operator operator = new Operator();
criteria.setOperator(operator);
WorkbookIcon icon = new WorkbookIcon();
icon.setSet("set-value");
icon.setIndex(99);
criteria.setIcon(icon);
criteria.setDynamicCriteria("dynamicCriteria-value");
UntypedNode values = new UntypedNode();
criteria.setValues(values);
criteria.setFilterOn("filterOn-value");
applyPostRequestBody.setCriteria(criteria);
graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").workbook().tables().byWorkbookTableId("{workbookTable-id}").columns().byWorkbookTableColumnId("{workbookTableColumn-id}").filter().apply().post(applyPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const apply = {
  criteria: {
    criterion1: 'criterion1-value',
    criterion2: 'criterion2-value',
    color: 'color-value',
    operator: {
    },
    icon: {
      set: 'set-value',
      index: 99
    },
    dynamicCriteria: 'dynamicCriteria-value',
    values: {
    },
    filterOn: 'filterOn-value'
  }
};

await client.api('/me/drive/items/{id}/workbook/tables/{id|name}/columns/{id|name}/filter/apply')
	.post(apply);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Drives\Item\Items\Item\Workbook\Tables\Item\Columns\Item\Filter\Apply\ApplyPostRequestBody;
use Microsoft\Graph\Generated\Models\WorkbookFilterCriteria;
use Microsoft\Graph\Generated\Models\WorkbookIcon;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ApplyPostRequestBody();
$criteria = new WorkbookFilterCriteria();
$criteria->setCriterion1('criterion1-value');
$criteria->setCriterion2('criterion2-value');
$criteria->setColor('color-value');
$criteriaOperator = new Operator();
$criteria->setOperator($criteriaOperator);
$criteriaIcon = new WorkbookIcon();
$criteriaIcon->setSet('set-value');
$criteriaIcon->setIndex(99);
$criteria->setIcon($criteriaIcon);
$criteria->setDynamicCriteria('dynamicCriteria-value');
$criteriaValues = new UntypedNode();
$criteria->setValues($criteriaValues);
$criteria->setFilterOn('filterOn-value');
$requestBody->setCriteria($criteria);

$graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->workbook()->tables()->byWorkbookTableId('workbookTable-id')->columns()->byWorkbookTableColumnId('workbookTableColumn-id')->filter()->apply()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.drives.item.items.item.workbook.tables.item.columns.item.filter.apply.apply_post_request_body import ApplyPostRequestBody
from msgraph.generated.models.workbook_filter_criteria import WorkbookFilterCriteria
from msgraph.generated.models.workbook_icon import WorkbookIcon
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ApplyPostRequestBody(
	criteria = WorkbookFilterCriteria(
		criterion1 = "criterion1-value",
		criterion2 = "criterion2-value",
		color = "color-value",
		operator = Operator(
		),
		icon = WorkbookIcon(
			set = "set-value",
			index = 99,
		),
		dynamic_criteria = "dynamicCriteria-value",
		values = UntypedNode(
		),
		filter_on = "filterOn-value",
	),
)

await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').workbook.tables.by_workbook_table_id('workbookTable-id').columns.by_workbook_table_column_id('workbookTableColumn-id').filter.apply.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```
