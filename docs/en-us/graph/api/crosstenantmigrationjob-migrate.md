<!-- Source: https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-migrate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# crossTenantMigrationJob: migrate

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Migrate a [cross-tenant migration job](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) asynchronously. The job must pass validation before migration can start. After a job is created by using the [Create crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/migrationsroot-post-crosstenantmigrationjobs?view=graph-rest-beta) method and validated by using the [validate](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-validate?view=graph-rest-beta) action, call this action to start the migration of user data from the source tenant to the target tenant for the specified workloads. Validation results expire after seven days; if expired, revalidate the job before you call the **migrate** API.

This action is asynchronous. After you call the **migrate** API, poll the [Get crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-get?view=graph-rest-beta) endpoint to check for a terminal status of `completed`, `completedWithErrors`, or `failed`.

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

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Microsoft 365 Migration Administrator
- Global Administrator

## HTTP request

```http
POST /solutions/migrations/crossTenantMigrationJobs/{crossTenantMigrationJobId}/migrate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code and a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) in the response body.

This method can also return the following error codes in the response body.

| Status code | Description |
| :--- | :--- |
| `404 Not Found` | The specified **crossTenantMigrationJob** wasn't found. |
| `409 Conflict` | The job isn't in a valid status for migration. The job must be in `validatePassed`, `failed`, or `completedWithErrors` status. |
| `409 Conflict` | The validation results expired \(more than seven days ago\). Revalidate the job before you call the **migrate** API. |

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
POST https://graph.microsoft.com/beta/solutions/migrations/crossTenantMigrationJobs/add14989-2b21-4001-81bd-a18b0bac1dea/migrate
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.Migrations.CrossTenantMigrationJobs["{crossTenantMigrationJob-id}"].Migrate.PostAsync();
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
migrate, err := graphClient.Solutions().Migrations().CrossTenantMigrationJobs().ByCrossTenantMigrationJobId("crossTenantMigrationJob-id").Migrate().Post(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.solutions().migrations().crossTenantMigrationJobs().byCrossTenantMigrationJobId("{crossTenantMigrationJob-id}").migrate().post();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/solutions/migrations/crossTenantMigrationJobs/add14989-2b21-4001-81bd-a18b0bac1dea/migrate')
	.version('beta')
	.post();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->migrations()->crossTenantMigrationJobs()->byCrossTenantMigrationJobId('crossTenantMigrationJob-id')->migrate()->post()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Migrations

Move-MgBetaCrossTenantMigrationJob -CrossTenantMigrationJobId $crossTenantMigrationJobId
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.migrations.cross_tenant_migration_jobs.by_cross_tenant_migration_job_id('crossTenantMigrationJob-id').migrate.post()
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.crossTenantMigrationJob",
  "id": "add14989-2b21-4001-81bd-a18b0bac1dea",
  "displayName": "Contoso_migration_job",
  "status": "processing",
  "jobType": "migrate",
  "message": "Migration job has been submitted successfully",
  "completeAfterDateTime": "2026-05-22T17:14:52Z",
  "sourceTenantId": "12345678-1234-1234-1234-123456789012",
  "targetTenantId": "87654321-4321-4321-4321-210987654321",
  "resourceType": "users",
  "resources": [],
  "workloads": [
    "Teams",
    "Exchange",
    "ODSP"
  ],
  "createdBy": "admin@fabrikam.onmicrosoft.com",
  "createdDateTime": "2026-05-04T20:55:10.5427196Z",
  "lastUpdatedDateTime": "2026-05-04T20:55:10Z",
  "exchangeSettings": {
    "targetDeliveryDomain": "fabrikam.com",
    "sourceEndpoint": "EXOHandler"
  }
}
```
