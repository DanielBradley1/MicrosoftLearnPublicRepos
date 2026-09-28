<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getrawremoteconnectionreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-02-26 -->

# cloudPcReports: getRawRemoteConnectionReports

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the raw real-time remote connection report for a Cloud PC without any calculation, such as roundTripTime or available bandwidth, which are aggregated hourly from the raw event data.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.Read.All | CloudPC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.Read.All | CloudPC.ReadWrite.All |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/reports/getRawRemoteConnectionReports
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| filter | String | OData filter syntax. Supported filters include `and`, `or`, `lt`, `le`, `gt`, `ge` and `eq`. |
| select | String collection | OData select syntax. The columns to include in the report. |
| skip | Int32 | The number of records to skip. |
| top | Int32 | The top number of records to return. |

## Response

If successful, this action returns a `200 OK` response code and a Stream in the response body.

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

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getRawRemoteConnectionReports
Content-Type: application/json
Content-length: 199

{
    "filter": "ActivityId eq 'cb6ad4c4-8a17-4245-a644-e4436b1ee204'",
    "select":["RoundTripTimeInMs", "AvailableBandwidthInMbps", "SignInDateTime"],
    "skip": 0,
    "top": 50
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.GetRawRemoteConnectionReports;

var requestBody = new GetRawRemoteConnectionReportsPostRequestBody
{
	Filter = "ActivityId eq 'cb6ad4c4-8a17-4245-a644-e4436b1ee204'",
	Select = new List<string>
	{
		"RoundTripTimeInMs",
		"AvailableBandwidthInMbps",
		"SignInDateTime",
	},
	Skip = 0,
	Top = 50,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.GetRawRemoteConnectionReports.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphdevicemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/devicemanagement"
	  //other-imports
)

requestBody := graphdevicemanagement.NewGetRawRemoteConnectionReportsPostRequestBody()
filter := "ActivityId eq 'cb6ad4c4-8a17-4245-a644-e4436b1ee204'"
requestBody.SetFilter(&filter) 
select := []string {
	"RoundTripTimeInMs",
	"AvailableBandwidthInMbps",
	"SignInDateTime",
}
requestBody.SetSelect(select)
skip := int32(0)
requestBody.SetSkip(&skip) 
top := int32(50)
requestBody.SetTop(&top) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().GetRawRemoteConnectionReports().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getrawremoteconnectionreports.GetRawRemoteConnectionReportsPostRequestBody getRawRemoteConnectionReportsPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getrawremoteconnectionreports.GetRawRemoteConnectionReportsPostRequestBody();
getRawRemoteConnectionReportsPostRequestBody.setFilter("ActivityId eq 'cb6ad4c4-8a17-4245-a644-e4436b1ee204'");
LinkedList<String> select = new LinkedList<String>();
select.add("RoundTripTimeInMs");
select.add("AvailableBandwidthInMbps");
select.add("SignInDateTime");
getRawRemoteConnectionReportsPostRequestBody.setSelect(select);
getRawRemoteConnectionReportsPostRequestBody.setSkip(0);
getRawRemoteConnectionReportsPostRequestBody.setTop(50);
graphClient.deviceManagement().virtualEndpoint().reports().getRawRemoteConnectionReports().post(getRawRemoteConnectionReportsPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stream = {
    filter: 'ActivityId eq \'cb6ad4c4-8a17-4245-a644-e4436b1ee204\'',
    select: ['RoundTripTimeInMs', 'AvailableBandwidthInMbps', 'SignInDateTime'],
    skip: 0,
    top: 50
};

await client.api('/deviceManagement/virtualEndpoint/reports/getRawRemoteConnectionReports')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\GetRawRemoteConnectionReports\GetRawRemoteConnectionReportsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetRawRemoteConnectionReportsPostRequestBody();
$requestBody->setFilter('ActivityId eq \'cb6ad4c4-8a17-4245-a644-e4436b1ee204\'');
$requestBody->setSelect(['RoundTripTimeInMs', 'AvailableBandwidthInMbps', 'SignInDateTime', 	]);
$requestBody->setSkip(0);
$requestBody->setTop(50);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->getRawRemoteConnectionReports()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.get_raw_remote_connection_reports.get_raw_remote_connection_reports_post_request_body import GetRawRemoteConnectionReportsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetRawRemoteConnectionReportsPostRequestBody(
	filter = "ActivityId eq 'cb6ad4c4-8a17-4245-a644-e4436b1ee204'",
	select = [
		"RoundTripTimeInMs",
		"AvailableBandwidthInMbps",
		"SignInDateTime",
	],
	skip = 0,
	top = 50,
)

await graph_client.device_management.virtual_endpoint.reports.get_raw_remote_connection_reports.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

{
    "TotalRowCount": 1,
    "Schema": [
        {
            "Column": "RoundTripTimeInMs",
            "PropertyType": "Double"
        }
        {
            "Column": "AvailableBandwidthInMbps",
            "PropertyType": "Double"
        },
        {
            "Column": "SignInDateTime",
            "PropertyType": "DateTime"
        }],
    "Values": [
        ["316", "8", "2023-07-03T18:14:34Z"]
    ]
}
```
