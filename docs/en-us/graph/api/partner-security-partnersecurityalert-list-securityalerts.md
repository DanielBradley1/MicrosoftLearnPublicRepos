<!-- Source: https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityalert-list-securityalerts?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-11 -->

# List securityAlerts

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [partnerSecurityAlert](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PartnerSecurity.Read.All | PartnerSecurity.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PartnerSecurity.Read.All | PartnerSecurity.ReadWrite.All |

## HTTP request

```http
GET /security/partner/securityAlerts
```

## Optional query parameters

This method supports the `$count`, `$filter`, and `$select` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.partner.security.partnerSecurityAlert](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta) objects in the response body.

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
GET https://graph.microsoft.com/beta/security/partner/securityAlerts
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Partner.SecurityAlerts.GetAsync();
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
securityAlerts, err := graphClient.Security().Partner().SecurityAlerts().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.partner.security.PartnerSecurityAlertCollectionResponse result = graphClient.security().partner().securityAlerts().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let securityAlerts = await client.api('/security/partner/securityAlerts')
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


$result = $graphServiceClient->security()->partner()->securityAlerts()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

Get-MgBetaSecurityPartnerSecurityAlert
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.security.partner.security_alerts.get()
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
  "value": [
    {
      "id": "d8b202fc-a216-3404-69ef-bdffa445eff6",
      "displayName": "Action Required: Virtual machine connecting to crypto currency mining pool Detected",
      "description": "Analysis of Azure resource network activity detected the resource was connecting to a crypto currency mining pool. This would often be an indication that your Azure resource is compromised.",
      "alertType": "networkConnectionsToCryptoMiningPools",
      "status": "active",
      "severity": "high",
      "confidenceLevel": "medium",
      "customerTenantId": "1889e718-414b-4bad-8bbe-c1135bd39a41",
      "subscriptionId": "5f6e6521-6e5f-4b0b-80aa-bd44fad7a398",
      "valueAddedResellerTenantId": "c296b2ce-8cd1-4346-9e82-d8eccca70d65",
      "catalogOfferId": "MS-AZR-0017G",
      "detectedDateTime": "2024-01-23T16:03:33.05Z",
      "firstObservedDateTime": "2024-01-23T16:03:33.05Z",
      "lastObservedDateTime": "2024-01-23T16:03:33.05Z",
      "resolvedReason": "fraud",
      "resolvedOnDateTime": "2024-02-23T16:03:33.05Z",
      "resolvedBy": "danas@contoso.com",
      "isTest": false,
      "affectedResources": [
        {
          "resourceId": "/subscriptions/subscription-id/resourceGroups/resourcegroup-name/providers/Microsoft.Compute/virtualMachines/vm-name",
          "resourceType": "AzureResource"
        }
      ],
      "activityLogs": [
        {
          "statusFrom": "active",
          "statusTo": "investigating",
          "updatedBy": "samanthab@contoso.com",
          "updatedDateTime": "2023-08-10T08:47:10.8454142Z"
        },
        {
          "statusFrom": "investigating",
          "statusTo": "resolved",
          "updatedBy": "samanthab@contoso.com",
          "updatedDateTime": "2023-08-10T08:47:25.2089246Z"
        }
      ],
      "additionalDetails": {
        "VM_IP": "[  \"vm-ip\"]",
        "MiningPool_IP": "[  \"mining-pool-ip\"]",
        "ConnectionCount": "5",
        "CryptoCurrencyMiningPoolDomainName": "pool-name.com"
      }
    },
    {
      "id": "5f6e6521-6e5f-4b0b-80aa-bd44fad7a398-758e2259-f00b-4dec-8087-0950afe6d6a4",
      "displayName": "Action Required: Subscription Usage Anomaly Detected",
      "description": "Analysis of Azure resource detected anomalies in: Anomalous increase in Machine Learning General purpose CPU deployment regions compared to trend in the last 30 days Subscription is part of a cluster of subscriptions that are controlled from the same login session IP Address.",
      "alertType": "usageAnomalyDetection",
      "status": "investigating",
      "severity": "high",
      "confidenceLevel": "medium",
      "customerTenantId": "1889e718-414b-4bad-8bbe-c1135bd39a41",
      "subscriptionId": "5f6e6521-6e5f-4b0b-80aa-bd44fad7a398",
      "valueAddedResellerTenantId": "c296b2ce-8cd1-4346-9e82-d8eccca70d65",
      "catalogOfferId": null,
      "detectedDateTime": "2024-01-23T16:03:33.05Z",
      "firstObservedDateTime": "2024-01-23T16:03:33.05Z",
      "lastObservedDateTime": "2024-01-23T16:03:33.05Z",
      "resolvedReason": null,
      "resolvedOnDateTime": null,
      "resolvedBy": "danas@contoso.com",
      "isTest": false,
      "affectedResources": [
        {
          "resourceId": "/subscriptions/subscription-id/resourceGroups/resourcegroup-name/providers/Microsoft.Compute/virtualMachines/vm-name",
          "resourceType": "AzureResource"
        }
      ],
      "activityLogs": [
        {
          "statusFrom": "active",
          "statusTo": "investigating",
          "updatedBy": "samanthab@contoso.com",
          "updatedDateTime": "2023-08-10T08:47:10.8454142Z"
        }
      ],
      "additionalDetails": {
        "VM_IP": "[  \"vm-ip\"]",
        "MiningPool_IP": "[  \"mining-pool-ip\"]",
        "ConnectionCount": "5",
        "CryptoCurrencyMiningPoolDomainName": "pool-name.com"
      }
    }
  ]
}
```
