<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-gettotalaggregatedremoteconnectionreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# cloudPcReports: getTotalAggregatedRemoteConnectionReports

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the total aggregated remote connection usage of a Cloud PC during a given time span.

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
POST /deviceManagement/virtualEndpoint/reports/getTotalAggregatedRemoteConnectionReports
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
| filter | String | OData filter syntax. Supported filters include `and`, `or`, `lt`, `le`, `gt`, `ge`, and `eq`. |
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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getTotalAggregatedRemoteConnectionReports
Content-Type: application/json
Content-length: 199

{
    "top": 25,
    "skip": 0,
    "filter": "(TotalUsageInHour ge 40 and TotalUsageInHour le 80)",
    "select": [
        "CloudPcId",
        "ManagedDeviceName",
        "UserPrincipalName",
        "TotalUsageInHour",
        "LastActiveTime",
        "PcType",
        "CreatedDate"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.GetTotalAggregatedRemoteConnectionReports;

var requestBody = new GetTotalAggregatedRemoteConnectionReportsPostRequestBody
{
	Top = 25,
	Skip = 0,
	Filter = "(TotalUsageInHour ge 40 and TotalUsageInHour le 80)",
	Select = new List<string>
	{
		"CloudPcId",
		"ManagedDeviceName",
		"UserPrincipalName",
		"TotalUsageInHour",
		"LastActiveTime",
		"PcType",
		"CreatedDate",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.GetTotalAggregatedRemoteConnectionReports.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewGetTotalAggregatedRemoteConnectionReportsPostRequestBody()
top := int32(25)
requestBody.SetTop(&top) 
skip := int32(0)
requestBody.SetSkip(&skip) 
filter := "(TotalUsageInHour ge 40 and TotalUsageInHour le 80)"
requestBody.SetFilter(&filter) 
select := []string {
	"CloudPcId",
	"ManagedDeviceName",
	"UserPrincipalName",
	"TotalUsageInHour",
	"LastActiveTime",
	"PcType",
	"CreatedDate",
}
requestBody.SetSelect(select)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().GetTotalAggregatedRemoteConnectionReports().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.gettotalaggregatedremoteconnectionreports.GetTotalAggregatedRemoteConnectionReportsPostRequestBody getTotalAggregatedRemoteConnectionReportsPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.gettotalaggregatedremoteconnectionreports.GetTotalAggregatedRemoteConnectionReportsPostRequestBody();
getTotalAggregatedRemoteConnectionReportsPostRequestBody.setTop(25);
getTotalAggregatedRemoteConnectionReportsPostRequestBody.setSkip(0);
getTotalAggregatedRemoteConnectionReportsPostRequestBody.setFilter("(TotalUsageInHour ge 40 and TotalUsageInHour le 80)");
LinkedList<String> select = new LinkedList<String>();
select.add("CloudPcId");
select.add("ManagedDeviceName");
select.add("UserPrincipalName");
select.add("TotalUsageInHour");
select.add("LastActiveTime");
select.add("PcType");
select.add("CreatedDate");
getTotalAggregatedRemoteConnectionReportsPostRequestBody.setSelect(select);
graphClient.deviceManagement().virtualEndpoint().reports().getTotalAggregatedRemoteConnectionReports().post(getTotalAggregatedRemoteConnectionReportsPostRequestBody);
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
    top: 25,
    skip: 0,
    filter: '(TotalUsageInHour ge 40 and TotalUsageInHour le 80)',
    select: [
        'CloudPcId',
        'ManagedDeviceName',
        'UserPrincipalName',
        'TotalUsageInHour',
        'LastActiveTime',
        'PcType',
        'CreatedDate'
    ]
};

await client.api('/deviceManagement/virtualEndpoint/reports/getTotalAggregatedRemoteConnectionReports')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\GetTotalAggregatedRemoteConnectionReports\GetTotalAggregatedRemoteConnectionReportsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetTotalAggregatedRemoteConnectionReportsPostRequestBody();
$requestBody->setTop(25);
$requestBody->setSkip(0);
$requestBody->setFilter('(TotalUsageInHour ge 40 and TotalUsageInHour le 80)');
$requestBody->setSelect(['CloudPcId', 'ManagedDeviceName', 'UserPrincipalName', 'TotalUsageInHour', 'LastActiveTime', 'PcType', 'CreatedDate', 	]);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->getTotalAggregatedRemoteConnectionReports()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.get_total_aggregated_remote_connection_reports.get_total_aggregated_remote_connection_reports_post_request_body import GetTotalAggregatedRemoteConnectionReportsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetTotalAggregatedRemoteConnectionReportsPostRequestBody(
	top = 25,
	skip = 0,
	filter = "(TotalUsageInHour ge 40 and TotalUsageInHour le 80)",
	select = [
		"CloudPcId",
		"ManagedDeviceName",
		"UserPrincipalName",
		"TotalUsageInHour",
		"LastActiveTime",
		"PcType",
		"CreatedDate",
	],
)

await graph_client.device_management.virtual_endpoint.reports.get_total_aggregated_remote_connection_reports.post(request_body)
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
            "Column": "CloudPcId",
            "PropertyType": "String"
        },
        {
            "Column": "ManagedDeviceName",
            "PropertyType": "String"
        },
        {
            "Column": "UserPrincipalName",
            "PropertyType": "String"
        },
        {
            "Column": "TotalUsageInHour",
            "PropertyType": "Double"
        },
        {
            "Column": "LastActiveTime",
            "PropertyType": "DateTime"
        },
        {
            "Column": "PcType",
            "PropertyType": "String"
        },
        {
            "Column": "CreatedDate",
            "PropertyType": "DateTime"
        }
    ],
    "Values": [
        [
            "40f9315c-5b63-4126-9f89-b7dcb145ffff",
            "CPC-DisplayName",
            "connie@contoso.com",
            66.36944444444444,
            "2023-04-17T01:43:18",
            "Cloud PC Enterprise 8vCPU/32GB/512GB",
            "2022-03-30T13:48:38"
        ]
    ]
}
```
