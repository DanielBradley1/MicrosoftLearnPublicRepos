<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-sensormigration-migrate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# sensorMigration: migrate

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Migrate the specified sensors to the unified security portal. This action initiates the migration process for one or more Microsoft Defender for Identity sensors.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityIdentitiesMigration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityIdentitiesMigration.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned the *Security Administrator* [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with supported permissions created through the Microsoft Defender XDR Unified Role-Based Access Control \(RBAC\).

## HTTP request

```http
POST /security/identities/sensorMigration/migrate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| sensorIds | String collection | The collection of sensor IDs to migrate. |

## Response

If successful, this action returns a `200 OK` response code and a [migrateSensorsResult](https://learn.microsoft.com/en-us/graph/api/resources/security-migratesensorsresult?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/security/identities/sensorMigration/migrate
Content-Type: application/json

{
  "sensorIds": [
    "fdce0c43-15e8-e322-7656-aff297505af5",
    "a1b2c3d4-e5f6-7890-abcd-ef1234567890"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Security.Identities.SensorMigration.MicrosoftGraphSecurityMigrate;

var requestBody = new MigratePostRequestBody
{
	SensorIds = new List<string>
	{
		"fdce0c43-15e8-e322-7656-aff297505af5",
		"a1b2c3d4-e5f6-7890-abcd-ef1234567890",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Identities.SensorMigration.MicrosoftGraphSecurityMigrate.PostAsync(requestBody);
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
	  graphsecurity "github.com/microsoftgraph/msgraph-beta-sdk-go/security"
	  //other-imports
)

requestBody := graphsecurity.NewMigratePostRequestBody()
sensorIds := []string {
	"fdce0c43-15e8-e322-7656-aff297505af5",
	"a1b2c3d4-e5f6-7890-abcd-ef1234567890",
}
requestBody.SetSensorIds(sensorIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphSecurityMigrate, err := graphClient.Security().Identities().SensorMigration().MicrosoftGraphSecurityMigrate().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.security.identities.sensormigration.microsoftgraphsecuritymigrate.MigratePostRequestBody migratePostRequestBody = new com.microsoft.graph.beta.security.identities.sensormigration.microsoftgraphsecuritymigrate.MigratePostRequestBody();
LinkedList<String> sensorIds = new LinkedList<String>();
sensorIds.add("fdce0c43-15e8-e322-7656-aff297505af5");
sensorIds.add("a1b2c3d4-e5f6-7890-abcd-ef1234567890");
migratePostRequestBody.setSensorIds(sensorIds);
var result = graphClient.security().identities().sensorMigration().microsoftGraphSecurityMigrate().post(migratePostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const migrateSensorsResult = {
  sensorIds: [
    'fdce0c43-15e8-e322-7656-aff297505af5',
    'a1b2c3d4-e5f6-7890-abcd-ef1234567890'
  ]
};

await client.api('/security/identities/sensorMigration/migrate')
	.version('beta')
	.post(migrateSensorsResult);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Security\Identities\SensorMigration\MicrosoftGraphSecurityMigrate\MigratePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MigratePostRequestBody();
$requestBody->setSensorIds(['fdce0c43-15e8-e322-7656-aff297505af5', 'a1b2c3d4-e5f6-7890-abcd-ef1234567890', 	]);

$result = $graphServiceClient->security()->identities()->sensorMigration()->microsoftGraphSecurityMigrate()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	sensorIds = @(
	"fdce0c43-15e8-e322-7656-aff297505af5"
"a1b2c3d4-e5f6-7890-abcd-ef1234567890"
)
}

Move-MgBetaSecurityIdentitySensorMigration -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.security.identities.sensormigration.microsoft_graph_security_migrate.migrate_post_request_body import MigratePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MigratePostRequestBody(
	sensor_ids = [
		"fdce0c43-15e8-e322-7656-aff297505af5",
		"a1b2c3d4-e5f6-7890-abcd-ef1234567890",
	],
)

result = await graph_client.security.identities.sensor_migration.microsoft_graph_security_migrate.post(request_body)
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
  "@odata.type": "#microsoft.graph.security.migrateSensorsResult",
  "successfulMigrationSensorIds": [
    "fdce0c43-15e8-e322-7656-aff297505af5"
  ],
  "failedMigrationSensorIds": [
    "a1b2c3d4-e5f6-7890-abcd-ef1234567890"
  ]
}
```
