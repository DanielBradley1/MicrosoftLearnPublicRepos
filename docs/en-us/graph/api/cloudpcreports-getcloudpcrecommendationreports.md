<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getcloudpcrecommendationreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# cloudPcReports: getCloudPcRecommendationReports \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the device recommendation reports for Cloud PCs, such as the usage category report. The usage category report categorizes a Cloud PC as `Undersized`, `Oversized`, `Rightsized`, or `Underutilized`, and also provides the recommended SKU when the Cloud PC isn't `Rightsized`.

Caution

This API is deprecated and will stop returning data on July 01, 2025. Going forward, use the [retrieveCloudPcRecommendationReports](https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecloudpcrecommendationreports?view=graph-rest-beta) API.

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
POST /deviceManagement/virtualEndpoint/reports/getCloudPcRecommendationReports
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
| filter | String | OData `$filter` syntax. Supported filters are: `and`, `or`, `lt`, `le`, `gt`, `ge`, and `eq`. |
| groupBy | String collection | Specifies how to group the reports. If used, must have the same content as the **select** parameter. |
| orderBy | String collection | Specifies how to sort the reports. |
| reportName | [cloudPcReportName](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreportname?view=graph-rest-beta) | Specifies the report name. Supports only `cloudPcUsageCategoryReports` for **cloudPcReportName**. |
| search | String | Specifies a String to search. |
| select | String collection | OData `$select` syntax. The selected columns of the reports. |
| skip | Int32 | Number of records to skip. |
| top | Int32 | The number of top records to return. |

## Response

If successful, this action returns a `200 OK` response code and a Stream in the response body.

## Examples

### Example 1: List recommendation reports by device

The following example shows how to list the reports of the top 50 devices.

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getCloudPcRecommendationReports
Content-Type: application/json
Content-length: 262

