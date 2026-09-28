<!-- Source: https://learn.microsoft.com/en-us/graph/api/reportroot-getmicrosoftappsfilestoragecontainerusagesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# reportRoot: getMicrosoftAppsFileStorageContainerUsageSummary

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get storage usage data for SharePoint Embedded file storage containers in a tenant. The response follows a hierarchical structure: Tenant > Geo > App. Use `$expand` to include nested levels. This method is available in the global service only.

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
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /reports/microsoftAppsFileStorageContainerUsageSummary
```

## Optional query parameters

This method supports the `$expand` OData query parameter to help customize the response. Use `$expand=usageByDataLocation` to include geo-level breakdown, or `$expand=usageByDataLocation($expand=usageByApp)` for the full hierarchy. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoftAppsFileStorageContainerUsage](https://learn.microsoft.com/en-us/graph/api/resources/microsoftappsfilestoragecontainerusage?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Get tenant-level summary

The following example returns only tenant-level totals \(storage used, container count\) without any geo or app breakdown.

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
GET https://graph.microsoft.com/beta/reports/microsoftAppsFileStorageContainerUsageSummary
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.MicrosoftAppsFileStorageContainerUsageSummary.GetAsync();
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
microsoftAppsFileStorageContainerUsageSummary, err := graphClient.Reports().MicrosoftAppsFileStorageContainerUsageSummary().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MicrosoftAppsFileStorageContainerUsage result = graphClient.reports().microsoftAppsFileStorageContainerUsageSummary().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let microsoftAppsFileStorageContainerUsage = await client.api('/reports/microsoftAppsFileStorageContainerUsageSummary')
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


$result = $graphServiceClient->reports()->microsoftAppsFileStorageContainerUsageSummary()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Get-MgBetaReportMicrosoftAppFileStorageContainerUsageSummary
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.reports.microsoft_apps_file_storage_container_usage_summary.get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerUsage",
  "id": "microsoftAppsFileStorageContainerUsageSummary",
  "totalActiveStorageUsedInBytes": 107374182400,
  "totalActiveContainerCount": 2450
}
```

### Example 2: Get tenant and geo-level breakdown

The following example returns tenant-level totals with geo-level breakdown using `$expand=usageByDataLocation`.

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
GET https://graph.microsoft.com/beta/reports/microsoftAppsFileStorageContainerUsageSummary?$expand=usageByDataLocation
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.MicrosoftAppsFileStorageContainerUsageSummary.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "usageByDataLocation" };
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

requestParameters := &graphreports.ReportsMicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetQueryParameters{
	Expand: [] string {"usageByDataLocation"},
}
configuration := &graphreports.ReportsMicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftAppsFileStorageContainerUsageSummary, err := graphClient.Reports().MicrosoftAppsFileStorageContainerUsageSummary().Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MicrosoftAppsFileStorageContainerUsage result = graphClient.reports().microsoftAppsFileStorageContainerUsageSummary().get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"usageByDataLocation"};
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

let microsoftAppsFileStorageContainerUsage = await client.api('/reports/microsoftAppsFileStorageContainerUsageSummary')
	.version('beta')
	.expand('usageByDataLocation')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Reports\MicrosoftAppsFileStorageContainerUsageSummary\MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetRequestConfiguration();
