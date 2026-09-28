<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreport-retrievecloudpcrecommendationreports?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# cloudPcReport: retrieveCloudPcRecommendationReports

Namespace: microsoft.graph

Retrieve Cloud PC recommendation [reports](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreport?view=graph-rest-1.0) for usage optimization and cost savings. The usage category report categorizes a Cloud PC as `Undersized`, `Oversized`, `Rightsized`, or `Underutilized`, and also provides the recommended SKU when the Cloud PC isn't `Rightsized`.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/report/retrieveCloudPcRecommendationReports
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| filter | String | OData `$filter` syntax. Supported filters are: `and`, `or`, `lt`, `le`, `gt`, `ge`, and `eq`. Optional. |
| groupBy | String collection | Specifies how to group the reports. If used, must have the same content as the **select** parameter. Optional. |
| orderBy | String collection | Specifies how to sort the reports. Optional. |
| reportType | [cloudPcRecommendationReportType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreport?view=graph-rest-1.0#cloudpcrecommendationreporttype-values) | The report type. Supports a subset of the values for **cloudPcRecommendationReportType**. The supported value is `cloudPcUsageCategoryReport`. Required. |
| search | String | Specifies a String to search. Optional. |
| select | String collection | OData `$select` syntax. The selected columns of the reports. Optional. |
| skip | Int32 | Number of records to skip. Optional. |
| top | Int32 | The number of top records to return. Optional. |

## Response

If successful, this action returns a `200 OK` response code and a Stream in the response body.

## Examples

### Example 1: Get device recommendation reports grouped by service plan and usage category

The following example shows how to get device recommendation reports grouped by service plan and usage category.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/report/retrieveCloudPcRecommendationReports
Content-Type: application/json

{
  "reportType": "cloudPcUsageCategoryReport",
  "select": [
    "ServicePlanId",
    "ServicePlanName",
    "UsageInsight"
  ],
  "groupBy": [
    "ServicePlanId",
    "ServicePlanName",
    "UsageInsight"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DeviceManagement.VirtualEndpoint.Report.RetrieveCloudPcRecommendationReports;
using Microsoft.Graph.Models;

var requestBody = new RetrieveCloudPcRecommendationReportsPostRequestBody
{
	ReportType = CloudPcRecommendationReportType.CloudPcUsageCategoryReport,
	Select = new List<string>
	{
		"ServicePlanId",
		"ServicePlanName",
		"UsageInsight",
	},
	GroupBy = new List<string>
	{
		"ServicePlanId",
		"ServicePlanName",
		"UsageInsight",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Report.RetrieveCloudPcRecommendationReports.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdevicemanagement "github.com/microsoftgraph/msgraph-sdk-go/devicemanagement"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphdevicemanagement.NewRetrieveCloudPcRecommendationReportsPostRequestBody()
reportType := graphmodels.CLOUDPCUSAGECATEGORYREPORT_CLOUDPCRECOMMENDATIONREPORTTYPE 
requestBody.SetReportType(&reportType) 
select := []string {
	"ServicePlanId",
	"ServicePlanName",
	"UsageInsight",
}
requestBody.SetSelect(select)
groupBy := []string {
	"ServicePlanId",
	"ServicePlanName",
	"UsageInsight",
}
requestBody.SetGroupBy(groupBy)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Report().RetrieveCloudPcRecommendationReports().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.devicemanagement.virtualendpoint.report.retrievecloudpcrecommendationreports.RetrieveCloudPcRecommendationReportsPostRequestBody retrieveCloudPcRecommendationReportsPostRequestBody = new com.microsoft.graph.devicemanagement.virtualendpoint.report.retrievecloudpcrecommendationreports.RetrieveCloudPcRecommendationReportsPostRequestBody();
retrieveCloudPcRecommendationReportsPostRequestBody.setReportType(CloudPcRecommendationReportType.CloudPcUsageCategoryReport);
LinkedList<String> select = new LinkedList<String>();
select.add("ServicePlanId");
select.add("ServicePlanName");
select.add("UsageInsight");
retrieveCloudPcRecommendationReportsPostRequestBody.setSelect(select);
LinkedList<String> groupBy = new LinkedList<String>();
groupBy.add("ServicePlanId");
groupBy.add("ServicePlanName");
groupBy.add("UsageInsight");
retrieveCloudPcRecommendationReportsPostRequestBody.setGroupBy(groupBy);
graphClient.deviceManagement().virtualEndpoint().report().retrieveCloudPcRecommendationReports().post(retrieveCloudPcRecommendationReportsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stream = {
  reportType: 'cloudPcUsageCategoryReport',
  select: [
    'ServicePlanId',
    'ServicePlanName',
    'UsageInsight'
  ],
  groupBy: [
    'ServicePlanId',
    'ServicePlanName',
    'UsageInsight'
  ]
};

await client.api('/deviceManagement/virtualEndpoint/report/retrieveCloudPcRecommendationReports')
	.post(stream);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DeviceManagement\VirtualEndpoint\Report\RetrieveCloudPcRecommendationReports\RetrieveCloudPcRecommendationReportsPostRequestBody;
use Microsoft\Graph\Generated\Models\CloudPcRecommendationReportType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RetrieveCloudPcRecommendationReportsPostRequestBody();
$requestBody->setReportType(new CloudPcRecommendationReportType('cloudPcUsageCategoryReport'));
$requestBody->setSelect(['ServicePlanId', 'ServicePlanName', 'UsageInsight', 	]);
$requestBody->setGroupBy(['ServicePlanId', 'ServicePlanName', 'UsageInsight', 	]);

$graphServiceClient->deviceManagement()->virtualEndpoint()->report()->retrieveCloudPcRecommendationReports()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

$params = @{
	reportType = "cloudPcUsageCategoryReport"
	select = @(
	"ServicePlanId"
"ServicePlanName"
"UsageInsight"
)
groupBy = @(
"ServicePlanId"
"ServicePlanName"
"UsageInsight"
)
}

Get-MgDeviceManagementVirtualEndpointReportCloudPcRecommendationReport -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.devicemanagement.virtualendpoint.report.retrieve_cloud_pc_recommendation_reports.retrieve_cloud_pc_recommendation_reports_post_request_body import RetrieveCloudPcRecommendationReportsPostRequestBody
from msgraph.generated.models.cloud_pc_recommendation_report_type import CloudPcRecommendationReportType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RetrieveCloudPcRecommendationReportsPostRequestBody(
	report_type = CloudPcRecommendationReportType.CloudPcUsageCategoryReport,
	select = [
		"ServicePlanId",
		"ServicePlanName",
		"UsageInsight",
	],
	group_by = [
		"ServicePlanId",
		"ServicePlanName",
		"UsageInsight",
	],
)

await graph_client.device_management.virtual_endpoint.report.retrieve_cloud_pc_recommendation_reports.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

{
  "TotalRowCount": 15,
  "Schema": [
    {
      "Column": "__Count",
      "PropertyType": "Int32"
    },
    {
      "Column": "ServicePlanId",
      "PropertyType": "String"
    },
    {
      "Column": "ServicePlanName",
      "PropertyType": "String"
    },
    {
      "Column": "UsageInsight",
      "PropertyType": "String"
    }
  ],
  "Values": [
    [
      26,
      "d3468c8c-3545-4f44-a32f-b465934d2498",
      "Cloud PC Enterprise 2vCPU/8GB/256GB",
      "Undersized"
    ],
    [
      12,
      "d3468c8c-3545-4f44-a32f-b465934d2498",
      "Cloud PC Enterprise 2vCPU/8GB/256GB",
      "Oversized"
    ],
    [
      300,
      "d3468c8c-3545-4f44-a32f-b465934d2498",
      "Cloud PC Enterprise 2vCPU/8GB/256GB",
      "Rightsized"
    ],
    [
      4,
      "d3468c8c-3545-4f44-a32f-b465934d2498",
      "Cloud PC Enterprise 2vCPU/8GB/256GB",
      "Underutilized"
    ]
  ]
}
```

### Example 2: Get device usage category reports for Cloud PCs

The following example shows how to get detailed usage category reports for individual Cloud PCs.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/report/retrieveCloudPcRecommendationReports
Content-Type: application/json

{
  "reportType": "cloudPcUsageCategoryReport",
  "filter": "",
  "select": [
    "CloudPcId",
    "ManagedDeviceName",
    "UserPrincipalName",
    "ServicePlanId",
    "ServicePlanName",
    "UsageInsight",
    "RecommendedPlanId",
    "RecommendedPlanName"
  ],
  "search": "",
  "skip": 0,
  "top": 15
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DeviceManagement.VirtualEndpoint.Report.RetrieveCloudPcRecommendationReports;
using Microsoft.Graph.Models;

var requestBody = new RetrieveCloudPcRecommendationReportsPostRequestBody
{
	ReportType = CloudPcRecommendationReportType.CloudPcUsageCategoryReport,
	Filter = "",
	Select = new List<string>
	{
		"CloudPcId",
		"ManagedDeviceName",
		"UserPrincipalName",
		"ServicePlanId",
		"ServicePlanName",
		"UsageInsight",
		"RecommendedPlanId",
		"RecommendedPlanName",
	},
	Search = "",
	Skip = 0,
	Top = 15,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Report.RetrieveCloudPcRecommendationReports.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdevicemanagement "github.com/microsoftgraph/msgraph-sdk-go/devicemanagement"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphdevicemanagement.NewRetrieveCloudPcRecommendationReportsPostRequestBody()
reportType := graphmodels.CLOUDPCUSAGECATEGORYREPORT_CLOUDPCRECOMMENDATIONREPORTTYPE 
requestBody.SetReportType(&reportType) 
filter := ""
requestBody.SetFilter(&filter) 
select := []string {
	"CloudPcId",
	"ManagedDeviceName",
	"UserPrincipalName",
	"ServicePlanId",
	"ServicePlanName",
	"UsageInsight",
	"RecommendedPlanId",
	"RecommendedPlanName",
}
requestBody.SetSelect(select)
search := ""
requestBody.SetSearch(&search) 
skip := int32(0)
requestBody.SetSkip(&skip) 
top := int32(15)
requestBody.SetTop(&top) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Report().RetrieveCloudPcRecommendationReports().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.devicemanagement.virtualendpoint.report.retrievecloudpcrecommendationreports.RetrieveCloudPcRecommendationReportsPostRequestBody retrieveCloudPcRecommendationReportsPostRequestBody = new com.microsoft.graph.devicemanagement.virtualendpoint.report.retrievecloudpcrecommendationreports.RetrieveCloudPcRecommendationReportsPostRequestBody();
retrieveCloudPcRecommendationReportsPostRequestBody.setReportType(CloudPcRecommendationReportType.CloudPcUsageCategoryReport);
retrieveCloudPcRecommendationReportsPostRequestBody.setFilter("");
LinkedList<String> select = new LinkedList<String>();
select.add("CloudPcId");
select.add("ManagedDeviceName");
select.add("UserPrincipalName");
select.add("ServicePlanId");
select.add("ServicePlanName");
select.add("UsageInsight");
select.add("RecommendedPlanId");
select.add("RecommendedPlanName");
retrieveCloudPcRecommendationReportsPostRequestBody.setSelect(select);
retrieveCloudPcRecommendationReportsPostRequestBody.setSearch("");
retrieveCloudPcRecommendationReportsPostRequestBody.setSkip(0);
retrieveCloudPcRecommendationReportsPostRequestBody.setTop(15);
graphClient.deviceManagement().virtualEndpoint().report().retrieveCloudPcRecommendationReports().post(retrieveCloudPcRecommendationReportsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stream = {
  reportType: 'cloudPcUsageCategoryReport',
  filter: '',
  select: [
    'CloudPcId',
    'ManagedDeviceName',
    'UserPrincipalName',
    'ServicePlanId',
    'ServicePlanName',
    'UsageInsight',
    'RecommendedPlanId',
    'RecommendedPlanName'
  ],
  search: '',
  skip: 0,
  top: 15
};

await client.api('/deviceManagement/virtualEndpoint/report/retrieveCloudPcRecommendationReports')
	.post(stream);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DeviceManagement\VirtualEndpoint\Report\RetrieveCloudPcRecommendationReports\RetrieveCloudPcRecommendationReportsPostRequestBody;
use Microsoft\Graph\Generated\Models\CloudPcRecommendationReportType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RetrieveCloudPcRecommendationReportsPostRequestBody();
$requestBody->setReportType(new CloudPcRecommendationReportType('cloudPcUsageCategoryReport'));
$requestBody->setFilter('');
$requestBody->setSelect(['CloudPcId', 'ManagedDeviceName', 'UserPrincipalName', 'ServicePlanId', 'ServicePlanName', 'UsageInsight', 'RecommendedPlanId', 'RecommendedPlanName', 	]);
$requestBody->setSearch('');
$requestBody->setSkip(0);
$requestBody->setTop(15);

$graphServiceClient->deviceManagement()->virtualEndpoint()->report()->retrieveCloudPcRecommendationReports()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

$params = @{
	reportType = "cloudPcUsageCategoryReport"
	filter = ""
	select = @(
	"CloudPcId"
"ManagedDeviceName"
"UserPrincipalName"
"ServicePlanId"
"ServicePlanName"
"UsageInsight"
"RecommendedPlanId"
"RecommendedPlanName"
)
search = ""
skip = 0
top = 15
}

Get-MgDeviceManagementVirtualEndpointReportCloudPcRecommendationReport -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.devicemanagement.virtualendpoint.report.retrieve_cloud_pc_recommendation_reports.retrieve_cloud_pc_recommendation_reports_post_request_body import RetrieveCloudPcRecommendationReportsPostRequestBody
from msgraph.generated.models.cloud_pc_recommendation_report_type import CloudPcRecommendationReportType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RetrieveCloudPcRecommendationReportsPostRequestBody(
	report_type = CloudPcRecommendationReportType.CloudPcUsageCategoryReport,
	filter = "",
	select = [
		"CloudPcId",
		"ManagedDeviceName",
		"UserPrincipalName",
		"ServicePlanId",
		"ServicePlanName",
		"UsageInsight",
		"RecommendedPlanId",
		"RecommendedPlanName",
	],
	search = "",
	skip = 0,
	top = 15,
)

await graph_client.device_management.virtual_endpoint.report.retrieve_cloud_pc_recommendation_reports.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

{
  "TotalRowCount": 15,
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
      "Column": "ServicePlanId",
      "PropertyType": "String"
    },
    {
      "Column": "ServicePlanName",
      "PropertyType": "String"
    },
    {
      "Column": "UsageInsight",
      "PropertyType": "String"
    },
    {
      "Column": "RecommendedPlanId",
      "PropertyType": "String"
    },
    {
      "Column": "RecommendedPlanName",
      "PropertyType": "String"
    }
  ],
  "Values": [
    [
      "1f574bb6-ac68-4f27-be1e-b810ae5e3b52",
      "CPC-Test-001",
      "test001@fabrikam.com",
      "d3468c8c-3545-4f44-a32f-b465934d2498",
      "Cloud PC Enterprise 2vCPU/8GB/256GB",
      "Undersized",
      "2de9c682-ca3f-4f2b-b360-dfc4775db133",
      "Cloud PC Enterprise 4vCPU/16GB/128GB"
    ],
    [
      "37ea6497-83fb-474b-b07b-54f0ac16f3ed",
      "CPC-Test-002",
      "test002@fabrikam.com",
      "d3468c8c-3545-4f44-a32f-b465934d2498",
      "Cloud PC Enterprise 2vCPU/8GB/256GB",
      "Oversized",
      "0d143570-9b92-4f57-adb5-e4efcd23b3bb",
      "Cloud PC Enterprise 2vCPU/4GB/256GB"
    ],
    [
      "4c6a1fb2-1ac7-40fc-a213-fb0eaec872f3",
      "CPC-Test-003",
      "test003@fabrikam.com",
      "d3468c8c-3545-4f44-a32f-b465934d2498",
      "Cloud PC Enterprise 2vCPU/8GB/256GB",
      "Rightsized",
      null,
      null
    ],
    [
      "632dbe76-2fe3-4a2f-8b91-8514ecfe9d8c",
      "CPC-Test-004",
      "test004@fabrikam.com",
      "d3468c8c-3545-4f44-a32f-b465934d2498",
      "Cloud PC Enterprise 2vCPU/8GB/256GB",
      "Underutilized",
      null,
      null
    ]
  ]
}
```
