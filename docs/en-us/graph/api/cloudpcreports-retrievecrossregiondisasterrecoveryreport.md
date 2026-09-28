<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievecrossregiondisasterrecoveryreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# cloudPcReports: retrieveCrossregionDisasterRecoveryReport

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the Windows 365 cross-region disaster recovery report, including cloudPcId, userId, deviceId, cloudPCDeviceDisplayName, userPrincipalName, enabledDRType, disasterRecoveryStatus, licenseType, drHealthStatus, currentRestorePointDateTime, backupCloudPcStatus, and activationExpirationDateTime.

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
POST /deviceManagement/virtualEndpoint/reports/retrieveCrossRegionDisasterRecoveryReport
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
| filter | String | OData `$filter` syntax. The supported filters are: `and`, `or`, `lt`, `le`, `gt`, `ge`, and `eq`. |
| groupBy | String collection | Specifies how to group the reports. If used, must have the same content as the **select** parameter. |
| orderBy | String collection | Specifies how to sort the reports. |
| reportName | [cloudPcDisasterRecoveryReportName](#cloudpcdisasterrecoveryreportname-values) | Indicates the name of the Cloud PC disaster recovery report. The possible values are: `crossRegionDisasterRecoveryReport`, `disasterRecoveryReport`, `unknownFutureValue`. When **reportName** isn't initialized, `crossRegionDisasterRecoveryReport` is the default value. |
| search | String | Specifies a String to search. |
| select | String collection | OData `$select` syntax. The selected columns of the reports. |
| skip | Int32 | The number of records to skip. |
| top | Int32 | The number of top records to return. |

### cloudPcDisasterRecoveryReportName values

| Member | Description |
| :--- | :--- |
| crossRegionDisasterRecoveryReport | Default. Indicates the report that shows the overview and details of Cloud PCs with cross-region disaster recovery configurations, health check, and status. |
| disasterRecoveryReport | Indicates the report that shows the disaster recovery status of Cloud PCs with their associated category. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/retrievecrossregiondisasterrecoveryreport
Content-Type: application/json
Content-length: 199

{
  "reportName": "crossRegionDisasterRecoveryReport",
  "filter": "DisasterRecoveryStatus eq 'Active outage'",
  "select": [
    "Id",
    "CloudPcId",
    "UserId",
    "UserSettingId",
    "DeviceId",
    "CloudPCDeviceDisplayName",
    "UserPrincipalName",
    "EnabledDRType",
    "DRHealthStatus",
    "LicenseType",
    "DisasterRecoveryStatus",
    "CurrentRestorePointDateTime",
    "BackupCloudPcStatus",
    "ActivationExpirationDateTime"
  ],
  "skip": 0,
  "top": 50
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.RetrieveCrossRegionDisasterRecoveryReport;
using Microsoft.Graph.Beta.Models;

var requestBody = new RetrieveCrossRegionDisasterRecoveryReportPostRequestBody
{
	ReportName = CloudPcDisasterRecoveryReportName.CrossRegionDisasterRecoveryReport,
	Filter = "DisasterRecoveryStatus eq 'Active outage'",
	Select = new List<string>
	{
		"Id",
		"CloudPcId",
		"UserId",
		"UserSettingId",
		"DeviceId",
		"CloudPCDeviceDisplayName",
		"UserPrincipalName",
		"EnabledDRType",
		"DRHealthStatus",
		"LicenseType",
		"DisasterRecoveryStatus",
		"CurrentRestorePointDateTime",
		"BackupCloudPcStatus",
		"ActivationExpirationDateTime",
	},
	Skip = 0,
	Top = 50,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.RetrieveCrossRegionDisasterRecoveryReport.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewRetrieveCrossRegionDisasterRecoveryReportPostRequestBody()
reportName := graphmodels.CROSSREGIONDISASTERRECOVERYREPORT_CLOUDPCDISASTERRECOVERYREPORTNAME 
requestBody.SetReportName(&reportName) 
filter := "DisasterRecoveryStatus eq 'Active outage'"
requestBody.SetFilter(&filter) 
select := []string {
	"Id",
	"CloudPcId",
	"UserId",
	"UserSettingId",
	"DeviceId",
	"CloudPCDeviceDisplayName",
	"UserPrincipalName",
	"EnabledDRType",
	"DRHealthStatus",
	"LicenseType",
	"DisasterRecoveryStatus",
	"CurrentRestorePointDateTime",
	"BackupCloudPcStatus",
	"ActivationExpirationDateTime",
}
requestBody.SetSelect(select)
skip := int32(0)
requestBody.SetSkip(&skip) 
top := int32(50)
requestBody.SetTop(&top) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().RetrieveCrossRegionDisasterRecoveryReport().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.retrievecrossregiondisasterrecoveryreport.RetrieveCrossRegionDisasterRecoveryReportPostRequestBody retrieveCrossRegionDisasterRecoveryReportPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.retrievecrossregiondisasterrecoveryreport.RetrieveCrossRegionDisasterRecoveryReportPostRequestBody();
retrieveCrossRegionDisasterRecoveryReportPostRequestBody.setReportName(CloudPcDisasterRecoveryReportName.CrossRegionDisasterRecoveryReport);
retrieveCrossRegionDisasterRecoveryReportPostRequestBody.setFilter("DisasterRecoveryStatus eq 'Active outage'");
LinkedList<String> select = new LinkedList<String>();
select.add("Id");
select.add("CloudPcId");
select.add("UserId");
select.add("UserSettingId");
select.add("DeviceId");
select.add("CloudPCDeviceDisplayName");
select.add("UserPrincipalName");
select.add("EnabledDRType");
select.add("DRHealthStatus");
select.add("LicenseType");
select.add("DisasterRecoveryStatus");
select.add("CurrentRestorePointDateTime");
select.add("BackupCloudPcStatus");
select.add("ActivationExpirationDateTime");
retrieveCrossRegionDisasterRecoveryReportPostRequestBody.setSelect(select);
retrieveCrossRegionDisasterRecoveryReportPostRequestBody.setSkip(0);
retrieveCrossRegionDisasterRecoveryReportPostRequestBody.setTop(50);
graphClient.deviceManagement().virtualEndpoint().reports().retrieveCrossRegionDisasterRecoveryReport().post(retrieveCrossRegionDisasterRecoveryReportPostRequestBody);
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
  reportName: 'crossRegionDisasterRecoveryReport',
  filter: 'DisasterRecoveryStatus eq \'Active outage\'',
  select: [
    'Id',
    'CloudPcId',
    'UserId',
    'UserSettingId',
    'DeviceId',
    'CloudPCDeviceDisplayName',
    'UserPrincipalName',
    'EnabledDRType',
    'DRHealthStatus',
    'LicenseType',
    'DisasterRecoveryStatus',
    'CurrentRestorePointDateTime',
    'BackupCloudPcStatus',
    'ActivationExpirationDateTime'
  ],
  skip: 0,
  top: 50
};

await client.api('/deviceManagement/virtualEndpoint/reports/retrievecrossregiondisasterrecoveryreport')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\RetrieveCrossRegionDisasterRecoveryReport\RetrieveCrossRegionDisasterRecoveryReportPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\CloudPcDisasterRecoveryReportName;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RetrieveCrossRegionDisasterRecoveryReportPostRequestBody();
$requestBody->setReportName(new CloudPcDisasterRecoveryReportName('crossRegionDisasterRecoveryReport'));
$requestBody->setFilter('DisasterRecoveryStatus eq \'Active outage\'');
$requestBody->setSelect(['Id', 'CloudPcId', 'UserId', 'UserSettingId', 'DeviceId', 'CloudPCDeviceDisplayName', 'UserPrincipalName', 'EnabledDRType', 'DRHealthStatus', 'LicenseType', 'DisasterRecoveryStatus', 'CurrentRestorePointDateTime', 'BackupCloudPcStatus', 'ActivationExpirationDateTime', 	]);
$requestBody->setSkip(0);
$requestBody->setTop(50);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->retrieveCrossRegionDisasterRecoveryReport()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.retrieve_cross_region_disaster_recovery_report.retrieve_cross_region_disaster_recovery_report_post_request_body import RetrieveCrossRegionDisasterRecoveryReportPostRequestBody
from msgraph_beta.generated.models.cloud_pc_disaster_recovery_report_name import CloudPcDisasterRecoveryReportName
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RetrieveCrossRegionDisasterRecoveryReportPostRequestBody(
	report_name = CloudPcDisasterRecoveryReportName.CrossRegionDisasterRecoveryReport,
	filter = "DisasterRecoveryStatus eq 'Active outage'",
	select = [
		"Id",
		"CloudPcId",
		"UserId",
		"UserSettingId",
		"DeviceId",
		"CloudPCDeviceDisplayName",
		"UserPrincipalName",
		"EnabledDRType",
		"DRHealthStatus",
		"LicenseType",
		"DisasterRecoveryStatus",
		"CurrentRestorePointDateTime",
		"BackupCloudPcStatus",
		"ActivationExpirationDateTime",
	],
	skip = 0,
	top = 50,
)

await graph_client.device_management.virtual_endpoint.reports.retrieve_cross_region_disaster_recovery_report.post(request_body)
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
      "Column": "Id",
      "PropertyType": "String"
    },
    {
      "Column": "CloudPcId",
      "PropertyType": "String"
    },
    {
      "Column": "UserId",
      "PropertyType": "String"
    },
    {
      "Column": "UserSettingId",
      "PropertyType": "String"
    },
    {
      "Column": "DeviceId",
      "PropertyType": "String"
    },
    {
      "Column": "CloudPcDeviceDisplayName",
      "PropertyType": "String"
    },
    {
      "Column": "UserPrincipalName",
      "PropertyType": "String"
    },
    {
      "Column": "EnabledDRType",
      "PropertyType": "String"
    },
    {
      "Column": "DRHealthStatus",
      "PropertyType": "String"
    },
    {
      "Column": "LicenseType",
      "PropertyType": "String"
    },
    {
      "Column": "DisasterRecoveryStatus",
      "PropertyType": "String"
    },
    {
      "Column": "CurrentRestorePointDateTime",
      "PropertyType": "DateTime"
    },
    {
      "Column": "BackupCloucPcStatus",
      "PropertyType": "String"
    },
    {
      "Column": "ActivationExpirationDateTime",
      "PropertyType": "DateTime"
    }
  ],
  "Values": [
    [
      "7768debd-7955-4b32-a654-a02894bce953",
      "69360332-619a-4b38-af5d-91ecef72f789",
      "c939b389-979f-4687-945d-d1220b3d4d24",
      "k739b389-979f-4j87-945d-d3220b3d4o24",
      "9330ff50-0a1b-4038-8fe8-3c4a67ec4dc5",
      "CPC-Cross-JG79E",
      "john.doe@contoso.com",
      "CrossRegionDR",
      "Unhealthy:'ANC unhealthy', 'Network mismatch'",
      "Cross Region",
      "Active outage",
      "2023-10-16 03:05:14.131 AM",
      "",
      "2023-10-19 07:05:14.131 AM"
    ]
  ]
}
```
