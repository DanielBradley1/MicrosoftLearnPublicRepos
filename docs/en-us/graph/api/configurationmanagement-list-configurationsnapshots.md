<!-- Source: https://learn.microsoft.com/en-us/graph/api/configurationmanagement-list-configurationsnapshots?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# List configurationSnapshots

Namespace: microsoft.graph

Get a list of [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) objects that represent configuration snapshots and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /admin/configurationManagement/configurationSnapshots
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

If successful, this method returns a `200 OK` response code and a collection of [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/admin/configurationManagement/configurationSnapshots
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.ConfigurationManagement.ConfigurationSnapshots.GetAsync();
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
configurationSnapshots, err := graphClient.Admin().ConfigurationManagement().ConfigurationSnapshots().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConfigurationBaselineCollectionResponse result = graphClient.admin().configurationManagement().configurationSnapshots().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let configurationSnapshots = await client.api('/admin/configurationManagement/configurationSnapshots')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->configurationManagement()->configurationSnapshots()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.ConfigurationManagement

Get-MgAdminConfigurationManagementConfigurationSnapshot
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.configuration_management.configuration_snapshots.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/configurationManagement/configurationSnapshots",
  "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET admin/configurationManagement/configurationSnapshots?$select=description,displayName",
  "value": [
    {
      "id": "5b15be20-897f-4b79-85a6-97871c708f6f",
      "displayName": "Exchange Configuration Baseline",
      "description": "Baseline capturing Exchange shared mailbox and accepted domain settings",
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
        }
      ]
    },
    {
      "id": "a8c3f2e1-4b9d-4c7a-9e2f-6d8b5a7c3e1f",
      "displayName": "Entra ID Security Baseline",
      "description": "Baseline for conditional access and authentication policies",
      "parameters": [
        {
          "displayName": "TenantId",
          "description": "Target tenant identifier",
          "parameterType": "string"
        }
      ],
      "resources": [
        {
          "displayName": "Corporate Network Access Policy",
          "resourceType": "microsoft.aad.conditionalaccesspolicy",
          "properties": {
            "DisplayName": "Block access from untrusted locations",
            "State": "Enabled",
            "IncludeLocations": "AllTrusted",
            "ExcludeLocations": [],
            "IncludeUsers": "All",
            "GrantControlsOperator": "OR"
          }
        },
        {
          "displayName": "MFA Registration Policy",
          "resourceType": "microsoft.aad.authenticationmethodspolicy",
          "properties": {
            "PolicyName": "MFARegistrationCampaign",
            "State": "Enabled",
            "IncludeTargets": "All",
            "SnoozeDurationInDays": "14"
          }
        }
      ]
    },
    {
      "id": "c2d5e8f1-9a3b-4e6c-8f2d-1a7b9c4e6f3a",
      "displayName": "Compliance Retention Baseline",
      "description": "Baseline for retention policies and labels",
      "parameters": [],
      "resources": [
        {
          "displayName": "Financial Records Retention",
          "resourceType": "microsoft.compliance.retentionpolicy",
          "properties": {
            "Name": "Finance-7YearRetention",
            "RetentionDuration": "2555",
            "Enabled": "True",
            "Comment": "Regulatory requirement for financial documents"
          }
        },
        {
          "displayName": "Legal Hold Label",
          "resourceType": "microsoft.compliance.retentionlabel",
          "properties": {
            "Name": "LegalHold",
            "RetentionDuration": "Unlimited",
            "RetentionAction": "Keep",
            "Comment": "Applied to items under legal review"
          }
        }
      ]
    }
  ]
}
```
