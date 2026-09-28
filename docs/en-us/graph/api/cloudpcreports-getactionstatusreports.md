<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-getactionstatusreports?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# cloudPcReports: getActionStatusReports

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the remote action status reports, including data such as the Cloud PC ID, Cloud PC device display name, initiating user's principal name, device owner's user principal name, action taken, and action state.

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
POST /deviceManagement/virtualEndpoint/reports/getActionStatusReports
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
| filter | String | OData `$filter` syntax. Supported filters are: `and`, `or`, `gt` ,`ge`, and `eq`. |
| groupBy | String collection | Specifies how to group the reports. If used, must have the same content as the **select** parameter. |
| orderBy | String collection | Specifies the order by columns name. The default **orderBy** column is `RequestDateTime`. |
| search | String | Specifies a String to search for. |
| select | String collection | OData `$select` syntax. The selected columns of the reports. |
| skip | Int32 | Number of records to skip. |
| top | Int32 | The number of top records to return. If not specified, the default limit is 25, with a maximum of 100. |

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/getActionStatusReports
Content-Type: application/json
Content-length: 199

{
  "filter": "ActionState eq 'failed'",
  "select": [
    "Id",
    "CloudPcDeviceDisplayName",
    "BulkActionId",
    "BulkActionDisplayName",
    "CloudPcId",
    "InitiatedByUserPrincipalName",
    "DeviceOwnerUserPrincipalName",
    "Action",
    "ActionState",
    "RequestDateTime",
    "LastUpdatedDateTime",
    "ActionParameters"
  ],
  "skip": 0,
  "top": 50
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Reports.GetActionStatusReports;

var requestBody = new GetActionStatusReportsPostRequestBody
{
	Filter = "ActionState eq 'failed'",
	Select = new List<string>
	{
		"Id",
		"CloudPcDeviceDisplayName",
		"BulkActionId",
		"BulkActionDisplayName",
		"CloudPcId",
		"InitiatedByUserPrincipalName",
		"DeviceOwnerUserPrincipalName",
		"Action",
		"ActionState",
		"RequestDateTime",
		"LastUpdatedDateTime",
		"ActionParameters",
	},
	Skip = 0,
	Top = 50,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.Reports.GetActionStatusReports.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewGetActionStatusReportsPostRequestBody()
filter := "ActionState eq 'failed'"
requestBody.SetFilter(&filter) 
select := []string {
	"Id",
	"CloudPcDeviceDisplayName",
	"BulkActionId",
	"BulkActionDisplayName",
	"CloudPcId",
	"InitiatedByUserPrincipalName",
	"DeviceOwnerUserPrincipalName",
	"Action",
	"ActionState",
	"RequestDateTime",
	"LastUpdatedDateTime",
	"ActionParameters",
}
requestBody.SetSelect(select)
skip := int32(0)
requestBody.SetSkip(&skip) 
top := int32(50)
requestBody.SetTop(&top) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().Reports().GetActionStatusReports().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getactionstatusreports.GetActionStatusReportsPostRequestBody getActionStatusReportsPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.reports.getactionstatusreports.GetActionStatusReportsPostRequestBody();
getActionStatusReportsPostRequestBody.setFilter("ActionState eq 'failed'");
LinkedList<String> select = new LinkedList<String>();
select.add("Id");
select.add("CloudPcDeviceDisplayName");
select.add("BulkActionId");
select.add("BulkActionDisplayName");
select.add("CloudPcId");
select.add("InitiatedByUserPrincipalName");
select.add("DeviceOwnerUserPrincipalName");
select.add("Action");
select.add("ActionState");
select.add("RequestDateTime");
select.add("LastUpdatedDateTime");
select.add("ActionParameters");
getActionStatusReportsPostRequestBody.setSelect(select);
getActionStatusReportsPostRequestBody.setSkip(0);
getActionStatusReportsPostRequestBody.setTop(50);
graphClient.deviceManagement().virtualEndpoint().reports().getActionStatusReports().post(getActionStatusReportsPostRequestBody);
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
  filter: 'ActionState eq \'failed\'',
  select: [
    'Id',
    'CloudPcDeviceDisplayName',
    'BulkActionId',
    'BulkActionDisplayName',
    'CloudPcId',
    'InitiatedByUserPrincipalName',
    'DeviceOwnerUserPrincipalName',
    'Action',
    'ActionState',
    'RequestDateTime',
    'LastUpdatedDateTime',
    'ActionParameters'
  ],
  skip: 0,
  top: 50
};

await client.api('/deviceManagement/virtualEndpoint/reports/getActionStatusReports')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Reports\GetActionStatusReports\GetActionStatusReportsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetActionStatusReportsPostRequestBody();
$requestBody->setFilter('ActionState eq \'failed\'');
$requestBody->setSelect(['Id', 'CloudPcDeviceDisplayName', 'BulkActionId', 'BulkActionDisplayName', 'CloudPcId', 'InitiatedByUserPrincipalName', 'DeviceOwnerUserPrincipalName', 'Action', 'ActionState', 'RequestDateTime', 'LastUpdatedDateTime', 'ActionParameters', 	]);
$requestBody->setSkip(0);
$requestBody->setTop(50);

$graphServiceClient->deviceManagement()->virtualEndpoint()->reports()->getActionStatusReports()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.reports.get_action_status_reports.get_action_status_reports_post_request_body import GetActionStatusReportsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetActionStatusReportsPostRequestBody(
	filter = "ActionState eq 'failed'",
	select = [
		"Id",
		"CloudPcDeviceDisplayName",
		"BulkActionId",
		"BulkActionDisplayName",
		"CloudPcId",
		"InitiatedByUserPrincipalName",
		"DeviceOwnerUserPrincipalName",
		"Action",
		"ActionState",
		"RequestDateTime",
		"LastUpdatedDateTime",
		"ActionParameters",
	],
	skip = 0,
	top = 50,
)

await graph_client.device_management.virtual_endpoint.reports.get_action_status_reports.post(request_body)
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
      "Column": "CloudPcDeviceDisplayName",
      "PropertyType": "String"
    },
    {
      "Column": "BulkActionId",
      "PropertyType": "String"
    },
    {
      "Column": "BulkActionDisplayName",
      "PropertyType": "String"
    },
    {
      "Column": "CloudPcId",
      "PropertyType": "String"
    },
    {
      "Column": "InitiatedByUserPrincipalName",
      "PropertyType": "String"
    },
    {
      "Column": "DeviceOwnerUserPrincipalName",
      "PropertyType": "String"
    },
    {
      "Column": "Action",
      "PropertyType": "String"
    },
    {
      "Column": "ActionState",
      "PropertyType": "String"
    },
    {
      "Column": "RequestDateTime",
      "PropertyType": "DateTime"
    },
    {
      "Column": "LastUpdatedDateTime",
      "PropertyType": "DateTime"
    },
    {
      "Column": "ActionParameters",
      "PropertyType": "Json"
    }
  ],
  "Values": [
    [
      "662009bc-7732-4f6f-8726-25883518b33e",
      "CloudPC-Connie",
      "bdc8e6dd-0455-4412-83d9-c818664fe1f1",
      "Resize to 64GB RAM - John",
      "bdc8e6dd-0455-4412-83d9-c818664fe1f1",
      "john@contoso.com",
      "connie@contoso.com",
      "Resize",
      "failed",
      "2020-07-23T10:10:57Z",
      "2023-07-23T18:14:34Z",
      {
        "targetServicePlanId": "3bba9856-7cf2-4396-904a-00de74fba3a4"
      }
    ]
  ]
}
```
