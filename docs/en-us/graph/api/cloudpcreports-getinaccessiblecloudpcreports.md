<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getinaccessiblecloudpcreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-21 -->

# cloudPcReports: getInaccessibleCloudPcReports

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get inaccessible Cloud PCs with details, including the latest health state, failed connection count, failed health check count, and system status. An inaccessible Cloud PC represents a Cloud PC that is in an unavailable state \(at least one of the health checks failed\) or has consecutive user connections failure.

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
POST /deviceManagement/virtualEndpoint/reports/getInaccessibleCloudPcReports
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Prefer: include-unknown-enum-members | Enables evolvable enum values beyond the sentinel value. For more information, see [Best practices for working with Microsoft Graph](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Optional. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that you can use with this method.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| filter | String | OData `$filter` syntax. Only `and`, `or`, `gt` ,`ge` and `eq` are currently supported. |
| groupBy | String collection | Specifies how to group the reports. If used, must have the same content as the select parameter. |
| orderBy | String collection | Specifies how to sort the reports. |
| reportName | cloudPCInaccessibleReportName | The report name. The possible values are: `inaccessibleCloudPcReports`, `inaccessibleCloudPcTrendReport`, `unknownFutureValue`, `regionalInaccessibleCloudPcTrendReport`. The default value is `inaccessibleCloudPcReports` if the **reportName** is empty. You must use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `regionalInaccessibleCloudPcTrendReport`. |
| search | String | Specifies a String to search for. |
| select | String collection | OData `$select` syntax. Represents the selected columns of the reports. |
| skip | Int32 | Number of records to skip. |
| top | Int32 | The number of top records to return. |

### cloudPCInaccessibleReportName values

| Member | Description |
| :--- | :--- |
| inaccessibleCloudPcReports | Indicates a report that contains details of Cloud PCs that are inaccessible, including those with consecutive connection failures or in an unavailable state. |
| inaccessibleCloudPcTrendReport | Indicates a daily aggregated report for a specified period that contains details of Cloud PCs that are inaccessible, including those with consecutive connection failures or in an unavailable state. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| regionalInaccessibleCloudPcTrendReport | Indicates the weekly regional aggregated report of inaccessible Cloud PC trends. |

## Response

If successful, this method returns a `200 OK` response code and a Stream object in the response body.

The following table describes the columns in the returned report when you specify `inaccessibleCloudPcReports` for the **reportName** property in your API call. For `inaccessibleCloudPcReports`, the member values must be in camel case format.

| Member | Description |
| :--- | :--- |
| cloudPcId | The unique identifier of the Cloud PC. |
| cloudPcName | The display name of the Cloud PC. |
| deviceHealthStatus | The current health status of the Cloud PC device. |
| deviceHealthStatusDateTime | The date and time when the device health status was last updated. |
| provisioningStatus | The provisioning status of the Cloud PC. |
| recentConnectionFailureCount | The count of recent connection failures for the Cloud PC. |
| recentDeviceHealthFailureCount | The count of recent device health check failures. |
| region | The Azure region where the Cloud PC is hosted. |
| systemStatus | The current system status of the Cloud PC. |
| systemStatusDateTime | The date and time when the system status was last updated. |
| userPrincipalName | The user principal name \(UPN\) of the user assigned to the Cloud PC. |

The following table describes the columns in the returned report when you specify `regionalInaccessibleCloudPcTrendReport` for the **reportName** property in your API call.

| Member | Description |
| :--- | :--- |
| CloudPcCount | The total number of Cloud PCs in the region. |
| HostRegionName | The name of the Azure region where the Cloud PCs are hosted. |
| Last24hPeakInaccessibleCloudPcCount | The peak number of inaccessible Cloud PCs during the last 24 hours. |
| WeeklyInaccessibleTrend | The trend in the weekly ratio of inaccessible Cloud PCs to the total Cloud PC count in the region. The trend is calculated using linear regression over four weeks of data. Values can be `Increasing` \(slope > 0.05\), `Decreasing` \(slope < -0.05\), or `Static` \(otherwise\). |
| WeeklyPeakInaccessibleCloudPcCount | The peak number of inaccessible Cloud PCs during the current week. The weekly period starts from Sunday to the current day. |

## Examples

### Example 1: Get reports of inaccessible Cloud PCs in a specific region

The following example shows how to get reports of inaccessible Cloud PCs in a specific region.

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getInaccessibleCloudPcReports
Content-Type: application/json
Content-length: 199

{
  "filter": "region eq 'westus2'",
  "orderBy": [
    "cloudPcId"
  ],
  "select": [
    "cloudPcId",
    "aadDeviceId",
    "cloudPcName",
    "userPrincipalName",
    "provisioningStatus",
    "region",
    "deviceHealthStatus",
    "deviceHealthStatusDateTime",
    "recentDeviceHealthFailureCount",
    "recentConnectionFailureCount",
    "systemStatus",
    "systemStatusDateTime"
  ],
  "top": 10,
  "skip": 0
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.GetInaccessibleCloudPcReports;

var requestBody = new GetInaccessibleCloudPcReportsPostRequestBody
{
	Filter = "region eq 'westus2'",
	OrderBy = new List<string>
	{
		"cloudPcId",
	},
	Select = new List<string>
	{
		"cloudPcId",
		"aadDeviceId",
		"cloudPcName",
		"userPrincipalName",
		"provisioningStatus",
		"region",
		"deviceHealthStatus",
		"deviceHealthStatusDateTime",
		"recentDeviceHealthFailureCount",
		"recentConnectionFailureCount",
		"systemStatus",
		"systemStatusDateTime",
	},
	Top = 10,
	Skip = 0,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.GetInaccessibleCloudPcReports.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewGetInaccessibleCloudPcReportsPostRequestBody()
filter := "region eq 'westus2'"
requestBody.SetFilter(&filter) 
orderBy := []string {
	"cloudPcId",
}
requestBody.SetOrderBy(orderBy)
select := []string {
	"cloudPcId",
	"aadDeviceId",
	"cloudPcName",
	"userPrincipalName",
	"provisioningStatus",
	"region",
	"deviceHealthStatus",
	"deviceHealthStatusDateTime",
	"recentDeviceHealthFailureCount",
	"recentConnectionFailureCount",
	"systemStatus",
	"systemStatusDateTime",
}
requestBody.SetSelect(select)
top := int32(10)
requestBody.SetTop(&top) 
skip := int32(0)
requestBody.SetSkip(&skip) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().GetInaccessibleCloudPcReports().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getinaccessiblecloudpcreports.GetInaccessibleCloudPcReportsPostRequestBody getInaccessibleCloudPcReportsPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getinaccessiblecloudpcreports.GetInaccessibleCloudPcReportsPostRequestBody();
getInaccessibleCloudPcReportsPostRequestBody.setFilter("region eq 'westus2'");
LinkedList<String> orderBy = new LinkedList<String>();
orderBy.add("cloudPcId");
getInaccessibleCloudPcReportsPostRequestBody.setOrderBy(orderBy);
LinkedList<String> select = new LinkedList<String>();
select.add("cloudPcId");
select.add("aadDeviceId");
select.add("cloudPcName");
select.add("userPrincipalName");
select.add("provisioningStatus");
select.add("region");
select.add("deviceHealthStatus");
select.add("deviceHealthStatusDateTime");
select.add("recentDeviceHealthFailureCount");
select.add("recentConnectionFailureCount");
select.add("systemStatus");
select.add("systemStatusDateTime");
getInaccessibleCloudPcReportsPostRequestBody.setSelect(select);
getInaccessibleCloudPcReportsPostRequestBody.setTop(10);
getInaccessibleCloudPcReportsPostRequestBody.setSkip(0);
graphClient.deviceManagement().virtualEndpoint().reports().getInaccessibleCloudPcReports().post(getInaccessibleCloudPcReportsPostRequestBody);
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
  filter: 'region eq \'westus2\'',
  orderBy: [
    'cloudPcId'
  ],
  select: [
    'cloudPcId',
    'aadDeviceId',
    'cloudPcName',
    'userPrincipalName',
    'provisioningStatus',
    'region',
    'deviceHealthStatus',
    'deviceHealthStatusDateTime',
    'recentDeviceHealthFailureCount',
    'recentConnectionFailureCount',
    'systemStatus',
    'systemStatusDateTime'
  ],
  top: 10,
  skip: 0
};

await client.api('/deviceManagement/virtualEndpoint/reports/getInaccessibleCloudPcReports')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\GetInaccessibleCloudPcReports\GetInaccessibleCloudPcReportsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetInaccessibleCloudPcReportsPostRequestBody();
$requestBody->setFilter('region eq \'westus2\'');
$requestBody->setOrderBy(['cloudPcId', 	]);
$requestBody->setSelect(['cloudPcId', 'aadDeviceId', 'cloudPcName', 'userPrincipalName', 'provisioningStatus', 'region', 'deviceHealthStatus', 'deviceHealthStatusDateTime', 'recentDeviceHealthFailureCount', 'recentConnectionFailureCount', 'systemStatus', 'systemStatusDateTime', 	]);
$requestBody->setTop(10);
$requestBody->setSkip(0);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->getInaccessibleCloudPcReports()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.get_inaccessible_cloud_pc_reports.get_inaccessible_cloud_pc_reports_post_request_body import GetInaccessibleCloudPcReportsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetInaccessibleCloudPcReportsPostRequestBody(
	filter = "region eq 'westus2'",
	order_by = [
		"cloudPcId",
	],
	select = [
		"cloudPcId",
		"aadDeviceId",
		"cloudPcName",
		"userPrincipalName",
		"provisioningStatus",
		"region",
		"deviceHealthStatus",
		"deviceHealthStatusDateTime",
		"recentDeviceHealthFailureCount",
		"recentConnectionFailureCount",
		"systemStatus",
		"systemStatusDateTime",
	],
	top = 10,
	skip = 0,
)

await graph_client.device_management.virtual_endpoint.reports.get_inaccessible_cloud_pc_reports.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

{
  "TotalRowCount": 2,
  "Schema": [
    {
      "Column": "cloudPcId",
      "PropertyType": "String"
    },
    {
      "Column": "aadDeviceId",
      "PropertyType": "String"
    },
    {
      "Column": "cloudPcName",
      "PropertyType": "String"
    },
    {
      "Column": "userPrincipalName",
      "PropertyType": "String"
    },
    {
      "Column": "provisioningStatus",
      "PropertyType": "String"
    },
    {
      "Column": "region",
      "PropertyType": "String"
    },
    {
      "Column": "deviceHealthStatus",
      "PropertyType": "String"
    },
    {
      "Column": "deviceHealthStatusDateTime",
      "PropertyType": "DateTime"
    },
    {
      "Column": "recentDeviceHealthFailureCount",
      "PropertyType": "Int32"
    },
    {
      "Column": "recentConnectionFailureCount",
      "PropertyType": "Int64"
    },
    {
      "Column": "systemStatus",
      "PropertyType": "String"
    },
    {
      "Column": "systemStatusDateTime",
      "PropertyType": "DateTime"
    }
  ],
  "Values": [
    [
      "04e279c5-b228-4700-93c3-6f1339c7c86d",
      "a8f78191-8e43-4165-9191-16867d372161",
      "CPC-test1-VGTEK",
      "bob@fabrikam.com",
      "Provisioned",
      "westus2",
      "ErrorVMNotRunning",
      "2023-06-26T03:55:04",
      3,
      0,
      "",
      null
    ],
    [
      "818ff73d-9764-4412-ad99-fc65a396daf3",
      "daefef60-a912-4180-a5c0-f607e346878f",
      "CPC-test2-C84W3",
      "megan@fabrikam.com",
      "Provisioned",
      "westus2",
      "ErrorVMNotRunning",
      "2023-06-26T04:03:49",
      3,
      0,
      "",
      null
    ]
  ]
}
```

### Example 2: Get the weekly regional aggregated report of inaccessible Cloud PC trends

The following example shows how to get the weekly regional aggregated report of inaccessible Cloud PC trends.

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getInaccessibleCloudPcReports
Content-Type: application/json
Prefer: include-unknown-enum-members

{
  "reportName": "regionalInaccessibleCloudPcTrendReport",
  "filter": "",
  "select": [
    "HostRegionName",
    "CloudPcCount",
    "WeeklyPeakInaccessibleCloudPcCount",
    "Last24hPeakInaccessibleCloudPcCount",
    "WeeklyInaccessibleTrend"
  ],
  "search": "",
  "skip": 0,
  "top": 50
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

{
  "TotalRowCount": 2,
  "Schema": [
    {
      "Column": "HostRegionName",
      "PropertyType": "String"
    },
    {
      "Column": "CloudPcCount",
      "PropertyType": "Int64"
    },
    {
      "Column": "WeeklyPeakInaccessibleCloudPcCount",
      "PropertyType": "Int64"
    },
    {
      "Column": "Last24hPeakInaccessibleCloudPcCount",
      "PropertyType": "Int64"
    },
    {
      "Column": "WeeklyInaccessibleTrend",
      "PropertyType": "String"
    }
  ],
  "Values": [
    [ "Japan East", 46, 10, 5, "Increasing" ],
    [ "East US", 1, 0, 0, "Decreasing" ]
  ]
}
```
