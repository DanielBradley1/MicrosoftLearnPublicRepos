<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-convertexternaltointernalmemberuser?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-16 -->

# user: convertExternalToInternalMemberUser

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Convert an externally authenticated user into an internal user. The user is able to sign into the host tenant as an internal user and access resources as a member. For more information about this conversion, see [Convert external users to internal users](https://learn.microsoft.com/en-us/entra/identity/users/convert-external-users-internal).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User-ConvertToInternal.ReadWrite.All | User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | User-ConvertToInternal.ReadWrite.All | User.ReadWrite.All |

Important

In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with a supported role permission. *User Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /users/{usersId}/convertExternalToInternalMemberUser
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| mail | String | Optional. |
| passwordProfile | [passwordProfile](https://learn.microsoft.com/en-us/graph/api/resources/passwordprofile?view=graph-rest-beta) | Required for users whose authentication is managed in the cloud. |
| userPrincipalName | String | Required for cloud users to change the **userPrincipalName**. Not required for on-premises synced users, as their **userPrincipalName** is managed on-premises. |

## Response

If successful, this method returns a `200 OK` response code and [conversionUserDetails](https://learn.microsoft.com/en-us/graph/api/resources/conversionuserdetails?view=graph-rest-beta) response object.

## Examples

### Example 1: Convert a cloud user and require them to reset their password on next sign in

#### Request

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
POST https://graph.microsoft.com/beta/users/0b8cc234-ef87-4015-9785-cbb42000d41c/convertExternalToInternalMemberUser
Content-type: application/json

{
    "userPrincipalName": "AdeleVance@contoso.com",
    "passwordProfile": {
        "password": "Zdi087#2jhkahf",
        "forceChangePasswordNextSignIn": "true"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Users.Item.ConvertExternalToInternalMemberUser;
using Microsoft.Graph.Beta.Models;

var requestBody = new ConvertExternalToInternalMemberUserPostRequestBody
{
	UserPrincipalName = "AdeleVance@contoso.com",
	PasswordProfile = new PasswordProfile
	{
		Password = "Zdi087#2jhkahf",
		ForceChangePasswordNextSignIn = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].ConvertExternalToInternalMemberUser.PostAsync(requestBody);
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
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewConvertExternalToInternalMemberUserPostRequestBody()
userPrincipalName := "AdeleVance@contoso.com"
requestBody.SetUserPrincipalName(&userPrincipalName) 
passwordProfile := graphmodels.NewPasswordProfile()
password := "Zdi087#2jhkahf"
passwordProfile.SetPassword(&password) 
forceChangePasswordNextSignIn := true
passwordProfile.SetForceChangePasswordNextSignIn(&forceChangePasswordNextSignIn) 
requestBody.SetPasswordProfile(passwordProfile)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
convertExternalToInternalMemberUser, err := graphClient.Users().ByUserId("user-id").ConvertExternalToInternalMemberUser().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.users.item.convertexternaltointernalmemberuser.ConvertExternalToInternalMemberUserPostRequestBody convertExternalToInternalMemberUserPostRequestBody = new com.microsoft.graph.beta.users.item.convertexternaltointernalmemberuser.ConvertExternalToInternalMemberUserPostRequestBody();
convertExternalToInternalMemberUserPostRequestBody.setUserPrincipalName("AdeleVance@contoso.com");
PasswordProfile passwordProfile = new PasswordProfile();
passwordProfile.setPassword("Zdi087#2jhkahf");
passwordProfile.setForceChangePasswordNextSignIn(true);
convertExternalToInternalMemberUserPostRequestBody.setPasswordProfile(passwordProfile);
var result = graphClient.users().byUserId("{user-id}").convertExternalToInternalMemberUser().post(convertExternalToInternalMemberUserPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const conversionUserDetails = {
    userPrincipalName: 'AdeleVance@contoso.com',
    passwordProfile: {
        password: 'Zdi087#2jhkahf',
        forceChangePasswordNextSignIn: 'true'
    }
};

await client.api('/users/0b8cc234-ef87-4015-9785-cbb42000d41c/convertExternalToInternalMemberUser')
	.version('beta')
	.post(conversionUserDetails);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\ConvertExternalToInternalMemberUser\ConvertExternalToInternalMemberUserPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\PasswordProfile;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConvertExternalToInternalMemberUserPostRequestBody();
$requestBody->setUserPrincipalName('AdeleVance@contoso.com');
$passwordProfile = new PasswordProfile();
$passwordProfile->setPassword('Zdi087#2jhkahf');
$passwordProfile->setForceChangePasswordNextSignIn(true);
$requestBody->setPasswordProfile($passwordProfile);

$result = $graphServiceClient->users()->byUserId('user-id')->convertExternalToInternalMemberUser()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Users.Actions

$params = @{
	userPrincipalName = "AdeleVance@contoso.com"
	passwordProfile = @{
		password = "Zdi087#2jhkahf"
		forceChangePasswordNextSignIn = "true"
	}
}

Convert-MgBetaUserExternalToInternalMemberUser -UserId $userId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.convert_external_to_internal_member_user.convert_external_to_internal_member_user_post_request_body import ConvertExternalToInternalMemberUserPostRequestBody
from msgraph_beta.generated.models.password_profile import PasswordProfile
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConvertExternalToInternalMemberUserPostRequestBody(
	user_principal_name = "AdeleVance@contoso.com",
	password_profile = PasswordProfile(
		password = "Zdi087#2jhkahf",
		force_change_password_next_sign_in = True,
	),
)

result = await graph_client.users.by_user_id('user-id').convert_external_to_internal_member_user.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.conversionUserDetails",
    "displayName": "Adele Vance",
    "userPrincipalName": "AdeleVance@contoso.com",
    "convertedToInternalUserDateTime": "2024-02-05T20:16:37.5012924Z",
    "mail": "AdeleV@woodgrove.com"
}
```

### Example 2: Convert a cloud user, change their mail address, and require password reset on next sign in

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/users/0b8cc234-ef87-4015-9785-cbb42000d41c/convertExternalToInternalMemberUser
Content-type: application/json

{
    "userPrincipalName": "AdeleVance@contoso.com",
    "passwordProfile": {
        "password": "Zdi087#2jhkahf",
        "forceChangePasswordNextSignIn": "true"
    },
    "mail": "AdeleV@contoso.com"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Users.Item.ConvertExternalToInternalMemberUser;
using Microsoft.Graph.Beta.Models;

var requestBody = new ConvertExternalToInternalMemberUserPostRequestBody
{
	UserPrincipalName = "AdeleVance@contoso.com",
	PasswordProfile = new PasswordProfile
	{
		Password = "Zdi087#2jhkahf",
		ForceChangePasswordNextSignIn = true,
	},
	Mail = "AdeleV@contoso.com",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].ConvertExternalToInternalMemberUser.PostAsync(requestBody);
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
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewConvertExternalToInternalMemberUserPostRequestBody()
userPrincipalName := "AdeleVance@contoso.com"
requestBody.SetUserPrincipalName(&userPrincipalName) 
passwordProfile := graphmodels.NewPasswordProfile()
password := "Zdi087#2jhkahf"
passwordProfile.SetPassword(&password) 
forceChangePasswordNextSignIn := true
passwordProfile.SetForceChangePasswordNextSignIn(&forceChangePasswordNextSignIn) 
requestBody.SetPasswordProfile(passwordProfile)
mail := "AdeleV@contoso.com"
requestBody.SetMail(&mail) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
convertExternalToInternalMemberUser, err := graphClient.Users().ByUserId("user-id").ConvertExternalToInternalMemberUser().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.users.item.convertexternaltointernalmemberuser.ConvertExternalToInternalMemberUserPostRequestBody convertExternalToInternalMemberUserPostRequestBody = new com.microsoft.graph.beta.users.item.convertexternaltointernalmemberuser.ConvertExternalToInternalMemberUserPostRequestBody();
convertExternalToInternalMemberUserPostRequestBody.setUserPrincipalName("AdeleVance@contoso.com");
PasswordProfile passwordProfile = new PasswordProfile();
passwordProfile.setPassword("Zdi087#2jhkahf");
passwordProfile.setForceChangePasswordNextSignIn(true);
convertExternalToInternalMemberUserPostRequestBody.setPasswordProfile(passwordProfile);
convertExternalToInternalMemberUserPostRequestBody.setMail("AdeleV@contoso.com");
var result = graphClient.users().byUserId("{user-id}").convertExternalToInternalMemberUser().post(convertExternalToInternalMemberUserPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const conversionUserDetails = {
    userPrincipalName: 'AdeleVance@contoso.com',
    passwordProfile: {
        password: 'Zdi087#2jhkahf',
        forceChangePasswordNextSignIn: 'true'
    },
    mail: 'AdeleV@contoso.com'
};

await client.api('/users/0b8cc234-ef87-4015-9785-cbb42000d41c/convertExternalToInternalMemberUser')
	.version('beta')
	.post(conversionUserDetails);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\ConvertExternalToInternalMemberUser\ConvertExternalToInternalMemberUserPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\PasswordProfile;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConvertExternalToInternalMemberUserPostRequestBody();
$requestBody->setUserPrincipalName('AdeleVance@contoso.com');
$passwordProfile = new PasswordProfile();
$passwordProfile->setPassword('Zdi087#2jhkahf');
$passwordProfile->setForceChangePasswordNextSignIn(true);
$requestBody->setPasswordProfile($passwordProfile);
$requestBody->setMail('AdeleV@contoso.com');

$result = $graphServiceClient->users()->byUserId('user-id')->convertExternalToInternalMemberUser()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Users.Actions

$params = @{
	userPrincipalName = "AdeleVance@contoso.com"
	passwordProfile = @{
		password = "Zdi087#2jhkahf"
		forceChangePasswordNextSignIn = "true"
	}
	mail = "AdeleV@contoso.com"
}

Convert-MgBetaUserExternalToInternalMemberUser -UserId $userId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.convert_external_to_internal_member_user.convert_external_to_internal_member_user_post_request_body import ConvertExternalToInternalMemberUserPostRequestBody
from msgraph_beta.generated.models.password_profile import PasswordProfile
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConvertExternalToInternalMemberUserPostRequestBody(
	user_principal_name = "AdeleVance@contoso.com",
	password_profile = PasswordProfile(
		password = "Zdi087#2jhkahf",
		force_change_password_next_sign_in = True,
	),
	mail = "AdeleV@contoso.com",
)

result = await graph_client.users.by_user_id('user-id').convert_external_to_internal_member_user.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.conversionUserDetails",
    "displayName": "Adele Vance",
    "userPrincipalName": "AdeleVance@contoso.com",
    "convertedToInternalUserDateTime": "2024-02-05T20:16:37.5012924Z",
    "mail": "AdeleV@woodgrove.com"
}
```

### Example 3: Convert external User to internal for a user synchronized from on-premises AD

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/users/0b8cc234-ef87-4015-9785-cbb42000d41c/convertExternalToInternalMemberUser
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].ConvertExternalToInternalMemberUser.PostAsync(null);
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
convertExternalToInternalMemberUser, err := graphClient.Users().ByUserId("user-id").ConvertExternalToInternalMemberUser().Post(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.users().byUserId("{user-id}").convertExternalToInternalMemberUser().post(null);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/users/0b8cc234-ef87-4015-9785-cbb42000d41c/convertExternalToInternalMemberUser')
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


$result = $graphServiceClient->users()->byUserId('user-id')->convertExternalToInternalMemberUser()->post()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Users.Actions

Convert-MgBetaUserExternalToInternalMemberUser -UserId $userId
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').convert_external_to_internal_member_user.post(None)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.conversionUserDetails",
    "displayName": "Adele Vance",
    "userPrincipalName": "AdeleVance@contoso.com",
    "convertedToInternalUserDateTime": "2024-02-05T20:16:37.5012924Z",
    "mail": "AdeleV@woodgrove.com"
}
```

## Related content

- [Convert external users to internal users](https://learn.microsoft.com/en-us/entra/identity/users/convert-external-users-internal)
