<!-- Source: https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-configure-permissions -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# Configure Azure AD Graph permissions for an app registration

Azure Active Directory \(Azure AD\) Graph [is deprecated and is in its retirement path](https://techcommunity.microsoft.com/t5/microsoft-entra-blog/important-azure-ad-graph-retirement-and-powershell-module/ba-p/3848270). To migrate your apps to [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview), follow the [App migration planning checklist](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist).

Your app might still temporarily require Azure AD Graph permissions to access resources. To configure Azure AD Graph permissions for your app registration, follow one of the three methods described in this article:

1. [Use the Microsoft Entra admin center to find the APIs your organization uses](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-configure-permissions?pivots=entra-portal-app-manifest#use-the-microsoft-entra-admin-center-to-find-the-apis-your-organization-uses)
2. [Update the application manifest on the Microsoft Entra admin center](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-configure-permissions?pivots=entra-portal-app-manifest#update-the-application-manifest-on-the-microsoft-entra-admin-center)
3. [Use the Microsoft Graph applications API](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-configure-permissions?pivots=entra-portal-app-manifest#use-the-microsoft-graph-applications-api)

Caution

Any app using Azure AD Graph stops functioning after the API is retired. For more information, see [Migrate Azure AD Graph apps to Microsoft Graph](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-overview).

## Prerequisites

The steps in this article require two sets of privileges:

- Privileges to add permissions to an app registration
- Privileges to grant those permissions to the app registration

A user with at least the *Privileged Role Administrator* role can do both, while a user with the *Application Administrator* or *Cloud Application Administrator* role can only add the permissions. To help you enforce separation of duties and least privilege access, separate the tasks of adding permissions and granting permissions to different users. For more information about the actions supported by these roles, see [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json).

In addition, you need the following resources and privileges:

- Sign in to an API client such as [Graph Explorer](https://aka.ms/ge) to run the HTTP requests.
- The app used to make these changes must be granted the `Application.ReadWrite.All` permission.

## Use the Microsoft Graph applications API

The Microsoft Graph [application object](https://learn.microsoft.com/en-us/graph/api/resources/application) includes a **requiredResourceAccess** property that is a collection of objects with information about the resource API and permissions. Use this property to configure Azure AD Graph permissions as described in the following steps.

### Step 1: Identify the permission IDs for the Azure AD Graph permissions your app requires

Identify the Azure AD Graph permissions your app requires, their permission IDs, and whether they're app roles \(application permissions\) or oauth2PermissionScopes \(delegated permissions\). For more information, see [Azure AD Graph permissions reference](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-permissions-differences).

Azure AD Graph is identified as a servicePrincipal object with `00000002-0000-0000-c000-000000000000` as its globally unique **appId** and `Windows Azure Active Directory` as its **displayName** and **appDisplayName**. Run the following request to retrieve the service principal object for Azure AD Graph in your tenant.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/servicePrincipals?$filter=appId eq '00000002-0000-0000-c000-000000000000'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "appId eq '00000002-0000-0000-c000-000000000000'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-sdk-go/serviceprincipals"
	  //other-imports
)


requestFilter := "appId eq '00000002-0000-0000-c000-000000000000'"

requestParameters := &graphserviceprincipals.ServicePrincipalsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphserviceprincipals.ServicePrincipalsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
servicePrincipals, err := graphClient.ServicePrincipals().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ServicePrincipalCollectionResponse result = graphClient.servicePrincipals().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "appId eq '00000002-0000-0000-c000-000000000000'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let servicePrincipals = await client.api('/servicePrincipals')
	.filter('appId eq \'00000002-0000-0000-c000-000000000000\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ServicePrincipals\ServicePrincipalsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ServicePrincipalsRequestBuilderGetRequestConfiguration();
$queryParameters = ServicePrincipalsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "appId eq '00000002-0000-0000-c000-000000000000'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->servicePrincipals()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgServicePrincipal -Filter "appId eq '00000002-0000-0000-c000-000000000000'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.service_principals.service_principals_request_builder import ServicePrincipalsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ServicePrincipalsRequestBuilder.ServicePrincipalsRequestBuilderGetQueryParameters(
		filter = "appId eq '00000002-0000-0000-c000-000000000000'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.service_principals.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

In the response object, the **appRoles** object lists details for Azure AD Graph application permissions, and the **oauth2PermissionScopes** object lists details for delegated permissions.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#servicePrincipals",
    "value": [
        {
            "id": "1804a6f8-e623-4520-8f40-ba1b0c11c42d",
            "accountEnabled": true,
            "appDisplayName": "Windows Azure Active Directory",
            "appDescription": null,
            "appId": "00000002-0000-0000-c000-000000000000",
            "appOwnerOrganizationId": "f8cdef31-a31e-4b4a-93e4-5f571e91255a",
            "appRoleAssignmentRequired": false,
            "displayName": "Windows Azure Active Directory",
            "servicePrincipalNames": [
                "https://graph.windows.net",
                "00000002-0000-0000-c000-000000000000/graph.microsoftazure.us",
                "00000002-0000-0000-c000-000000000000/graph.windows.net",
                "00000002-0000-0000-c000-000000000000/directory.windows.net",
                "00000002-0000-0000-c000-000000000000",
                "https://graph.windows.net/",
                "https://graph.microsoftazure.us"
            ],
            "servicePrincipalType": "Application",
            "signInAudience": "AzureADMultipleOrgs",
            "appRoles": [
                {
                    "allowedMemberTypes": [
                        "Application"
                    ],
                    "description": "Allows the app to read applications and service principals without a signed-in user",
                    "displayName": "Read all applications",
                    "id": "3afa6a7d-9b1a-42eb-948e-1650a849e176",
                    "isEnabled": true,
                    "origin": "Application",
                    "value": "Application.Read.All"
                }
            ],
            "oauth2PermissionScopes": [
                {
                    "adminConsentDescription": "Allows users to sign in to the app, and allows the app to read the profile of signed-in users. It also allow the app to read basic company information of signed-in users.",
                    "adminConsentDisplayName": "Sign in and read user profile",
                    "id": "311a71cc-e848-46a1-bdf8-97ff7156d8e6",
                    "isEnabled": true,
                    "type": "User",
                    "userConsentDescription": "Allows you to sign in to the app with your work account and let the app read your profile. It also allows the app to read basic company information.",
                    "userConsentDisplayName": "Sign you in and read your profile",
                    "value": "User.Read"
                }
            ]
        }
    ]
}
```

From the preceding truncated output, `311a71cc-e848-46a1-bdf8-97ff7156d8e6` is the permission ID for the *User.Read* delegated permission, and `3afa6a7d-9b1a-42eb-948e-1650a849e176` is the permission ID for the *Application.Read.All* application permission in Azure AD Graph.

### Step 2: Add Azure AD Graph permissions to your app

The following example calls the [Update application](https://learn.microsoft.com/en-us/graph/api/application-update) API to add the Azure AD Graph *User.Read* and *Application.Read.All* delegated and application permissions to an app registration identified by object ID `581088ba-83c5-4975-b8af-11d2d7a76e98`.

Important

To update the **requiredResourceAccess** property, you must pass in both existing and new permissions. Passing in only new permissions overwrites and removes the existing permissions.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
PATCH https://graph.microsoft.com/v1.0/applications/581088ba-83c5-4975-b8af-11d2d7a76e98
Content-Type: application/json

{
    "requiredResourceAccess": [
        {
            "resourceAppId": "00000002-0000-0000-c000-000000000000",
            "resourceAccess": [
                {
                    "id": "311a71cc-e848-46a1-bdf8-97ff7156d8e6",
                    "type": "Scope"
                },
                {
                    "id": "3afa6a7d-9b1a-42eb-948e-1650a849e176",
                    "type": "Role"
                }
            ]
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
	RequiredResourceAccess = new List<RequiredResourceAccess>
	{
		new RequiredResourceAccess
		{
			ResourceAppId = "00000002-0000-0000-c000-000000000000",
			ResourceAccess = new List<ResourceAccess>
			{
				new ResourceAccess
				{
					Id = Guid.Parse("311a71cc-e848-46a1-bdf8-97ff7156d8e6"),
					Type = "Scope",
				},
				new ResourceAccess
				{
					Id = Guid.Parse("3afa6a7d-9b1a-42eb-948e-1650a849e176"),
					Type = "Role",
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications["{application-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewApplication()


requiredResourceAccess := graphmodels.NewRequiredResourceAccess()
resourceAppId := "00000002-0000-0000-c000-000000000000"
requiredResourceAccess.SetResourceAppId(&resourceAppId) 


resourceAccess := graphmodels.NewResourceAccess()
id := uuid.MustParse("311a71cc-e848-46a1-bdf8-97ff7156d8e6")
resourceAccess.SetId(&id) 
type := "Scope"
resourceAccess.SetType(&type) 
resourceAccess1 := graphmodels.NewResourceAccess()
id := uuid.MustParse("3afa6a7d-9b1a-42eb-948e-1650a849e176")
resourceAccess1.SetId(&id) 
type := "Role"
resourceAccess1.SetType(&type) 

resourceAccess := []graphmodels.ResourceAccessable {
	resourceAccess,
	resourceAccess1,
}
requiredResourceAccess.SetResourceAccess(resourceAccess)

requiredResourceAccess := []graphmodels.RequiredResourceAccessable {
	requiredResourceAccess,
}
requestBody.SetRequiredResourceAccess(requiredResourceAccess)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
LinkedList<RequiredResourceAccess> requiredResourceAccess = new LinkedList<RequiredResourceAccess>();
RequiredResourceAccess requiredResourceAccess1 = new RequiredResourceAccess();
requiredResourceAccess1.setResourceAppId("00000002-0000-0000-c000-000000000000");
LinkedList<ResourceAccess> resourceAccess = new LinkedList<ResourceAccess>();
ResourceAccess resourceAccess1 = new ResourceAccess();
resourceAccess1.setId(UUID.fromString("311a71cc-e848-46a1-bdf8-97ff7156d8e6"));
resourceAccess1.setType("Scope");
resourceAccess.add(resourceAccess1);
ResourceAccess resourceAccess2 = new ResourceAccess();
resourceAccess2.setId(UUID.fromString("3afa6a7d-9b1a-42eb-948e-1650a849e176"));
resourceAccess2.setType("Role");
resourceAccess.add(resourceAccess2);
requiredResourceAccess1.setResourceAccess(resourceAccess);
requiredResourceAccess.add(requiredResourceAccess1);
application.setRequiredResourceAccess(requiredResourceAccess);
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
    requiredResourceAccess: [
        {
            resourceAppId: '00000002-0000-0000-c000-000000000000',
            resourceAccess: [
                {
                    id: '311a71cc-e848-46a1-bdf8-97ff7156d8e6',
                    type: 'Scope'
                },
                {
                    id: '3afa6a7d-9b1a-42eb-948e-1650a849e176',
                    type: 'Role'
                }
            ]
        }
    ]
};

await client.api('/applications/581088ba-83c5-4975-b8af-11d2d7a76e98')
	.update(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Application;
use Microsoft\Graph\Generated\Models\RequiredResourceAccess;
use Microsoft\Graph\Generated\Models\ResourceAccess;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$requiredResourceAccessRequiredResourceAccess1 = new RequiredResourceAccess();
$requiredResourceAccessRequiredResourceAccess1->setResourceAppId('00000002-0000-0000-c000-000000000000');
$resourceAccessResourceAccess1 = new ResourceAccess();
$resourceAccessResourceAccess1->setId('311a71cc-e848-46a1-bdf8-97ff7156d8e6');
$resourceAccessResourceAccess1->setType('Scope');
$resourceAccessArray []= $resourceAccessResourceAccess1;
$resourceAccessResourceAccess2 = new ResourceAccess();
$resourceAccessResourceAccess2->setId('3afa6a7d-9b1a-42eb-948e-1650a849e176');
$resourceAccessResourceAccess2->setType('Role');
$resourceAccessArray []= $resourceAccessResourceAccess2;
$requiredResourceAccessRequiredResourceAccess1->setResourceAccess($resourceAccessArray);

$requiredResourceAccessArray []= $requiredResourceAccessRequiredResourceAccess1;
$requestBody->setRequiredResourceAccess($requiredResourceAccessArray);


$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	requiredResourceAccess = @(
		@{
			resourceAppId = "00000002-0000-0000-c000-000000000000"
			resourceAccess = @(
				@{
					id = "311a71cc-e848-46a1-bdf8-97ff7156d8e6"
					type = "Scope"
				}
				@{
					id = "3afa6a7d-9b1a-42eb-948e-1650a849e176"
					type = "Role"
				}
			)
		}
	)
}

Update-MgApplication -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.application import Application
from msgraph.generated.models.required_resource_access import RequiredResourceAccess
from msgraph.generated.models.resource_access import ResourceAccess
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	required_resource_access = [
		RequiredResourceAccess(
			resource_app_id = "00000002-0000-0000-c000-000000000000",
			resource_access = [
				ResourceAccess(
					id = UUID("311a71cc-e848-46a1-bdf8-97ff7156d8e6"),
					type = "Scope",
				),
				ResourceAccess(
					id = UUID("3afa6a7d-9b1a-42eb-948e-1650a849e176"),
					type = "Role",
				),
			],
		),
	],
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 204 No Content
```

### Step 3: Verify you added the Azure AD Graph permissions to your app

Verify that your app registration has the Azure AD Graph API permissions you added in Step 2 by:

1. Calling the Microsoft Graph GET /application/{id} endpoint and reading the **requiredResourceAccess** property as follows:

   ```msgraph
   GET https://graph.microsoft.com/v1.0/applications/581088ba-83c5-4975-b8af-11d2d7a76e98?$select=id,requiredResourceAccess
   ```

2. Checking the **App registrations** page in the Microsoft Entra admin center.

### Step 4: Grant admin consent

Though you added Azure AD Graph permissions, you didn't grant these permissions to the app. Many permissions require admin consent before they can be used to access organizational data. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as a privileged role administrator and grant admin consent for the permissions to the app registration.

## Grant API permissions without using the consent prompt

When using Microsoft Graph and any related SDKs, you can grant permissions to an app registration without the need to use the Microsoft Entra admin center and selecting the *Grant admin consent for \[Company\]* button on the API permissions page. For more information, see [Grant or revoke API permissions programmatically](https://learn.microsoft.com/en-us/graph/permissions-grant-via-msgraph).

## Use the Microsoft Entra admin center to find the APIs your organization uses

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Expand **Identity** > **Applications** > select **App registrations**.
3. In the **App registrations** window, under the **All applications** tab, select the app that you want to add Azure AD Graph permissions to.
4. From the left pane of the window, under the **Manage** menu group, select **API permissions**. In the **Configured permissions** window, select **Add a permission**.
5. In the **Request API permissions** window, switch to the **APIs my organization uses** tab and search for `Windows Azure Active Directory` or `00000002-0000-0000-c000-000000000000`. Select from the filtered result set to reveal the **Azure Active Directory Graph** permissions window.

   ![Azure AD Graph API is named Windows Azure Active Directory and has clientID 00000002-0000-0000-c000-000000000000.](https://learn.microsoft.com/en-us/graph/images/aadgraph-to-msgraph-migration/AzureADGraphPermissionsAPI.png)
6. Select the **Delegated permissions** or **Application permissions** tab to choose from the list of delegated and application permissions respectively. Select **Add permissions** to add the permission to your app registration.
7. After adding the permissions you need, back in the **Configured permissions** window, select **Grant admin consent** to grant the Azure AD Graph permissions to your app registration.

## Update the application manifest on the Microsoft Entra admin center

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Expand the **Identity** menu, select **Applications**, then select **App registrations**.
3. In the **App registrations** window, under the **All applications** tab, select the app that you want to add Azure AD Graph permissions to.
4. In the left pane of the window, under the **Manage** menu group, select **Manifest** to open an editor that allows you to directly edit the attributes of the app registration object.

   ![An app registration Manifest file allows you to edit the attributes of your application.](https://learn.microsoft.com/en-us/graph/images/aadgraph-to-msgraph-migration/AppRegistrationManifest.png)
5. Carefully edit the **requiredResourceAccess** property in the app's manifest to add the following details:

   Tip

   - You can edit the app manifest on the Microsoft Entra admin center or select **Download** to edit the manifest locally, and then use **Upload** to reapply it to your application.
   - To learn more about how to configure the **requiredResourceAccess** property, see [requiredResourceAccess resource type](https://learn.microsoft.com/en-us/graph/api/resources/requiredresourceaccess).
   - Refer to the [Azure AD Graph permissions reference](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-permissions-differences) for details of Azure AD Graph permission names, IDs, and types.


   1. If the app isn't assigned any Azure AD Graph permissions, add the **resourceAppId** property and assign the value `00000002-0000-0000-c000-000000000000` representing Azure AD Graph.
   2. Add the **resourceAccess** property and configure the permissions.


   The following JSON snippet shows a **requiredResourceAccess** property with Azure AD Graph as the resource, and assigned the *User.Read* and *Application.Read.All* oauth2PermissionScope \(delegated permission\) and appRole \(application permission\) respectively.


   ```JSON
   "requiredResourceAccess": [
       {
           "resourceAppId": "00000002-0000-0000-c000-000000000000",
           "resourceAccess": [
               {
                   "id": "311a71cc-e848-46a1-bdf8-97ff7156d8e6",
                   "type": "Scope"
               },
               {
                   "id": "3afa6a7d-9b1a-42eb-948e-1650a849e176",
                   "type": "Role"
               }
           ]
       }
   ],
   ```

6. Save your changes.
7. Back under the **Manage** menu group, select **API permissions** and in the **Configured permissions** for your app registration, select **Grant admin consent** to grant the Azure AD Graph permissions to your app registration.

## Related content

- [application object](https://learn.microsoft.com/en-us/graph/api/resources/application)
- [Grant permissions programmatically without interactive consent](https://learn.microsoft.com/en-us/graph/permissions-grant-via-msgraph)
- [Azure AD Graph permissions reference](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-permissions-differences)
