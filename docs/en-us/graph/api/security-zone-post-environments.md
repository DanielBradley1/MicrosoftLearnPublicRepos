<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-zone-post-environments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create environment

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create an [environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) object to attach it to a [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta). You can create up to 1,000 environments per zone.

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
POST /security/zones/{zoneId}/environments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) object.

You can specify the following properties when you create an **environment**.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Environment identifier. Required. |
| kind | microsoft.graph.security.environmentKind | Environment type. The possible values are: `azureSubscription`, `awsOrganization`, `awsAccount`, `gcpOrganization`, `gcpProject`, `dockersHubOrganization`, `devOpsConnection`, `azureDevOpsOrganization`, `gitHubOrganization`, `gitLabGroup`, `jFrogArtifactory`, `unknownFutureValue`. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/security/zones/f6e190cba2f64bcba703694aedb81712/environments
Content-Type: application/json

{
  "kind": "azureSubscription",
  "id": "/subscriptions/d34fd44c-ebfa-4a9c-bceb-9eeafe72ac15"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security;

var requestBody = new EnvironmentObject
{
	Kind = EnvironmentKind.AzureSubscription,
	Id = "/subscriptions/d34fd44c-ebfa-4a9c-bceb-9eeafe72ac15",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Zones["{zone-id}"].Environments.PostAsync(requestBody);
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

requestBody := graphmodelssecurity.NewEnvironment()
kind := graphmodels.AZURESUBSCRIPTION_ENVIRONMENTKIND 
requestBody.SetKind(&kind) 
id := "/subscriptions/d34fd44c-ebfa-4a9c-bceb-9eeafe72ac15"
requestBody.SetId(&id) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
environments, err := graphClient.Security().Zones().ByZoneId("zone-id").Environments().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.Environment environment = new com.microsoft.graph.beta.models.security.Environment();
environment.setKind(com.microsoft.graph.beta.models.security.EnvironmentKind.AzureSubscription);
environment.setId("/subscriptions/d34fd44c-ebfa-4a9c-bceb-9eeafe72ac15");
com.microsoft.graph.models.security.Environment result = graphClient.security().zones().byZoneId("{zone-id}").environments().post(environment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const environment = {
  kind: 'azureSubscription',
  id: '/subscriptions/d34fd44c-ebfa-4a9c-bceb-9eeafe72ac15'
};

await client.api('/security/zones/f6e190cba2f64bcba703694aedb81712/environments')
	.version('beta')
	.post(environment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\Environment;
use Microsoft\Graph\Beta\Generated\Models\Security\EnvironmentKind;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Environment();
$requestBody->setKind(new EnvironmentKind('azureSubscription'));
$requestBody->setId('/subscriptions/d34fd44c-ebfa-4a9c-bceb-9eeafe72ac15');

$result = $graphServiceClient->security()->zones()->byZoneId('zone-id')->environments()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	kind = "azureSubscription"
	id = "/subscriptions/d34fd44c-ebfa-4a9c-bceb-9eeafe72ac15"
}

New-MgBetaSecurityZoneEnvironment -ZoneId $zoneId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.environment import Environment
from msgraph_beta.generated.models.environment_kind import EnvironmentKind
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Environment(
	kind = EnvironmentKind.AzureSubscription,
	id = "/subscriptions/d34fd44c-ebfa-4a9c-bceb-9eeafe72ac15",
)

result = await graph_client.security.zones.by_zone_id('zone-id').environments.post(request_body)
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
  "@odata.context": "https://graph.microsoft.com/beta/security/$metadata#environments/$entity",
  "@odata.type": "#microsoft.graph.security.environment",
  "kind": "azureSubscription",
  "id": "/subscriptions/d34fd44c-ebfa-4a9c-bceb-9eeafe72ac15"
}
```
