<!-- Source: https://learn.microsoft.com/en-us/graph/api/configurationbaseline-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# Get configurationBaseline

Namespace: microsoft.graph

Read the properties and relationships of a [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) object that is attached to a specific monitor.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ConfigurationMonitoring.Read.All | ConfigurationMonitoring.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ConfigurationMonitoring.Read.All | ConfigurationMonitoring.ReadWrite.All |

## HTTP request

```http
GET /admin/configurationManagement/configurationMonitors/{configurationMonitorId}/baseline
```

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) object in the response body.

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
GET https://graph.microsoft.com/v1.0/admin/configurationManagement/configurationMonitors/b86049ce-0180-404e-803a-5616d49290d7/baseline
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.ConfigurationManagement.ConfigurationMonitors["{configurationMonitor-id}"].Baseline.GetAsync();
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
baseline, err := graphClient.Admin().ConfigurationManagement().ConfigurationMonitors().ByConfigurationMonitorId("configurationMonitor-id").Baseline().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConfigurationBaseline result = graphClient.admin().configurationManagement().configurationMonitors().byConfigurationMonitorId("{configurationMonitor-id}").baseline().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let configurationBaseline = await client.api('/admin/configurationManagement/configurationMonitors/b86049ce-0180-404e-803a-5616d49290d7/baseline')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->configurationManagement()->configurationMonitors()->byConfigurationMonitorId('configurationMonitor-id')->baseline()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.ConfigurationManagement

Get-MgAdminConfigurationManagementConfigurationMonitorBaseline -ConfigurationMonitorId $configurationMonitorId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.configuration_management.configuration_monitors.by_configuration_monitor_id('configurationMonitor-id').baseline.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/configurationManagement/configurationMonitors('f1b46220-74af-4347-9ac7-89fe17d57bd7')/baseline/$entity",
  "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET admin/configurationManagement/configurationMonitors('<guid>')/baseline?$select=description,displayName",
  "id": "5b15be20-897f-4b79-85a6-97871c708f6f",
  "displayName": "Demo Baseline",
  "description": "This is a baseline with SharedMailbox, AcceptedDomain and MailContact",
  "parameters": [],
  "resources": [
    {
      "displayName": "TestSharedMailbox Resource",
      "resourceType": "microsoft.exchange.sharedmailbox",
      "properties": {
        "DisplayName": "TestSharedMailbox",
        "Alias": "testSharedMailbox",
        "Identity": "TestSharedMailbox",
        "Ensure": "Present",
        "PrimarySmtpAddress": "testSharedMailbox@contoso.onmicrosoft.com",
        "EmailAddresses": [
          "abc@contoso.onmicrosoft.com"
        ]
      }
    },
    {
      "displayName": "Accepted Domain",
      "resourceType": "microsoft.exchange.accepteddomain",
      "properties": {
        "Identity": "contoso.onmicrosoft.com",
        "DomainType": "InternalRelay",
        "Ensure": "Present"
      }
    },
    {
      "displayName": "Mail Contact Resource",
      "resourceType": "microsoft.exchange.mailcontact",
      "properties": {
        "Name": "Chris",
        "DisplayName": "Chris",
        "ExternalEmailAddress": "SMTP:chris@fabrikam.com",
        "Alias": "Chrisa",
        "Ensure": "Present"
      }
    }
  ]
}
```
