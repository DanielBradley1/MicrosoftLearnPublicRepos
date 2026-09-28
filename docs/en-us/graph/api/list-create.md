<!-- Source: https://learn.microsoft.com/en-us/graph/api/list-create?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create a new list

Namespace: microsoft.graph

Create a new [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Manage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Manage.All | Sites.ReadWrite.All |

## HTTP request

```http
POST /sites/{site-id}/lists
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following is an example of how to create a new generic list.

> **Note:** Custom columns are optional.

In addition to any columns specified here, new lists are created with columns defined in the referenced **template**. If the **list** facet or **template** is unspecified, the list defaults to the `genericList` template, which includes a *Title* column.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/sites/{site-id}/lists
Content-Type: application/json

{
  "displayName": "Books",
  "columns": [
    {
      "name": "Author",
      "text": { }
    },
    {
      "name": "PageCount",
      "number": { }
    }
  ],
  "list": {
    "template": "genericList"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new List
{
	DisplayName = "Books",
	Columns = new List<ColumnDefinition>
	{
		new ColumnDefinition
		{
			Name = "Author",
			Text = new TextColumn
			{
			},
		},
		new ColumnDefinition
		{
			Name = "PageCount",
			Number = new NumberColumn
			{
			},
		},
	},
	List = new ListInfo
	{
		Template = "genericList",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Lists.PostAsync(requestBody);
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

requestBody := graphmodels.NewList()
displayName := "Books"
requestBody.SetDisplayName(&displayName) 


columnDefinition := graphmodels.NewColumnDefinition()
name := "Author"
columnDefinition.SetName(&name) 
text := graphmodels.NewTextColumn()
columnDefinition.SetText(text)
columnDefinition1 := graphmodels.NewColumnDefinition()
name := "PageCount"
columnDefinition1.SetName(&name) 
number := graphmodels.NewNumberColumn()
columnDefinition1.SetNumber(number)

columns := []graphmodels.ColumnDefinitionable {
	columnDefinition,
	columnDefinition1,
}
requestBody.SetColumns(columns)
list := graphmodels.NewListInfo()
template := "genericList"
list.SetTemplate(&template) 
requestBody.SetList(list)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
lists, err := graphClient.Sites().BySiteId("site-id").Lists().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

List list = new List();
list.setDisplayName("Books");
LinkedList<ColumnDefinition> columns = new LinkedList<ColumnDefinition>();
ColumnDefinition columnDefinition = new ColumnDefinition();
columnDefinition.setName("Author");
TextColumn text = new TextColumn();
columnDefinition.setText(text);
columns.add(columnDefinition);
ColumnDefinition columnDefinition1 = new ColumnDefinition();
columnDefinition1.setName("PageCount");
NumberColumn number = new NumberColumn();
columnDefinition1.setNumber(number);
columns.add(columnDefinition1);
list.setColumns(columns);
ListInfo list1 = new ListInfo();
list1.setTemplate("genericList");
list.setList(list1);
List result = graphClient.sites().bySiteId("{site-id}").lists().post(list);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const list = {
  displayName: 'Books',
  columns: [
    {
      name: 'Author',
      text: { }
    },
    {
      name: 'PageCount',
      number: { }
    }
  ],
  list: {
    template: 'genericList'
  }
};

await client.api('/sites/{site-id}/lists')
	.post(list);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\List;
use Microsoft\Graph\Generated\Models\ColumnDefinition;
use Microsoft\Graph\Generated\Models\TextColumn;
use Microsoft\Graph\Generated\Models\NumberColumn;
use Microsoft\Graph\Generated\Models\ListInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EscapedList();
$requestBody->setDisplayName('Books');
$columnsColumnDefinition1 = new ColumnDefinition();
$columnsColumnDefinition1->setName('Author');
$columnsColumnDefinition1Text = new TextColumn();
$columnsColumnDefinition1->setText($columnsColumnDefinition1Text);
$columnsArray []= $columnsColumnDefinition1;
$columnsColumnDefinition2 = new ColumnDefinition();
$columnsColumnDefinition2->setName('PageCount');
$columnsColumnDefinition2Number = new NumberColumn();
$columnsColumnDefinition2->setNumber($columnsColumnDefinition2Number);
$columnsArray []= $columnsColumnDefinition2;
$requestBody->setColumns($columnsArray);

$list = new ListInfo();
$list->setTemplate('genericList');
$requestBody->setEscapedList($list);

$result = $graphServiceClient->sites()->bySiteId('site-id')->lists()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	displayName = "Books"
	columns = @(
		@{
			name = "Author"
			text = @{
			}
		}
		@{
			name = "PageCount"
			number = @{
			}
		}
	)
	list = @{
		template = "genericList"
	}
}

New-MgSiteList -SiteId $siteId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.list import List
from msgraph.generated.models.column_definition import ColumnDefinition
from msgraph.generated.models.text_column import TextColumn
from msgraph.generated.models.number_column import NumberColumn
from msgraph.generated.models.list_info import ListInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = List_(
	display_name = "Books",
	columns = [
		ColumnDefinition(
			name = "Author",
			text = TextColumn(
			),
		),
		ColumnDefinition(
			name = "PageCount",
			number = NumberColumn(
			),
		),
	],
	list = ListInfo(
		template = "genericList",
	),
)

result = await graph_client.sites.by_site_id('site-id').lists.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object is truncated for clarity. Default properties will be returned from the actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "22e03ef3-6ef4-424d-a1d3-92a337807c30",
  "createdDateTime": "2017-04-30T01:21:00Z",
  "createdBy": {
    "user": {
      "displayName": "Ryan Gregg",
      "id": "8606e4d5-d582-4f5f-aeba-7d7c18b20cfd"
    }
  },
  "lastModifiedDateTime": "2016-08-30T08:26:00Z",
  "lastModifiedBy": {
    "user": {
      "displayName": "Ryan Gregg",
      "id": "8606e4d5-d582-4f5f-aeba-7d7c18b20cfd"
    }
  }
}
```
