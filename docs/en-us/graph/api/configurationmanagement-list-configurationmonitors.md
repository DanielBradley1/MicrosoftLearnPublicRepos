<!-- Source: https://learn.microsoft.com/en-us/graph/api/configurationmanagement-list-configurationmonitors?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# List configurationMonitors

Namespace: microsoft.graph

Get a list of the [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) objects and their properties.

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
GET /admin/configurationManagement/configurationMonitors
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

If successful, this method returns a `200 OK` response code and a collection of [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/admin/configurationManagement/configurationMonitors
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.ConfigurationManagement.ConfigurationMonitors.GetAsync();
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
configurationMonitors, err := graphClient.Admin().ConfigurationManagement().ConfigurationMonitors().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConfigurationMonitorCollectionResponse result = graphClient.admin().configurationManagement().configurationMonitors().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let configurationMonitors = await client.api('/admin/configurationManagement/configurationMonitors')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->configurationManagement()->configurationMonitors()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.ConfigurationManagement

Get-MgAdminConfigurationManagementConfigurationMonitor
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.configuration_management.configuration_monitors.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/configurationManagement/configurationMonitors",
  "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET admin/configurationManagement/configurationMonitors?$select=createdBy,createdDateTime",
  "value": [
    {
      "id": "bf77ee1e-7750-40cb-8bcd-524dc4cdab02",
      "inactivationReason": null,
      "displayName": "Demo Monitor",
      "description": "This is a Monitor with EXO resources",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "status": "active",
      "monitorRunFrequencyInHours": 6,
      "mode": "monitorOnly",
      "createdDateTime": "2024-12-12T09:52:18.7982733Z",
      "lastModifiedBy": {
        "user": {
          "id": "823da47e-fc25-48d8-8b5a-6186c760f0df",
          "displayName": "System Administrator"
        }
      },
      "lastModifiedDateTime": "2024-12-12T09:52:18.8274415Z",
      "createdBy": {
        "user": {
          "id": "823da47e-fc25-48d8-8b5a-6186c760f0df",
          "displayName": "System Administrator"
        }
      },
      "parameters": {
        "FQDN": "contoso.onmicrosoft.com",
        "TenantId": "2fcf1c68-b412-4c85-bfb2-cb20152a6843"
      }
    },
    {
      "id": "b166c9cb-db29-438b-95fb-247da1dc72c3",
      "inactivationReason": null,
      "displayName": "Demo Monitor 1",
      "description": "It is a monitor that is monitoring all accepted domains of the tenant",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "status": "active",
      "monitorRunFrequencyInHours": 6,
      "mode": "monitorOnly",
      "createdDateTime": "2024-12-12T05:24:01.9729016Z",
      "lastModifiedBy": {
        "user": {
          "id": "823da47e-fc25-48d8-8b5a-6186c760f0df",
          "displayName": "System Administrator"
        }
      },
      "lastModifiedDateTime": "2024-12-12T05:24:02.030975Z",
      "createdBy": {
        "user": {
          "id": "823da47e-fc25-48d8-8b5a-6186c760f0df",
          "displayName": "System Administrator"
        }
      },
      "parameters": {
        "FQDN": "contoso.onmicrosoft.com",
        "TenantId": "2fcf1c68-b412-4c85-bfb2-cb20152a6843"
      }
    },
    {
      "id": "a1cbec62-453e-421f-94b5-7a4288bc122a",
      "inactivationReason": null,
      "displayName": "Sample Monitor",
      "description": "Sample EXO Monitor with SharedMailbox AcceptedDomain and MailContact",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "status": "active",
      "monitorRunFrequencyInHours": 6,
      "mode": "monitorOnly",
      "createdDateTime": "2024-12-11T05:50:42.6436339Z",
      "lastModifiedBy": {
        "user": {
          "id": "823da47e-fc25-48d8-8b5a-6186c760f0df",
          "displayName": "System Administrator"
        }
      },
      "lastModifiedDateTime": "2024-12-11T05:50:42.6974645Z",
      "createdBy": {
        "user": {
          "id": "823da47e-fc25-48d8-8b5a-6186c760f0df",
          "displayName": "System Administrator"
        }
      },
      "parameters": {
        "FQDN": "contoso.onmicrosoft.com",
        "TenantId": "2fcf1c68-b412-4c85-bfb2-cb20152a6843"
      }
    }
  ]
}
```
