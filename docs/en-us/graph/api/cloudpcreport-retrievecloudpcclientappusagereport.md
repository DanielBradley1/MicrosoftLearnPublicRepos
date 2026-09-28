<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreport-retrievecloudpcclientappusagereport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# cloudPcReport: retrieveCloudPcClientAppUsageReport

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve related [reports](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreport?view=graph-rest-beta) on Cloud PC usage, including the client application used by users to sign in to the Cloud PC device.

The Remote Desktop client standalone installer \(MSI\) for Windows will reach end of support on March 27, 2026. Before that date, IT administrators should migrate users to Windows App to ensure continued access to remote resources through Azure Virtual Desktop, Windows 365, and Microsoft Dev Box. [Learn](https://techcommunity.microsoft.com/blog/windows-itpro-blog/prepare-for-the-remote-desktop-client-for-windows-end-of-support/4397724) more about preparing for the Remote Desktop Client for Windows end of support.

This API enables IT administrators to check the migration status by confirming whether users are still using the legacy Remote Desktop client and identifying their last sign-in dates, thereby helping monitor progress and ensure compliance with migration requirements.

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
POST /deviceManagement/virtualEndpoint/report/retrieveCloudPcClientAppUsageReport
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this method.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| filter | String | OData `$filter` syntax. Supported filters are: `and`, `or`, `lt`, `le`, `gt`, `ge`, and `eq`. Optional. |
| groupBy | String collection | Specifies how to group the reports. If used, must have the same content as the **select** parameter. Optional. |
| orderBy | String collection | Specifies how to sort the reports. Optional. |
| reportType | [cloudPcClientAppUsageReportType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreport?view=graph-rest-beta#cloudpcclientappusagereporttype-values) | The report type. The supported value is `microsoftRemoteDesktopClientUsageReport`. Required. |
| search | String | Specifies a String to search. Optional. |
| select | String collection | OData `$select` syntax. The selected columns of the reports. Optional. |
| skip | Int32 | Number of records to skip. Optional. |
| top | Int32 | The number of top records to return. Optional. |

## Response

If successful, this method returns a `200 OK` response code and a Stream object in the response body.

The following table explains the schema in the response.

| Column | Type | Description |
| :--- | :--- | :--- |
| UPN | String | The user principal name. |
| LastSignOn | String | The date when the user last signed in using the legacy Remote Desktop client. The format is YYYY-MM-DD and always in UTC time. |
| DaysWithUsage | String | The total number of days the user signed in through the legacy Remote Desktop client in the last 28 days, calculated using UTC time. |

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/report/retrieveCloudPcClientAppUsageReport
Content-Type: application/json

{
    "filter": "",
    "reportType":"microsoftRemoteDesktopClientUsageReport",
    "select": ["UPN", "LastSignOn", "DaysWithUsage"],
    "search": "",
    "skip": 0,
    "top": 50
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Report.RetrieveCloudPcClientAppUsageReport;
using Microsoft.Graph.Beta.Models;

var requestBody = new RetrieveCloudPcClientAppUsageReportPostRequestBody
{
	Filter = "",
	ReportType = CloudPcClientAppUsageReportType.MicrosoftRemoteDesktopClientUsageReport,
	Select = new List<string>
	{
		"UPN",
		"LastSignOn",
		"DaysWithUsage",
	},
	Search = "",
	Skip = 0,
	Top = 50,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Report.RetrieveCloudPcClientAppUsageReport.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewRetrieveCloudPcClientAppUsageReportPostRequestBody()
filter := ""
requestBody.SetFilter(&filter) 
reportType := graphmodels.MICROSOFTREMOTEDESKTOPCLIENTUSAGEREPORT_CLOUDPCCLIENTAPPUSAGEREPORTTYPE 
requestBody.SetReportType(&reportType) 
select := []string {
	"UPN",
	"LastSignOn",
	"DaysWithUsage",
}
requestBody.SetSelect(select)
search := ""
requestBody.SetSearch(&search) 
skip := int32(0)
requestBody.SetSkip(&skip) 
top := int32(50)
requestBody.SetTop(&top) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Report().RetrieveCloudPcClientAppUsageReport().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.report.retrievecloudpcclientappusagereport.RetrieveCloudPcClientAppUsageReportPostRequestBody retrieveCloudPcClientAppUsageReportPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.report.retrievecloudpcclientappusagereport.RetrieveCloudPcClientAppUsageReportPostRequestBody();
retrieveCloudPcClientAppUsageReportPostRequestBody.setFilter("");
retrieveCloudPcClientAppUsageReportPostRequestBody.setReportType(CloudPcClientAppUsageReportType.MicrosoftRemoteDesktopClientUsageReport);
LinkedList<String> select = new LinkedList<String>();
select.add("UPN");
select.add("LastSignOn");
select.add("DaysWithUsage");
retrieveCloudPcClientAppUsageReportPostRequestBody.setSelect(select);
retrieveCloudPcClientAppUsageReportPostRequestBody.setSearch("");
retrieveCloudPcClientAppUsageReportPostRequestBody.setSkip(0);
retrieveCloudPcClientAppUsageReportPostRequestBody.setTop(50);
graphClient.deviceManagement().virtualEndpoint().report().retrieveCloudPcClientAppUsageReport().post(retrieveCloudPcClientAppUsageReportPostRequestBody);
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
    filter: '',
    reportType: 'microsoftRemoteDesktopClientUsageReport',
    select: ['UPN', 'LastSignOn', 'DaysWithUsage'],
    search: '',
    skip: 0,
    top: 50
};

await client.api('/deviceManagement/virtualEndpoint/report/retrieveCloudPcClientAppUsageReport')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Report\RetrieveCloudPcClientAppUsageReport\RetrieveCloudPcClientAppUsageReportPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\CloudPcClientAppUsageReportType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RetrieveCloudPcClientAppUsageReportPostRequestBody();
$requestBody->setFilter('');
$requestBody->setReportType(new CloudPcClientAppUsageReportType('microsoftRemoteDesktopClientUsageReport'));
$requestBody->setSelect(['UPN', 'LastSignOn', 'DaysWithUsage', 	]);
$requestBody->setSearch('');
$requestBody->setSkip(0);
$requestBody->setTop(50);

$graphServiceClient->deviceManagement()->virtualEndpoint()->report()->retrieveCloudPcClientAppUsageReport()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.report.retrieve_cloud_pc_client_app_usage_report.retrieve_cloud_pc_client_app_usage_report_post_request_body import RetrieveCloudPcClientAppUsageReportPostRequestBody
from msgraph_beta.generated.models.cloud_pc_client_app_usage_report_type import CloudPcClientAppUsageReportType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RetrieveCloudPcClientAppUsageReportPostRequestBody(
	filter = "",
	report_type = CloudPcClientAppUsageReportType.MicrosoftRemoteDesktopClientUsageReport,
	select = [
		"UPN",
		"LastSignOn",
		"DaysWithUsage",
	],
	search = "",
	skip = 0,
	top = 50,
)

await graph_client.device_management.virtual_endpoint.report.retrieve_cloud_pc_client_app_usage_report.post(request_body)
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
            "Column": "UPN",
            "PropertyType": "String"
        },
        {
            "Column": "LastSignOn",
            "PropertyType": "String"
        },
        {
            "Column": "DaysWithUsage",
            "PropertyType": "Int64"
        }
    ],
    "Values" :[
        ["test001@contoso.onmicrosoft.com", "2025-10-28", 10],
        ["test002@contoso.onmicrosoft.com", "2025-10-30",  5],
        ["test003@contoso.onmicrosoft.com", "2025-10-31", 19]
    ]
}
```
