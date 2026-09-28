<!-- Source: https://learn.microsoft.com/en-us/graph/authenticationmethods-get-started -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Manage users' authentication methods using Microsoft Graph

[Authentication methods](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-methods) are the ways that users authenticate in Microsoft Entra ID. The following authentication methods are available in Microsoft Entra ID today and are manageable through Microsoft Graph:

- Windows Hello for Business
- Microsoft Authenticator
- FIDO2 security key
- Certificate-based authentication
- OATH hardware tokens \(preview\)
- OATH software tokens
- Temporary Access Pass \(TAP\)
- SMS
- Voice
- Password

Authentication methods are used in primary, second-factor, and step-up authentication, and also in the self-service password reset \(SSPR\) process.

## What can you do with the authentication methods APIs?

You can use the authentication method APIs to integrate to your apps for managing a user's authentication methods. For example, you can:

- Add a phone number for a user, who can then use that number for SMS and voice call authentication if they're enabled to use it by policy
- Update or delete the phone number assigned to a user
- Enable or disable the number for SMS sign-in
- Reset a user's password

Important

We don't recommend using the authentication methods APIs for scenarios where you need to iterate over your entire user population for auditing or security check purposes. For these types of scenarios, we recommend using the [authentication method registration and usage reporting APIs](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-usage-insights-overview) \(some APIs are available on the `beta` endpoint only\).

## Use policies to manage authentication methods in your tenant

You can choose what authentication methods are allowed for users in your tenant by configuring **authentication method policies**. For each policy, you configure whether the authentication method is enabled, its settings, and can explicitly define the groups of users that are allowed or not allowed to use the method.

## Sample scenario

In this article, you learn how to:

- Authenticate to Microsoft Entra ID with the right roles and permissions
- Check the user's authentication methods
- Add new phone numbers for the user
- Remove a phone number from the user
- Reset the user's password

## Step 1: Authenticate to Microsoft Entra ID with the right roles and permissions

Sign in to an API client such as [Graph Explorer](https://aka.ms/ge) with an account that has at least the *Privileged Authentication Administrator* or *Authentication Administrator* [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). You can use a test tenant with sample data to try out the APIs.

Next, grant the app the *UserAuthenticationMethod.ReadWrite.All* permission. You need this permission to perform both the read and write operations in this scenario.

You can now start using the APIs. In this scenario, you use the APIs to manage Cameron White's authentication methods.

## Step 2: Check the user's authentication methods

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users/CameronW@Contoso.com/authentication/methods
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Authentication.Methods.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
methods, err := graphClient.Users().ByUserId("user-id").Authentication().Methods().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationMethodCollectionResponse result = graphClient.users().byUserId("{user-id}").authentication().methods().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let methods = await client.api('/users/CameronW@Contoso.com/authentication/methods')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->authentication()->methods()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgUserAuthenticationMethod -UserId $userId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').authentication.methods.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

From this response, Cameron has only the password authentication method enabled. `28c10230-6103-485e-b985-444c60001490` is the globally unique ID of the password authentication method across Microsoft Entra ID.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('CameronW%40contoso.com')/authentication/methods",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET users('<key>')/authentication/methods?$select=id",
    "value": [
        {
            "@odata.type": "#microsoft.graph.passwordAuthenticationMethod",
            "id": "28c10230-6103-485e-b985-444c60001490",
            "password": null,
            "createdDateTime": "2023-09-18T10:38:07Z"
        }
    ]
}
```

## Step 3: Add new phone numbers for the user

In this step, you add a new *mobile* phone number for Cameron to use.

### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/users/CameronW@Contoso.com/authentication/phoneMethods
Content-Type: application/json

{
    "phoneNumber": "+1 2065555555",
    "phoneType": "mobile"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PhoneAuthenticationMethod
{
	PhoneNumber = "+1 2065555555",
	PhoneType = AuthenticationPhoneType.Mobile,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Authentication.PhoneMethods.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewPhoneAuthenticationMethod()
phoneNumber := "+1 2065555555"
requestBody.SetPhoneNumber(&phoneNumber) 
phoneType := graphmodels.MOBILE_AUTHENTICATIONPHONETYPE 
requestBody.SetPhoneType(&phoneType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
phoneMethods, err := graphClient.Users().ByUserId("user-id").Authentication().PhoneMethods().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PhoneAuthenticationMethod phoneAuthenticationMethod = new PhoneAuthenticationMethod();
phoneAuthenticationMethod.setPhoneNumber("+1 2065555555");
phoneAuthenticationMethod.setPhoneType(AuthenticationPhoneType.Mobile);
PhoneAuthenticationMethod result = graphClient.users().byUserId("{user-id}").authentication().phoneMethods().post(phoneAuthenticationMethod);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const phoneAuthenticationMethod = {
    phoneNumber: '+1 2065555555',
    phoneType: 'mobile'
};

await client.api('/users/CameronW@Contoso.com/authentication/phoneMethods')
	.post(phoneAuthenticationMethod);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\PhoneAuthenticationMethod;
use Microsoft\Graph\Generated\Models\AuthenticationPhoneType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PhoneAuthenticationMethod();
$requestBody->setPhoneNumber('+1 2065555555');
$requestBody->setPhoneType(new AuthenticationPhoneType('mobile'));

$result = $graphServiceClient->users()->byUserId('user-id')->authentication()->phoneMethods()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	phoneNumber = "+1 2065555555"
	phoneType = "mobile"
}

New-MgUserAuthenticationPhoneMethod -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.phone_authentication_method import PhoneAuthenticationMethod
from msgraph.generated.models.authentication_phone_type import AuthenticationPhoneType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PhoneAuthenticationMethod(
	phone_number = "+1 2065555555",
	phone_type = AuthenticationPhoneType.Mobile,
)

result = await graph_client.users.by_user_id('user-id').authentication.phone_methods.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('CameronW%40contoso.com')/authentication/phoneMethods/$entity",
    "id": "3179e48a-750b-4051-897c-87b9720928f7",
    "phoneNumber": "+1 2065555555",
    "phoneType": "mobile",
    "smsSignInState": "notAllowedByPolicy"
}
```

