<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-product-getknownissuesbytimerange?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# product: getKnownIssuesByTimeRange

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get known issues related to a particular product based on a specified timeframe in the past.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.ReadWrite.All | Not Available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.ReadWrite.All | Not Available. |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Intune Administrator*, or *Windows Update Deployment Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
GET /admin/windows/updates/products/{id}/GetKnownIssuesByTimeRange(daysInPast={daysInPast},includeAllActive={includeAllActive})
```

## Query parameters

The following table shows the parameters that must be used with this function.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| daysInPast | Int32 | The number of days to look up in the past. This filter is applied on all known issues that are in final status and have a resolved date time. |
| includeAllActive | Boolean | If set to `true`, the response includes all active known issues. If set to `false`, the response doesn't include any active known issues. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.windowsUpdates.knownIssue](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-knownissue?view=graph-rest-beta) objects for the given time range in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/admin/windows/updates/products/1/GetKnownIssuesByTimeRange(daysInPast=70,includeAllActive=false)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Windows.Updates.Products["{product-id}"].MicrosoftGraphWindowsUpdatesGetKnownIssuesByTimeRangeWithDaysInPast(1).GetAsGetKnownIssuesByTimeRangeWithDaysInPastGetResponseAsync();
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


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
daysInPast := int32(1)
microsoftGraphWindowsUpdatesGetKnownIssuesByTimeRange, err := graphClient.Admin().Windows().Updates().Products().ByProductId("product-id").MicrosoftGraphWindowsUpdatesGetKnownIssuesByTimeRangeWithDaysInPastWithIncludeAllActive(&daysInPast, &includeAllActive).GetAsGetKnownIssuesByTimeRangeWithDaysInPastGetResponse(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.admin().windows().updates().products().byProductId("{product-id}").microsoftGraphWindowsUpdatesGetKnownIssuesByTimeRangeWithDaysInPast(1).get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getKnownIssuesByTimeRange = await client.api('/admin/windows/updates/products/1/GetKnownIssuesByTimeRange(daysInPast=70,includeAllActive=false)')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->windows()->updates()->products()->byProductId('product-id')->microsoftGraphWindowsUpdatesGetKnownIssuesByTimeRangeWithDaysInPast(1)->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.WindowsUpdates

Get-MgBetaWindowsUpdatesProductKnownIssueByTimeRange -ProductId $productId -DaysInPast $daysInPastId -IncludeAllActive $includeAllActiveId 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.windows.updates.products.by_product_id('product-id').microsoft_graph_windows_updates_get_known_issues_by_time_range_with_days_in_past(1).get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.windowsUpdates.knownIssue)",
  "value": [
    {
      "id": "WI670072",
      "status": "mitigatedExternal",
      "webViewUrl": "https://admin.microsoft.com/Adminportal/Home#/windowsreleasehealth/knownissues/:/issue/WI670072",
      "description": "Investigation concluded that the error reported by users was not caused by the August 2023 preview updates.",
      "startDateTime": "2023-08-22T10:00:00-07:00",
      "title": "Microsoft received reports about an “UNSUPPORTED_PROCESSOR” error",
      "resolvedDateTime": "2023-09-07T16:14:07.1881817-07:00",
      "lastUpdatedDateTime": "2023-09-07T16:41:58.577-07:00",
      "originatingKnowledgeBaseArticle": {
        "Url": "https://support.microsoft.com/help/5029351",
        "Id": "KB5029351"
      },
      "resolvingKnowledgeBaseArticle": null,
      "safeguardHoldIds": [],
      "knownIssueHistories": [
        {
          "createdDateTime": "2023-08-24T02:51:27.29Z",
          "body": {
            "content": "Microsoft has received reports of an issue in which users are receiving an “UNSUPPORTED_PROCESSOR” error message on a blue screen after installing updates released on August 22, 2023 (KB5029351 (https://support.microsoft.com/help/5029351)) and then restarting their device. KB5029351 (https://support.microsoft.com/help/5029351) might automatically uninstall to allow Windows to start up as expected. KB5029351 (https://support.microsoft.com/help/5029351) might not offer to some Windows devices which might be affected by this issue.\n\nIf you are experiencing issues, please use Feedback Hub to file a report following the below steps:\n    1. Launch Feedback Hub by opening the Start menu and typing \"Feedback hub\", or pressing the Windows key + F\n    2. Fill in the \"Summarize your feedback\" and \"Explain in more detail\" boxes, then click Next.\n    3. Under the \"Choose a category\" section, click the \"Problem\" button, and select \"Install and Update\" category. Then select \"Downloading, installing, and configuring Windows Update” subcategory. Click Next.\n    4. Under the \"Find similar feedback\" section, select the \"Make new bug\" radio button and click Next.\n    5. Under the \"Add more details\" section, supply any relevant detail (Note this is not critical to addressing your issue).\n    6. Expand the \"Recreate my problem\" box and press \"Start recording\". Reproduce the issue on your device.\n    7. Press \"Stop recording\" once finished. Click the \"Submit\" button.\nFor additional information, see Send feedback to Microsoft with the Feedback Hub app (https://support.microsoft.com/windows/send-feedback-to-microsoft-with-the-feedback-hub-app-f59187f8-8739-22d6-ba93-f66612949332).\n\nNext steps: We are presently investigating to determine if this is an issue caused by Microsoft. We will provide an update when more information is available.\n\nAffected platforms:\n    -  Client: Windows 11, version 22H2; Windows 10, version 22H2; Windows 11, version 21H2\n    -  Server: None\n",
            "contentType": "html"
          }
        }
      ]
    }
  ]
}
```
