<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-logs-list-generativeaiinsights?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# List generativeAIInsights

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of [generativeAIInsight](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-generativeaiinsight?view=graph-rest-beta) objects and their properties for Global Secure Access traffic insights.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess-Reports.Read.All | NetworkAccess.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess-Reports.Read.All | NetworkAccess.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Global Secure Access Log Reader
- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
GET /networkAccess/logs/generativeAiInsights
```

## Optional query parameters

This method supports the `$filter`, `$orderby`, and `$top` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

| Name | Syntax | Notes |
| :--- | :--- | :--- |
| Filter | `/logs/generativeAiInsights?$filter=activity eq 'prompt'` | Filter by all scalar properties. |
| Server-side pagination | `@odata.nextLink=https://graph.microsoft.com/beta/networkAccess/logs/generativeAiInsights?$skiptoken="generatedtoken"` | The page size defaults to 1,000 and can't exceed it. |
| Sort | `/logs/generativeAiInsights?$orderby=createdDateTime desc` | You can order by all scalar properties. |
| Top | `/logs/generativeAiInsights?$top=50` | The maximum value is 1,000. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [generativeAIInsight](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-generativeaiinsight?view=graph-rest-beta) objects in the response body.

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
GET https://graph.microsoft.com/beta/networkAccess/logs/generativeAiInsights?$filter=activity eq 'prompt'&$orderby=createdDateTime desc&$top=25
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.Logs.GenerativeAIInsights.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "activity eq 'prompt'";
	requestConfiguration.QueryParameters.Orderby = new string []{ "createdDateTime desc" };
	requestConfiguration.QueryParameters.Top = 25;
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
	  graphnetworkaccess "github.com/microsoftgraph/msgraph-beta-sdk-go/networkaccess"
	  //other-imports
)


requestFilter := "activity eq 'prompt'"
requestTop := int32(25)

requestParameters := &graphnetworkaccess.LogsGenerativeAIInsightsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Orderby: [] string {"createdDateTime desc"},
	Top: &requestTop,
}
configuration := &graphnetworkaccess.LogsGenerativeAIInsightsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
generativeAIInsights, err := graphClient.NetworkAccess().Logs().GenerativeAIInsights().Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.networkaccess.GenerativeAIInsightCollectionResponse result = graphClient.networkAccess().logs().generativeAIInsights().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "activity eq 'prompt'";
	requestConfiguration.queryParameters.orderby = new String []{"createdDateTime desc"};
	requestConfiguration.queryParameters.top = 25;
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

let generativeAIInsights = await client.api('/networkAccess/logs/generativeAiInsights')
	.version('beta')
	.filter('activity eq \'prompt\'')
	.orderby('createdDateTime desc')
	.top(25)
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\NetworkAccess\Logs\GenerativeAIInsights\GenerativeAIInsightsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GenerativeAIInsightsRequestBuilderGetRequestConfiguration();
$queryParameters = GenerativeAIInsightsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "activity eq 'prompt'";
$queryParameters->orderby = ["createdDateTime desc"];
$queryParameters->top = 25;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->networkAccess()->logs()->generativeAIInsights()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

Get-MgBetaNetworkAccessLogGenerativeAiInsight -Filter "activity eq 'prompt'" -Sort "createdDateTime desc" -Top 25 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.network_access.logs.generative_a_i_insights.generative_a_i_insights_request_builder import GenerativeAIInsightsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GenerativeAIInsightsRequestBuilder.GenerativeAIInsightsRequestBuilderGetQueryParameters(
		filter = "activity eq 'prompt'",
		orderby = ["createdDateTime desc"],
		top = 25,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.network_access.logs.generative_a_i_insights.get(request_configuration = request_configuration)
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/logs/generativeAiInsights",
  "value": [
    {
      "transactionId": "2088d793-6050-4458-b283-f0cdd0fab280",
      "content": "Generate me a photo of a cat",
      "createdDateTime": "2025-01-14T15:09:45Z",
      "activity": "prompt",
      "subactivity": "chat-interaction",
      "destinationUrl": "https://copilot.microsoft.com/chat",
      "userPrincipalName": "charles@fabrikam.com",
      "eventId": "aaf43b7f-59f8-4d6a-9a8b-8d6bb2a37f2f",
      "eventType": "prompt",
      "mcpClientName": null,
      "mcpServerName": null,
      "sessionId": ""
    },
    {
      "transactionId": "f7ac7830-18cc-4e98-9df2-c6d9fbe08d42",
      "content": "Generate me a summary of our Q1 sales data",
      "createdDateTime": "2025-01-14T15:12:31Z",
      "activity": "mcp",
      "subactivity": "tools/call",
      "destinationUrl": "https://copilot.microsoft.com/mcp",
      "userPrincipalName": "adele@fabrikam.com",
      "eventId": "6de0e17d-13db-4025-b2f3-f32b3f9ee9b8",
      "eventType": "mcpInitialize",
      "mcpClientName": "copilot-studio",
      "mcpServerName": "finance-tools",
      "sessionId": "5f1b7fb5-4d02-4f14-88f8-ef5b21e2f208"
    }
  ]
}
```

## Related content

- [logs resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-logs?view=graph-rest-beta)
- [generativeAIInsight resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-generativeaiinsight?view=graph-rest-beta)
- [List networkAccessTraffic](https://learn.microsoft.com/en-us/graph/api/networkaccess-logs-list-traffic?view=graph-rest-beta)
