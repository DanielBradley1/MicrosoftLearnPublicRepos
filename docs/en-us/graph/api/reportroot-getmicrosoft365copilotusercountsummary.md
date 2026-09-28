<!-- Source: https://learn.microsoft.com/en-us/graph/api/reportroot-getmicrosoft365copilotusercountsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# reportRoot: getMicrosoft365CopilotUserCountSummary

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Going forward, use the Microsoft 365 Copilot usage APIs under the `/copilot` URL path segment. For more information, see [Copilot report root](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/admin-settings/reports/resources/copilotreportroot) and [Get Copilot user count summary](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/admin-settings/reports/copilotreportroot-getmicrosoft365copilotusercountsummary).

Get the aggregated number of active and enabled users of Microsoft 365 Copilot for a specified time period.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Reports.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Reports.Read.All | Not available. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). This operation supports the following built-in roles, which provide only the least privilege necessary:

- Company Administrator
- Exchange Administrator
- SharePoint Administrator
- Lync Administrator
- Teams Service Administrator
- Teams Communications Administrator
- Global Reader
- Usage Summary Reports Reader
- Reports Reader

For more information, see [Authorization for APIs to read Microsoft 365 usage reports](https://learn.microsoft.com/en-us/graph/reportroot-authorization).

## HTTP request

```http
GET /reports/getMicrosoft365CopilotUserCountSummary(period='{period_value}')
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| period | String | The number of previous days over which to report aggregated usage. The supported values are: `D7`, `D30`, `D90`, `D180`, `ALL`. The first four values follow the format Dn where n represents the number of days over which to aggregate data. `ALL` indicates to report usage for 7, 30, 90, and 180 days. |

## Optional query parameters

This method supports the `$format` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response. The default output type is `application/json`. However, if you want to specify the output type, you can use the OData `$format` query parameter to set the default output to `text/csv` or `application/json`.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

### CSV

If successful, this method returns a `302 Found` response that redirects to a preauthenticated download URL for the report. That URL can be found in the `Location` header in the response.

Preauthenticated download URLs are only valid for a short period of time \(a few minutes\) and don't require an `Authorization` header.

The CSV file has the following headers for columns.

- Report Refresh Date
- Report Period
- Any App Enabled Users
- Any App Active Users
- Microsoft Teams Enabled Users
- Microsoft Teams Active Users
- Word Enabled Users
- Word Active Users
- PowerPoint Enabled Users
- PowerPoint Active Users
- Outlook Enabled Users
- Outlook Active Users
- Excel Enabled Users
- Excel Active Users
- OneNote Enabled Users
- OneNote Active Users
- Loop Enabled Users
- Loop Active Users
- Copilot Chat Enabled Users
- Copilot Chat Active Users

### JSON

If successful, this method returns a `200 OK` response code and a JSON object in the response body.

## Examples

### Example 1: CSV output

The following example outputs a URL for a CSV file.

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

```msgraph
GET https://graph.microsoft.com/beta/reports/getMicrosoft365CopilotUserCountSummary(period='D7')?$format=text/csv
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Reports.GetMicrosoft365CopilotUserCountSummaryWithPeriod("{period}").GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Format = "text/csv";
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
	  graphreports "github.com/microsoftgraph/msgraph-beta-sdk-go/reports"
	  //other-imports
)


requestFormat := "text/csv"

