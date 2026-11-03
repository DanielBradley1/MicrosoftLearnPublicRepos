<!-- Source: https://learn.microsoft.com/en-us/graph/api/migrationsroot-post-crosstenantmigrationjobs?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# Create crossTenantMigrationJob

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta). A job defines the migration batch but doesn't start validation or migration. After you create the job, call [validate](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-validate?view=graph-rest-beta) to verify tenant and resource configuration, then call [migrate](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-migrate?view=graph-rest-beta) to begin the actual migration.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CrossTenantContentMigration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CrossTenantContentMigration.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Microsoft 365 Migration Administrator
- Global Administrator

## HTTP request

```http
POST /solutions/migrations/crossTenantMigrationJobs
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) object.

You can specify the following properties when creating a **crossTenantMigrationJob**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the crossTenantMigrationJob. Must be unique per tenant. Required. |
| completeAfterDateTime | DateTimeOffset | Time when the migration batch should begin processing. Required. |
| sourceTenantId | String | Tenant ID \(GUID\) of the source tenant for the migration. Required. |
| exchangeSettings | [exchangeOnlineCrossTenantMigrationSettings](https://learn.microsoft.com/en-us/graph/api/resources/exchangeonlinecrosstenantmigrationsettings?view=graph-rest-beta) | Settings for Exchange Online migrations. Optional, but required if Exchange is a specified workload. |
| workloads | String collection | Workloads to migrate on the resources. Optional. If excluded, all available workloads are included in the migration. |
| resourceType | String | Type of resources to migrate. Only `Users` is supported at this time. Required. |
| resources | String collection | Object IDs \(GUID\) of the resources to migrate. Limit of 2,000 resources per [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta). Required. |

## Response

If successful, this method returns a `201 Created` response code and a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/solutions/migrations/crossTenantMigrationJobs
Content-Type: application/json

{
  "displayName": "xtmigration_user_req_1",
  "completeAfterDateTime": "2024-12-09T22:48:03.092Z",
  "sourceTenantId": "12345678-1234-1234-1234-123456789012",
  "exchangeSettings": {
    "targetDeliveryDomain": "xtmigration.onmicrosoft.com",
    "sourceEndpoint": "sampleEndpointText"
  },
  "resources": [
    "4dd550d9-9ea2-4e71-a16b-60b1d1c4f506",
    "63f15b55-f61a-49cb-a599-2e3d233afb2c",
    "41d94bac-3a53-47d6-a89e-583830104e15"
  ],
  "resourceType": "Users",
  "workloads": [
    "Teams",
    "Exchange",
    "ODSP"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CrossTenantMigrationJob
{
	DisplayName = "xtmigration_user_req_1",
	CompleteAfterDateTime = DateTimeOffset.Parse("2024-12-09T22:48:03.092Z"),
	SourceTenantId = "12345678-1234-1234-1234-123456789012",
	ExchangeSettings = new ExchangeOnlineCrossTenantMigrationSettings
	{
		TargetDeliveryDomain = "xtmigration.onmicrosoft.com",
		SourceEndpoint = "sampleEndpointText",
	},
	Resources = new List<string>
	{
		"4dd550d9-9ea2-4e71-a16b-60b1d1c4f506",
		"63f15b55-f61a-49cb-a599-2e3d233afb2c",
		"41d94bac-3a53-47d6-a89e-583830104e15",
	},
	ResourceType = "Users",
	Workloads = new List<string>
	{
		"Teams",
		"Exchange",
		"ODSP",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.Migrations.CrossTenantMigrationJobs.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewCrossTenantMigrationJob()
displayName := "xtmigration_user_req_1"
requestBody.SetDisplayName(&displayName) 
completeAfterDateTime , err := time.Parse(time.RFC3339, "2024-12-09T22:48:03.092Z")
requestBody.SetCompleteAfterDateTime(&completeAfterDateTime) 
sourceTenantId := "12345678-1234-1234-1234-123456789012"
requestBody.SetSourceTenantId(&sourceTenantId) 
exchangeSettings := graphmodels.NewExchangeOnlineCrossTenantMigrationSettings()
targetDeliveryDomain := "xtmigration.onmicrosoft.com"
exchangeSettings.SetTargetDeliveryDomain(&targetDeliveryDomain) 
sourceEndpoint := "sampleEndpointText"
exchangeSettings.SetSourceEndpoint(&sourceEndpoint) 
requestBody.SetExchangeSettings(exchangeSettings)
resources := []string {
	"4dd550d9-9ea2-4e71-a16b-60b1d1c4f506",
	"63f15b55-f61a-49cb-a599-2e3d233afb2c",
	"41d94bac-3a53-47d6-a89e-583830104e15",
}
requestBody.SetResources(resources)
resourceType := "Users"
requestBody.SetResourceType(&resourceType) 
workloads := []string {
	"Teams",
	"Exchange",
	"ODSP",
}
requestBody.SetWorkloads(workloads)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
crossTenantMigrationJobs, err := graphClient.Solutions().Migrations().CrossTenantMigrationJobs().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CrossTenantMigrationJob crossTenantMigrationJob = new CrossTenantMigrationJob();
crossTenantMigrationJob.setDisplayName("xtmigration_user_req_1");
OffsetDateTime completeAfterDateTime = OffsetDateTime.parse("2024-12-09T22:48:03.092Z");
crossTenantMigrationJob.setCompleteAfterDateTime(completeAfterDateTime);
crossTenantMigrationJob.setSourceTenantId("12345678-1234-1234-1234-123456789012");
ExchangeOnlineCrossTenantMigrationSettings exchangeSettings = new ExchangeOnlineCrossTenantMigrationSettings();
exchangeSettings.setTargetDeliveryDomain("xtmigration.onmicrosoft.com");
exchangeSettings.setSourceEndpoint("sampleEndpointText");
crossTenantMigrationJob.setExchangeSettings(exchangeSettings);
LinkedList<String> resources = new LinkedList<String>();
resources.add("4dd550d9-9ea2-4e71-a16b-60b1d1c4f506");
resources.add("63f15b55-f61a-49cb-a599-2e3d233afb2c");
resources.add("41d94bac-3a53-47d6-a89e-583830104e15");
crossTenantMigrationJob.setResources(resources);
crossTenantMigrationJob.setResourceType("Users");
LinkedList<String> workloads = new LinkedList<String>();
workloads.add("Teams");
workloads.add("Exchange");
workloads.add("ODSP");
crossTenantMigrationJob.setWorkloads(workloads);
CrossTenantMigrationJob result = graphClient.solutions().migrations().crossTenantMigrationJobs().post(crossTenantMigrationJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const crossTenantMigrationJob = {
  displayName: 'xtmigration_user_req_1',
  completeAfterDateTime: '2024-12-09T22:48:03.092Z',
  sourceTenantId: '12345678-1234-1234-1234-123456789012',
  exchangeSettings: {
    targetDeliveryDomain: 'xtmigration.onmicrosoft.com',
    sourceEndpoint: 'sampleEndpointText'
  },
  resources: [
    '4dd550d9-9ea2-4e71-a16b-60b1d1c4f506',
    '63f15b55-f61a-49cb-a599-2e3d233afb2c',
    '41d94bac-3a53-47d6-a89e-583830104e15'
  ],
  resourceType: 'Users',
  workloads: [
    'Teams',
    'Exchange',
    'ODSP'
  ]
};

await client.api('/solutions/migrations/crossTenantMigrationJobs')
	.version('beta')
	.post(crossTenantMigrationJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CrossTenantMigrationJob;
use Microsoft\Graph\Beta\Generated\Models\ExchangeOnlineCrossTenantMigrationSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CrossTenantMigrationJob();
$requestBody->setDisplayName('xtmigration_user_req_1');
$requestBody->setCompleteAfterDateTime(new \DateTime('2024-12-09T22:48:03.092Z'));
$requestBody->setSourceTenantId('12345678-1234-1234-1234-123456789012');
$exchangeSettings = new ExchangeOnlineCrossTenantMigrationSettings();
$exchangeSettings->setTargetDeliveryDomain('xtmigration.onmicrosoft.com');
$exchangeSettings->setSourceEndpoint('sampleEndpointText');
$requestBody->setExchangeSettings($exchangeSettings);
$requestBody->setResources(['4dd550d9-9ea2-4e71-a16b-60b1d1c4f506', '63f15b55-f61a-49cb-a599-2e3d233afb2c', '41d94bac-3a53-47d6-a89e-583830104e15', 	]);
$requestBody->setResourceType('Users');
$requestBody->setWorkloads(['Teams', 'Exchange', 'ODSP', 	]);

$result = $graphServiceClient->solutions()->migrations()->crossTenantMigrationJobs()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Migrations

$params = @{
	displayName = "xtmigration_user_req_1"
	completeAfterDateTime = [System.DateTime]::Parse("2024-12-09T22:48:03.092Z")
	sourceTenantId = "12345678-1234-1234-1234-123456789012"
	exchangeSettings = @{
		targetDeliveryDomain = "xtmigration.onmicrosoft.com"
		sourceEndpoint = "sampleEndpointText"
	}
	resources = @(
	"4dd550d9-9ea2-4e71-a16b-60b1d1c4f506"
"63f15b55-f61a-49cb-a599-2e3d233afb2c"
"41d94bac-3a53-47d6-a89e-583830104e15"
)
resourceType = "Users"
workloads = @(
"Teams"
"Exchange"
"ODSP"
)
}

New-MgBetaCrossTenantMigrationJob -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.cross_tenant_migration_job import CrossTenantMigrationJob
from msgraph_beta.generated.models.exchange_online_cross_tenant_migration_settings import ExchangeOnlineCrossTenantMigrationSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CrossTenantMigrationJob(
	display_name = "xtmigration_user_req_1",
	complete_after_date_time = "2024-12-09T22:48:03.092Z",
	source_tenant_id = "12345678-1234-1234-1234-123456789012",
	exchange_settings = ExchangeOnlineCrossTenantMigrationSettings(
		target_delivery_domain = "xtmigration.onmicrosoft.com",
		source_endpoint = "sampleEndpointText",
	),
	resources = [
		"4dd550d9-9ea2-4e71-a16b-60b1d1c4f506",
		"63f15b55-f61a-49cb-a599-2e3d233afb2c",
		"41d94bac-3a53-47d6-a89e-583830104e15",
	],
	resource_type = "Users",
	workloads = [
		"Teams",
		"Exchange",
		"ODSP",
	],
)

result = await graph_client.solutions.migrations.cross_tenant_migration_jobs.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#solutions/migrations/crossTenantMigrationJobs/$entity",
  "id": "add14989-2b21-4001-81bd-a18b0bac1dea",
  "displayName": "Contoso_migration_job",
  "jobType": "validate",
  "status": "submitted",
  "message": "",
  "completeAfterDateTime": "2023-12-17T20:38:04.101Z",
  "targetTenantId": "87654321-4321-4321-4321-210987654321",
  "sourceTenantId": "12345678-1234-1234-1234-123456789012",
  "exchangeSettings": {
    "targetDeliveryDomain": "fabrikam.onmicrosoft.com",
    "sourceEndpoint": "sampleEndpointText"
  },
  "resources": [
    "4dd550d9-9ea2-4e71-a16b-60b1d1c4f506",
    "63f15b55-f61a-49cb-a599-2e3d233afb2c",
    "41d94bac-3a53-47d6-a89e-583830104e15"
  ],
  "resourceType": "Users",
  "workloads": ["Teams", "Exchange", "ODSP"],
  "createdBy": "admin@fabrikam.onmicrosoft.com",
  "createdDateTime": "2025-11-14T20:55:10.5427196Z",
  "lastUpdatedDateTime": "2025-11-14T20:55:10.5427196Z"
}
```
