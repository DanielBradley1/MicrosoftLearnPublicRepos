<!-- Source: https://learn.microsoft.com/en-us/graph/api/auditlogroot-getsummarizednoninteractivesignins?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-29 -->

# auditLogRoot: getSummarizedNonInteractiveSignIns

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Returns aggregated non-interactive [sign-in event](https://learn.microsoft.com/en-us/graph/api/resources/summarizedsignin?view=graph-rest-beta) counts grouped by user, application, IP address, and time window, with drill-down capability using individual requestIds via the [/signIns](https://learn.microsoft.com/en-us/graph/api/signin-list?view=graph-rest-beta) endpoint. This includes autonomous agent sign-in events.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AuditLog.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AuditLog.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Reports Reader
- Security Administrator
- Security Reader

## HTTP request

```http
GET /auditLogs/getSummarizedNonInteractiveSignIns(aggregationWindow='{aggregationWindow}')
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| aggregationWindow | aggregationWindow | The aggregation window to get summary for. The possible values are: `h1` \(1 hour\), `h6` \(6 hours\), `d1` \(1 day\). |

## Optional query parameters

This method supports the `$filter` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response. You can apply `$filter` on one or more of the following properties of the [summarizedSignIn](https://learn.microsoft.com/en-us/graph/api/resources/summarizedsignin?view=graph-rest-beta) resource. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters). You may also apply the `$top` query parameter to limit the number of results returned to a specific number. The default and max `$top` parameter is 1000 records.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [summarizedSignIn](https://learn.microsoft.com/en-us/graph/api/resources/summarizedsignin?view=graph-rest-beta) collection in the response body.

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
GET https://graph.microsoft.com/beta/auditLogs/getSummarizedNonInteractiveSignIns(aggregationWindow='d1')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.AuditLogs.GetSummarizedNonInteractiveSignInsWithAggregationWindow("h1").GetAsGetSummarizedNonInteractiveSignInsWithAggregationWindowGetResponseAsync();
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
aggregationWindow := "h1"
getSummarizedNonInteractiveSignIns, err := graphClient.AuditLogs().GetSummarizedNonInteractiveSignInsWithAggregationWindow(&aggregationWindow).GetAsGetSummarizedNonInteractiveSignInsWithAggregationWindowGetResponse(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.auditLogs().getSummarizedNonInteractiveSignInsWithAggregationWindow("h1").get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getSummarizedNonInteractiveSignIns = await client.api('/auditLogs/getSummarizedNonInteractiveSignIns(aggregationWindow='d1')')
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


$result = $graphServiceClient->auditLogs()->getSummarizedNonInteractiveSignInsWithAggregationWindow('h1', )->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Get-MgBetaAuditLogSummarizedNonInteractiveSignIn -AggregationWindow $aggregationWindowId 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.audit_logs.get_summarized_non_interactive_sign_ins_with_aggregation_window("h1").get()
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
      "signInCount": 18,
      "aggregationDateTime": "2025-02-26T06:00:00Z",
      "id": "00000000-0000-0000-0000-000000000000",
      "firstSignInDateTime": "2025-02-26T06:08:33Z",
      "userPrincipalName": "",
      "appId": "00000000-0000-0000-0000-000000000000",
      "appDisplayName": "Azure Logic Apps",
      "ipAddress": "0.0.0.0",
      "conditionalAccessStatus": "success",
      "resourceDisplayName": "Azure Storage",
      "resourceId": "00000000-0000-0000-0000-000000000000",
      "tenantId": "00000000-0000-0000-0000-000000000000",
      "servicePrincipalName": null,
      "servicePrincipalId": "",
      "status": {
        "errorCode": 0,
        "failureReason": null,
        "additionalDetails": null
      },
      "managedServiceIdentity": {
        "msiType": "systemAssigned",
        "associatedResourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Logic/workflows/myLogicApp",
        "federatedTokenId": null,
        "federatedTokenIssuer": null
      },
      "agent": {
        "agentType": "notAgentic",
        "parentAppId": null
      }
    },
    {
      "signInCount": 9,
      "aggregationDateTime": "2025-02-26T06:00:00Z",
      "id": "00000000-0000-0000-0000-000000000000",
      "firstSignInDateTime": "2025-02-26T06:18:55Z",
      "userPrincipalName": "",
      "appId": "00000000-0000-0000-0000-000000000000",
      "appDisplayName": "Azure Portal",
      "ipAddress": "0.0.0.0",
      "conditionalAccessStatus": "success",
      "resourceDisplayName": "Microsoft Graph",
      "resourceId": "00000000-0000-0000-0000-000000000000",
      "tenantId": "00000000-0000-0000-0000-000000000000",
      "servicePrincipalName": null,
      "servicePrincipalId": "",
      "status": {
        "errorCode": 0,
        "failureReason": null,
        "additionalDetails": null
      },
      "managedServiceIdentity": {
        "msiType": "userAssigned",
        "associatedResourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myUserAssignedIdentity",
        "federatedTokenId": "arn:aws:iam::123456789012:role/MyFederatedRole",
        "federatedTokenIssuer": "https://token.actions.githubusercontent.com"
      },
      "agent": {
        "agentType": "notAgentic",
        "parentAppId": null
      }
    },
    {
      "signInCount": 5,
      "aggregationDateTime": "2025-02-26T06:00:00Z",
      "id": "00000000-0000-0000-0000-000000000000",
      "firstSignInDateTime": "2025-02-26T06:42:17Z",
      "userPrincipalName": "",
      "appId": "00000000-0000-0000-0000-000000000000",
      "appDisplayName": "Azure DevOps",
      "ipAddress": "0.0.0.0",
      "conditionalAccessStatus": "failure",
      "resourceDisplayName": "Azure Key Vault",
      "resourceId": "00000000-0000-0000-0000-000000000000",
      "tenantId": "00000000-0000-0000-0000-000000000000",
      "servicePrincipalName": null,
      "servicePrincipalId": "",
      "status": {
        "errorCode": 70011,
        "failureReason": "The resource is not available",
        "additionalDetails": "Managed identity not found"
      },
      "managedServiceIdentity": {
        "msiType": "systemAssigned",
        "associatedResourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp",
        "federatedTokenId": null,
        "federatedTokenIssuer": null
      },
      "agent": {
        "agentType": "notAgentic",
        "parentAppId": null
      }
    }
  ]
}
```
