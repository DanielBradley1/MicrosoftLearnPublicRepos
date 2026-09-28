<!-- Source: https://learn.microsoft.com/en-us/graph/api/application-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# Update application

Namespace: microsoft.graph

Update the properties of an [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) object. This API can also update an [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) object when the **@odata.type** property is set to `#microsoft.graph.agentIdentityBlueprint`.

Important

Using PATCH to set [**passwordCredential**](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredential?view=graph-rest-1.0) is not supported. Use the [addPassword](https://learn.microsoft.com/en-us/graph/api/application-addpassword?view=graph-rest-1.0) and [removePassword](https://learn.microsoft.com/en-us/graph/api/application-removepassword?view=graph-rest-1.0) methods to update the password or secret for an application.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Application.ReadWrite.All | Not available. |
| Application | Application.ReadWrite.OwnedBy | Application.ReadWrite.All |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- A non-admin member or guest who has default user permissions, unless [the tenant admin restricted access](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#restrict-member-users-default-permissions).
- Application Developer. This role can create apps even when the admin restricted access to members and guests. The principal with this role is assigned ownership of the app they create.
- Directory Writers. This role can update extension properties.
- Hybrid Identity Administrator. This role can update only basic properties.
- Security Administrator
- Cloud Application Administrator
- Application Administrator

In delegated scenarios using work or school accounts, the following privileges are supported for managing agent identity blueprints:

- The signed-in user is the owner, or
- The signed-in user is assigned the *Agent ID Administrator* role.

## HTTP request

You can address the application using either its **id** or **appId**. **id** and **appId** are referred to as the **Object ID** and **Application \(Client\) ID**, respectively, in app registrations in the Microsoft Entra admin center. Replace `{applicationObjectId}` with the **id** for the application object.

```http
PATCH /applications/{applicationObjectId}
PATCH /applications(appId='{appId}')
```

To update the logo, use the PUT method as follows.

```http
PUT /applications/{applicationObjectId}/logo
PUT /applications(appId='{appId}')/logo
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| api | [apiApplication](https://learn.microsoft.com/en-us/graph/api/resources/apiapplication?view=graph-rest-1.0) | Specifies settings for an application that implements a web API. |
| appRoles | [appRole](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) collection | The collection of roles defined for the application. These roles can be assigned to users, groups, or service principals. Not nullable. |
| displayName | String | The display name for the application. |
| groupMembershipClaims | String | Configures the **groups** claim issued in a user or OAuth 2.0 access token that the application expects. To set this attribute, use one of the following valid string values:<br><br>- `None`<br>- `SecurityGroup`: For security groups and Microsoft Entra roles<br>- `All`: This will get all of the security groups, distribution groups, and Microsoft Entra directory roles that the signed-in user is a member of |
| identifierUris | String collection | The URIs that identify the application within its Microsoft Entra tenant, or within a verified custom domain if the application is multitenant. For more information, see [Application Objects and Service Principal Objects](https://learn.microsoft.com/en-us/azure/active-directory/develop/app-objects-and-service-principals). Not nullable. |
| info | [informationalUrl](https://learn.microsoft.com/en-us/graph/api/resources/informationalurl?view=graph-rest-1.0) | Basic profile information of the application such as app's marketing, support, terms of service, and privacy statement URLs. The terms of service and privacy statement are surfaced to users through the user consent experience. For more information, see [Add Terms of service and privacy statement for registered Microsoft Entra apps](https://learn.microsoft.com/en-us/azure/active-directory/develop/howto-add-terms-of-service-privacy-statement). |
| isFallbackPublicClient | Boolean | Specifies the fallback application type as public client, such as an installed application running on a mobile device. The default value is `false`, which means the fallback application type is confidential client such as web app. There are certain scenarios where Microsoft Entra ID cannot determine the client application type \(for example, [ROPC](https://tools.ietf.org/html/rfc6749#section-4.3) flow where it is configured without specifying a redirect URI\). In those cases, Microsoft Entra ID will interpret the application type based on the value of this property. |
| keyCredentials | [keyCredential](https://learn.microsoft.com/en-us/graph/api/resources/keycredential?view=graph-rest-1.0) collection | The collection of key credentials associated with the application. Not nullable. |
| logo | Stream | The main logo for the application. Not nullable. Use the PUT method to update the logo. |
| managerApplications | Guid collection | A collection of application IDs for Microsoft first-party applications designated as managers. This property is supported only on [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) objects and isn't updated by using this **Update application** API. To update **managerApplications**, use the dedicated **Update agentIdentityBlueprint** API. Updating **managerApplications** on non-agent-blueprint applications returns a `400 Bad Request` error. Only Microsoft first-party application IDs can be added as managers; adding a third-party application returns a `400 Bad Request` error. The maximum allowed is 10 manager applications; exceeding this limit returns a `400 Bad Request` error. |
| nativeAuthenticationApisEnabled | nativeAuthenticationApisEnabled | Specifies whether the native authentication APIs are enabled so that the application can use them to provide native authentication. The possible values are: `none`, `all`, and `unknownFutureValue`. For more information, see [Native Authentication](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-native-authentication). |
| optionalClaims | optionalClaims | Application developers can configure optional claims in their Microsoft Entra apps to specify which claims they want in tokens sent to their application by the Microsoft security token service. See [optional claims](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-optional-claims) for more information. |
| parentalControlSettings | [parentalControlSettings](https://learn.microsoft.com/en-us/graph/api/resources/parentalcontrolsettings?view=graph-rest-1.0) | Specifies parental control settings for an application. |
| publicClient | [publicClientApplication](https://learn.microsoft.com/en-us/graph/api/resources/publicclientapplication?view=graph-rest-1.0) | Specifies settings for installed clients such as desktop or mobile devices. |
| requiredResourceAccess | [requiredResourceAccess](https://learn.microsoft.com/en-us/graph/api/resources/requiredresourceaccess?view=graph-rest-1.0) collection | Specifies the resources that the application needs to access. This property also specifies the set of delegated permissions and application roles that it needs for each of those resources. This configuration of access to the required resources drives the consent experience. No more than 50 resource services \(APIs\) can be configured. Beginning mid-October 2021, the total number of required permissions must not exceed 400. Not nullable. |
| samlMetadataUrl | String | The URL where the service exposes SAML metadata for federation. This property is valid only for single-tenant applications. |
| signInAudience | String | Specifies what Microsoft accounts are supported for the current application. Supported values are:<br><br>- `AzureADMyOrg`: Users with a Microsoft work or school account in my organization's Microsoft Entra tenant \(i.e. single tenant\)<br>- `AzureADMultipleOrgs`: Users with a Microsoft work or school account in any organization's Microsoft Entra tenant \(i.e. multi-tenant\)<br>- `AzureADandPersonalMicrosoftAccount`: Users with a personal Microsoft account, or a work or school account in any organization's Microsoft Entra tenant<br><br>  <br>The value for this property has implications on other app object properties. As a result, if you change this property, you may need to change other properties first. For more information, see [Validation differences for signInAudience](https://learn.microsoft.com/en-us/azure/active-directory/develop/supported-accounts-validation?context=graph/context). |
| spa | [spaApplication](https://learn.microsoft.com/en-us/graph/api/resources/spaapplication?view=graph-rest-1.0) | Specifies settings for a single-page application, including sign out URLs and redirect URIs for authorization codes and access tokens. |
| tags | String collection | Custom strings that can be used to categorize and identify the application. Not nullable. |
| tokenEncryptionKeyId | String | Specifies the keyId of a public key from the keyCredentials collection. When configured, Microsoft Entra ID encrypts all the tokens it emits by using the key this property points to. The application code that receives the encrypted token must use the matching private key to decrypt the token before it can be used for the signed-in user. |
| uniqueName | String | The unique identifier that can be assigned to an application and used as an alternate key. Can updated only if `null` and is immutable once set. |
| web | [webApplication](https://learn.microsoft.com/en-us/graph/api/resources/webapplication?view=graph-rest-1.0) | Specifies settings for a web application. |

## Response

If successful, this method returns a `204 No Content` response code and doesn't return anything in the response body.

## Examples

### Example 1: Update the displayName for an application

#### Request

The following example shows the request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/applications/{id}
Content-type: application/json

{
  "displayName": "New display name"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Application
{
	DisplayName = "New display name",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications["{application-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewApplication()
displayName := "New display name"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
application.setDisplayName("New display name");
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
  displayName: 'New display name'
};

await client.api('/applications/{id}')
	.update(application);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Application;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$requestBody->setDisplayName('New display name');

$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	displayName = "New display name"
}

Update-MgApplication -ApplicationId $applicationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.application import Application
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	display_name = "New display name",
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Update the appRoles for an application

The following example updates the **appRoles** collection for an application. To keep any existing app roles, include them in the request. Any existing objects in the collection that aren't included in the request are replaced with the new objects. This object is synchronized with the corresponding property of the service principal in the tenant.

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
PATCH https://graph.microsoft.com/v1.0/applications/fda284b5-f0ad-4763-8289-31a273fca865
Content-type: application/json

{
    "appRoles": [
        {
            "allowedMemberTypes": [
                "User",
                "Application"
            ],
            "description": "Survey.Read",
            "displayName": "Survey.Read",
            "id": "ebb7c86c-fb47-4e3f-8191-420ff1b9de4a",
            "isEnabled": false,
            "origin": "Application",
            "value": "Survey.Read"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Application
{
	AppRoles = new List<AppRole>
	{
		new AppRole
		{
			AllowedMemberTypes = new List<string>
			{
				"User",
				"Application",
			},
			Description = "Survey.Read",
			DisplayName = "Survey.Read",
			Id = Guid.Parse("ebb7c86c-fb47-4e3f-8191-420ff1b9de4a"),
			IsEnabled = false,
			Origin = "Application",
			Value = "Survey.Read",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications["{application-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewApplication()


appRole := graphmodels.NewAppRole()
allowedMemberTypes := []string {
	"User",
	"Application",
}
appRole.SetAllowedMemberTypes(allowedMemberTypes)
description := "Survey.Read"
appRole.SetDescription(&description) 
displayName := "Survey.Read"
appRole.SetDisplayName(&displayName) 
id := uuid.MustParse("ebb7c86c-fb47-4e3f-8191-420ff1b9de4a")
appRole.SetId(&id) 
isEnabled := false
appRole.SetIsEnabled(&isEnabled) 
origin := "Application"
appRole.SetOrigin(&origin) 
value := "Survey.Read"
appRole.SetValue(&value) 

appRoles := []graphmodels.AppRoleable {
	appRole,
}
requestBody.SetAppRoles(appRoles)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
LinkedList<AppRole> appRoles = new LinkedList<AppRole>();
AppRole appRole = new AppRole();
LinkedList<String> allowedMemberTypes = new LinkedList<String>();
allowedMemberTypes.add("User");
allowedMemberTypes.add("Application");
appRole.setAllowedMemberTypes(allowedMemberTypes);
appRole.setDescription("Survey.Read");
appRole.setDisplayName("Survey.Read");
appRole.setId(UUID.fromString("ebb7c86c-fb47-4e3f-8191-420ff1b9de4a"));
appRole.setIsEnabled(false);
appRole.setOrigin("Application");
appRole.setValue("Survey.Read");
appRoles.add(appRole);
application.setAppRoles(appRoles);
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
    appRoles: [
        {
            allowedMemberTypes: [
                'User',
                'Application'
            ],
            description: 'Survey.Read',
            displayName: 'Survey.Read',
            id: 'ebb7c86c-fb47-4e3f-8191-420ff1b9de4a',
            isEnabled: false,
            origin: 'Application',
            value: 'Survey.Read'
        }
    ]
};

await client.api('/applications/fda284b5-f0ad-4763-8289-31a273fca865')
	.update(application);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Application;
use Microsoft\Graph\Generated\Models\AppRole;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$appRolesAppRole1 = new AppRole();
$appRolesAppRole1->setAllowedMemberTypes(['User', 'Application', 	]);
$appRolesAppRole1->setDescription('Survey.Read');
$appRolesAppRole1->setDisplayName('Survey.Read');
$appRolesAppRole1->setId('ebb7c86c-fb47-4e3f-8191-420ff1b9de4a');
$appRolesAppRole1->setIsEnabled(false);
$appRolesAppRole1->setOrigin('Application');
$appRolesAppRole1->setValue('Survey.Read');
$appRolesArray []= $appRolesAppRole1;
$requestBody->setAppRoles($appRolesArray);


$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	appRoles = @(
		@{
			allowedMemberTypes = @(
			"User"
		"Application"
	)
	description = "Survey.Read"
	displayName = "Survey.Read"
	id = "ebb7c86c-fb47-4e3f-8191-420ff1b9de4a"
	isEnabled = $false
	origin = "Application"
	value = "Survey.Read"
}
)
}

Update-MgApplication -ApplicationId $applicationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.application import Application
from msgraph.generated.models.app_role import AppRole
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	app_roles = [
		AppRole(
			allowed_member_types = [
				"User",
				"Application",
			],
			description = "Survey.Read",
			display_name = "Survey.Read",
			id = UUID("ebb7c86c-fb47-4e3f-8191-420ff1b9de4a"),
			is_enabled = False,
			origin = "Application",
			value = "Survey.Read",
		),
	],
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```
