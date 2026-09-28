<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getdailyaggregatedremoteconnectionreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-02-26 -->

# cloudPcReports: getDailyAggregatedRemoteConnectionReports

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the daily aggregated remote connection reports, such as round trip time, available bandwidth, and so on, in a given period.

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
POST /deviceManagement/virtualEndpoint/reports/getDailyAggregatedRemoteConnectionReports
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
| select | String collection | OData select syntax. Represents the selected columns of the reports. |
| search | String | Specifies a string to search |
| groupBy | String collection | Specify how to group the reports. If used, must have the same contents as select parameter |
| orderBy | String collection | Specify how to sort the reports. |
| skip | Int32 | Number of records to skip. |
| top | Int32 | The number of top records to return. |

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getDailyAggregatedRemoteConnectionReports
Content-Type: application/json
Content-length: 199

{
    "filter" : "CloudPcId eq '5db15afe-025d-4f1b-b43a-d0554b63ffff' and RoundTripTimeInMsP50 lt 100 and EventDateTime gt 2022-06-01 ", 
    "search" : "abc0907", 
    "select" : ["EventDateTime", "CloudPcId", "ManagedDeviceName", "UsageInHour", "RoundTripTimeInMsP50", "AvailableBandwidthInMbpsP50", "RemoteSignInTimeInSecP50", "UserPrincipalName"],
    "skip": "0",
    "top": "25"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.GetDailyAggregatedRemoteConnectionReports;

var requestBody = new GetDailyAggregatedRemoteConnectionReportsPostRequestBody
{
	Filter = "CloudPcId eq '5db15afe-025d-4f1b-b43a-d0554b63ffff' and RoundTripTimeInMsP50 lt 100 and EventDateTime gt 2022-06-01 ",
	Search = "abc0907",
	Select = new List<string>
	{
		"EventDateTime",
		"CloudPcId",
		"ManagedDeviceName",
		"UsageInHour",
		"RoundTripTimeInMsP50",
		"AvailableBandwidthInMbpsP50",
		"RemoteSignInTimeInSecP50",
		"UserPrincipalName",
	},
	Skip = 0,
	Top = 25,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.GetDailyAggregatedRemoteConnectionReports.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewGetDailyAggregatedRemoteConnectionReportsPostRequestBody()
filter := "CloudPcId eq '5db15afe-025d-4f1b-b43a-d0554b63ffff' and RoundTripTimeInMsP50 lt 100 and EventDateTime gt 2022-06-01 "
requestBody.SetFilter(&filter) 
search := "abc0907"
requestBody.SetSearch(&search) 
select := []string {
	"EventDateTime",
	"CloudPcId",
	"ManagedDeviceName",
	"UsageInHour",
	"RoundTripTimeInMsP50",
	"AvailableBandwidthInMbpsP50",
	"RemoteSignInTimeInSecP50",
	"UserPrincipalName",
}
requestBody.SetSelect(select)
skip := int32(0)
requestBody.SetSkip(&skip) 
top := int32(25)
requestBody.SetTop(&top) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().GetDailyAggregatedRemoteConnectionReports().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getdailyaggregatedremoteconnectionreports.GetDailyAggregatedRemoteConnectionReportsPostRequestBody getDailyAggregatedRemoteConnectionReportsPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getdailyaggregatedremoteconnectionreports.GetDailyAggregatedRemoteConnectionReportsPostRequestBody();
getDailyAggregatedRemoteConnectionReportsPostRequestBody.setFilter("CloudPcId eq '5db15afe-025d-4f1b-b43a-d0554b63ffff' and RoundTripTimeInMsP50 lt 100 and EventDateTime gt 2022-06-01 ");
getDailyAggregatedRemoteConnectionReportsPostRequestBody.setSearch("abc0907");
LinkedList<String> select = new LinkedList<String>();
select.add("EventDateTime");
select.add("CloudPcId");
select.add("ManagedDeviceName");
select.add("UsageInHour");
select.add("RoundTripTimeInMsP50");
select.add("AvailableBandwidthInMbpsP50");
select.add("RemoteSignInTimeInSecP50");
select.add("UserPrincipalName");
getDailyAggregatedRemoteConnectionReportsPostRequestBody.setSelect(select);
getDailyAggregatedRemoteConnectionReportsPostRequestBody.setSkip(0);
getDailyAggregatedRemoteConnectionReportsPostRequestBody.setTop(25);
graphClient.deviceManagement().virtualEndpoint().reports().getDailyAggregatedRemoteConnectionReports().post(getDailyAggregatedRemoteConnectionReportsPostRequestBody);
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
    filter: 'CloudPcId eq \'5db15afe-025d-4f1b-b43a-d0554b63ffff\' and RoundTripTimeInMsP50 lt 100 and EventDateTime gt 2022-06-01 ', 
    search: 'abc0907', 
    select: ['EventDateTime', 'CloudPcId', 'ManagedDeviceName', 'UsageInHour', 'RoundTripTimeInMsP50', 'AvailableBandwidthInMbpsP50', 'RemoteSignInTimeInSecP50', 'UserPrincipalName'],
    skip: '0',
    top: '25'
};

await client.api('/deviceManagement/virtualEndpoint/reports/getDailyAggregatedRemoteConnectionReports')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\GetDailyAggregatedRemoteConnectionReports\GetDailyAggregatedRemoteConnectionReportsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetDailyAggregatedRemoteConnectionReportsPostRequestBody();
$requestBody->setFilter('CloudPcId eq \'5db15afe-025d-4f1b-b43a-d0554b63ffff\' and RoundTripTimeInMsP50 lt 100 and EventDateTime gt 2022-06-01 ');
$requestBody->setSearch('abc0907');
$requestBody->setSelect(['EventDateTime', 'CloudPcId', 'ManagedDeviceName', 'UsageInHour', 'RoundTripTimeInMsP50', 'AvailableBandwidthInMbpsP50', 'RemoteSignInTimeInSecP50', 'UserPrincipalName', 	]);
$requestBody->setSkip(0);
$requestBody->setTop(25);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->getDailyAggregatedRemoteConnectionReports()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.get_daily_aggregated_remote_connection_reports.get_daily_aggregated_remote_connection_reports_post_request_body import GetDailyAggregatedRemoteConnectionReportsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetDailyAggregatedRemoteConnectionReportsPostRequestBody(
	filter = "CloudPcId eq '5db15afe-025d-4f1b-b43a-d0554b63ffff' and RoundTripTimeInMsP50 lt 100 and EventDateTime gt 2022-06-01 ",
	search = "abc0907",
	select = [
		"EventDateTime",
		"CloudPcId",
		"ManagedDeviceName",
		"UsageInHour",
		"RoundTripTimeInMsP50",
		"AvailableBandwidthInMbpsP50",
		"RemoteSignInTimeInSecP50",
		"UserPrincipalName",
	],
	skip = 0,
	top = 25,
)

await graph_client.device_management.virtual_endpoint.reports.get_daily_aggregated_remote_connection_reports.post(request_body)
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
            "Column": "UsageInHour",
            "PropertyType": "Double"
        },
        {
            "Column": "RoundTripTimeInMsP50",
            "PropertyType": "Double"
        },
        {
            "Column": "RemoteSignInTimeInSecP50",
            "PropertyType": "Double"
        },
        {
            "Column": "AvailableBandwidthInMbpsP50",
            "PropertyType": "Double"
        },
        {
            "Column": "EventDateTime",
            "PropertyType": "DateTime"
        }
    ],
    "Values": [
        [
            16.310277777777777,
            393.0,
            9.088,
            1.423828125,
            "2022-09-15T00:00:00"
        ]
    ]
}
```
