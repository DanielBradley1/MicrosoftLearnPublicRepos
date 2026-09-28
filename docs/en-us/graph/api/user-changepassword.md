<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-changepassword?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-30 -->

# user: changePassword

Namespace: microsoft.graph

Update the signed-in [user's](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) password. Any user can update their password without belonging to any administrator role. To update another user's password in either delegated or app-only scenarios, update the **passwordProfile** property of the user instead. See [Example 3: Update the passwordProfile of a user and reset their password](https://learn.microsoft.com/en-us/graph/api/user-update?view=graph-rest-1.0#example-3-update-the-passwordprofile-of-a-user-and-reset-their-password).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User-PasswordProfile.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/changePassword
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| currentPassword | String | Your current password. |
| newPassword | String | Your new password. |

## Response

If successful, this method returns a `204 No Content` response code.

## Example

The following example shows a request to update your own password.

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
POST https://graph.microsoft.com/v1.0/me/changePassword
Content-type: application/json

{
    "currentPassword": "xWwvJ]6NMw+bWH-d",
    "newPassword": "0eM85N54wFxWwvJ]"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.ChangePassword;

var requestBody = new ChangePasswordPostRequestBody
{
	CurrentPassword = "xWwvJ]6NMw+bWH-d",
	NewPassword = "0eM85N54wFxWwvJ]",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Me.ChangePassword.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

requestBody := graphusers.NewItemChangePasswordPostRequestBody()
currentPassword := "xWwvJ]6NMw+bWH-d"
requestBody.SetCurrentPassword(&currentPassword) 
newPassword := "0eM85N54wFxWwvJ]"
requestBody.SetNewPassword(&newPassword) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Me().ChangePassword().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.changepassword.ChangePasswordPostRequestBody changePasswordPostRequestBody = new com.microsoft.graph.users.item.changepassword.ChangePasswordPostRequestBody();
changePasswordPostRequestBody.setCurrentPassword("xWwvJ]6NMw+bWH-d");
changePasswordPostRequestBody.setNewPassword("0eM85N54wFxWwvJ]");
graphClient.me().changePassword().post(changePasswordPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const changePassword = {
    currentPassword: 'xWwvJ]6NMw+bWH-d',
    newPassword: '0eM85N54wFxWwvJ]'
};

await client.api('/me/changePassword')
	.post(changePassword);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\ChangePassword\ChangePasswordPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChangePasswordPostRequestBody();
$requestBody->setCurrentPassword('xWwvJ]6NMw+bWH-d');
$requestBody->setNewPassword('0eM85N54wFxWwvJ]');

$graphServiceClient->me()->changePassword()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users.Actions

$params = @{
	currentPassword = "xWwvJ]6NMw+bWH-d"
	newPassword = "0eM85N54wFxWwvJ]"
}

# A UPN can also be used as -UserId.
Update-MgUserPassword -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.change_password.change_password_post_request_body import ChangePasswordPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChangePasswordPostRequestBody(
	current_password = "xWwvJ]6NMw+bWH-d",
	new_password = "0eM85N54wFxWwvJ]",
)

await graph_client.me.change_password.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```

## Related content

- [Update the passwordProfile of a user to reset their password](https://learn.microsoft.com/en-us/graph/api/user-update?view=graph-rest-1.0#example-3-update-the-passwordprofile-of-a-user-and-reset-their-password)