requestParameters := &graphreports.ReportsGetMicrosoft365CopilotUserCountSummaryWithPeriodWithVersionRequestBuilderGetQueryParameters{
	Format: &requestFormat,
}
configuration := &graphreports.ReportsGetMicrosoft365CopilotUserCountSummaryWithPeriodWithVersionRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
period := "{period}"
graphClient.Reports().GetMicrosoft365CopilotUserCountSummaryWithPeriodWithVersion(&period, &version).Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.reports().getMicrosoft365CopilotUserCountSummaryWithPeriod("{period}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.format = "text/csv";
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

let stream = await client.api('/reports/getMicrosoft365CopilotUserCountSummary(period='D7')')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Reports\GetMicrosoft365CopilotUserCountSummary(period='{period}',version='@version')\GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilderGetRequestConfiguration();
$queryParameters = GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->format = "text/csv";
$requestConfiguration->queryParameters = $queryParameters;


$graphServiceClient->reports()->getMicrosoft365CopilotUserCountSummaryWithPeriod('{period}', )->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Get-MgBetaReportMicrosoft365CopilotUserCountSummary -Format "text/csv"  -Period $periodId 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.reports.get_microsoft365_copilot_user_count_summary(period='{period}',version='@version').get_microsoft365_copilot_user_count_summary_with_periodversion='@version'_request_builder import GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilder.GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilderGetQueryParameters(
		format = "text/csv",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

await graph_client.reports.get_microsoft365_copilot_user_count_summary_with_period("{period}").get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 302 Found
Content-Type: text/plain
Location: https://reports.office.com/data/download/JDFKdf2_eJXKS034dbc7e0t__XDe
```

The CSV file in the `Location` header of the 302 response has the following schema.

```http
HTTP/1.1 200 OK
Content-Type: application/octet-stream

Report Refresh Date,Report Period,Any App Enabled Users,Any App Active Users,Microsoft Teams Enabled Users,Microsoft Teams Active Users  ,Word Enabled Users,Word Active Users,PowerPoint Enabled Users,PowerPoint Active Users,Outlook Enabled Users,Outlook Active Users,Excel Enabled Users,Excel Active Users,OneNote Enabled Users,OneNote Active Users,Loop Enabled Users,Loop Active Users,Copilot Chat Enabled Users,Copilot Chat Active Users
```

### Example 2: JSON output

The following example returns JSON data.

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

```msgraph
GET https://graph.microsoft.com/beta/reports/getMicrosoft365CopilotUserCountSummary(period='D7')?$format=application/json
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Reports.GetMicrosoft365CopilotUserCountSummaryWithPeriod("{period}").GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Format = "application/json";
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
	  graphreports "github.com/microsoftgraph/msgraph-beta-sdk-go/reports"
	  //other-imports
)


requestFormat := "application/json"

requestParameters := &graphreports.ReportsGetMicrosoft365CopilotUserCountSummaryWithPeriodWithVersionRequestBuilderGetQueryParameters{
	Format: &requestFormat,
}
configuration := &graphreports.ReportsGetMicrosoft365CopilotUserCountSummaryWithPeriodWithVersionRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
period := "{period}"
graphClient.Reports().GetMicrosoft365CopilotUserCountSummaryWithPeriodWithVersion(&period, &version).Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.reports().getMicrosoft365CopilotUserCountSummaryWithPeriod("{period}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.format = "application/json";
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

let stream = await client.api('/reports/getMicrosoft365CopilotUserCountSummary(period='D7')')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Reports\GetMicrosoft365CopilotUserCountSummary(period='{period}',version='@version')\GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilderGetRequestConfiguration();
$queryParameters = GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->format = "application/json";
$requestConfiguration->queryParameters = $queryParameters;


$graphServiceClient->reports()->getMicrosoft365CopilotUserCountSummaryWithPeriod('{period}', )->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Get-MgBetaReportMicrosoft365CopilotUserCountSummary -Format "application/json"  -Period $periodId 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.reports.get_microsoft365_copilot_user_count_summary(period='{period}',version='@version').get_microsoft365_copilot_user_count_summary_with_periodversion='@version'_request_builder import GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilder.GetMicrosoft365CopilotUserCountSummaryWithPeriodversion='@version'RequestBuilderGetQueryParameters(
		format = "application/json",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

await graph_client.reports.get_microsoft365_copilot_user_count_summary_with_period("{period}").get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 537

{
    "value": [
        {
            "reportRefreshDate": "2024-08-20",
            "adoptionByProduct": [
                {
                    "reportPeriod": 7,
                    "anyAppEnabledUsers": 359229,
                    "anyAppActiveUsers": 165115,
                    "microsoftTeamsEnabledUsers": 359096,
                    "microsoftTeamsActiveUsers": 123341,
                    "wordEnabledUsers": 359096,
                    "wordActiveUsers": 21459,
                    "powerPointEnabledUsers": 359096,
                    "powerPointActiveUsers": 8530,
                    "outlookEnabledUsers": 359096,
                    "outlookActiveUsers": 37270,
                    "excelEnabledUsers": 359096,
                    "excelActiveUsers": 6709,
                    "oneNoteEnabledUsers": 359096,
                    "oneNoteActiveUsers": 1660,
                    "loopEnabledUsers": 359096,
                    "loopActiveUsers": 1345,
                    "copilotChatEnabledUsers": 359096,
                    "copilotChatActiveUsers": 65480
                }
            ]
        }
    ]
}
```
