<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-product-findbykbnumber?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# product: findByKbNumber

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Find the product revisions associated with a knowledge base number and the known issues directly or indirectly related to the knowledge base number.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Intune Administrator*, or *Windows Update Deployment Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
GET /admin/windows/updates/products/FindByKbNumber(kbNumber={kbNumber})
```

## Query parameters

The following table shows the parameter that must be used with this function.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| kbNumber | Int32 | Knowledge base article number. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.windowsUpdates.product](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-product?view=graph-rest-beta) objects in the response body.

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
GET https://graph.microsoft.com/beta/admin/windows/updates/products/FindByKbNumber(kbNumber=5029332)?expand=revisions($expand=catalogEntry,knowledgeBaseArticle),knownIssues
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Windows.Updates.Products.MicrosoftGraphWindowsUpdatesFindByKbNumberWithKbNumber(1).GetAsFindByKbNumberWithKbNumberGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "revisions($expand=catalogEntry,knowledgeBaseArticle)","knownIssues" };
});
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
	  graphadmin "github.com/microsoftgraph/msgraph-beta-sdk-go/admin"
	  //other-imports
)

requestParameters := &graphadmin.WindowsUpdatesProductsfindByKbNumberRequestBuilderGetQueryParameters{
	Expand: [] string {"revisions($expand=catalogEntry,knowledgeBaseArticle)","knownIssues"},
}
configuration := &graphadmin.WindowsUpdatesProductsfindByKbNumberRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
kbNumber := int32(1)
microsoftGraphWindowsUpdatesFindByKbNumber, err := graphClient.Admin().Windows().Updates().Products().MicrosoftGraphWindowsUpdatesFindByKbNumberWithKbNumber(&kbNumber).GetAsFindByKbNumberWithKbNumberGetResponse(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.admin().windows().updates().products().microsoftGraphWindowsUpdatesFindByKbNumberWithKbNumber(1).get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"revisions($expand=catalogEntry,knowledgeBaseArticle)", "knownIssues"};
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let findByKbNumber = await client.api('/admin/windows/updates/products/FindByKbNumber(kbNumber=5029332)?expand=revisions($expand=catalogEntry,knowledgeBaseArticle),knownIssues')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Admin\Windows\Updates\Products\Microsoft\Graph\WindowsUpdates\FindByKbNumber(kbNumber={kbNumber})\FindByKbNumberWithKbNumberRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new MicrosoftFindByKbNumberWithKbNumberRequestBuilderGetRequestConfiguration();
$queryParameters = MicrosoftFindByKbNumberWithKbNumberRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["revisions(\$expand=catalogEntry,knowledgeBaseArticle)","knownIssues"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->admin()->windows()->updates()->products()->microsoftGraphWindowsUpdatesFindByKbNumberWithKbNumber(1)->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.WindowsUpdates

Find-MgBetaWindowsUpdatesProductByKbNumber -ExpandProperty "revisions(`$expand=catalogEntry,knowledgeBaseArticle),knownIssues"  -KbNumber $kbNumberId 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.admin.windows.updates.products.microsoft.graph.windows_updates.find_by_kb_number(kb_number={kb_number}).find_by_kb_number_with_kb_number_request_builder import FindByKbNumberWithKbNumberRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = FindByKbNumberWithKbNumberRequestBuilder.FindByKbNumberWithKbNumberRequestBuilderGetQueryParameters(
		expand = ["revisions($expand=catalogEntry,knowledgeBaseArticle)","knownIssues"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.admin.windows.updates.products.microsoft_graph_windows_updates_find_by_kb_number_with_kb_number(1).get(request_configuration = request_configuration)
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.windowsUpdates.product)",
  "value": [
    {
      "id": "1",
      "name": "Windows 11, version 21H2",
      "groupName": "Windows 11",
      "friendlyNames": [
        "Version 21H2 (OS build 22000)"
      ],
      "revisions": [
        {
          "id": "10.0.22000.2360",
          "displayName": "Windows 11, version 21H2, build 22000.2360",
          "releaseDateTime": "2023-08-22T00:00:00Z",
          "version": "21H2",
          "osBuild": {
            "BuildNumber": 22000,
            "MajorVersion": 10,
            "MinorVersion": 0,
            "UpdateBuildRevision": 2360
          },
          "catalogEntry": {
            "@odata.type": "#microsoft.graph.windowsUpdates.qualityUpdateCatalogEntry",
            "deployableUntilDateTime": null,
            "displayName": "08/22/2023 - 2023.08 D Update for Windows 10 and later",
            "id": "10cb1ba292c5586e22c9991be3f12fbd39f2ebf231cb5d201c67f42fbaccc567",
            "releaseDateTime": "2023-08-22T00:00:00Z",
            "catalogName": "2023-08 Cumulative Update Preview for Windows 10 and later",
            "isExpeditable": true,
            "qualityUpdateCadence": "Monthly",
            "qualityUpdateClassification": "NonSecurity",
            "shortName": "2023.08 D",
            "cveSeverityInformation": null
          },
          "knowledgeBaseArticle": {
            "Url": "https://support.microsoft.com/help/5029332",
            "Id": "KB5029332"
          }
        }
      ],
      "knownIssues": [
        {
          "id": "WI670073",
          "status": "mitigatedExternal",
          "webViewUrl": "https://admin.microsoft.com/Adminportal/Home#/windowsreleasehealth/knownissues/:/issue/WI670073",
          "description": "Investigation concluded that the error reported by users was not caused by the August 2023 preview updates.",
          "startDateTime": "2023-08-22T10:00:00-07:00",
          "title": "Microsoft received reports about an “UNSUPPORTED_PROCESSOR” error",
          "resolvedDateTime": "2023-09-07T16:14:07.1881817-07:00",
          "lastUpdatedDateTime": "2023-09-07T16:41:58.577-07:00",
          "originatingKnowledgeBaseArticle": {
            "Url": "https://support.microsoft.com/help/5029332",
            "Id": "KB5029332"
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
  ]
}
```
