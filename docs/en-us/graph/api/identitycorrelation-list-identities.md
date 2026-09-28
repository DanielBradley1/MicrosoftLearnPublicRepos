<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitycorrelation-list-identities?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-08 -->

# List correlatedIdentity objects

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

List the [correlatedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/correlatedidentity?view=graph-rest-beta) results for an [identityCorrelation](https://learn.microsoft.com/en-us/graph/api/resources/identitycorrelation?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ProvisioningLog.Read.All | AuditLog.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ProvisioningLog.Read.All | AuditLog.Read.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Enterprise Application Owner
- Application Administrator
- Cloud Application Administrator
- Hybrid Identity Administrator
- Global Reader
- Reports Reader
- Security Administrator
- Security Operator
- Security Reader

## HTTP request

```http
GET /reports/correlations/{identityCorrelationId}/identities
```

## Optional query parameters

This method supports the `$filter` \(`eq` on **id**, **error**, **status**, **sourceIdentity**, and **targetIdentity**\), `$orderby` \(**correlatedDateTime**\), `$top`, and `$count` OData query parameters to help customize the response. The `$count` query parameter is only supported when filtering on the **status** property. The default and maximum page sizes are 1,000 entries. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [correlatedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/correlatedidentity?view=graph-rest-beta) objects in the response body.

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
GET https://graph.microsoft.com/beta/reports/correlations/{identityCorrelationId}/identities
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Reports.Correlations["{identityCorrelation-id}"].Identities.GetAsync();
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
identities, err := graphClient.Reports().Correlations().ByIdentityCorrelationId("identityCorrelation-id").Identities().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CorrelatedIdentityCollectionResponse result = graphClient.reports().correlations().byIdentityCorrelationId("{identityCorrelation-id}").identities().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let identities = await client.api('/reports/correlations/{identityCorrelationId}/identities')
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


$result = $graphServiceClient->reports()->correlations()->byIdentityCorrelationId('identityCorrelation-id')->identities()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Reports

Get-MgBetaReportCorrelationIdentity -IdentityCorrelationId $identityCorrelationId
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.reports.correlations.by_identity_correlation_id('identityCorrelation-id').identities.get()
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
      "@odata.type": "#microsoft.graph.correlatedIdentity",
      "id": "a3f7b2c1-4e89-4d6a-b5c8-9e2f1a7d3b60",
      "correlatedDateTime": "2026-05-01T01:27:00Z",
      "sourceIdentity": {
        "anchor": {
          "name": "objectId",
          "value": "jamie998877"
        },
        "matchingProperty": {
          "name": "userPrincipalName",
          "value": "jamie@contoso.com"
        },
        "identityType": "user",
        "details": {}
      },
      "targetIdentity": {
        "anchor": {
          "name": "id",
          "value": "d8e4c6a2-7f13-4b95-a1d9-5c3e8b6f2a74"
        },
        "matchingProperty": {
          "name": "upn",
          "value": "jamie@contoso.com"
        },
        "identityType": "user",
        "details": {}
      },
      "status": "correlatedAssigned",
      "error": null
    },
    {
      "@odata.type": "#microsoft.graph.correlatedIdentity",
      "id": "b4c8d3e2-5f9a-4e7b-c6d9-0f3a2b8e4c71",
      "correlatedDateTime": "2026-05-01T01:28:00Z",
      "sourceIdentity": null,
      "targetIdentity": {
        "anchor": {
          "name": "id",
          "value": "e9f5d7b3-8a24-4c06-b2ea-6d4f9c7a3b85"
        },
        "matchingProperty": {
          "name": "upn",
          "value": "alex@contoso.com"
        },
        "identityType": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
        "details": {}
      },
      "status": "uncorrelated",
      "error": null
    },
    {
      "@odata.type": "#microsoft.graph.correlatedIdentity",
      "id": "c5d9e4f3-6a0b-4f8c-d7e0-1a4b3c9f5d82",
      "correlatedDateTime": "2026-05-01T01:29:00Z",
      "sourceIdentity": null,
      "targetIdentity": {
        "anchor": {
          "name": "id",
          "value": "f0a6e8c4-9b35-4d17-c3fb-7e5a0d8b4c96"
        },
        "matchingProperty": {
          "name": "upn",
          "value": "morgan@@company..com"
        },
        "identityType": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
        "details": {}
      },
      "status": "failToCorrelate",
      "error": {
        "code": "AzureActiveDirectoryInvalidUserPrinicipalNameFormat",
        "message": "The format of this user principal name is unexpected"
      }
    },
    {
      "@odata.type": "#microsoft.graph.correlatedIdentity",
      "id": "d6e0f5a4-7b1c-4a9d-e8f1-2b5c4d0a6e93",
      "correlatedDateTime": "2026-05-01T01:30:00Z",
      "sourceIdentity": {
        "anchor": {
          "name": "objectId",
          "value": "taylor667788"
        },
        "matchingProperty": {
          "name": "userPrincipalName",
          "value": "taylor@contoso.com"
        },
        "identityType": "user",
        "details": {}
      },
      "targetIdentity": {
        "anchor": {
          "name": "id",
          "value": "a1b7f9d5-0c46-4e28-d4ac-8f6b1e9c5d07"
        },
        "matchingProperty": {
          "name": "upn",
          "value": "taylor@contoso.com"
        },
        "identityType": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
        "details": {}
      },
      "status": "correlatedNotAssigned",
      "error": null
    }
  ]
}
```
