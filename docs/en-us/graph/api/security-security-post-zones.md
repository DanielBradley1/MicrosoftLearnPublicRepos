<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-security-post-zones?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# Create zone

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) object. You can create up to 1,000 zones per tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Zone.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Zone.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Security Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /security/zones
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) object.

You can specify the following properties when you create a **zone**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description of the zone. Optional. |
| displayName | String | Human-readable name of the zone. Required. |
| environments | [microsoft.graph.security.environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) collection | Collection of environments to attach to the zone. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/security/zones
Content-Type: application/json

{
  "displayName": "Production Zone",
  "description": "Zone for production environments",
  "environments": [
    {
      "kind": "awsAccount",
      "id": "181994123251"
    },
    {
      "kind": "awsAccount",
      "id": "326438728454"
    },
    {
      "kind": "azureSubscription",
      "id": "/subscriptions/02687862-a843-4846-81f0-efe9ef244daa"
    },
    {
      "kind": "gcpProject",
      "id": "69483221284"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security;

var requestBody = new Zone
{
	DisplayName = "Production Zone",
	Description = "Zone for production environments",
	Environments = new List<EnvironmentObject>
	{
		new EnvironmentObject
		{
			Kind = EnvironmentKind.AwsAccount,
			Id = "181994123251",
		},
		new EnvironmentObject
		{
			Kind = EnvironmentKind.AwsAccount,
			Id = "326438728454",
		},
		new EnvironmentObject
		{
			Kind = EnvironmentKind.AzureSubscription,
			Id = "/subscriptions/02687862-a843-4846-81f0-efe9ef244daa",
		},
		new EnvironmentObject
		{
			Kind = EnvironmentKind.GcpProject,
			Id = "69483221284",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Zones.PostAsync(requestBody);
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
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-beta-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewZone()
displayName := "Production Zone"
requestBody.SetDisplayName(&displayName) 
description := "Zone for production environments"
requestBody.SetDescription(&description) 


environment := graphmodelssecurity.NewEnvironment()
kind := graphmodels.AWSACCOUNT_ENVIRONMENTKIND 
environment.SetKind(&kind) 
id := "181994123251"
environment.SetId(&id) 
environment1 := graphmodelssecurity.NewEnvironment()
kind := graphmodels.AWSACCOUNT_ENVIRONMENTKIND 
environment1.SetKind(&kind) 
id := "326438728454"
environment1.SetId(&id) 
environment2 := graphmodelssecurity.NewEnvironment()
kind := graphmodels.AZURESUBSCRIPTION_ENVIRONMENTKIND 
environment2.SetKind(&kind) 
id := "/subscriptions/02687862-a843-4846-81f0-efe9ef244daa"
environment2.SetId(&id) 
environment3 := graphmodelssecurity.NewEnvironment()
kind := graphmodels.GCPPROJECT_ENVIRONMENTKIND 
environment3.SetKind(&kind) 
id := "69483221284"
environment3.SetId(&id) 

environments := []graphmodelssecurity.Environmentable {
	environment,
	environment1,
	environment2,
	environment3,
}
requestBody.SetEnvironments(environments)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
zones, err := graphClient.Security().Zones().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.Zone zone = new com.microsoft.graph.beta.models.security.Zone();
zone.setDisplayName("Production Zone");
zone.setDescription("Zone for production environments");
LinkedList<com.microsoft.graph.beta.models.security.Environment> environments = new LinkedList<com.microsoft.graph.beta.models.security.Environment>();
com.microsoft.graph.beta.models.security.Environment environment = new com.microsoft.graph.beta.models.security.Environment();
environment.setKind(com.microsoft.graph.beta.models.security.EnvironmentKind.AwsAccount);
environment.setId("181994123251");
environments.add(environment);
com.microsoft.graph.beta.models.security.Environment environment1 = new com.microsoft.graph.beta.models.security.Environment();
environment1.setKind(com.microsoft.graph.beta.models.security.EnvironmentKind.AwsAccount);
environment1.setId("326438728454");
environments.add(environment1);
com.microsoft.graph.beta.models.security.Environment environment2 = new com.microsoft.graph.beta.models.security.Environment();
environment2.setKind(com.microsoft.graph.beta.models.security.EnvironmentKind.AzureSubscription);
environment2.setId("/subscriptions/02687862-a843-4846-81f0-efe9ef244daa");
environments.add(environment2);
com.microsoft.graph.beta.models.security.Environment environment3 = new com.microsoft.graph.beta.models.security.Environment();
environment3.setKind(com.microsoft.graph.beta.models.security.EnvironmentKind.GcpProject);
environment3.setId("69483221284");
environments.add(environment3);
zone.setEnvironments(environments);
com.microsoft.graph.models.security.Zone result = graphClient.security().zones().post(zone);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const zone = {
  displayName: 'Production Zone',
  description: 'Zone for production environments',
  environments: [
    {
      kind: 'awsAccount',
      id: '181994123251'
    },
    {
      kind: 'awsAccount',
      id: '326438728454'
    },
    {
      kind: 'azureSubscription',
      id: '/subscriptions/02687862-a843-4846-81f0-efe9ef244daa'
    },
    {
      kind: 'gcpProject',
      id: '69483221284'
    }
  ]
};

await client.api('/security/zones')
	.version('beta')
	.post(zone);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\Zone;
use Microsoft\Graph\Beta\Generated\Models\Security\Environment;
use Microsoft\Graph\Beta\Generated\Models\Security\EnvironmentKind;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Zone();
$requestBody->setDisplayName('Production Zone');
$requestBody->setDescription('Zone for production environments');
$environmentsEnvironment1 = new Environment();
$environmentsEnvironment1->setKind(new EnvironmentKind('awsAccount'));
$environmentsEnvironment1->setId('181994123251');
$environmentsArray []= $environmentsEnvironment1;
$environmentsEnvironment2 = new Environment();
$environmentsEnvironment2->setKind(new EnvironmentKind('awsAccount'));
$environmentsEnvironment2->setId('326438728454');
$environmentsArray []= $environmentsEnvironment2;
$environmentsEnvironment3 = new Environment();
$environmentsEnvironment3->setKind(new EnvironmentKind('azureSubscription'));
$environmentsEnvironment3->setId('/subscriptions/02687862-a843-4846-81f0-efe9ef244daa');
$environmentsArray []= $environmentsEnvironment3;
$environmentsEnvironment4 = new Environment();
$environmentsEnvironment4->setKind(new EnvironmentKind('gcpProject'));
$environmentsEnvironment4->setId('69483221284');
$environmentsArray []= $environmentsEnvironment4;
$requestBody->setEnvironments($environmentsArray);


$result = $graphServiceClient->security()->zones()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	displayName = "Production Zone"
	description = "Zone for production environments"
	environments = @(
		@{
			kind = "awsAccount"
			id = "181994123251"
		}
		@{
			kind = "awsAccount"
			id = "326438728454"
		}
		@{
			kind = "azureSubscription"
			id = "/subscriptions/02687862-a843-4846-81f0-efe9ef244daa"
		}
		@{
			kind = "gcpProject"
			id = "69483221284"
		}
	)
}

New-MgBetaSecurityZone -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.zone import Zone
from msgraph_beta.generated.models.security.environment import Environment
from msgraph_beta.generated.models.environment_kind import EnvironmentKind
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Zone(
	display_name = "Production Zone",
	description = "Zone for production environments",
	environments = [
		Environment(
			kind = EnvironmentKind.AwsAccount,
			id = "181994123251",
		),
		Environment(
			kind = EnvironmentKind.AwsAccount,
			id = "326438728454",
		),
		Environment(
			kind = EnvironmentKind.AzureSubscription,
			id = "/subscriptions/02687862-a843-4846-81f0-efe9ef244daa",
		),
		Environment(
			kind = EnvironmentKind.GcpProject,
			id = "69483221284",
		),
	],
)

result = await graph_client.security.zones.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/security/$metadata#zones/$entity",
  "@odata.type": "#microsoft.graph.security.zone",
  "id": "05cfec937c214892a14448562ef4bf4a",
  "displayName": "Production Zone",
  "description": "Zone for production environments",
  "created": {
    "by": "Yarin",
    "dateTime": "2023-10-01T12:00:00Z"
  },
  "modified": {
    "by": "Yarin",
    "dateTime": "2023-10-01T12:00:00Z"
  },
  "environments": [
    {
      "kind": "awsAccount",
      "id": "181994123251"
    },
    {
      "kind": "awsAccount",
      "id": "326438728454"
    },
    {
      "kind": "azureSubscription",
      "id": "/subscriptions/02687862-a843-4846-81f0-efe9ef244daa"
    },
    {
      "kind": "gcpProject",
      "id": "69483221284"
    }
  ],
  "aggregations": [
    {
      "kind": "azureSubscription",
      "count": 1
    },
    {
      "kind": "awsAccount",
      "count": 2
    },
    {
      "kind": "gcpProject",
      "count": 1
    }
  ]
}
```
