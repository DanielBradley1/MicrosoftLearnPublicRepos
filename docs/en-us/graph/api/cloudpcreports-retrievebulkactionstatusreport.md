<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcreports-retrievebulkactionstatusreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# cloudPcReports: retrieveBulkActionStatusReport

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the bulk remote action status report, including data such as the bulk action ID, bulk action display name, initiating user's principal name, action type, and action state.

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
POST /deviceManagement/virtualEndpoint/reports/retrieveBulkActionStatusReport
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
| search | String | Specifies a string to search for. |
| select | String collection | OData `$select` syntax. The selected columns of the reports. |
| skip | Int32 | Number of records to skip. |
| top | Int32 | The number of top records to return. If not specified, the default limit is 25, with a maximum of 100. |

## Response

If successful, this method returns a `200 OK` response code and a stream object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/reports/retrieveBulkActionStatusReport
Content-Type: application/octet-stream

{
  "filter": "RequestDateTime ge datetime'2024-08-30'",
  "select": [
    "BulkActionId",
    "BulkActionDisplayName",
    "Action",
    "BulkActionStatus",
    "InitiatedByUserPrincipalName",
    "RequestDateTime",
    "SucceedCount",
    "FailedCount",
    "InprogressCount",
    "TotalCount",
    "Completion"
  ],
  "skip": 0,
  "top": 50
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

using var requestBody = new MemoryStream(); //stream to upload

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.Reports.RetrieveBulkActionStatusReport.PostAsRetrieveBulkActionStatusReportPostResponseAsync(requestBody);
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
	  //other-imports
)

const requestBody := make([]byte, 0)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
retrieveBulkActionStatusReport, err := graphClient.DeviceManagement().VirtualEndpoint().Reports().RetrieveBulkActionStatusReport().PostAsRetrieveBulkActionStatusReportPostResponse(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ByteArrayInputStream stream = new ByteArrayInputStream(new byte[0]); //stream to upload
var result = graphClient.deviceManagement().virtualEndpoint().reports().retrieveBulkActionStatusReport().post(stream);
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
  filter: 'RequestDateTime ge datetime\'2024-08-30\'',
  select: [
    'BulkActionId',
    'BulkActionDisplayName',
    'Action',
    'BulkActionStatus',
    'InitiatedByUserPrincipalName',
    'RequestDateTime',
    'SucceedCount',
    'FailedCount',
    'InprogressCount',
    'TotalCount',
    'Completion'
  ],
  skip: 0,
  top: 50
};

await client.api('/deviceManagement/virtualEndpoint/reports/retrieveBulkActionStatusReport')
	.version('beta')
	.post(stream);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BytesIO()

result = await graph_client.device_management.virtual_endpoint.reports.retrieve_bulk_action_status_report.post(request_body)
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
      "Column": "BulkActionId",
      "PropertyType": "String"
    },
    {
      "Column": "BulkActionDisplayName",
      "PropertyType": "String"
    },
    {
      "Column": "Action",
      "PropertyType": "String"
    },
    {
      "Column": "BulkActionStatus",
      "PropertyType": "String"
    },
    {
      "Column": "RequestDateTime",
      "PropertyType": "DateTime"
    },
    {
      "Column": "SucceedCount",
      "PropertyType": "Int64"
    },
    {
      "Column": "FailedCount",
      "PropertyType": "Int64"
    },
    {
      "Column": "InprogressCount",
      "PropertyType": "Int64"
    },
    {
      "Column": "TotalCount",
      "PropertyType": "Int64"
    }
  ],
  "Values": [
    [
      "63792ef5-db62-437f-8d7e-7b3b695abb48",
      "BulkRestart on 2024-8-22 17:26:52 GMT+0800 (China Standard Time)",
      "Restart",
      "",
      "2024-08-22T09:26:54",
      1,
      0,
      0,
      1
    ]
  ]
}
```
