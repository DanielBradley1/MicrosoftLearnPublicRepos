<!-- Source: https://learn.microsoft.com/en-us/graph/api/migrationsroot-list-crosstenantmigrationjobs?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# List crossTenantMigrationJob objects

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) objects and their properties. By default 20 objects are returned. More can be retrieved through the `@odata.nextLink` url provided in the response.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CrossTenantContentMigration.Read.All | CrossTenantContentMigration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CrossTenantContentMigration.Read.All | CrossTenantContentMigration.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Microsoft 365 Migration Administrator
- Global Administrator

## HTTP request

```http
GET /solutions/migrations/crossTenantMigrationJobs
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) objects in the response body.

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
GET https://graph.microsoft.com/beta/solutions/migrations/crossTenantMigrationJobs
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.Migrations.CrossTenantMigrationJobs.GetAsync();
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
crossTenantMigrationJobs, err := graphClient.Solutions().Migrations().CrossTenantMigrationJobs().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CrossTenantMigrationJobCollectionResponse result = graphClient.solutions().migrations().crossTenantMigrationJobs().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let crossTenantMigrationJobs = await client.api('/solutions/migrations/crossTenantMigrationJobs')
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


$result = $graphServiceClient->solutions()->migrations()->crossTenantMigrationJobs()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Migrations

Get-MgBetaCrossTenantMigrationJob
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.migrations.cross_tenant_migration_jobs.get()
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#solutions/migrations/crossTenantMigrationJobs",
  "@odata.nextLink": "https://graph.microsoft.com/beta/solutions/migrations/CrossTenantMigrationJobs?$skiptoken=%5b%7B%22compositeToken%22%3a%7B%22token%22%3a%22%2bRID%3a~q1NPAJxLNS1QBAAAAAAAAA%3d%3d%23RT%3a1%23TRC%3a20%23RTD%3aHPJJmKT1uZqlBBnGyNSOBMHbIcd%5d",
  "value": [
    {
      "id": "012ec4f4-df7e-41ae-ba95-6d7ccb8f74a1",
      "displayName": "Contoso_migration_job",
      "status": "completed",
      "jobType": "migrate",
      "message": "The batch and all of its users have been successfully migrated with no failures.",
      "completeAfterDateTime": "2025-11-06T09:11:33.2115505Z",
      "sourceTenantId": "12345678-1234-1234-1234-123456789012",
      "targetTenantId": "87654321-4321-4321-4321-210987654321",
      "resourceType": "users",
      "resources": [],
      "workloads": [],
      "createdBy": "a0d9fdb1-171f-4e2b-8a82-06775ad24790",
      "createdDateTime": "2025-11-06T09:06:34.4773205Z",
      "lastUpdatedDateTime": "2025-11-06T11:26:00Z",
      "exchangeSettings": {
        "targetDeliveryDomain": "fabrikam.onmicrosoft.com",
        "sourceEndpoint": "EXOHandler"
      }
    },
    {
      "id": "0d1d9dbb-7676-4731-a601-5e8406fd7bcf",
      "displayName": "Contoso_validation_job",
      "status": "validatePassed",
      "jobType": "validate",
      "message": "Validation has completed successfully with no failures.",
      "completeAfterDateTime": "2025-05-22T17:14:52Z",
      "sourceTenantId": "12345678-1234-1234-1234-123456789012",
      "targetTenantId": "87654321-4321-4321-4321-210987654321",
      "resourceType": "users",
      "resources": [],
      "workloads": [
        "teams"
      ],
      "createdBy": "a0d9fdb1-171f-4e2b-8a82-06775ad24790",
      "createdDateTime": "2025-11-07T00:19:21.4810014Z",
      "lastUpdatedDateTime": "2025-11-07T00:22:03Z",
      "exchangeSettings": {
        "targetDeliveryDomain": "fabrikam.onmicrosoft.com",
        "sourceEndpoint": "EXOHandler"
      }
    }
  ]
}
```
