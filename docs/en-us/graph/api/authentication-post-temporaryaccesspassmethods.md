<!-- Source: https://learn.microsoft.com/en-us/graph/api/authentication-post-temporaryaccesspassmethods?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-02 -->

# Create temporaryAccessPassMethod

Namespace: microsoft.graph

Create a new [temporaryAccessPassAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0) object on a user. A user can only have one Temporary Access Pass that's usable within its specified lifetime. If the user requires a new Temporary Access Pass while the current Temporary Access Pass is valid, the admin can create a new Temporary Access Pass for the user, the previous Temporary Access Pass will be deleted, and a new Temporary Access Pass will be created.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthMethod-TAP.Read | UserAuthenticationMethod.ReadWrite.All, UserAuthenticationMethod.Read, UserAuthenticationMethod.Read.All, UserAuthenticationMethod.ReadWrite, UserAuthMethod-TAP.Read.All, UserAuthMethod-TAP.ReadWrite, UserAuthMethod-TAP.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserAuthMethod-TAP.Read.All | UserAuthenticationMethod.ReadWrite.All, UserAuthenticationMethod.Read.All, UserAuthMethod-TAP.ReadWrite.All |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Authentication Administrator
- Privileged Authentication Administrator

When users manage their own authentication methods, the system prompts them to complete multi-factor authentication \(MFA\) if they last authenticated more than 10 minutes ago in the current session.

## HTTP request

```http
POST /users/{id | userPrincipalName}/authentication/temporaryAccessPassMethods
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [temporaryAccessPassAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0) object.

The following table describes optional properties that can be used when creating the [temporaryAccessPassAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| isUsableOnce | Boolean | Optional. Determines if the pass is limited to a one-time use. If `true`, the pass can be used once; if `false`, the pass can be used multiple times within its **lifetimeInMinutes** setting. A multi-use Temporary Access Pass \(`isUsableOnce = false`\), can only be created and used for sign-in if it is allowed by the [Temporary Access Pass authentication method policy](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethodconfiguration?view=graph-rest-1.0). |
| lifetimeInMinutes | Int32 | Optional. The lifetime of the temporaryAccessPass in minutes starting at creation time or at startDateTime, if set. Must be between 10 and 43200 \(equivalent to 30 days\). If not specified, the **defaultLifetimeInMinutes** setting in the [Temporary Access Pass authentication method policy](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethodconfiguration?view=graph-rest-1.0) is applied. |
| startDateTime | DateTimeOffset | Optional. The date and time when the temporaryAccessPass becomes available to use. If not specified, the Temporary Access Pass is available to use immediately after it's created. |

## Response

If successful, this method returns a `201 Created` response code and a [temporaryAccessPassAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/users/071cc716-8147-4397-a5ba-b2105951cc0b/authentication/temporaryAccessPassMethods
Content-Type: application/json

{
    "startDateTime": "2022-06-05T00:00:00.000Z",
    "lifetimeInMinutes": 60,
    "isUsableOnce": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new TemporaryAccessPassAuthenticationMethod
{
	StartDateTime = DateTimeOffset.Parse("2022-06-05T00:00:00.000Z"),
	LifetimeInMinutes = 60,
	IsUsableOnce = false,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Authentication.TemporaryAccessPassMethods.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewTemporaryAccessPassAuthenticationMethod()
startDateTime , err := time.Parse(time.RFC3339, "2022-06-05T00:00:00.000Z")
requestBody.SetStartDateTime(&startDateTime) 
lifetimeInMinutes := int32(60)
requestBody.SetLifetimeInMinutes(&lifetimeInMinutes) 
isUsableOnce := false
requestBody.SetIsUsableOnce(&isUsableOnce) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
temporaryAccessPassMethods, err := graphClient.Users().ByUserId("user-id").Authentication().TemporaryAccessPassMethods().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TemporaryAccessPassAuthenticationMethod temporaryAccessPassAuthenticationMethod = new TemporaryAccessPassAuthenticationMethod();
OffsetDateTime startDateTime = OffsetDateTime.parse("2022-06-05T00:00:00.000Z");
temporaryAccessPassAuthenticationMethod.setStartDateTime(startDateTime);
temporaryAccessPassAuthenticationMethod.setLifetimeInMinutes(60);
temporaryAccessPassAuthenticationMethod.setIsUsableOnce(false);
TemporaryAccessPassAuthenticationMethod result = graphClient.users().byUserId("{user-id}").authentication().temporaryAccessPassMethods().post(temporaryAccessPassAuthenticationMethod);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const temporaryAccessPassAuthenticationMethod = {
    startDateTime: '2022-06-05T00:00:00.000Z',
    lifetimeInMinutes: 60,
    isUsableOnce: false
};

await client.api('/users/071cc716-8147-4397-a5ba-b2105951cc0b/authentication/temporaryAccessPassMethods')
	.post(temporaryAccessPassAuthenticationMethod);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TemporaryAccessPassAuthenticationMethod;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TemporaryAccessPassAuthenticationMethod();
$requestBody->setStartDateTime(new \DateTime('2022-06-05T00:00:00.000Z'));
$requestBody->setLifetimeInMinutes(60);
$requestBody->setIsUsableOnce(false);

$result = $graphServiceClient->users()->byUserId('user-id')->authentication()->temporaryAccessPassMethods()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	startDateTime = [System.DateTime]::Parse("2022-06-05T00:00:00.000Z")
	lifetimeInMinutes = 60
	isUsableOnce = $false
}

New-MgUserAuthenticationTemporaryAccessPassMethod -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.temporary_access_pass_authentication_method import TemporaryAccessPassAuthenticationMethod
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TemporaryAccessPassAuthenticationMethod(
	start_date_time = "2022-06-05T00:00:00.000Z",
	lifetime_in_minutes = 60,
	is_usable_once = False,
)

result = await graph_client.users.by_user_id('user-id').authentication.temporary_access_pass_methods.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.temporaryAccessPassAuthenticationMethod",
    "id": "6f1967b7-15e8-4935-ac26-d50770ed07a7",
    "temporaryAccessPass": "+drkzqAD",
    "createdDateTime": "2022-06-02T16:21:09.765173Z",
    "startDateTime": "2022-06-05T00:00:00Z",
    "lifetimeInMinutes": 60,
    "isUsableOnce": false,
    "isUsable": false,
    "methodUsabilityReason": "NotYetValid"
}
```
