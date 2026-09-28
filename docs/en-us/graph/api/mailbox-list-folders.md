<!-- Source: https://learn.microsoft.com/en-us/graph/api/mailbox-list-folders?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# List folders

Namespace: microsoft.graph

Get all the [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) objects in the specified mailbox, including any search folders.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MailboxFolder.Read | MailboxFolder.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | MailboxFolder.Read.All | MailboxFolder.ReadWrite.All |

## HTTP request

```http
GET /admin/exchange/mailboxes/{mailboxId}/folders
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$top`, `$skip`, `$orderby`, `$count`, and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: List folders

The following example shows how to get the **mailboxFolder** collection directly under the root folder of the user's mailbox.

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
GET https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Exchange.Mailboxes["{mailbox-id}"].Folders.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
folders, err := graphClient.Admin().Exchange().Mailboxes().ByMailboxId("mailbox-id").Folders().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MailboxFolderCollectionResponse result = graphClient.admin().exchange().mailboxes().byMailboxId("{mailbox-id}").folders().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let folders = await client.api('/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->exchange()->mailboxes()->byMailboxId('mailbox-id')->folders()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.exchange.mailboxes.by_mailbox_id('mailbox-id').folders.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 232

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders",
    "value": [
        {
            "@odata.type": "#microsoft.graph.mailboxFolder",
            "id": "EDSVrdi3lRAAACgfQBAAA=",
            "displayName": "Archive",
            "parentFolderId": "NJWt2LeVEAAAIBCAAAAA==",
            "parentMailboxUrl": "https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93",
            "childFolderCount": 0,
            "totalItemCount": 2,
            "wellKnownName": "archive",
            "type": "IPF.Note"
        },
        {
            "@odata.type": "#microsoft.graph.mailboxFolder",
            "id": "NJWt2LeVEAAAIBDQAAAA==",
            "displayName": "Project Calendar",
            "parentFolderId": "NJWt2LeVEAAAIBCAAAAA==",
            "parentMailboxUrl": "https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93",
            "childFolderCount": 5,
            "totalItemCount": 6,
            "wellKnownName": null,
            "type": "IPF.Appointment"
        }
    ],
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders?%24skip=10"
}
```

### Example 2: List folders with query parameters

The following example uses the `$filter`, `$select`, and `$top` query parameters. The `$filter` parameter refines the results and returns only folders of **type** `IPF.Appointment`. The `$select` parameter is specified to return only the **displayName**, **type**, and **wellKnownName** properties, and the `$top` parameter sets the page size of the result set to return the first five folders in the mailbox.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
GET https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders?$filter=type eq 'IPF.Appointment'&$select=displayName,type,wellKnownName&$top=5
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Exchange.Mailboxes["{mailbox-id}"].Folders.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "type eq 'IPF.Appointment'";
	requestConfiguration.QueryParameters.Select = new string []{ "displayName","type","wellKnownName" };
	requestConfiguration.QueryParameters.Top = 5;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)


requestFilter := "type eq 'IPF.Appointment'"
requestTop := int32(5)

requestParameters := &graphadmin.ExchangeMailboxesItemFoldersRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Select: [] string {"displayName","type","wellKnownName"},
	Top: &requestTop,
}
configuration := &graphadmin.ExchangeMailboxesItemFoldersRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
folders, err := graphClient.Admin().Exchange().Mailboxes().ByMailboxId("mailbox-id").Folders().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MailboxFolderCollectionResponse result = graphClient.admin().exchange().mailboxes().byMailboxId("{mailbox-id}").folders().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "type eq 'IPF.Appointment'";
	requestConfiguration.queryParameters.select = new String []{"displayName", "type", "wellKnownName"};
	requestConfiguration.queryParameters.top = 5;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let folders = await client.api('/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders')
	.filter('type eq \'IPF.Appointment\'')
	.select('displayName,type,wellKnownName')
	.top(5)
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Exchange\Mailboxes\Item\Folders\FoldersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new FoldersRequestBuilderGetRequestConfiguration();
$queryParameters = FoldersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "type eq 'IPF.Appointment'";
$queryParameters->select = ["displayName","type","wellKnownName"];
$queryParameters->top = 5;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->admin()->exchange()->mailboxes()->byMailboxId('mailbox-id')->folders()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.exchange.mailboxes.item.folders.folders_request_builder import FoldersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = FoldersRequestBuilder.FoldersRequestBuilderGetQueryParameters(
		filter = "type eq 'IPF.Appointment'",
		select = ["displayName","type","wellKnownName"],
		top = 5,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.admin.exchange.mailboxes.by_mailbox_id('mailbox-id').folders.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 232

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders",
    "value": [
        {
            "@odata.type": "#microsoft.graph.mailboxFolder",
            "id": "NJWt2LeVEAAAIBDQAAAA==",
            "displayName": "Project Calendar",
            "parentMailboxUrl": "https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93",
            "type": "IPF.Appointment",
            "wellKnownName": null
        }
    ]
}
```
