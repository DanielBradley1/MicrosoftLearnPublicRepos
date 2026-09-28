<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-post-exportjobs?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-21 -->

# Create cloudPcExportJob

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [cloudPcExportJob](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexportjob?view=graph-rest-beta) resource to initiate downloading the entire or specified portion of a report.

Use the [GET cloudPcExportJob](https://learn.microsoft.com/en-us/graph/api/cloudpcexportjob-get?view=graph-rest-beta) operation to verify the **exportJobStatus** property of the **cloudPcExportJob** resource. When the property result is `completed`, the report finishes downloading to the location specified by the **exportUrl** property.

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
POST /deviceManagement/virtualEndpoint/reports/exportJobs
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudPcExportJob](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexportjob?view=graph-rest-beta) object.

You can specify the following properties when you create a **cloudPcExportJob**.

| Property | Type | Description |
| :--- | :--- | :--- |
| filter | String | The filter applied on the report. Optional. |
| format | String | The format of the exported report. Optional. |
| reportName | [cloudPcReportName](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreportname?view=graph-rest-beta) | The report name. |
| select | String collection | The selected columns of the report. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [cloudPcExportJob](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexportjob?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create an export job to download the TotalAggregatedRemoteConnectionReports report

The following example shows how to create an export job to download the `TotalAggregatedRemoteConnectionReports` report.

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/exportJobs
Content-Type: application/json
Content-length: 315

{
  "reportName": "TotalAggregatedRemoteConnectionReports",
  "select": [
    "CloudPcId",
    "ManagedDeviceName",
    "UserPrincipalName",
    "DaysSinceLastSignIn",
    "TotalUsageInHour"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CloudPcExportJob
{
	ReportName = CloudPcReportName.TotalAggregatedRemoteConnectionReports,
	Select = new List<string>
	{
		"CloudPcId",
		"ManagedDeviceName",
		"UserPrincipalName",
		"DaysSinceLastSignIn",
		"TotalUsageInHour",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.Reports.ExportJobs.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewCloudPcExportJob()
reportName := graphmodels.TOTALAGGREGATEDREMOTECONNECTIONREPORTS_CLOUDPCREPORTNAME 
requestBody.SetReportName(&reportName) 
select := []string {
	"CloudPcId",
	"ManagedDeviceName",
	"UserPrincipalName",
	"DaysSinceLastSignIn",
	"TotalUsageInHour",
}
requestBody.SetSelect(select)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
exportJobs, err := graphClient.DeviceManagement().VirtualEndpoint().Reports().ExportJobs().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcExportJob cloudPcExportJob = new CloudPcExportJob();
cloudPcExportJob.setReportName(CloudPcReportName.TotalAggregatedRemoteConnectionReports);
LinkedList<String> select = new LinkedList<String>();
select.add("CloudPcId");
select.add("ManagedDeviceName");
select.add("UserPrincipalName");
select.add("DaysSinceLastSignIn");
select.add("TotalUsageInHour");
cloudPcExportJob.setSelect(select);
CloudPcExportJob result = graphClient.deviceManagement().virtualEndpoint().reports().exportJobs().post(cloudPcExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcExportJob = {
  reportName: 'TotalAggregatedRemoteConnectionReports',
  select: [
    'CloudPcId',
    'ManagedDeviceName',
    'UserPrincipalName',
    'DaysSinceLastSignIn',
    'TotalUsageInHour'
  ]
};

await client.api('/deviceManagement/virtualEndpoint/reports/exportJobs')
	.version('beta')
	.post(cloudPcExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CloudPcExportJob;
use Microsoft\Graph\Beta\Generated\Models\CloudPcReportName;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcExportJob();
$requestBody->setReportName(new CloudPcReportName('totalAggregatedRemoteConnectionReports'));
$requestBody->setSelect(['CloudPcId', 'ManagedDeviceName', 'UserPrincipalName', 'DaysSinceLastSignIn', 'TotalUsageInHour', 	]);

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->exportJobs()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.DeviceManagement.Administration

$params = @{
	reportName = "TotalAggregatedRemoteConnectionReports"
	select = @(
	"CloudPcId"
"ManagedDeviceName"
"UserPrincipalName"
"DaysSinceLastSignIn"
"TotalUsageInHour"
)
}

New-MgBetaDeviceManagementVirtualEndpointReportExportJob -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.cloud_pc_export_job import CloudPcExportJob
from msgraph_beta.generated.models.cloud_pc_report_name import CloudPcReportName
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcExportJob(
	report_name = CloudPcReportName.TotalAggregatedRemoteConnectionReports,
	select = [
		"CloudPcId",
		"ManagedDeviceName",
		"UserPrincipalName",
		"DaysSinceLastSignIn",
		"TotalUsageInHour",
	],
)

result = await graph_client.device_management.virtual_endpoint.reports.export_jobs.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#deviceManagement/virtualEndpoint/reports/exportJobs/$entity",
  "id": "TotalAggregatedRemoteConnectionReports__d39979c9-a0a2-4916-a158-1b984742ffff",
  "reportName": "totalAggregatedRemoteConnectionReports",
  "filter": null,
  "select": [
    "CloudPcId",
    "ManagedDeviceName",
    "UserPrincipalName",
    "DaysSinceLastSignIn",
    "TotalUsageInHour"
  ],
  "format": null,
  "expirationDateTime": "0001-01-01T00:00:00Z",
  "requestDateTime": "2022-09-16T12:00:06.5137388Z",
  "exportJobStatus": "inProgress",
  "exportUrl": null
}
```

### Example 2: Create an export job to download the RemoteConnectionQualityReports report.

The following example shows how to create an export job to download the `RemoteConnectionQualityReports` report.

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/exportJobs
Content-Type: application/json
Content-length: 315

{
  "reportName": "RemoteConnectionQualityReports",
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
    "EventDateTime"
  ],
  "filter": "EventDateTime gt datetime'2023-06-14T07:40:41.694Z'"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CloudPcExportJob
{
	ReportName = CloudPcReportName.RemoteConnectionQualityReports,
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
		"EventDateTime",
	},
	Filter = "EventDateTime gt datetime'2023-06-14T07:40:41.694Z'",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.Reports.ExportJobs.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewCloudPcExportJob()
reportName := graphmodels.REMOTECONNECTIONQUALITYREPORTS_CLOUDPCREPORTNAME 
requestBody.SetReportName(&reportName) 
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
	"EventDateTime",
}
requestBody.SetSelect(select)
filter := "EventDateTime gt datetime'2023-06-14T07:40:41.694Z'"
requestBody.SetFilter(&filter) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
exportJobs, err := graphClient.DeviceManagement().VirtualEndpoint().Reports().ExportJobs().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcExportJob cloudPcExportJob = new CloudPcExportJob();
cloudPcExportJob.setReportName(CloudPcReportName.RemoteConnectionQualityReports);
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
select.add("EventDateTime");
cloudPcExportJob.setSelect(select);
cloudPcExportJob.setFilter("EventDateTime gt datetime'2023-06-14T07:40:41.694Z'");
CloudPcExportJob result = graphClient.deviceManagement().virtualEndpoint().reports().exportJobs().post(cloudPcExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcExportJob = {
  reportName: 'RemoteConnectionQualityReports',
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
    'EventDateTime'
  ],
  filter: 'EventDateTime gt datetime\'2023-06-14T07:40:41.694Z\''
};

await client.api('/deviceManagement/virtualEndpoint/reports/exportJobs')
	.version('beta')
	.post(cloudPcExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CloudPcExportJob;
use Microsoft\Graph\Beta\Generated\Models\CloudPcReportName;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcExportJob();
$requestBody->setReportName(new CloudPcReportName('remoteConnectionQualityReports'));
$requestBody->setSelect(['CloudPcId', 'ManagedDeviceName', 'AvgRoundTripTimeInMsP50', 'LastConnectionRoundTripTimeInMs', 'AvgAvailableBandwidthInMbpsP50', 'LastConnectionAvailableBandWidthInMSps', 'AvgRemoteSignInTimeInSecP50', 'UDPConnectionPercentage', 'LastConnectionGateway', 'LastConnectionProtocol', 'EventDateTime', 	]);
$requestBody->setFilter('EventDateTime gt datetime\'2023-06-14T07:40:41.694Z\'');

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->exportJobs()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.DeviceManagement.Administration

$params = @{
	reportName = "RemoteConnectionQualityReports"
	select = @(
	"CloudPcId"
"ManagedDeviceName"
"AvgRoundTripTimeInMsP50"
"LastConnectionRoundTripTimeInMs"
"AvgAvailableBandwidthInMbpsP50"
"LastConnectionAvailableBandWidthInMSps"
"AvgRemoteSignInTimeInSecP50"
"UDPConnectionPercentage"
"LastConnectionGateway"
"LastConnectionProtocol"
"EventDateTime"
)
filter = "EventDateTime gt datetime'2023-06-14T07:40:41.694Z'"
}

New-MgBetaDeviceManagementVirtualEndpointReportExportJob -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.cloud_pc_export_job import CloudPcExportJob
from msgraph_beta.generated.models.cloud_pc_report_name import CloudPcReportName
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcExportJob(
	report_name = CloudPcReportName.RemoteConnectionQualityReports,
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
		"EventDateTime",
	],
	filter = "EventDateTime gt datetime'2023-06-14T07:40:41.694Z'",
)

result = await graph_client.device_management.virtual_endpoint.reports.export_jobs.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#deviceManagement/virtualEndpoint/reports/exportJobs/$entity",
  "id": "RemoteConnectionQualityReports__85678957-6202-4e29-97e6-eb26ef07f330",
  "reportName": "remoteConnectionQualityReports",
  "filter": "EventDateTime gt datetime'2023-06-14T07:40:41.694Z'",
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
    "EventDateTime"
  ],
  "format": null,
  "expirationDateTime": null,
  "requestDateTime": "2023-06-14T07:40:41.694Z",
  "exportJobStatus": "inProgress",
  "exportUrl": null
}
```