Run the same request, adding an *office* phoneType.

## Step 4: Verify the user's authentication methods

### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users/CameronW@Contoso.com/authentication/methods
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Authentication.Methods.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
methods, err := graphClient.Users().ByUserId("user-id").Authentication().Methods().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationMethodCollectionResponse result = graphClient.users().byUserId("{user-id}").authentication().methods().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let methods = await client.api('/users/CameronW@Contoso.com/authentication/methods')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->authentication()->methods()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgUserAuthenticationMethod -UserId $userId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').authentication.methods.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('CameronW%40contoso.com')/authentication/methods",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET users('<key>')/authentication/methods?$select=id",
    "value": [
        {
            "@odata.type": "#microsoft.graph.phoneAuthenticationMethod",
            "id": "e37fc753-ff3b-4958-9484-eaa9425c82bc",
            "phoneNumber": "+1 4255550199",
            "phoneType": "office",
            "smsSignInState": "notSupported"
        },
        {
            "@odata.type": "#microsoft.graph.phoneAuthenticationMethod",
            "id": "3179e48a-750b-4051-897c-87b9720928f7",
            "phoneNumber": "+1 2065555555",
            "phoneType": "mobile",
            "smsSignInState": "notAllowedByPolicy"
        },
        {
            "@odata.type": "#microsoft.graph.passwordAuthenticationMethod",
            "id": "28c10230-6103-485e-b985-444c60001490",
            "password": null,
            "createdDateTime": "2023-09-18T10:38:07Z"
        }
    ]
}
```

Confirm that you can see both numbers as expected. The IDs of the different phone number types are globally the same across Microsoft Entra ID as follows:

- `b6332ec1-7057-4abe-9331-3d72feddfe41` for *alternateMobile* phone type
- `e37fc753-ff3b-4958-9484-eaa9425c82bc` for *office* phone type
- `3179e48a-750b-4051-897c-87b9720928f7` for *mobile* phone type

## Step 5: Remove a phone number from the user

Cameron is now working from home so you need to remove the *office* number from his account.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
DELETE https://graph.microsoft.com/v1.0/users/CameronW@Contoso.com/authentication/phoneMethods/e37fc753-ff3b-4958-9484-eaa9425c82bc
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].Authentication.PhoneMethods["{phoneAuthenticationMethod-id}"].DeleteAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").Authentication().PhoneMethods().ByPhoneAuthenticationMethodId("phoneAuthenticationMethod-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.users().byUserId("{user-id}").authentication().phoneMethods().byPhoneAuthenticationMethodId("{phoneAuthenticationMethod-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/users/CameronW@Contoso.com/authentication/phoneMethods/e37fc753-ff3b-4958-9484-eaa9425c82bc')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->users()->byUserId('user-id')->authentication()->phoneMethods()->byPhoneAuthenticationMethodId('phoneAuthenticationMethod-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Remove-MgUserAuthenticationPhoneMethod -UserId $userId -PhoneAuthenticationMethodId $phoneAuthenticationMethodId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.users.by_user_id('user-id').authentication.phone_methods.by_phone_authentication_method_id('phoneAuthenticationMethod-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The request returns a `204 No Content` response code. To verify that the *office* phone method was removed from Cameron's account, rerun the request in Step 4. Cameron should now have only the mobile phone and password authentication methods.

## Step 6: Reset the user's password

Cameron has forgotten their password and you need to reset it for them. You can reset a user's password and specify a temporary password, or you can let Microsoft Entra ID generate a temporary password.

In both methods, the response includes a *Location* header with a URL you can use to check the status of the operation via a GET operation. The reset operation doesn't complete immediately as Microsoft Entra ID needs to sync the password, including down to Active Directory in the tenant's on-premises infrastructure \(for on-premises users\). The URL is valid for 24 hours.

### Option 1: Reset the user's password and supply a temporary new password

#### Request

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/users/CameronW@Contoso.com/authentication/passwordMethods/28c10230-6103-485e-b985-444c60001490/resetPassword
Content-Type: application/json

{
    "newPassword": "29sdjfw#fajsdA_a_3an3223"
}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const passwordResetResponse = {
    newPassword: '29sdjfw#fajsdA_a_3an3223'
};

await client.api('/users/CameronW@Contoso.com/authentication/passwordMethods/28c10230-6103-485e-b985-444c60001490/resetPassword')
	.post(passwordResetResponse);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 202 Accepted

Location: https://graph.microsoft.com/v1.0/users/a87cc624-b550-4559-b934-3bc0325a4808/authentication/operations/cc8e9b0e-7495-47f2-ad4a-3daa966543c6?aadgdc=DUB02P&aadgsu=ssprprod-a
```

