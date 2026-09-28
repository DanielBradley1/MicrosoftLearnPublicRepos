<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getconnectionqualityreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-02-26 -->

# cloudPcReports: getConnectionQualityReports \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the overall connection quality reports for all devices within a current tenant during a given time period, including metrics like the average round trip time \(P50\), average available bandwidth, and UDP connection percentage. Get also other real-time metrics such as last connection round trip time, last connection client IP, last connection gateway, and last connection protocol.

Caution

This API is deprecated and will stop returning data on December 31, 2024. Going forward, use the [retrieveConnectionQualityReports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrieveconnectionqualityreports?view=graph-rest-beta) API.

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
POST /deviceManagement/virtualEndpoint/reports/getConnectionQualityReports
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
| filter | String | OData `$filter` syntax. Supported filters include: `and`, `or`, `lt`, `le`, `gt`, `ge`, and `eq`. |
| groupBy | String collection | Specify how to group the reports. If used, must have the same contents as the **select** parameter. |
| orderBy | String collection | Specify how to sort the reports. |
| search | String | Specifies a String to search. |
| select | String collection | OData `$select` syntax. The selected columns of the reports. |
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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getConnectionQualityReports
Content-Type: application/json
Content-length: 200

{
  "filter": "EventDateTime gt datetime'2023-04-16T07:40:41.694Z'",
  "search": "",
  "select": [
    "CloudPcId",
    "ManagedDeviceName",
    "AvgRoundTripTimeInMsP50",
    "LastConnectionRoundTripTimeInMs",
    "AvgAvailableBandwidthInMbpsP50",
    "LastConnectionAvailableBandWidthInMSps",
    "AvgRemoteSignInTimeInSecP50",
    "UDPConnectionPercentage",
    "LastConnectionGateway",
    "LastConnectionProtocol",
    "LastActiveTime"
  ],
  "skip": "0",
  "top": "25",
  "orderBy": []
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.GetConnectionQualityReports;

var requestBody = new GetConnectionQualityReportsPostRequestBody
{
	Filter = "EventDateTime gt datetime'2023-04-16T07:40:41.694Z'",
	Search = "",
	Select = new List<string>
	{
		"CloudPcId",
		"ManagedDeviceName",
		"AvgRoundTripTimeInMsP50",
		"LastConnectionRoundTripTimeInMs",
		"AvgAvailableBandwidthInMbpsP50",
		"LastConnectionAvailableBandWidthInMSps",
		"AvgRemoteSignInTimeInSecP50",
		"UDPConnectionPercentage",
		"LastConnectionGateway",
		"LastConnectionProtocol",
		"LastActiveTime",
	},
	Skip = 0,
	Top = 25,
	OrderBy = new List<string>
	{
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.GetConnectionQualityReports.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewGetConnectionQualityReportsPostRequestBody()
filter := "EventDateTime gt datetime'2023-04-16T07:40:41.694Z'"
requestBody.SetFilter(&filter) 
search := ""
requestBody.SetSearch(&search) 
select := []string {
	"CloudPcId",
	"ManagedDeviceName",
	"AvgRoundTripTimeInMsP50",
	"LastConnectionRoundTripTimeInMs",
	"AvgAvailableBandwidthInMbpsP50",
	"LastConnectionAvailableBandWidthInMSps",
	"AvgRemoteSignInTimeInSecP50",
	"UDPConnectionPercentage",
	"LastConnectionGateway",
	"LastConnectionProtocol",
	"LastActiveTime",
}
requestBody.SetSelect(select)
skip := int32(0)
requestBody.SetSkip(&skip) 
top := int32(25)
requestBody.SetTop(&top) 
orderBy := []string {

}
requestBody.SetOrderBy(orderBy)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().GetConnectionQualityReports().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getconnectionqualityreports.GetConnectionQualityReportsPostRequestBody getConnectionQualityReportsPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getconnectionqualityreports.GetConnectionQualityReportsPostRequestBody();
getConnectionQualityReportsPostRequestBody.setFilter("EventDateTime gt datetime'2023-04-16T07:40:41.694Z'");
getConnectionQualityReportsPostRequestBody.setSearch("");
LinkedList<String> select = new LinkedList<String>();
select.add("CloudPcId");
select.add("ManagedDeviceName");
select.add("AvgRoundTripTimeInMsP50");
select.add("LastConnectionRoundTripTimeInMs");
select.add("AvgAvailableBandwidthInMbpsP50");
select.add("LastConnectionAvailableBandWidthInMSps");
select.add("AvgRemoteSignInTimeInSecP50");
select.add("UDPConnectionPercentage");
select.add("LastConnectionGateway");
select.add("LastConnectionProtocol");
select.add("LastActiveTime");
getConnectionQualityReportsPostRequestBody.setSelect(select);
getConnectionQualityReportsPostRequestBody.setSkip(0);
getConnectionQualityReportsPostRequestBody.setTop(25);
LinkedList<String> orderBy = new LinkedList<String>();
getConnectionQualityReportsPostRequestBody.setOrderBy(orderBy);
graphClient.deviceManagement().virtualEndpoint().reports().getConnectionQualityReports().post(getConnectionQualityReportsPostRequestBody);
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
  filter: 'EventDateTime gt datetime\'2023-04-16T07:40:41.694Z\'',
  search: '',
  select: [
    'CloudPcId',
    'ManagedDeviceName',
    'AvgRoundTripTimeInMsP50',
    'LastConnectionRoundTripTimeInMs',
    'AvgAvailableBandwidthInMbpsP50',
    'LastConnectionAvailableBandWidthInMSps',
    'AvgRemoteSignInTimeInSecP50',
    'UDPConnectionPercentage',
    'LastConnectionGateway',
    'LastConnectionProtocol',
    'LastActiveTime'
  ],
  skip: '0',
  top: '25',
  orderBy: []
};

await client.api('/deviceManagement/virtualEndpoint/reports/getConnectionQualityReports')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\GetConnectionQualityReports\GetConnectionQualityReportsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetConnectionQualityReportsPostRequestBody();
$requestBody->setFilter('EventDateTime gt datetime\'2023-04-16T07:40:41.694Z\'');
$requestBody->setSearch('');
$requestBody->setSelect(['CloudPcId', 'ManagedDeviceName', 'AvgRoundTripTimeInMsP50', 'LastConnectionRoundTripTimeInMs', 'AvgAvailableBandwidthInMbpsP50', 'LastConnectionAvailableBandWidthInMSps', 'AvgRemoteSignInTimeInSecP50', 'UDPConnectionPercentage', 'LastConnectionGateway', 'LastConnectionProtocol', 'LastActiveTime', 	]);
$requestBody->setSkip(0);
$requestBody->setTop(25);
$requestBody->setOrderBy([	]);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->getConnectionQualityReports()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.get_connection_quality_reports.get_connection_quality_reports_post_request_body import GetConnectionQualityReportsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetConnectionQualityReportsPostRequestBody(
	filter = "EventDateTime gt datetime'2023-04-16T07:40:41.694Z'",
	search = "",
	select = [
		"CloudPcId",
		"ManagedDeviceName",
		"AvgRoundTripTimeInMsP50",
		"LastConnectionRoundTripTimeInMs",
		"AvgAvailableBandwidthInMbpsP50",
		"LastConnectionAvailableBandWidthInMSps",
		"AvgRemoteSignInTimeInSecP50",
		"UDPConnectionPercentage",
		"LastConnectionGateway",
		"LastConnectionProtocol",
		"LastActiveTime",
	],
	skip = 0,
	top = 25,
	order_by = [
	],
)

await graph_client.device_management.virtual_endpoint.reports.get_connection_quality_reports.post(request_body)
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
  "TotalRowCount": 3,
  "Schema": [
    {
      "Column": "CloudPcId",
      "PropertyType": "String"
    },
    {
      "Column": "ManagedDeviceName",
      "PropertyType": "String"
    },
    {
      "Column": "AvgRoundTripTimeInMsP50",
      "PropertyType": "Double"
    },
    {
      "Column": "LastConnectionRoundTripTimeInMs",
      "PropertyType": "Double"
    },
    {
      "Column": "AvgAvailableBandwidthInMbpsP50",
      "PropertyType": "Double"
    },
    {
      "Column": "LastConnectionAvailableBandWidthInMSps",
      "PropertyType": "Double"
    },
    {
      "Column": "AvgRemoteSignInTimeInSecP50",
      "PropertyType": "Double"
    },
    {
      "Column": "UDPConnectionPercentage",
      "PropertyType": "Double"
    },
    {
      "Column": "LastConnectionGateway",
      "PropertyType": "String"
    },
    {
      "Column": "LastConnectionProtocol",
      "PropertyType": "String"
    },
    {
      "Column": "LastActiveTime",
      "PropertyType": "DateTime"
    }
  ],
  "Values": [
    [
      "1", "f5ff445f-7488-40f8-8ab9-ee784a9c1f33", "Cloud PC-Ana Bowman", "110", "90", "0.32", "0.41", "10.15", "0.80", "East US 2", "192.168.1.01", "UDP (STUN)", "2023-04-17T00:00:00Z"
    ],
    [
      "1", "f5ff445f-7488-40f8-8ab9-ee784a9c1f33", "Cloud PC-Isabel Bowman", "201", "72", "1.22", "1.7", "10.37", "0.62", "West US 3", "192.168.1.02", "UDP (STUN)", "2023-04-18T00:00:00Z"
    ],
    [
      "1", "f5ff445f-7488-40f8-8ab9-ee784a9c1f33", "Cloud PC-Mary Bowman", "213", "200", "1.74", "0.88", "12.35", "0.45", "East US 2", "192.168.1.03", "TCP", "2023-04-19T00:00:00Z"
    ]
  ]
}
```
