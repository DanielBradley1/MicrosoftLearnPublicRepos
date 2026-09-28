<!-- Source: https://learn.microsoft.com/en-us/graph/api/workbook-tablerowoperationresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# workbook: tableRowOperationResult

Namespace: microsoft.graph

This function is the last in a series of steps to create a [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) resource asynchronously.

A best practice to create multiple table rows is to batch them in one [create tableRow](https://learn.microsoft.com/en-us/graph/api/table-post-rows?view=graph-rest-1.0) operation and carry out the operation asynchronously.

An asynchronous request to create table rows involves the following steps:

1. Issue an async [Create tableRow](https://learn.microsoft.com/en-us/graph/api/table-post-rows?view=graph-rest-1.0) request and get the query URL returned in the `Location` response header.
2. Use the query URL returned from step 1 to issue the [Get workbookOperation](https://learn.microsoft.com/en-us/graph/api/workbookoperation-get?view=graph-rest-1.0) request and get the operation ID for step 3. Alternatively, for convenience, after you get a `succeeded` **operationStatus** result, you can get the query URL from the **resourceLocation** property of the [workbookOperation](https://learn.microsoft.com/en-us/graph/api/resources/workbookoperation?view=graph-rest-1.0) returned in the response, and apply the query URL to step 3.
3. Use the query URL returned from step 2 as the GET request URL for this function **tableRowOperationResult**. A successful function call returns the new table rows in a [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) resource.

This function doesn't do anything if called independently.

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
GET /me/drive/items/{id}/workbook/tableRowOperationResult(key={operation-id})
GET /me/drive/root:/{item-path}:/workbook/tableRowOperationResult(key={operation-id})
```

## Function parameters

The request URL requires the following query parameter.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| key | String | The **operationId** provided in the **workbookOperation** response returned in the preceding [Get workbookOperation](https://learn.microsoft.com/en-us/graph/api/workbookoperation-get?view=graph-rest-1.0) request. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Workbook-Session-Id | Workbook session ID that determines whether changes are persisted. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/drive/items/01CCETFLK7GVZTZHSQNRD2AEI5XWTCU6FJ/workbook/tableRowOperationResult(key='0195cfac-bd22-4f91-b276-dece0aa2378b')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Workbook.TableRowOperationResultWithKey("{key}").GetAsync();
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
key := "{key}"
tableRowOperationResult, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Workbook().TableRowOperationResultWithKey(&key).Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").workbook().tableRowOperationResultWithKey("{key}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let workbookTableRow = await client.api('/me/drive/items/01CCETFLK7GVZTZHSQNRD2AEI5XWTCU6FJ/workbook/tableRowOperationResult(key='0195cfac-bd22-4f91-b276-dece0aa2378b')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->workbook()->tableRowOperationResultWithKey('{key}', )->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').workbook.table_row_operation_result_with_key("{key}").get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "index": 99,
  "values": "[[1, 2, 3]]"
}
```
