<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getremoteconnectionhistoricalreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# cloudPcReports: getRemoteConnectionHistoricalReports

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the remote connection history records of a Cloud PC during a given period. This report contains data such as signInDateTime, signOutDateTime, usageInHour, remoteSignInTimeInSec and roundTripTimeInMsP50, and so on. This data is aggregated hourly for a specified time period, such as the last seven days.

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
POST /deviceManagement/virtualEndpoint/reports/getRemoteConnectionHistoricalReports
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
| filter | String | OData filter syntax. Supported filters include `and`, `or`, `lt`, `le`, `gt`, `ge` and `eq`. The `CloudPcId` filter is required; for example: `CloudPcId eq xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`. If this filter is missing, malformed, or invalid, a query config will be thrown. |
| select | String collection | OData select syntax. The columns to include in the report. |
| search | String | The string to search for. |
| groupBy | String collection | A list of columns that describe how to group the data in the report. |
| orderBy | String collection | A list of columns that describe how to sort the data in the report. |
| skip | Int32 | Number of records to skip. |
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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getRemoteConnectionHistoricalReports
Content-Type: application/json
Content-length: 199

{
    "filter": "CloudPcId eq '40f9315c-5b63-4126-9f89-b7dcb14fffff' and SignInDateTime gt datetime'2022-09-09T01:22:51.849Z'",
    "select": [
        "SignInDateTime",
        "SignOutDateTime",
        "UsageInHour",
        "RoundTripTimeInMsP50",
        "AvailableBandwidthInMbpsP50",
        "RemoteSignInTimeInSec"
    ],
    "top": 25,
    "skip": 0
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.GetRemoteConnectionHistoricalReports;

var requestBody = new GetRemoteConnectionHistoricalReportsPostRequestBody
{
	Filter = "CloudPcId eq '40f9315c-5b63-4126-9f89-b7dcb14fffff' and SignInDateTime gt datetime'2022-09-09T01:22:51.849Z'",
	Select = new List<string>
	{
		"SignInDateTime",
		"SignOutDateTime",
		"UsageInHour",
		"RoundTripTimeInMsP50",
		"AvailableBandwidthInMbpsP50",
		"RemoteSignInTimeInSec",
	},
	Top = 25,
	Skip = 0,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.GetRemoteConnectionHistoricalReports.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewGetRemoteConnectionHistoricalReportsPostRequestBody()
filter := "CloudPcId eq '40f9315c-5b63-4126-9f89-b7dcb14fffff' and SignInDateTime gt datetime'2022-09-09T01:22:51.849Z'"
requestBody.SetFilter(&filter) 
select := []string {
	"SignInDateTime",
	"SignOutDateTime",
	"UsageInHour",
	"RoundTripTimeInMsP50",
	"AvailableBandwidthInMbpsP50",
	"RemoteSignInTimeInSec",
}
requestBody.SetSelect(select)
top := int32(25)
requestBody.SetTop(&top) 
skip := int32(0)
requestBody.SetSkip(&skip) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().GetRemoteConnectionHistoricalReports().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getremoteconnectionhistoricalreports.GetRemoteConnectionHistoricalReportsPostRequestBody getRemoteConnectionHistoricalReportsPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getremoteconnectionhistoricalreports.GetRemoteConnectionHistoricalReportsPostRequestBody();
getRemoteConnectionHistoricalReportsPostRequestBody.setFilter("CloudPcId eq '40f9315c-5b63-4126-9f89-b7dcb14fffff' and SignInDateTime gt datetime'2022-09-09T01:22:51.849Z'");
LinkedList<String> select = new LinkedList<String>();
select.add("SignInDateTime");
select.add("SignOutDateTime");
select.add("UsageInHour");
select.add("RoundTripTimeInMsP50");
select.add("AvailableBandwidthInMbpsP50");
select.add("RemoteSignInTimeInSec");
getRemoteConnectionHistoricalReportsPostRequestBody.setSelect(select);
getRemoteConnectionHistoricalReportsPostRequestBody.setTop(25);
getRemoteConnectionHistoricalReportsPostRequestBody.setSkip(0);
graphClient.deviceManagement().virtualEndpoint().reports().getRemoteConnectionHistoricalReports().post(getRemoteConnectionHistoricalReportsPostRequestBody);
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
    filter: 'CloudPcId eq \'40f9315c-5b63-4126-9f89-b7dcb14fffff\' and SignInDateTime gt datetime\'2022-09-09T01:22:51.849Z\'',
    select: [
        'SignInDateTime',
        'SignOutDateTime',
        'UsageInHour',
        'RoundTripTimeInMsP50',
        'AvailableBandwidthInMbpsP50',
        'RemoteSignInTimeInSec'
    ],
    top: 25,
    skip: 0
};

await client.api('/deviceManagement/virtualEndpoint/reports/getRemoteConnectionHistoricalReports')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\GetRemoteConnectionHistoricalReports\GetRemoteConnectionHistoricalReportsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetRemoteConnectionHistoricalReportsPostRequestBody();
$requestBody->setFilter('CloudPcId eq \'40f9315c-5b63-4126-9f89-b7dcb14fffff\' and SignInDateTime gt datetime\'2022-09-09T01:22:51.849Z\'');
$requestBody->setSelect(['SignInDateTime', 'SignOutDateTime', 'UsageInHour', 'RoundTripTimeInMsP50', 'AvailableBandwidthInMbpsP50', 'RemoteSignInTimeInSec', 	]);
$requestBody->setTop(25);
$requestBody->setSkip(0);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->getRemoteConnectionHistoricalReports()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.get_remote_connection_historical_reports.get_remote_connection_historical_reports_post_request_body import GetRemoteConnectionHistoricalReportsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetRemoteConnectionHistoricalReportsPostRequestBody(
	filter = "CloudPcId eq '40f9315c-5b63-4126-9f89-b7dcb14fffff' and SignInDateTime gt datetime'2022-09-09T01:22:51.849Z'",
	select = [
		"SignInDateTime",
		"SignOutDateTime",
		"UsageInHour",
		"RoundTripTimeInMsP50",
		"AvailableBandwidthInMbpsP50",
		"RemoteSignInTimeInSec",
	],
	top = 25,
	skip = 0,
)

await graph_client.device_management.virtual_endpoint.reports.get_remote_connection_historical_reports.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

{
    "TotalRowCount": 4,
    "Schema": [
        {
            "Column": "SignInDateTime",
            "PropertyType": "DateTime"
        },
        {
            "Column": "SignOutDateTime",
            "PropertyType": "DateTime"
        },
        {
            "Column": "UsageInHour",
            "PropertyType": "Double"
        },
        {
            "Column": "RoundTripTimeInMsP50",
            "PropertyType": "Double"
        },
        {
            "Column": "AvailableBandwidthInMbpsP50",
            "PropertyType": "Double"
        },
        {
            "Column": "RemoteSignInTimeInSec",
            "PropertyType": "Double"
        }
    ],
    "Values": [
        [
            "2022-09-06T05:28:52",
            "2022-09-06T07:03:16",
            1.5733333333333333,
            293.0,
            5.22265625,
            19.606
        ],
        [
            "2022-09-06T13:25:04",
            "2022-09-06T13:25:37",
            0.009166666666666667,
            332.0,
            0.9345703125,
            11.264
        ],
        [
            "2022-09-06T13:26:26",
            "2022-09-06T13:48:00",
            0.3591666666666667,
            304.0,
            3.84765625,
            9.075
        ],
        [
            "2022-09-07T00:17:50",
            "2022-09-07T23:56:44",
            23.648055555555555,
            300.0,
            1.9375,
            10.977
        ]
    ]
}
```
