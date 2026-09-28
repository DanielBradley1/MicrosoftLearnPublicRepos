<!-- Source: https://learn.microsoft.com/en-us/graph/api/authentication-post-externalauthenticationmethods?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-13 -->

# Create externalAuthenticationMethod

Namespace: microsoft.graph

Create a new [externalAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethod?view=graph-rest-1.0) object. This API doesn't support self-service operations.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthMethod-External.ReadWrite | UserAuthMethod-External.ReadWrite.All, UserAuthenticationMethod.ReadWrite, UserAuthenticationMethod.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserAuthMethod-External.ReadWrite.All | UserAuthenticationMethod.ReadWrite.All |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Authentication Administrator
- Privileged Authentication Administrator

When users manage their own authentication methods, the system prompts them to complete multi-factor authentication \(MFA\) if they last authenticated more than 10 minutes ago in the current session.

## HTTP request

Assign an external MFA to another user. This API doesn't support self-service operations.

```http
POST /users/{usersId}/authentication/externalAuthenticationMethods
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [externalAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethod?view=graph-rest-1.0) object.

You can specify the following properties when creating an **externalAuthenticationMethod**.

| Property | Type | Description |
| :--- | :--- | :--- |
| configurationId | String | A unique identifier used to manage and integrate external auth methods within Microsoft Entra ID. Required. |
| displayName | String | Custom name given to the registered external MFA. Required. |

## Response

If successful, this method returns a `201 Created` response code and an [externalAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethod?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/users/{id}/authentication/externalAuthenticationMethods
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.externalAuthenticationMethod",
  "configurationId": "26310fee-860b-4eab-8749-ab730dcf335e",
  "displayName": "Adatum"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ExternalAuthenticationMethod
{
	OdataType = "#microsoft.graph.externalAuthenticationMethod",
	ConfigurationId = "26310fee-860b-4eab-8749-ab730dcf335e",
	DisplayName = "Adatum",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Authentication.ExternalAuthenticationMethods.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewExternalAuthenticationMethod()
configurationId := "26310fee-860b-4eab-8749-ab730dcf335e"
requestBody.SetConfigurationId(&configurationId) 
displayName := "Adatum"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
externalAuthenticationMethods, err := graphClient.Users().ByUserId("user-id").Authentication().ExternalAuthenticationMethods().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExternalAuthenticationMethod externalAuthenticationMethod = new ExternalAuthenticationMethod();
externalAuthenticationMethod.setOdataType("#microsoft.graph.externalAuthenticationMethod");
externalAuthenticationMethod.setConfigurationId("26310fee-860b-4eab-8749-ab730dcf335e");
externalAuthenticationMethod.setDisplayName("Adatum");
ExternalAuthenticationMethod result = graphClient.users().byUserId("{user-id}").authentication().externalAuthenticationMethods().post(externalAuthenticationMethod);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const externalAuthenticationMethod = {
  '@odata.type': '#microsoft.graph.externalAuthenticationMethod',
  configurationId: '26310fee-860b-4eab-8749-ab730dcf335e',
  displayName: 'Adatum'
};

await client.api('/users/{id}/authentication/externalAuthenticationMethods')
	.post(externalAuthenticationMethod);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExternalAuthenticationMethod;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalAuthenticationMethod();
$requestBody->setOdataType('#microsoft.graph.externalAuthenticationMethod');
$requestBody->setConfigurationId('26310fee-860b-4eab-8749-ab730dcf335e');
$requestBody->setDisplayName('Adatum');

$result = $graphServiceClient->users()->byUserId('user-id')->authentication()->externalAuthenticationMethods()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.externalAuthenticationMethod"
	configurationId = "26310fee-860b-4eab-8749-ab730dcf335e"
	displayName = "Adatum"
}

New-MgUserAuthenticationExternalAuthenticationMethod -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.external_authentication_method import ExternalAuthenticationMethod
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalAuthenticationMethod(
	odata_type = "#microsoft.graph.externalAuthenticationMethod",
	configuration_id = "26310fee-860b-4eab-8749-ab730dcf335e",
	display_name = "Adatum",
)

result = await graph_client.users.by_user_id('user-id').authentication.external_authentication_methods.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.externalAuthenticationMethod",
  "id": "78381c69-811f-51f6-66ec-c2c2aa0e2b46",
  "createdDateTime": "2025-04-02T16:01:39",
  "configurationId": "26310fee-860b-4eab-8749-ab730dcf335e",
  "displayName": "Adatum"
}
```