$queryParameters = MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["usageByDataLocation"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->reports()->microsoftAppsFileStorageContainerUsageSummary()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Get-MgBetaReportMicrosoftAppFileStorageContainerUsageSummary -ExpandProperty "usageByDataLocation" 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.reports.microsoft_apps_file_storage_container_usage_summary.microsoft_apps_file_storage_container_usage_summary_request_builder import MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilder.MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetQueryParameters(
		expand = ["usageByDataLocation"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.reports.microsoft_apps_file_storage_container_usage_summary.get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerUsage",
  "id": "microsoftAppsFileStorageContainerUsageSummary",
  "totalActiveStorageUsedInBytes": 107374182400,
  "totalActiveContainerCount": 2450,
  "usageByDataLocation": [
    {
      "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerGeoUsage",
      "dataLocationCode": "NAM",
      "activeStorageUsedInBytes": 85899345920,
      "activeContainerCount": 1980
    },
    {
      "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerGeoUsage",
      "dataLocationCode": "EUR",
      "activeStorageUsedInBytes": 21474836480,
      "activeContainerCount": 470
    }
  ]
}
```

### Example 3: Get full hierarchy with app-level breakdown

The following example returns the full tenant > geo > app hierarchy using `$expand=usageByDataLocation($expand=usageByApp)`.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
GET https://graph.microsoft.com/beta/reports/microsoftAppsFileStorageContainerUsageSummary?$expand=usageByDataLocation($expand=usageByApp)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.MicrosoftAppsFileStorageContainerUsageSummary.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "usageByDataLocation($expand=usageByApp)" };
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

requestParameters := &graphreports.ReportsMicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetQueryParameters{
	Expand: [] string {"usageByDataLocation($expand=usageByApp)"},
}
configuration := &graphreports.ReportsMicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftAppsFileStorageContainerUsageSummary, err := graphClient.Reports().MicrosoftAppsFileStorageContainerUsageSummary().Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MicrosoftAppsFileStorageContainerUsage result = graphClient.reports().microsoftAppsFileStorageContainerUsageSummary().get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"usageByDataLocation($expand=usageByApp)"};
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

let microsoftAppsFileStorageContainerUsage = await client.api('/reports/microsoftAppsFileStorageContainerUsageSummary')
	.version('beta')
	.expand('usageByDataLocation($expand=usageByApp)')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Reports\MicrosoftAppsFileStorageContainerUsageSummary\MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetRequestConfiguration();
$queryParameters = MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["usageByDataLocation(\$expand=usageByApp)"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->reports()->microsoftAppsFileStorageContainerUsageSummary()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Get-MgBetaReportMicrosoftAppFileStorageContainerUsageSummary -ExpandProperty "usageByDataLocation(`$expand=usageByApp)" 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.reports.microsoft_apps_file_storage_container_usage_summary.microsoft_apps_file_storage_container_usage_summary_request_builder import MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilder.MicrosoftAppsFileStorageContainerUsageSummaryRequestBuilderGetQueryParameters(
		expand = ["usageByDataLocation($expand=usageByApp)"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.reports.microsoft_apps_file_storage_container_usage_summary.get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerUsage",
  "id": "microsoftAppsFileStorageContainerUsageSummary",
  "totalActiveStorageUsedInBytes": 107374182400,
  "totalActiveContainerCount": 2450,
  "usageByDataLocation": [
    {
      "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerGeoUsage",
      "dataLocationCode": "NAM",
      "activeStorageUsedInBytes": 85899345920,
      "activeContainerCount": 1980,
      "usageByApp": [
        {
          "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerAppUsage",
          "appId": "a187e399-0c36-4b98-8f04-1edc167a0996",
          "displayName": "Loop",
          "activeStorageUsedInBytes": 53687091200,
          "activeContainerCount": 1200
        },
        {
          "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerAppUsage",
          "appId": "5e2795e3-ce8c-4cfb-b302-35fe5cd01597",
          "displayName": "Designer",
          "activeStorageUsedInBytes": 32212254720,
          "activeContainerCount": 780
        }
      ]
    },
    {
      "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerGeoUsage",
      "dataLocationCode": "EUR",
      "activeStorageUsedInBytes": 21474836480,
      "activeContainerCount": 470,
      "usageByApp": [
        {
          "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerAppUsage",
          "appId": "a187e399-0c36-4b98-8f04-1edc167a0996",
          "displayName": "Loop",
          "activeStorageUsedInBytes": 16106127360,
          "activeContainerCount": 350
        },
        {
          "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerAppUsage",
          "appId": "5e2795e3-ce8c-4cfb-b302-35fe5cd01597",
          "displayName": "Designer",
          "activeStorageUsedInBytes": 5368709120,
          "activeContainerCount": 120
        }
      ]
    }
  ]
}
```
