<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecloudpctroubleshootreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# cloudPcReports: retrieveCloudPcTroubleshootReports

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get Cloud PC troubleshooting reports. You can get tenant-level reports, configuration reports, user and device reports, and view data table reports. For the report types grouped by scope, including the mandatory filter parameters and response columns per `reportName`, see [Cloud PC troubleshoot report types](https://learn.microsoft.com/en-us/graph/cloudpc-troubleshoot-report-types).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.Read.All | CloudPC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.Read.All | CloudPC.ReadWrite.All |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/reports/retrieveCloudPcTroubleshootReports
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| filter | String | OData `$filter` syntax. Supported filters are: `and`, `or`, `gt`, `ge`, and `eq`. Required for most **reportName** values, but optional for some. For the mandatory filter parameters per **reportName**, see [Cloud PC troubleshoot report types](https://learn.microsoft.com/en-us/graph/cloudpc-troubleshoot-report-types). |
| groupBy | String collection | A list of columns that describe how to group the data in the report. Optional. |
| orderBy | String collection | Specifies the order by column name. Optional. |
| reportName | [cloudPCTroubleshootReportType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreports?view=graph-rest-beta#cloudpctroubleshootreporttype-values) | The report name. The possible values are: `troubleshootTenantGlobalFilterReport`, `troubleshootTenantNetworkTrendReport`, `troubleshootTenantNetworkAggregatedReport`, `troubleshootTenantConnectionFailureRateTrendReport`, `troubleshootTenantConnectionFailureRateAggregatedReport`, `troubleshootTenantCloudPCHealthTrendReport`, `troubleshootTenantCloudPCHealthAggregatedReport`, `troubleshootTenantActiveConnectionCountTrendReport`, `troubleshootTenantActiveConnectionCountAggregatedReport`, `troubleshootTenantMeanTimeToFailureTrendReport`, `troubleshootTenantMeanTimeToFailureAggregatedReport`, `troubleshootTenantRemoteSignInTimeTrendReport`, `troubleshootTenantRemoteSignInTimeAggregatedReport`, `troubleshootEventsOfViewDataTableReport`, `troubleshootTenantEnvironmentMetricsOfViewDataTableReport`, `troubleshootCloudPCMetricsOfViewDataTableReport`, `troubleshootConfigurationConnectionCountTrendV1Report`, `troubleshootConfigurationTotalConnectionCountBarV1Report`, `troubleshootConfigurationGlobalFilterV1Report`, `troubleshootConnectionConfigurationOfViewDataTableV1Report`, `troubleshootTenantConnectedDevicesOfViewDataTableReport`, `troubleshootEnvironmentOverviewOfViewDataTableReport`, `troubleshootCloudPCNetworkTrendReport`, `troubleshootCloudPCNetworkAggregatedReport`, `troubleshootCloudPCErrorTrendReport`, `troubleshootCloudPCErrorAggregatedReport`, `troubleshootCloudPCDurationTrendReport`, `troubleshootCloudPCDurationAggregatedReport`, `troubleshootCloudPCRemoteSignInTimeTrendReport`, `troubleshootCloudPCRemoteSignInTimeAggregatedReport`, `troubleshootCloudPCListReport`, `troubleshootCloudPCHealthTrendReport`, `troubleshootMatchedUserReport`, `troubleshootMatchedCloudPCReport`, `troubleshootUserListReport`, `unknownFutureValue`. For the report type description and scope grouping, see [Cloud PC troubleshoot report types](https://learn.microsoft.com/en-us/graph/cloudpc-troubleshoot-report-types). Use the `Prefer: include-unknown-enum-members` request header to receive future members added to this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) by their actual name instead of `unknownFutureValue`. Required. |
| search | String | The search string. Optional. |
| select | String collection | OData `$select` syntax. The selected columns of the reports. Optional. |
| skip | Int32 | Number of records to skip. Optional. |
| top | Int32 | The number of top records to return. If not specified, the default limit is 25, with a maximum of 1000. Optional. |

Parameter values can be empty strings \(`''`\) if you don't want to filter on that dimension, unless the report type marks them as required. The maximum supported date range is 28 days for tenant-level and user and device reports, and 180 days for configuration-level reports.

## Response

If successful, this action returns a `200 OK` response code and a Stream in the response body. The columns returned in the Stream vary by **reportName**. For the response columns per **reportName**, see [Cloud PC troubleshoot report types](https://learn.microsoft.com/en-us/graph/cloudpc-troubleshoot-report-types).

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/retrieveCloudPcTroubleshootReports
Content-Type: application/json

{
  "reportName": "troubleshootTenantActiveConnectionCountTrendReport",
  "select": [
    "EventDateTime",
    "TotalActiveConnectionCountAvg",
    "GroupColumn"
  ],
  "filter": "(TimeRange eq 'Last 7 days') and (PolicyNameParam eq '') and (RegionParam eq '') and (UserSettingNameParam eq '') and (ServicePlanTypeParam eq 'Enterprise') and (ServicePlanNameParam eq '') and (OSBuildVersionParam eq '') and (AADJoinTypeParam eq '') and (ImageNameParam eq '') and (GatewayRegionParam eq '') and (ClientOSParam eq '') and (ClientTypeParam eq '') and (TransportTypeParam eq '') and (CloudPCEndpointCountryRegionParam eq '') and (CloudPCEndpointStateParam eq '') and (CloudPCEndpointCityParam eq '')",
  "top": 1000,
  "skip": 0,
  "groupBy": [
    "GatewayRegion"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.RetrieveCloudPcTroubleshootReports;
using Microsoft.Graph.Beta.Models;

var requestBody = new RetrieveCloudPcTroubleshootReportsPostRequestBody
{
	ReportName = CloudPCTroubleshootReportType.TroubleshootDetailsReport,
	Select = new List<string>
	{
		"EventDateTime",
		"TotalActiveConnectionCountAvg",
		"GroupColumn",
	},
	Filter = "(TimeRange eq 'Last 7 days') and (PolicyNameParam eq '') and (RegionParam eq '') and (UserSettingNameParam eq '') and (ServicePlanTypeParam eq 'Enterprise') and (ServicePlanNameParam eq '') and (OSBuildVersionParam eq '') and (AADJoinTypeParam eq '') and (ImageNameParam eq '') and (GatewayRegionParam eq '') and (ClientOSParam eq '') and (ClientTypeParam eq '') and (TransportTypeParam eq '') and (CloudPCEndpointCountryRegionParam eq '') and (CloudPCEndpointStateParam eq '') and (CloudPCEndpointCityParam eq '')",
	Top = 1000,
	Skip = 0,
	GroupBy = new List<string>
	{
		"GatewayRegion",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.RetrieveCloudPcTroubleshootReports.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewRetrieveCloudPcTroubleshootReportsPostRequestBody()
reportName := graphmodels.TROUBLESHOOTTENANTACTIVECONNECTIONCOUNTTRENDREPORT_CLOUDPCTROUBLESHOOTREPORTTYPE 
requestBody.SetReportName(&reportName) 
select := []string {
	"EventDateTime",
	"TotalActiveConnectionCountAvg",
	"GroupColumn",
}
requestBody.SetSelect(select)
filter := "(TimeRange eq 'Last 7 days') and (PolicyNameParam eq '') and (RegionParam eq '') and (UserSettingNameParam eq '') and (ServicePlanTypeParam eq 'Enterprise') and (ServicePlanNameParam eq '') and (OSBuildVersionParam eq '') and (AADJoinTypeParam eq '') and (ImageNameParam eq '') and (GatewayRegionParam eq '') and (ClientOSParam eq '') and (ClientTypeParam eq '') and (TransportTypeParam eq '') and (CloudPCEndpointCountryRegionParam eq '') and (CloudPCEndpointStateParam eq '') and (CloudPCEndpointCityParam eq '')"
requestBody.SetFilter(&filter) 
top := int32(1000)
requestBody.SetTop(&top) 
skip := int32(0)
requestBody.SetSkip(&skip) 
groupBy := []string {
	"GatewayRegion",
}
requestBody.SetGroupBy(groupBy)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().RetrieveCloudPcTroubleshootReports().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.retrievecloudpctroubleshootreports.RetrieveCloudPcTroubleshootReportsPostRequestBody retrieveCloudPcTroubleshootReportsPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.retrievecloudpctroubleshootreports.RetrieveCloudPcTroubleshootReportsPostRequestBody();
retrieveCloudPcTroubleshootReportsPostRequestBody.setReportName(CloudPCTroubleshootReportType.TroubleshootDetailsReport);
LinkedList<String> select = new LinkedList<String>();
select.add("EventDateTime");
select.add("TotalActiveConnectionCountAvg");
select.add("GroupColumn");
retrieveCloudPcTroubleshootReportsPostRequestBody.setSelect(select);
retrieveCloudPcTroubleshootReportsPostRequestBody.setFilter("(TimeRange eq 'Last 7 days') and (PolicyNameParam eq '') and (RegionParam eq '') and (UserSettingNameParam eq '') and (ServicePlanTypeParam eq 'Enterprise') and (ServicePlanNameParam eq '') and (OSBuildVersionParam eq '') and (AADJoinTypeParam eq '') and (ImageNameParam eq '') and (GatewayRegionParam eq '') and (ClientOSParam eq '') and (ClientTypeParam eq '') and (TransportTypeParam eq '') and (CloudPCEndpointCountryRegionParam eq '') and (CloudPCEndpointStateParam eq '') and (CloudPCEndpointCityParam eq '')");
retrieveCloudPcTroubleshootReportsPostRequestBody.setTop(1000);
retrieveCloudPcTroubleshootReportsPostRequestBody.setSkip(0);
LinkedList<String> groupBy = new LinkedList<String>();
groupBy.add("GatewayRegion");
retrieveCloudPcTroubleshootReportsPostRequestBody.setGroupBy(groupBy);
graphClient.deviceManagement().virtualEndpoint().reports().retrieveCloudPcTroubleshootReports().post(retrieveCloudPcTroubleshootReportsPostRequestBody);
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
  reportName: 'troubleshootTenantActiveConnectionCountTrendReport',
  select: [
    'EventDateTime',
    'TotalActiveConnectionCountAvg',
    'GroupColumn'
  ],
  filter: '(TimeRange eq \'Last 7 days\') and (PolicyNameParam eq \'\') and (RegionParam eq \'\') and (UserSettingNameParam eq \'\') and (ServicePlanTypeParam eq \'Enterprise\') and (ServicePlanNameParam eq \'\') and (OSBuildVersionParam eq \'\') and (AADJoinTypeParam eq \'\') and (ImageNameParam eq \'\') and (GatewayRegionParam eq \'\') and (ClientOSParam eq \'\') and (ClientTypeParam eq \'\') and (TransportTypeParam eq \'\') and (CloudPCEndpointCountryRegionParam eq \'\') and (CloudPCEndpointStateParam eq \'\') and (CloudPCEndpointCityParam eq \'\')',
  top: 1000,
  skip: 0,
  groupBy: [
    'GatewayRegion'
  ]
};

await client.api('/deviceManagement/virtualEndpoint/reports/retrieveCloudPcTroubleshootReports')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\RetrieveCloudPcTroubleshootReports\RetrieveCloudPcTroubleshootReportsPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\CloudPCTroubleshootReportType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RetrieveCloudPcTroubleshootReportsPostRequestBody();
$requestBody->setReportName(new CloudPCTroubleshootReportType('troubleshootTenantActiveConnectionCountTrendReport'));
$requestBody->setSelect(['EventDateTime', 'TotalActiveConnectionCountAvg', 'GroupColumn', 	]);
$requestBody->setFilter('(TimeRange eq \'Last 7 days\') and (PolicyNameParam eq \'\') and (RegionParam eq \'\') and (UserSettingNameParam eq \'\') and (ServicePlanTypeParam eq \'Enterprise\') and (ServicePlanNameParam eq \'\') and (OSBuildVersionParam eq \'\') and (AADJoinTypeParam eq \'\') and (ImageNameParam eq \'\') and (GatewayRegionParam eq \'\') and (ClientOSParam eq \'\') and (ClientTypeParam eq \'\') and (TransportTypeParam eq \'\') and (CloudPCEndpointCountryRegionParam eq \'\') and (CloudPCEndpointStateParam eq \'\') and (CloudPCEndpointCityParam eq \'\')');
$requestBody->setTop(1000);
$requestBody->setSkip(0);
$requestBody->setGroupBy(['GatewayRegion', 	]);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->retrieveCloudPcTroubleshootReports()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.retrieve_cloud_pc_troubleshoot_reports.retrieve_cloud_pc_troubleshoot_reports_post_request_body import RetrieveCloudPcTroubleshootReportsPostRequestBody
from msgraph_beta.generated.models.cloud_p_c_troubleshoot_report_type import CloudPCTroubleshootReportType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RetrieveCloudPcTroubleshootReportsPostRequestBody(
	report_name = CloudPCTroubleshootReportType.TroubleshootDetailsReport,
	select = [
		"EventDateTime",
		"TotalActiveConnectionCountAvg",
		"GroupColumn",
	],
	filter = "(TimeRange eq 'Last 7 days') and (PolicyNameParam eq '') and (RegionParam eq '') and (UserSettingNameParam eq '') and (ServicePlanTypeParam eq 'Enterprise') and (ServicePlanNameParam eq '') and (OSBuildVersionParam eq '') and (AADJoinTypeParam eq '') and (ImageNameParam eq '') and (GatewayRegionParam eq '') and (ClientOSParam eq '') and (ClientTypeParam eq '') and (TransportTypeParam eq '') and (CloudPCEndpointCountryRegionParam eq '') and (CloudPCEndpointStateParam eq '') and (CloudPCEndpointCityParam eq '')",
	top = 1000,
	skip = 0,
	group_by = [
		"GatewayRegion",
	],
)

await graph_client.device_management.virtual_endpoint.reports.retrieve_cloud_pc_troubleshoot_reports.post(request_body)
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
  "TotalRowCount": 840,
  "Schema": [
    {
      "Column": "EventDateTime",
      "PropertyType": "DateTime"
    },
    {
      "Column": "TotalActiveConnectionCountAvg",
      "PropertyType": "Double"
    },
    {
      "Column": "GroupColumn",
      "PropertyType": "String"
    }
  ],
  "Values": [
    ["2026-03-25T04:00:00", 0.63, "australiaeast"],
    ["2026-03-25T04:00:00", 2.88, "japaneast"],
    ["2026-03-25T04:00:00", 3.63, "japanwest"],
    ["2026-03-25T04:00:00", 7.88, "southeastasia"],
    ["2026-03-25T04:00:00", 10.0, "westus2"],
    ["2026-03-25T08:00:00", 0.75, "israelcentral"],
    ["2026-03-25T08:00:00", 1.75, "japaneast"],
    ["2026-03-25T08:00:00", 8.13, "southeastasia"]
  ]
}
```
