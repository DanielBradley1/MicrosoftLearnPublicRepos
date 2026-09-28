<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getcloudpcperformancereport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-28 -->

# cloudPcReports: getCloudPCPerformanceReport \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a report related to the performance of Cloud PCs.

Caution

This API is deprecated and stopped returning data on December 31, 2024. Going forward, use the [retrieveCloudPcTenantMetricsReport](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecloudpctenantmetricsreport?view=graph-rest-beta) API.

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
POST /deviceManagement/virtualEndpoint/reports/getCloudPCPerformanceReport
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that you can use with this method.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| filter | String | OData `$filter` syntax. Supported filters are: `and`, `or`, `gt`, and `eq`. |
| groupBy | String collection | Specifies how to group the reports. If used, must have the same content as the **select** parameter. |
| orderBy | String collection | Specifies how to sort the reports. |
| reportName | [cloudPCPerformanceReportName](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreports?view=graph-rest-beta#cloudpcperformancereportname-values) | The report name. The possible values are: `performanceTrendReport`, `unknownFutureValue`. |
| search | String | Specifies a String to search. |
| select | String collection | OData `$select` syntax. The selected columns of the reports. |
| skip | Int32 | Number of records to skip. |
| top | Int32 | Specifies the page size. If not defined, the default is 25, with a maximum of 100. |

## Response

If successful, this method returns a `200 OK` response code and a Stream object in the response body.

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getCloudPcPerformanceReport
Content-Type: application/json

{
  "reportName": "performanceTrendReport",
  "filter": "EventDateTime gt datetime'2023-10-13T00:00:00.000Z'",
  "select": [
    "EventDateTime",
    "SlowRoundTripTimeCloudPcCount",
    "LowUdpConnectionPercentageCount",
    "NoActiveTimeConnectedCount",
    "LowActiveTimeConnectedCount"
  ],
  "search": "",
  "skip": 0,
  "top": 50
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.GetCloudPcPerformanceReport;
using Microsoft.Graph.Beta.Models;

var requestBody = new GetCloudPcPerformanceReportPostRequestBody
{
	ReportName = CloudPCPerformanceReportName.PerformanceTrendReport,
	Filter = "EventDateTime gt datetime'2023-10-13T00:00:00.000Z'",
	Select = new List<string>
	{
		"EventDateTime",
		"SlowRoundTripTimeCloudPcCount",
		"LowUdpConnectionPercentageCount",
		"NoActiveTimeConnectedCount",
		"LowActiveTimeConnectedCount",
	},
	Search = "",
	Skip = 0,
	Top = 50,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.GetCloudPcPerformanceReport.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphdevicemanagement.NewGetCloudPcPerformanceReportPostRequestBody()
reportName := graphmodels.PERFORMANCETRENDREPORT_CLOUDPCPERFORMANCEREPORTNAME 
requestBody.SetReportName(&reportName) 
filter := "EventDateTime gt datetime'2023-10-13T00:00:00.000Z'"
requestBody.SetFilter(&filter) 
select := []string {
	"EventDateTime",
	"SlowRoundTripTimeCloudPcCount",
	"LowUdpConnectionPercentageCount",
	"NoActiveTimeConnectedCount",
	"LowActiveTimeConnectedCount",
}
requestBody.SetSelect(select)
search := ""
requestBody.SetSearch(&search) 
skip := int32(0)
requestBody.SetSkip(&skip) 
top := int32(50)
requestBody.SetTop(&top) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().GetCloudPcPerformanceReport().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getcloudpcperformancereport.GetCloudPcPerformanceReportPostRequestBody getCloudPcPerformanceReportPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getcloudpcperformancereport.GetCloudPcPerformanceReportPostRequestBody();
getCloudPcPerformanceReportPostRequestBody.setReportName(CloudPCPerformanceReportName.PerformanceTrendReport);
getCloudPcPerformanceReportPostRequestBody.setFilter("EventDateTime gt datetime'2023-10-13T00:00:00.000Z'");
LinkedList<String> select = new LinkedList<String>();
select.add("EventDateTime");
select.add("SlowRoundTripTimeCloudPcCount");
select.add("LowUdpConnectionPercentageCount");
select.add("NoActiveTimeConnectedCount");
select.add("LowActiveTimeConnectedCount");
getCloudPcPerformanceReportPostRequestBody.setSelect(select);
getCloudPcPerformanceReportPostRequestBody.setSearch("");
getCloudPcPerformanceReportPostRequestBody.setSkip(0);
getCloudPcPerformanceReportPostRequestBody.setTop(50);
graphClient.deviceManagement().virtualEndpoint().reports().getCloudPcPerformanceReport().post(getCloudPcPerformanceReportPostRequestBody);
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
  reportName: 'performanceTrendReport',
  filter: 'EventDateTime gt datetime\'2023-10-13T00:00:00.000Z\'',
  select: [
    'EventDateTime',
    'SlowRoundTripTimeCloudPcCount',
    'LowUdpConnectionPercentageCount',
    'NoActiveTimeConnectedCount',
    'LowActiveTimeConnectedCount'
  ],
  search: '',
  skip: 0,
  top: 50
};

await client.api('/deviceManagement/virtualEndpoint/reports/getCloudPcPerformanceReport')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\GetCloudPcPerformanceReport\GetCloudPcPerformanceReportPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\CloudPCPerformanceReportName;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetCloudPcPerformanceReportPostRequestBody();
$requestBody->setReportName(new CloudPCPerformanceReportName('performanceTrendReport'));
$requestBody->setFilter('EventDateTime gt datetime\'2023-10-13T00:00:00.000Z\'');
$requestBody->setSelect(['EventDateTime', 'SlowRoundTripTimeCloudPcCount', 'LowUdpConnectionPercentageCount', 'NoActiveTimeConnectedCount', 'LowActiveTimeConnectedCount', 	]);
$requestBody->setSearch('');
$requestBody->setSkip(0);
$requestBody->setTop(50);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->getCloudPcPerformanceReport()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.get_cloud_pc_performance_report.get_cloud_pc_performance_report_post_request_body import GetCloudPcPerformanceReportPostRequestBody
from msgraph_beta.generated.models.cloud_p_c_performance_report_name import CloudPCPerformanceReportName
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetCloudPcPerformanceReportPostRequestBody(
	report_name = CloudPCPerformanceReportName.PerformanceTrendReport,
	filter = "EventDateTime gt datetime'2023-10-13T00:00:00.000Z'",
	select = [
		"EventDateTime",
		"SlowRoundTripTimeCloudPcCount",
		"LowUdpConnectionPercentageCount",
		"NoActiveTimeConnectedCount",
		"LowActiveTimeConnectedCount",
	],
	search = "",
	skip = 0,
	top = 50,
)

await graph_client.device_management.virtual_endpoint.reports.get_cloud_pc_performance_report.post(request_body)
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
  "TotalRowCount": 2,
  "Schema": [
    {
      "Column": "EventDateTime",
      "PropertyType": "DateTime"
    },
    {
      "Column": "SlowRoundTripTimeCloudPcCount",
      "PropertyType": "Int64"
    },
    {
      "Column": "LowUdpConnectionPercentageCount",
      "PropertyType": "Int64"
    },
    {
      "Column": "NoActiveTimeConnectedCount",
      "PropertyType": "Int64"
    },
    {
      "Column": "LowActiveTimeConnectedCount",
      "PropertyType": "Int64"
    }
  ],
  "Values": [
    [
      "2023-10-16T00:00:00Z",
      3,
      8,
      3,
      92
    ],
    [
      "2023-10-15T00:00:00Z",
      4,
      6,
      5,
      91
    ]
  ]
}
```
