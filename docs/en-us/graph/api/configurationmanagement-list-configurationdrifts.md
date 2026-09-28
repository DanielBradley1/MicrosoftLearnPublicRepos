<!-- Source: https://learn.microsoft.com/en-us/graph/api/configurationmanagement-list-configurationdrifts?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# List configurationDrifts

Namespace: microsoft.graph

Get a list of the [configurationDrift](https://learn.microsoft.com/en-us/graph/api/resources/configurationdrift?view=graph-rest-1.0) objects and their properties.

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
GET /admin/configurationManagement/configurationDrifts
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

If successful, this method returns a `200 OK` response code and a collection of [configurationDrift](https://learn.microsoft.com/en-us/graph/api/resources/configurationdrift?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/admin/configurationManagement/configurationDrifts
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.ConfigurationManagement.ConfigurationDrifts.GetAsync();
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
configurationDrifts, err := graphClient.Admin().ConfigurationManagement().ConfigurationDrifts().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConfigurationDriftCollectionResponse result = graphClient.admin().configurationManagement().configurationDrifts().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let configurationDrifts = await client.api('/admin/configurationManagement/configurationDrifts')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->configurationManagement()->configurationDrifts()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.ConfigurationManagement

Get-MgAdminConfigurationManagementConfigurationDrift
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.configuration_management.configuration_drifts.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/configurationManagement/configurationDrifts",
  "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET admin/configurationManagement/configurationDrifts?$select=baselineResourceDisplayName,driftedProperties",
  "value": [
    {
      "id": "4e808e99-7f60-4194-8294-02ede71effd8",
      "monitorId": "b166c9cb-db29-438b-95fb-247da1dc72c3",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "resourceType": "microsoft.exchange.accepteddomain",
      "baselineResourceDisplayName": "Accepted Domain",
      "firstReportedDateTime": "2024-12-12T09:00:57.4830642Z",
      "status": "active",
      "resourceInstanceIdentifier": {
        "Identity": "contoso.onmicrosoft.com"
      },
      "driftedProperties": [
        {
          "propertyName": "Ensure",
          "currentValue": "Absent",
          "desiredValue": "Present"
        }
      ]
    },
    {
      "id": "f30f8d6b-ea1e-4e1e-995e-341735ea01f4",
      "monitorId": "a7d89e42-1c3f-4b8e-9f2a-8c5d7e6f4a3b",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "resourceType": "microsoft.aad.conditionalaccesspolicy",
      "baselineResourceDisplayName": "Corporate Network Access Policy",
      "firstReportedDateTime": "2024-12-12T06:00:39.2072475Z",
      "status": "active",
      "resourceInstanceIdentifier": {
        "DisplayName": "Block access from untrusted locations"
      },
      "driftedProperties": [
        {
          "propertyName": "State",
          "currentValue": "Disabled",
          "desiredValue": "Enabled"
        },
        {
          "propertyName": "IncludeLocations",
          "currentValue": "All",
          "desiredValue": "AllTrusted"
        }
      ]
    },
    {
      "id": "9d43b643-71ab-4415-8d98-ca28c7cf0df4",
      "monitorId": "69b6b9ba-20c9-4ffb-beef-263c07063222",
      "tenantId": "96bf81b4-2694-42bb-9204-70081135ca61",
      "resourceType": "microsoft.compliance.retentionpolicy",
      "baselineResourceDisplayName": "Financial Records Retention",
      "firstReportedDateTime": "2024-12-12T06:00:38.1402661Z",
      "status": "active",
      "resourceInstanceIdentifier": {
        "Name": "Finance-7YearRetention"
      },
      "driftedProperties": [
        {
          "propertyName": "RetentionDuration",
          "currentValue": "1825",
          "desiredValue": "2555"
        },
        {
          "propertyName": "Enabled",
          "currentValue": "False",
          "desiredValue": "True"
        }
      ]
    }
  ]
}
```
