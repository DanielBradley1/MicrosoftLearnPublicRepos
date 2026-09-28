<!-- Source: https://learn.microsoft.com/en-us/graph/api/configurationmanagement-list-configurationmonitoringresults?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# List configurationMonitoringResults

Namespace: microsoft.graph

Get a list of the [configurationMonitoringResult](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitoringresult?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ConfigurationMonitoring.Read.All | ConfigurationMonitoring.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ConfigurationMonitoring.Read.All | ConfigurationMonitoring.ReadWrite.All |

## HTTP request

```http
GET /admin/configurationManagement/configurationMonitoringResults
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$orderBy`, and `$top` OData query parameters to help customize the response. The default page size is 100 items and the maximum page size is 999 items. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [configurationMonitoringResult](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitoringresult?view=graph-rest-1.0) objects in the response body.

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

```http
GET https://graph.microsoft.com/v1.0/admin/configurationManagement/configurationMonitoringResults
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.ConfigurationManagement.ConfigurationMonitoringResults.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
configurationMonitoringResults, err := graphClient.Admin().ConfigurationManagement().ConfigurationMonitoringResults().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConfigurationMonitoringResultCollectionResponse result = graphClient.admin().configurationManagement().configurationMonitoringResults().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let configurationMonitoringResults = await client.api('/admin/configurationManagement/configurationMonitoringResults')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->configurationManagement()->configurationMonitoringResults()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.ConfigurationManagement

Get-MgAdminConfigurationManagementConfigurationMonitoringResult
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.configuration_management.configuration_monitoring_results.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/configurationManagement/configurationMonitoringResults",
  "@microsoft.graph.tips": "This request only returns a subset of the resource's properties. Your app will need to use $select to return non-default properties. To find out what other properties are available for this resource see https://learn.microsoft.com/graph/api/resources/configurationMonitoringResult",
  "value": [
    {
      "id": "66fa1689-22cb-49c1-8b5a-c94822b7b13b",
      "monitorId": "69b6b9ba-20c9-4ffb-beef-263c07063222",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "runInitiationDateTime": "2024-12-12T09:00:36.1084955Z",
      "runCompletionDateTime": "2024-12-12T09:00:36.1084955Z",
      "runStatus": "failed",
      "driftsCount": 0
    },
    {
      "id": "3c7e14e9-2393-4ce8-8a02-584836d49c29",
      "monitorId": "69b6b9ba-20c9-4ffb-beef-263c07063222",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "runInitiationDateTime": "2024-12-12T06:00:21.6023183Z",
      "runCompletionDateTime": "2024-12-12T06:00:21.6023183Z",
      "runStatus": "successful",
      "driftsCount": 3
    },
    {
      "id": "17fc9f1c-771a-4ec4-9894-48ab2d89dd2c",
      "monitorId": "69b6b9ba-20c9-4ffb-beef-263c07063222",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "runInitiationDateTime": "2024-12-12T03:00:07.9629206Z",
      "runCompletionDateTime": "2024-12-12T03:00:07.9629206Z",
      "runStatus": "failed",
      "driftsCount": 0
    },
    {
      "id": "ebffda35-90c8-4157-a757-cecbc0df968c",
      "monitorId": "69b6b9ba-20c9-4ffb-beef-263c07063222",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "runInitiationDateTime": "2024-12-12T00:00:15.2616957Z",
      "runCompletionDateTime": "2024-12-12T00:00:15.2616957Z",
      "runStatus": "failed",
      "driftsCount": 0
    },
    {
      "id": "962827e5-b82a-4d50-b343-be268db625c9",
      "monitorId": "69b6b9ba-20c9-4ffb-beef-263c07063222",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "runInitiationDateTime": "2024-12-11T21:00:11.4750106Z",
      "runCompletionDateTime": "2024-12-11T21:00:11.4750106Z",
      "runStatus": "failed",
      "driftsCount": 0
    },
    {
      "id": "2196ccc4-85d7-4427-ab81-8a8a46422d0d",
      "monitorId": "69b6b9ba-20c9-4ffb-beef-263c07063222",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "runInitiationDateTime": "2024-12-11T18:00:38.3070963Z",
      "runCompletionDateTime": "2024-12-11T18:00:38.3070963Z",
      "runStatus": "successful",
      "driftsCount": 3
    },
    {
      "id": "89acf0d8-3f6e-454d-b786-ef8370075d4a",
      "monitorId": "69b6b9ba-20c9-4ffb-beef-263c07063222",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "runInitiationDateTime": "2024-12-11T15:05:18.4677889Z",
      "runCompletionDateTime": "2024-12-11T15:05:18.4677889Z",
      "runStatus": "failed",
      "driftsCount": 0
    },
    {
      "id": "80e9906d-417b-4f79-a1b3-532260d090bf",
      "monitorId": "69b6b9ba-20c9-4ffb-beef-263c07063222",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "runInitiationDateTime": "2024-12-11T12:18:34.1083345Z",
      "runCompletionDateTime": "2024-12-11T12:18:34.1083345Z",
      "runStatus": "successful",
      "driftsCount": 3
    }
  ]
}
```