### Option 2: Reset the user's password and let Microsoft Entra ID generate a temporary new password

In this request, you don't provide a new password and instead let Microsoft Entra ID generate a password and return it in the response.

```http
POST https://graph.microsoft.com/v1.0/users/CameronW@Contoso.com/authentication/passwordMethods/28c10230-6103-485e-b985-444c60001490/resetPassword
```

#### Response

```http
HTTP/1.1 202 Accepted

Location: https://graph.microsoft.com/v1.0/users/a87cc624-b550-4559-b934-3bc0325a4808/authentication/operations/ba0c9a11-5163-4353-89ba-81501617ede0?aadgdc=AM4P&aadgsu=ssprprod-a
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.passwordResetResponse",
    "newPassword": "Hopu0277"
}
```

### Check the status of the password reset operation

#### Request

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users/a87cc624-b550-4559-b934-3bc0325a4808/authentication/operations/ba0c9a11-5163-4353-89ba-81501617ede0?aadgdc=AM4P&aadgsu=ssprprod-a
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Authentication.Operations["{longRunningOperation-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Aadgdc = "AM4P";
	requestConfiguration.QueryParameters.Aadgsu = "ssprprod-a";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestAadgdc := "AM4P"
requestAadgsu := "ssprprod-a"

requestParameters := &graphusers.ItemAuthenticationOperationsItemRequestBuilderGetQueryParameters{
	Aadgdc: &requestAadgdc,
	Aadgsu: &requestAadgsu,
}
configuration := &graphusers.ItemAuthenticationOperationsItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
operations, err := graphClient.Users().ByUserId("user-id").Authentication().Operations().ByLongRunningOperationId("longRunningOperation-id").Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LongRunningOperation result = graphClient.users().byUserId("{user-id}").authentication().operations().byLongRunningOperationId("{longRunningOperation-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.aadgdc = "AM4P";
	requestConfiguration.queryParameters.aadgsu = "ssprprod-a";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let longRunningOperation = await client.api('/users/a87cc624-b550-4559-b934-3bc0325a4808/authentication/operations/ba0c9a11-5163-4353-89ba-81501617ede0?aadgdc=AM4P&aadgsu=ssprprod-a')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Authentication\Operations\Item\LongRunningOperationItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new LongRunningOperationItemRequestBuilderGetRequestConfiguration();
$queryParameters = LongRunningOperationItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->aadgdc = "AM4P";
$queryParameters->aadgsu = "ssprprod-a";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->byUserId('user-id')->authentication()->operations()->byLongRunningOperationId('longRunningOperation-id')->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgUserAuthenticationOperation -UserId $userId -LongRunningOperationId $longRunningOperationId -Aadgdc "AM4P" -Aadgsu "ssprprod-a" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.authentication.operations.item.long_running_operation_item_request_builder import LongRunningOperationItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = LongRunningOperationItemRequestBuilder.LongRunningOperationItemRequestBuilderGetQueryParameters(
		aadgdc = "AM4P",
		aadgsu = "ssprprod-a",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.by_user_id('user-id').authentication.operations.by_long_running_operation_id('longRunningOperation-id').get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 202 Accepted

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('a87cc624-b550-4559-b934-3bc0325a4808')/authentication/operations/$entity",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET users('<guid>')/authentication/operations('<guid>')?$select=createdDateTime,lastActionDateTime",
    "id": "ba0c9a11-5163-4353-89ba-81501617ede0",
    "createdDateTime": "2024-01-18T16:37:10Z",
    "lastActionDateTime": "2024-01-18T16:37:10Z",
    "status": "succeeded",
    "statusDetail": "ResetSuccess",
    "resourceLocation": "https://graph.microsoft.com/v1.0/users/a87cc624-b550-4559-b934-3bc0325a4808/authentication/methods/28c10230-6103-485e-b985-444c60001490"
}
```

## API reference

Looking for the API reference for authentication methods?

- See [Microsoft Entra authentication methods API overview](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-overview)
- See the [Microsoft Entra authentication methods policies API reference](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-overview)
