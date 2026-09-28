<!-- Source: https://learn.microsoft.com/en-us/graph/api/itemanalytics-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-20 -->

# Get itemAnalytics

Namespace: microsoft.graph

Get [itemAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/itemanalytics?view=graph-rest-1.0) about the views that took place under this resource. The **itemAnalytics** resource is a convenient way to get activity stats for `allTime` and the `lastSevenDays`. For a custom time range or interval, use the [getActivitiesByInterval](https://learn.microsoft.com/en-us/graph/api/itemactivitystat-getactivitybyinterval?view=graph-rest-1.0) API.

> **Note:** The **itemAnalytics** resource is not yet available in all [national deployments](https://learn.microsoft.com/en-us/graph/deployments).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.Read | Files.Read.All, Files.ReadWrite, Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Files.Read.All | Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All |

## HTTP request

```http
GET /drives/{drive-id}/items/{item-id}/analytics/allTime
GET /sites/{site-id}/analytics/allTime
GET /sites/{site-id}/lists/{list-id}/items/{item-id}/analytics/allTime
GET /drives/{drive-id}/items/{item-id}/analytics/lastSevenDays
GET /sites/{site-id}/analytics/lastSevenDays
GET /sites/{site-id}/lists/{list-id}/items/{item-id}/analytics/lastSevenDays
```

Note

The value for `{item-id}` in the `/sites/{site-id}/lists/{list-id}/items/{item-id}` request is the `listItemUniqueId`. To get the `listItemUniqueId` of an item, call the `/sites/{site-id}/lists/{list-id}/items/{item-id}?$select=sharepointIds` endpoint. For details, see [sharePointIds](https://learn.microsoft.com/en-us/graph/api/resources/sharepointids).

## Optional query parameters

This method supports the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [itemAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/itemanalytics?view=graph-rest-1.0) objects in the response body.

## Example

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

```msgraph
GET /drives/{drive-id}/items/{item-id}/analytics/allTime
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Analytics.AllTime.GetAsync();
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
allTime, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Analytics().AllTime().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ItemActivityStat result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").analytics().allTime().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let itemActivityStat = await client.api('/drives/{drive-id}/items/{item-id}/analytics/allTime')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->analytics()->allTime()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

Get-MgDriveItemAnalyticTime -DriveId $driveId -DriveItemId $driveItemId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').analytics.all_time.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "allTime": {
        "access": {
            "actionCount": 123,
            "actorCount": 89
        }
    }
}
```
