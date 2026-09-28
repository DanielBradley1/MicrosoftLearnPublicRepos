<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getfrontlinereport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# cloudPcReports: getFrontlineReport

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the [Windows 365 Frontline](https://www.microsoft.com/en/windows-365/frontline) reports, such as real-time or historical data reports.

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
POST /deviceManagement/virtualEndpoint/reports/getFrontlineReport
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
| reportName | String | Specifies the report name. |
| filter | String | OData filter syntax. Supported filters include `and`, `or`, `lt`, `le`, `gt`, `ge`, and `eq`. |
| select | String collection | OData select syntax. Represents the selected columns of the reports. |
| search | String | Specifies a string to search. |
| groupBy | String collection | Specifies how to group the reports. If used, must have the same content as the **select** parameter. |
| orderBy | String collection | Specifies how to sort the reports. |
| skip | Int32 | The number of records to skip. |
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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getFrontlineReport
Content-Type: application/json
Content-length: 199

{
    "reportName": "frontlineLicenseUsageReport",
    "filter": "ServicePlanId eq '2d1d344e-d10c-41bb-953b-b3a47521dca0' and DateTimeUTC gt datetime'2022-11-30'",
    "select":["ServicePlanId", "LicenseCount", "ClaimedLicenseCount", "DateTimeUTC"],
    "skip": 0,
    "top": 100
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.GetFrontlineReport;
using Microsoft.Graph.Beta.Models;

var requestBody = new GetFrontlineReportPostRequestBody
{
	ReportName = CloudPcReportName.FrontlineLicenseUsageReport,
	Filter = "ServicePlanId eq '2d1d344e-d10c-41bb-953b-b3a47521dca0' and DateTimeUTC gt datetime'2022-11-30'",
	Select = new List<string>
	{
		"ServicePlanId",
		"LicenseCount",
		"ClaimedLicenseCount",
		"DateTimeUTC",
	},
	Skip = 0,
	Top = 100,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.GetFrontlineReport.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewGetFrontlineReportPostRequestBody()
reportName := graphmodels.FRONTLINELICENSEUSAGEREPORT_CLOUDPCREPORTNAME 
requestBody.SetReportName(&reportName) 
filter := "ServicePlanId eq '2d1d344e-d10c-41bb-953b-b3a47521dca0' and DateTimeUTC gt datetime'2022-11-30'"
requestBody.SetFilter(&filter) 
select := []string {
	"ServicePlanId",
	"LicenseCount",
	"ClaimedLicenseCount",
	"DateTimeUTC",
}
requestBody.SetSelect(select)
skip := int32(0)
requestBody.SetSkip(&skip) 
top := int32(100)
requestBody.SetTop(&top) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().GetFrontlineReport().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getfrontlinereport.GetFrontlineReportPostRequestBody getFrontlineReportPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getfrontlinereport.GetFrontlineReportPostRequestBody();
getFrontlineReportPostRequestBody.setReportName(CloudPcReportName.FrontlineLicenseUsageReport);
getFrontlineReportPostRequestBody.setFilter("ServicePlanId eq '2d1d344e-d10c-41bb-953b-b3a47521dca0' and DateTimeUTC gt datetime'2022-11-30'");
LinkedList<String> select = new LinkedList<String>();
select.add("ServicePlanId");
select.add("LicenseCount");
select.add("ClaimedLicenseCount");
select.add("DateTimeUTC");
getFrontlineReportPostRequestBody.setSelect(select);
getFrontlineReportPostRequestBody.setSkip(0);
getFrontlineReportPostRequestBody.setTop(100);
graphClient.deviceManagement().virtualEndpoint().reports().getFrontlineReport().post(getFrontlineReportPostRequestBody);
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
    reportName: 'frontlineLicenseUsageReport',
    filter: 'ServicePlanId eq \'2d1d344e-d10c-41bb-953b-b3a47521dca0\' and DateTimeUTC gt datetime\'2022-11-30\'',
    select: ['ServicePlanId', 'LicenseCount', 'ClaimedLicenseCount', 'DateTimeUTC'],
    skip: 0,
    top: 100
};

await client.api('/deviceManagement/virtualEndpoint/reports/getFrontlineReport')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\GetFrontlineReport\GetFrontlineReportPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\CloudPcReportName;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetFrontlineReportPostRequestBody();
$requestBody->setReportName(new CloudPcReportName('frontlineLicenseUsageReport'));
$requestBody->setFilter('ServicePlanId eq \'2d1d344e-d10c-41bb-953b-b3a47521dca0\' and DateTimeUTC gt datetime\'2022-11-30\'');
$requestBody->setSelect(['ServicePlanId', 'LicenseCount', 'ClaimedLicenseCount', 'DateTimeUTC', 	]);
$requestBody->setSkip(0);
$requestBody->setTop(100);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->getFrontlineReport()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.get_frontline_report.get_frontline_report_post_request_body import GetFrontlineReportPostRequestBody
from msgraph_beta.generated.models.cloud_pc_report_name import CloudPcReportName
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetFrontlineReportPostRequestBody(
	report_name = CloudPcReportName.FrontlineLicenseUsageReport,
	filter = "ServicePlanId eq '2d1d344e-d10c-41bb-953b-b3a47521dca0' and DateTimeUTC gt datetime'2022-11-30'",
	select = [
		"ServicePlanId",
		"LicenseCount",
		"ClaimedLicenseCount",
		"DateTimeUTC",
	],
	skip = 0,
	top = 100,
)

await graph_client.device_management.virtual_endpoint.reports.get_frontline_report.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

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
      "name": "ServicePlanId",
      "type": "String"
    },
    {
      "name": "LicenseCount",
      "type": "Int32"
    },
    {
      "name": "ClaimedLicenseCount",
      "type": "Int32"
    },
    {
      "name": "DateTimeUTC",
      "type": "DateTime"
    }
  ],
  "Values": [
    [
      "2d1d344e-d10c-41bb-953b-b3a47521dca0", 100, 10, "2022-12-02T00:00:00"
    ],
    [
      "2d1d344e-d10c-41bb-953b-b3a47521dca0", 100, 11, "2022-12-01T00:00:00"
    ]
  ]
}
```