{
  "reportName": "cloudPcUsageCategoryReports",
  "top": 50,
  "skip": 0,
  "search": "",
  "filter": "",
  "select": [
    "CloudPcId",
    "ManagedDeviceName",
    "UserPrincipalName",
    "UsageInsight",
    "CurrentSize",
    "RecommendedSize",
    "UsageInHour",
    "DevicePerfSummary"
  ],
  "orderBy": [
    "ManagedDeviceName"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.GetCloudPcRecommendationReports;
using Microsoft.Graph.Beta.Models;

var requestBody = new GetCloudPcRecommendationReportsPostRequestBody
{
	ReportName = CloudPcReportName.CloudPcUsageCategoryReports,
	Top = 50,
	Skip = 0,
	Search = "",
	Filter = "",
	Select = new List<string>
	{
		"CloudPcId",
		"ManagedDeviceName",
		"UserPrincipalName",
		"UsageInsight",
		"CurrentSize",
		"RecommendedSize",
		"UsageInHour",
		"DevicePerfSummary",
	},
	OrderBy = new List<string>
	{
		"ManagedDeviceName",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.GetCloudPcRecommendationReports.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewGetCloudPcRecommendationReportsPostRequestBody()
reportName := graphmodels.CLOUDPCUSAGECATEGORYREPORTS_CLOUDPCREPORTNAME 
requestBody.SetReportName(&reportName) 
top := int32(50)
requestBody.SetTop(&top) 
skip := int32(0)
requestBody.SetSkip(&skip) 
search := ""
requestBody.SetSearch(&search) 
filter := ""
requestBody.SetFilter(&filter) 
select := []string {
	"CloudPcId",
	"ManagedDeviceName",
	"UserPrincipalName",
	"UsageInsight",
	"CurrentSize",
	"RecommendedSize",
	"UsageInHour",
	"DevicePerfSummary",
}
requestBody.SetSelect(select)
orderBy := []string {
	"ManagedDeviceName",
}
requestBody.SetOrderBy(orderBy)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().GetCloudPcRecommendationReports().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getcloudpcrecommendationreports.GetCloudPcRecommendationReportsPostRequestBody getCloudPcRecommendationReportsPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getcloudpcrecommendationreports.GetCloudPcRecommendationReportsPostRequestBody();
getCloudPcRecommendationReportsPostRequestBody.setReportName(CloudPcReportName.CloudPcUsageCategoryReports);
getCloudPcRecommendationReportsPostRequestBody.setTop(50);
getCloudPcRecommendationReportsPostRequestBody.setSkip(0);
getCloudPcRecommendationReportsPostRequestBody.setSearch("");
getCloudPcRecommendationReportsPostRequestBody.setFilter("");
LinkedList<String> select = new LinkedList<String>();
select.add("CloudPcId");
select.add("ManagedDeviceName");
select.add("UserPrincipalName");
select.add("UsageInsight");
select.add("CurrentSize");
select.add("RecommendedSize");
select.add("UsageInHour");
select.add("DevicePerfSummary");
getCloudPcRecommendationReportsPostRequestBody.setSelect(select);
LinkedList<String> orderBy = new LinkedList<String>();
orderBy.add("ManagedDeviceName");
getCloudPcRecommendationReportsPostRequestBody.setOrderBy(orderBy);
graphClient.deviceManagement().virtualEndpoint().reports().getCloudPcRecommendationReports().post(getCloudPcRecommendationReportsPostRequestBody);
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
  reportName: 'cloudPcUsageCategoryReports',
  top: 50,
  skip: 0,
  search: '',
  filter: '',
  select: [
    'CloudPcId',
    'ManagedDeviceName',
    'UserPrincipalName',
    'UsageInsight',
    'CurrentSize',
    'RecommendedSize',
    'UsageInHour',
    'DevicePerfSummary'
  ],
  orderBy: [
    'ManagedDeviceName'
  ]
};

await client.api('/deviceManagement/virtualEndpoint/reports/getCloudPcRecommendationReports')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\GetCloudPcRecommendationReports\GetCloudPcRecommendationReportsPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\CloudPcReportName;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetCloudPcRecommendationReportsPostRequestBody();
$requestBody->setReportName(new CloudPcReportName('cloudPcUsageCategoryReports'));
$requestBody->setTop(50);
$requestBody->setSkip(0);
$requestBody->setSearch('');
$requestBody->setFilter('');
$requestBody->setSelect(['CloudPcId', 'ManagedDeviceName', 'UserPrincipalName', 'UsageInsight', 'CurrentSize', 'RecommendedSize', 'UsageInHour', 'DevicePerfSummary', 	]);
$requestBody->setOrderBy(['ManagedDeviceName', 	]);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->getCloudPcRecommendationReports()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.get_cloud_pc_recommendation_reports.get_cloud_pc_recommendation_reports_post_request_body import GetCloudPcRecommendationReportsPostRequestBody
from msgraph_beta.generated.models.cloud_pc_report_name import CloudPcReportName
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetCloudPcRecommendationReportsPostRequestBody(
	report_name = CloudPcReportName.CloudPcUsageCategoryReports,
	top = 50,
	skip = 0,
	search = "",
	filter = "",
	select = [
		"CloudPcId",
		"ManagedDeviceName",
		"UserPrincipalName",
		"UsageInsight",
		"CurrentSize",
		"RecommendedSize",
		"UsageInHour",
		"DevicePerfSummary",
	],
	order_by = [
		"ManagedDeviceName",
	],
)

await graph_client.device_management.virtual_endpoint.reports.get_cloud_pc_recommendation_reports.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

{
  "TotalRowCount": 489,
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
      "Column": "UsageInsight",
      "PropertyType": "String"
    },
    {
      "Column": "CurrentSize",
      "PropertyType": "Json"
    },
    {
      "Column": "RecommendedSize",
      "PropertyType": "Json"
    },
    {
      "Column": "UsageInHour",
      "PropertyType": "Double"
    },
    {
      "Column": "DevicePerfSummary",
      "PropertyType": "Json"
    }
  ],
  "Values": [
    [
      "4db3619f-be92-42a7-8c74-43fab185da6f",
      "1MoveHost",
      "connie_1@contoso.com",
      "Rightsized",
      {
        "NumvCPUs": 2,
        "RamInGB": 8,
        "OsDiskSizeInGB": 128
      },
      null,
      0,
      {
        "CPUUsagePercentageP90": 0.3,
        "RAMUsagePercentageP90": 0.4
      }
    ],
    [
      "f2ee066c-f63e-4acd-a41e-e348db71cb4d",
      "AXFBF",
      "connie_2@contoso.com",
      "Rightsized",
      {
        "NumvCPUs": 2,
        "RamInGB": 8,
        "OsDiskSizeInGB": 128
      },
      null,
      0,
      {
        "CPUUsagePercentageP90": 0.2,
        "RAMUsagePercentageP90": 0.3
      }
    ]
  ]
}
```

### Example 2: Get summary reports by usage insight

The following example shows how to summarize the report by usage insight.

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getCloudPcRecommendationReports
Content-Type: application/json
Content-length: 262

{
  "reportName": "cloudPcUsageCategoryReports",
  "select": [
    "UsageInsight"
  ],
  "groupBy": [
    "UsageInsight"
  ],
  "filter": ""
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.GetCloudPcRecommendationReports;
using Microsoft.Graph.Beta.Models;

var requestBody = new GetCloudPcRecommendationReportsPostRequestBody
{
	ReportName = CloudPcReportName.CloudPcUsageCategoryReports,
	Select = new List<string>
	{
		"UsageInsight",
	},
	GroupBy = new List<string>
	{
		"UsageInsight",
	},
	Filter = "",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.GetCloudPcRecommendationReports.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewGetCloudPcRecommendationReportsPostRequestBody()
reportName := graphmodels.CLOUDPCUSAGECATEGORYREPORTS_CLOUDPCREPORTNAME 
requestBody.SetReportName(&reportName) 
select := []string {
	"UsageInsight",
}
requestBody.SetSelect(select)
groupBy := []string {
	"UsageInsight",
}
requestBody.SetGroupBy(groupBy)
filter := ""
requestBody.SetFilter(&filter) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().GetCloudPcRecommendationReports().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getcloudpcrecommendationreports.GetCloudPcRecommendationReportsPostRequestBody getCloudPcRecommendationReportsPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getcloudpcrecommendationreports.GetCloudPcRecommendationReportsPostRequestBody();
getCloudPcRecommendationReportsPostRequestBody.setReportName(CloudPcReportName.CloudPcUsageCategoryReports);
LinkedList<String> select = new LinkedList<String>();
select.add("UsageInsight");
getCloudPcRecommendationReportsPostRequestBody.setSelect(select);
LinkedList<String> groupBy = new LinkedList<String>();
groupBy.add("UsageInsight");
getCloudPcRecommendationReportsPostRequestBody.setGroupBy(groupBy);
getCloudPcRecommendationReportsPostRequestBody.setFilter("");
graphClient.deviceManagement().virtualEndpoint().reports().getCloudPcRecommendationReports().post(getCloudPcRecommendationReportsPostRequestBody);
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
  reportName: 'cloudPcUsageCategoryReports',
  select: [
    'UsageInsight'
  ],
  groupBy: [
    'UsageInsight'
  ],
  filter: ''
};

await client.api('/deviceManagement/virtualEndpoint/reports/getCloudPcRecommendationReports')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\GetCloudPcRecommendationReports\GetCloudPcRecommendationReportsPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\CloudPcReportName;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetCloudPcRecommendationReportsPostRequestBody();
$requestBody->setReportName(new CloudPcReportName('cloudPcUsageCategoryReports'));
$requestBody->setSelect(['UsageInsight', 	]);
$requestBody->setGroupBy(['UsageInsight', 	]);
$requestBody->setFilter('');

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->getCloudPcRecommendationReports()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.get_cloud_pc_recommendation_reports.get_cloud_pc_recommendation_reports_post_request_body import GetCloudPcRecommendationReportsPostRequestBody
from msgraph_beta.generated.models.cloud_pc_report_name import CloudPcReportName
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetCloudPcRecommendationReportsPostRequestBody(
	report_name = CloudPcReportName.CloudPcUsageCategoryReports,
	select = [
		"UsageInsight",
	],
	group_by = [
		"UsageInsight",
	],
	filter = "",
)

await graph_client.device_management.virtual_endpoint.reports.get_cloud_pc_recommendation_reports.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

{
  "TotalRowCount": 4,
  "Schema": [
    {
      "Column": "__Count",
      "PropertyType": "Int32"
    },
    {
      "Column": "UsageInsight",
      "PropertyType": "String"
    }
  ],
  "Values": [
    [
      200,
      "Rightsized"
    ],
    [
      50,
      "Undersized"
    ],
    [
      30,
      "Oversized"
    ],
    [
      40,
      "Underutilized"
    ]
  ]
}
```
