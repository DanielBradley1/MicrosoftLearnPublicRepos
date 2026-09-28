<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-post-users?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# Create User

Namespace: microsoft.graph

Create a new [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). The request body contains the user to create. At a minimum, you must specify the required properties for the user. You can optionally specify any other writable properties.

Note

To create external users as part of B2B collaboration with your organization, use the [invitation API](https://learn.microsoft.com/en-us/graph/api/invitation-post?view=graph-rest-1.0). To create a customer, citizen, or business partner in Microsoft Entra External ID in external tenants, see [Example 3: Create a customer account](#example-3-create-a-customer-account-in-external-tenants).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.Create | User.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | User.Create | User.ReadWrite.All, Directory.ReadWrite.All |

## HTTP request

```http
POST /users
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create a user. If you're including an **identities** property for the user you're creating, not all the properties listed are required. For a social identity, none of the properties are required.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| accountEnabled | Boolean | true if the account is enabled; otherwise, false. |
| displayName | String | The name to display in the address book for the user. |
| onPremisesImmutableId | String | Required only when creating a new user account if you are using a federated domain for the user's **userPrincipalName** \(UPN\) property. |
| mailNickname | String | The mail alias for the user. |
| passwordProfile | [PasswordProfile](https://learn.microsoft.com/en-us/graph/api/resources/passwordprofile?view=graph-rest-1.0) | The password profile for the user. |
| userPrincipalName | String | The user principal name \(someuser@contoso.com\). It's an Internet-style login name for the user based on the Internet standard RFC 822. By convention, this should map to the user's email name. The general format is alias@domain, where domain must be present in the tenant's collection of verified domains. The verified domains for the tenant can be accessed from the **verifiedDomains** property of [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0).  <br>NOTE: This property cannot contain accent characters. Only the following characters are allowed `A - Z`, `a - z`, `0 - 9`, ` ' . - _ ! # ^ ~`. For the complete list of allowed characters, see [username policies](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-sspr-policy#userprincipalname-policies-that-apply-to-all-user-accounts). |

Because the **user** resource supports [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview), you can use the `POST` operation and add custom properties with your own data to the user instance while creating it.

Note

Federated users created via this API are forced to sign in every 12 hours by default. For information about how to change this, see [Exceptions for token lifetimes](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-configurable-token-lifetimes#exceptions).

## Response

If successful, this method returns `201 Created` response code and [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) object in the response body.

## Example

### Example 1: Create a user

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
POST https://graph.microsoft.com/v1.0/users
Content-type: application/json

{
  "accountEnabled": true,
  "displayName": "Adele Vance",
  "mailNickname": "AdeleV",
  "userPrincipalName": "AdeleV@contoso.com",
  "passwordProfile" : {
    "forceChangePasswordNextSignIn": true,
    "password": "xWwvJ]6NMw+bWH-d"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new User
{
	AccountEnabled = true,
	DisplayName = "Adele Vance",
	MailNickname = "AdeleV",
	UserPrincipalName = "AdeleV@contoso.com",
	PasswordProfile = new PasswordProfile
	{
		ForceChangePasswordNextSignIn = true,
		Password = "xWwvJ]6NMw+bWH-d",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.PostAsync(requestBody);
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

requestBody := graphmodels.NewUser()
accountEnabled := true
requestBody.SetAccountEnabled(&accountEnabled) 
displayName := "Adele Vance"
requestBody.SetDisplayName(&displayName) 
mailNickname := "AdeleV"
requestBody.SetMailNickname(&mailNickname) 
userPrincipalName := "AdeleV@contoso.com"
requestBody.SetUserPrincipalName(&userPrincipalName) 
passwordProfile := graphmodels.NewPasswordProfile()
forceChangePasswordNextSignIn := true
passwordProfile.SetForceChangePasswordNextSignIn(&forceChangePasswordNextSignIn) 
password := "xWwvJ]6NMw+bWH-d"
passwordProfile.SetPassword(&password) 
requestBody.SetPasswordProfile(passwordProfile)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
user.setAccountEnabled(true);
user.setDisplayName("Adele Vance");
user.setMailNickname("AdeleV");
user.setUserPrincipalName("AdeleV@contoso.com");
PasswordProfile passwordProfile = new PasswordProfile();
passwordProfile.setForceChangePasswordNextSignIn(true);
passwordProfile.setPassword("xWwvJ]6NMw+bWH-d");
user.setPasswordProfile(passwordProfile);
User result = graphClient.users().post(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
  accountEnabled: true,
  displayName: 'Adele Vance',
  mailNickname: 'AdeleV',
  userPrincipalName: 'AdeleV@contoso.com',
  passwordProfile: {
    forceChangePasswordNextSignIn: true,
    password: 'xWwvJ]6NMw+bWH-d'
  }
};

await client.api('/users')
	.post(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\PasswordProfile;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$requestBody->setAccountEnabled(true);
$requestBody->setDisplayName('Adele Vance');
$requestBody->setMailNickname('AdeleV');
$requestBody->setUserPrincipalName('AdeleV@contoso.com');
$passwordProfile = new PasswordProfile();
$passwordProfile->setForceChangePasswordNextSignIn(true);
$passwordProfile->setPassword('xWwvJ]6NMw+bWH-d');
$requestBody->setPasswordProfile($passwordProfile);

$result = $graphServiceClient->users()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	accountEnabled = $true
	displayName = "Adele Vance"
	mailNickname = "AdeleV"
	userPrincipalName = "AdeleV@contoso.com"
	passwordProfile = @{
		forceChangePasswordNextSignIn = $true
		password = "xWwvJ]6NMw+bWH-d"
	}
}

New-MgUser -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.password_profile import PasswordProfile
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	account_enabled = True,
	display_name = "Adele Vance",
	mail_nickname = "AdeleV",
	user_principal_name = "AdeleV@contoso.com",
	password_profile = PasswordProfile(
		force_change_password_next_sign_in = True,
		password = "xWwvJ]6NMw+bWH-d",
	),
)

result = await graph_client.users.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

In the request body, supply a JSON representation of [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) object.

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "id": "87d349ed-44d7-43e1-9a83-5f2406dee5bd",
    "businessPhones": [],
    "displayName": "Adele Vance",
    "givenName": "Adele",
    "jobTitle": "Product Marketing Manager",
    "mail": "AdeleV@contoso.com",
    "mobilePhone": "+1 425 555 0109",
    "officeLocation": "18/2111",
    "preferredLanguage": "en-US",
    "surname": "Vance",
    "userPrincipalName": "AdeleV@contoso.com"
}
```

### Example 2: Create a user with social and local account identities in Azure AD B2C

Create a new user, with a local account identity with a sign-in name, an email address as sign-in, and with a social identity. This example is typically used for migration scenarios in Azure AD B2C tenants.

Note

For local account identities, password expirations must be disabled, and force change password at next sign-in must also be disabled.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/users
Content-type: application/json

{
  "displayName": "John Smith",
  "identities": [
    {
      "signInType": "userName",
      "issuer": "contoso.com",
      "issuerAssignedId": "johnsmith"
    },
    {
      "signInType": "emailAddress",
      "issuer": "contoso.com",
      "issuerAssignedId": "jsmith@yahoo.com"
    },
    {
      "signInType": "federated",
      "issuer": "facebook.com",
      "issuerAssignedId": "5eecb0cd"
    }
  ],
  "passwordProfile" : {
    "password": "password-value",
    "forceChangePasswordNextSignIn": false
  },
  "passwordPolicies": "DisablePasswordExpiration"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new User
{
	DisplayName = "John Smith",
	Identities = new List<ObjectIdentity>
	{
		new ObjectIdentity
		{
			SignInType = "userName",
			Issuer = "contoso.com",
			IssuerAssignedId = "johnsmith",
		},
		new ObjectIdentity
		{
			SignInType = "emailAddress",
			Issuer = "contoso.com",
			IssuerAssignedId = "jsmith@yahoo.com",
		},
		new ObjectIdentity
		{
			SignInType = "federated",
			Issuer = "facebook.com",
			IssuerAssignedId = "5eecb0cd",
		},
	},
	PasswordProfile = new PasswordProfile
	{
		Password = "password-value",
		ForceChangePasswordNextSignIn = false,
	},
	PasswordPolicies = "DisablePasswordExpiration",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.PostAsync(requestBody);
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

requestBody := graphmodels.NewUser()
displayName := "John Smith"
requestBody.SetDisplayName(&displayName) 


objectIdentity := graphmodels.NewObjectIdentity()
signInType := "userName"
objectIdentity.SetSignInType(&signInType) 
issuer := "contoso.com"
objectIdentity.SetIssuer(&issuer) 
issuerAssignedId := "johnsmith"
objectIdentity.SetIssuerAssignedId(&issuerAssignedId) 
objectIdentity1 := graphmodels.NewObjectIdentity()
signInType := "emailAddress"
objectIdentity1.SetSignInType(&signInType) 
issuer := "contoso.com"
objectIdentity1.SetIssuer(&issuer) 
issuerAssignedId := "jsmith@yahoo.com"
objectIdentity1.SetIssuerAssignedId(&issuerAssignedId) 
objectIdentity2 := graphmodels.NewObjectIdentity()
signInType := "federated"
objectIdentity2.SetSignInType(&signInType) 
issuer := "facebook.com"
objectIdentity2.SetIssuer(&issuer) 
issuerAssignedId := "5eecb0cd"
objectIdentity2.SetIssuerAssignedId(&issuerAssignedId) 

identities := []graphmodels.ObjectIdentityable {
	objectIdentity,
	objectIdentity1,
	objectIdentity2,
}
requestBody.SetIdentities(identities)
passwordProfile := graphmodels.NewPasswordProfile()
password := "password-value"
passwordProfile.SetPassword(&password) 
forceChangePasswordNextSignIn := false
passwordProfile.SetForceChangePasswordNextSignIn(&forceChangePasswordNextSignIn) 
requestBody.SetPasswordProfile(passwordProfile)
passwordPolicies := "DisablePasswordExpiration"
requestBody.SetPasswordPolicies(&passwordPolicies) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
user.setDisplayName("John Smith");
LinkedList<ObjectIdentity> identities = new LinkedList<ObjectIdentity>();
ObjectIdentity objectIdentity = new ObjectIdentity();
objectIdentity.setSignInType("userName");
objectIdentity.setIssuer("contoso.com");
objectIdentity.setIssuerAssignedId("johnsmith");
identities.add(objectIdentity);
ObjectIdentity objectIdentity1 = new ObjectIdentity();
objectIdentity1.setSignInType("emailAddress");
objectIdentity1.setIssuer("contoso.com");
objectIdentity1.setIssuerAssignedId("jsmith@yahoo.com");
identities.add(objectIdentity1);
ObjectIdentity objectIdentity2 = new ObjectIdentity();
objectIdentity2.setSignInType("federated");
objectIdentity2.setIssuer("facebook.com");
objectIdentity2.setIssuerAssignedId("5eecb0cd");
identities.add(objectIdentity2);
user.setIdentities(identities);
PasswordProfile passwordProfile = new PasswordProfile();
passwordProfile.setPassword("password-value");
passwordProfile.setForceChangePasswordNextSignIn(false);
user.setPasswordProfile(passwordProfile);
user.setPasswordPolicies("DisablePasswordExpiration");
User result = graphClient.users().post(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
  displayName: 'John Smith',
  identities: [
    {
      signInType: 'userName',
      issuer: 'contoso.com',
      issuerAssignedId: 'johnsmith'
    },
    {
      signInType: 'emailAddress',
      issuer: 'contoso.com',
      issuerAssignedId: 'jsmith@yahoo.com'
    },
    {
      signInType: 'federated',
      issuer: 'facebook.com',
      issuerAssignedId: '5eecb0cd'
    }
  ],
  passwordProfile: {
    password: 'password-value',
    forceChangePasswordNextSignIn: false
  },
  passwordPolicies: 'DisablePasswordExpiration'
};

await client.api('/users')
	.post(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\ObjectIdentity;
use Microsoft\Graph\Generated\Models\PasswordProfile;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$requestBody->setDisplayName('John Smith');
$identitiesObjectIdentity1 = new ObjectIdentity();
$identitiesObjectIdentity1->setSignInType('userName');
$identitiesObjectIdentity1->setIssuer('contoso.com');
$identitiesObjectIdentity1->setIssuerAssignedId('johnsmith');
$identitiesArray []= $identitiesObjectIdentity1;
$identitiesObjectIdentity2 = new ObjectIdentity();
$identitiesObjectIdentity2->setSignInType('emailAddress');
$identitiesObjectIdentity2->setIssuer('contoso.com');
$identitiesObjectIdentity2->setIssuerAssignedId('jsmith@yahoo.com');
$identitiesArray []= $identitiesObjectIdentity2;
$identitiesObjectIdentity3 = new ObjectIdentity();
$identitiesObjectIdentity3->setSignInType('federated');
$identitiesObjectIdentity3->setIssuer('facebook.com');
$identitiesObjectIdentity3->setIssuerAssignedId('5eecb0cd');
$identitiesArray []= $identitiesObjectIdentity3;
$requestBody->setIdentities($identitiesArray);

$passwordProfile = new PasswordProfile();
$passwordProfile->setPassword('password-value');
$passwordProfile->setForceChangePasswordNextSignIn(false);
$requestBody->setPasswordProfile($passwordProfile);
$requestBody->setPasswordPolicies('DisablePasswordExpiration');

$result = $graphServiceClient->users()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	displayName = "John Smith"
	identities = @(
		@{
			signInType = "userName"
			issuer = "contoso.com"
			issuerAssignedId = "johnsmith"
		}
		@{
			signInType = "emailAddress"
			issuer = "contoso.com"
			issuerAssignedId = "jsmith@yahoo.com"
		}
		@{
			signInType = "federated"
			issuer = "facebook.com"
			issuerAssignedId = "5eecb0cd"
		}
	)
	passwordProfile = @{
		password = "password-value"
		forceChangePasswordNextSignIn = $false
	}
	passwordPolicies = "DisablePasswordExpiration"
}

New-MgUser -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.object_identity import ObjectIdentity
from msgraph.generated.models.password_profile import PasswordProfile
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	display_name = "John Smith",
	identities = [
		ObjectIdentity(
			sign_in_type = "userName",
			issuer = "contoso.com",
			issuer_assigned_id = "johnsmith",
		),
		ObjectIdentity(
			sign_in_type = "emailAddress",
			issuer = "contoso.com",
			issuer_assigned_id = "jsmith@yahoo.com",
		),
		ObjectIdentity(
			sign_in_type = "federated",
			issuer = "facebook.com",
			issuer_assigned_id = "5eecb0cd",
		),
	],
	password_profile = PasswordProfile(
		password = "password-value",
		force_change_password_next_sign_in = False,
	),
	password_policies = "DisablePasswordExpiration",
)

result = await graph_client.users.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
  "displayName": "John Smith",
  "id": "4c7be08b-361f-41a8-b1ef-1712f7a3dfb2",
  "identities": [
    {
      "signInType": "userName",
      "issuer": "contoso.com",
      "issuerAssignedId": "johnsmith"
    },
    {
      "signInType": "emailAddress",
      "issuer": "contoso.com",
      "issuerAssignedId": "jsmith@yahoo.com"
    },
    {
      "signInType": "federated",
      "issuer": "facebook.com",
      "issuerAssignedId": "5eecb0cd"
    }
  ],
  "passwordPolicies": "DisablePasswordExpiration"
}
```

### Example 3: Create a customer account in external tenants

This example shows how to create a customer account in Microsoft Entra External ID in external tenants.

Note

For local account identities, password expirations must be disabled.

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/users
Content-type: application/json

{
    "displayName": "Test User",
    "identities": [
        {
            "signInType": "emailAddress",
            "issuer": "contoso.onmicrosoft.com",
            "issuerAssignedId": "adelev@adatum.com"
        }
    ],
    "mail": "adelev@adatum.com",
    "passwordProfile": {
        "password": "passwordValue",
        "forceChangePasswordNextSignIn": true
    },
    "passwordPolicies": "DisablePasswordExpiration"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new User
{
	DisplayName = "Test User",
	Identities = new List<ObjectIdentity>
	{
		new ObjectIdentity
		{
			SignInType = "emailAddress",
			Issuer = "contoso.onmicrosoft.com",
			IssuerAssignedId = "adelev@adatum.com",
		},
	},
	Mail = "adelev@adatum.com",
	PasswordProfile = new PasswordProfile
	{
		Password = "passwordValue",
		ForceChangePasswordNextSignIn = true,
	},
	PasswordPolicies = "DisablePasswordExpiration",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.PostAsync(requestBody);
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

requestBody := graphmodels.NewUser()
displayName := "Test User"
requestBody.SetDisplayName(&displayName) 


objectIdentity := graphmodels.NewObjectIdentity()
signInType := "emailAddress"
objectIdentity.SetSignInType(&signInType) 
issuer := "contoso.onmicrosoft.com"
objectIdentity.SetIssuer(&issuer) 
issuerAssignedId := "adelev@adatum.com"
objectIdentity.SetIssuerAssignedId(&issuerAssignedId) 

identities := []graphmodels.ObjectIdentityable {
	objectIdentity,
}
requestBody.SetIdentities(identities)
mail := "adelev@adatum.com"
requestBody.SetMail(&mail) 
passwordProfile := graphmodels.NewPasswordProfile()
password := "passwordValue"
passwordProfile.SetPassword(&password) 
forceChangePasswordNextSignIn := true
passwordProfile.SetForceChangePasswordNextSignIn(&forceChangePasswordNextSignIn) 
requestBody.SetPasswordProfile(passwordProfile)
passwordPolicies := "DisablePasswordExpiration"
requestBody.SetPasswordPolicies(&passwordPolicies) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
user.setDisplayName("Test User");
LinkedList<ObjectIdentity> identities = new LinkedList<ObjectIdentity>();
ObjectIdentity objectIdentity = new ObjectIdentity();
objectIdentity.setSignInType("emailAddress");
objectIdentity.setIssuer("contoso.onmicrosoft.com");
objectIdentity.setIssuerAssignedId("adelev@adatum.com");
identities.add(objectIdentity);
user.setIdentities(identities);
user.setMail("adelev@adatum.com");
PasswordProfile passwordProfile = new PasswordProfile();
passwordProfile.setPassword("passwordValue");
passwordProfile.setForceChangePasswordNextSignIn(true);
user.setPasswordProfile(passwordProfile);
user.setPasswordPolicies("DisablePasswordExpiration");
User result = graphClient.users().post(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    displayName: 'Test User',
    identities: [
        {
            signInType: 'emailAddress',
            issuer: 'contoso.onmicrosoft.com',
            issuerAssignedId: 'adelev@adatum.com'
        }
    ],
    mail: 'adelev@adatum.com',
    passwordProfile: {
        password: 'passwordValue',
        forceChangePasswordNextSignIn: true
    },
    passwordPolicies: 'DisablePasswordExpiration'
};

await client.api('/users')
	.post(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\ObjectIdentity;
use Microsoft\Graph\Generated\Models\PasswordProfile;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$requestBody->setDisplayName('Test User');
$identitiesObjectIdentity1 = new ObjectIdentity();
$identitiesObjectIdentity1->setSignInType('emailAddress');
$identitiesObjectIdentity1->setIssuer('contoso.onmicrosoft.com');
$identitiesObjectIdentity1->setIssuerAssignedId('adelev@adatum.com');
$identitiesArray []= $identitiesObjectIdentity1;
$requestBody->setIdentities($identitiesArray);

$requestBody->setMail('adelev@adatum.com');
$passwordProfile = new PasswordProfile();
$passwordProfile->setPassword('passwordValue');
$passwordProfile->setForceChangePasswordNextSignIn(true);
$requestBody->setPasswordProfile($passwordProfile);
$requestBody->setPasswordPolicies('DisablePasswordExpiration');

$result = $graphServiceClient->users()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	displayName = "Test User"
	identities = @(
		@{
			signInType = "emailAddress"
			issuer = "contoso.onmicrosoft.com"
			issuerAssignedId = "adelev@adatum.com"
		}
	)
	mail = "adelev@adatum.com"
	passwordProfile = @{
		password = "passwordValue"
		forceChangePasswordNextSignIn = $true
	}
	passwordPolicies = "DisablePasswordExpiration"
}

New-MgUser -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.object_identity import ObjectIdentity
from msgraph.generated.models.password_profile import PasswordProfile
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	display_name = "Test User",
	identities = [
		ObjectIdentity(
			sign_in_type = "emailAddress",
			issuer = "contoso.onmicrosoft.com",
			issuer_assigned_id = "adelev@adatum.com",
		),
	],
	mail = "adelev@adatum.com",
	password_profile = PasswordProfile(
		password = "passwordValue",
		force_change_password_next_sign_in = True,
	),
	password_policies = "DisablePasswordExpiration",
)

result = await graph_client.users.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "id": "daabd280-3978-4d29-acce-d677b9cf2e4d",
    "businessPhones": [],
    "displayName": "Test User",
    "givenName": null,
    "jobTitle": null,
    "mail": "adelev@adatum.com",
    "mobilePhone": null,
    "officeLocation": null,
    "preferredLanguage": null,
    "surname": null,
    "userPrincipalName": "daabd280-3978-4d29-acce-d677b9cf2e4d@contoso.onmicrosoft.com"
}
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
