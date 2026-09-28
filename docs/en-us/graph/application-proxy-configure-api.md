<!-- Source: https://learn.microsoft.com/en-us/graph/application-proxy-configure-api -->
<!-- Sitemap-Last-Modified: 2024-05-20 -->

# Configure Microsoft Entra application proxy using Microsoft Graph APIs

[Microsoft Entra application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/overview-what-is-app-proxy) provides secure remote access and single sign-on \(SSO\) to on-premises web applications. It allows users to access their on-premises applications through an external URL, the My Apps portal, or other internal application portals.

In this tutorial, you learn how to Configure Microsoft Entra application proxy using Microsoft Graph APIs.

Important

The app proxy-specific API operations are currently available only on the `beta` endpoint.

## Prerequisites

- Install a connector and complete the [prerequisites](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-add-on-premises-application#prerequisites) for application proxy so that connectors can communicate with Microsoft Entra services.
- Sign in to an API client such as [Graph Explorer](https://aka.ms/ge) with an account that has at least the Cloud Application Administrator role.
- Grant yourself the Microsoft Graph `Directory.ReadWrite.All` delegated permission.
- Have a test user to assign to the application.

## Step 1: Create a custom application

To configure application proxy, you first create a custom application, and then update the app proxy settings in the application's **onPremisesPublishing** property. In this tutorial, you use an application template to create an instance of a custom application and service principal in your tenant. The template ID for a custom application is `8adf8e6e-67b2-4cf2-a259-e3dc5476c621`, which you can discover by running the following query: [GET https://graph.microsoft.com/v1.0/applicationTemplates?$filter=displayName eq 'Custom'](https://developer.microsoft.com/en-us/graph/graph-explorer?request=applicationTemplates%3F%24filter%3DdisplayName%2Beq%2B%27Custom%27&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com).

From the response, record the **id** of both the service principal and the application objects, and the value of **appId** for use later in the tutorial.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/applicationTemplates/8adf8e6e-67b2-4cf2-a259-e3dc5476c621/instantiate
Content-type: application/json

{
  "displayName": "Contoso IWA App"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.ApplicationTemplates.Item.Instantiate;

var requestBody = new InstantiatePostRequestBody
{
	DisplayName = "Contoso IWA App",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ApplicationTemplates["{applicationTemplate-id}"].Instantiate.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphapplicationtemplates "github.com/microsoftgraph/msgraph-sdk-go/applicationtemplates"
	  //other-imports
)

requestBody := graphapplicationtemplates.NewInstantiatePostRequestBody()
displayName := "Contoso IWA App"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
instantiate, err := graphClient.ApplicationTemplates().ByApplicationTemplateId("applicationTemplate-id").Instantiate().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.applicationtemplates.item.instantiate.InstantiatePostRequestBody instantiatePostRequestBody = new com.microsoft.graph.applicationtemplates.item.instantiate.InstantiatePostRequestBody();
instantiatePostRequestBody.setDisplayName("Contoso IWA App");
var result = graphClient.applicationTemplates().byApplicationTemplateId("{applicationTemplate-id}").instantiate().post(instantiatePostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const applicationServicePrincipal = {
  displayName: 'Contoso IWA App'
};

await client.api('/applicationTemplates/8adf8e6e-67b2-4cf2-a259-e3dc5476c621/instantiate')
	.post(applicationServicePrincipal);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ApplicationTemplates\Item\Instantiate\InstantiatePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new InstantiatePostRequestBody();
$requestBody->setDisplayName('Contoso IWA App');

$result = $graphServiceClient->applicationTemplates()->byApplicationTemplateId('applicationTemplate-id')->instantiate()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	displayName = "Contoso IWA App"
}

Invoke-MgInstantiateApplicationTemplate -ApplicationTemplateId $applicationTemplateId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.applicationtemplates.item.instantiate.instantiate_post_request_body import InstantiatePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = InstantiatePostRequestBody(
	display_name = "Contoso IWA App",
)

result = await graph_client.application_templates.by_application_template_id('applicationTemplate-id').instantiate.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.applicationServicePrincipal",
    "application": {
        "id": "bf21f7e9-9d25-4da2-82ab-7fdd85049f83",
        "appId": "32977d3b-ee0e-4614-9f50-f583a07842d2",
        "applicationTemplateId": "8adf8e6e-67b2-4cf2-a259-e3dc5476c621",
        "createdDateTime": "2024-02-22T16:48:09Z",
        "deletedDateTime": null,
        "displayName": "Contoso IWA App",
        "description": null,
        "groupMembershipClaims": null,
        "identifierUris": [],
        "isFallbackPublicClient": false,
        "signInAudience": "AzureADMyOrg",
        "tags": [],
        "tokenEncryptionKeyId": null,
        "defaultRedirectUri": null,
        "samlMetadataUrl": null,
        "optionalClaims": null,
        "addIns": [],
        "api": {
            "acceptMappedClaims": null,
            "knownClientApplications": [],
            "requestedAccessTokenVersion": null,
            "oauth2PermissionScopes": [
                {
                    "adminConsentDescription": "Allow the application to access Contoso IWA App on behalf of the signed-in user.",
                    "adminConsentDisplayName": "Access Contoso IWA App",
                    "id": "5cda2e1e-d9fd-4f69-b981-48fbc8a16be1",
                    "isEnabled": true,
                    "type": "User",
                    "userConsentDescription": "Allow the application to access Contoso IWA App on your behalf.",
                    "userConsentDisplayName": "Access Contoso IWA App",
                    "value": "user_impersonation"
                }
            ],
            "preAuthorizedApplications": []
        },
        "appRoles": [
            {
                "allowedMemberTypes": [
                    "User"
                ],
                "displayName": "User",
                "id": "18d14569-c3bd-439b-9a66-3a2aee01d14f",
                "isEnabled": true,
                "description": "User",
                "value": null,
                "origin": "Application"
            },
            {
                "allowedMemberTypes": [
                    "User"
                ],
                "displayName": "msiam_access",
                "id": "b9632174-c057-4f7e-951b-be3adc52bfe6",
                "isEnabled": true,
                "description": "msiam_access",
                "value": null,
                "origin": "Application"
            }
        ],
        "info": {
            "logoUrl": null,
            "marketingUrl": null,
            "privacyStatementUrl": null,
            "supportUrl": null,
            "termsOfServiceUrl": null
        },
        "keyCredentials": [],
        "parentalControlSettings": {
            "countriesBlockedForMinors": [],
            "legalAgeGroupRule": "Allow"
        },
        "passwordCredentials": [],
        "publicClient": {
            "redirectUris": []
        },
        "requiredResourceAccess": [],
        "verifiedPublisher": {
            "displayName": null,
            "verifiedPublisherId": null,
            "addedDateTime": null
        },
        "web": {
            "homePageUrl": "https://account.activedirectory.windowsazure.com:444/applications/default.aspx?metadata=customappsso|ISV9.1|primary|z",
            "redirectUris": [],
            "logoutUrl": null
        }
    },
    "servicePrincipal": {
        "id": "a8cac399-cde5-4516-a674-819503c61313",
        "deletedDateTime": null,
        "accountEnabled": true,
        "appId": "32977d3b-ee0e-4614-9f50-f583a07842d2",
        "applicationTemplateId": "8adf8e6e-67b2-4cf2-a259-e3dc5476c621",
        "appDisplayName": "Contoso IWA App",
        "alternativeNames": [],
        "appOwnerOrganizationId": "38d49456-54d4-455d-a8d6-c383c71e0a6d",
        "displayName": "Contoso IWA App",
        "appRoleAssignmentRequired": true,
        "loginUrl": null,
        "logoutUrl": null,
        "homepage": "https://account.activedirectory.windowsazure.com:444/applications/default.aspx?metadata=customappsso|ISV9.1|primary|z",
        "notificationEmailAddresses": [],
        "preferredSingleSignOnMode": null,
        "preferredTokenSigningKeyThumbprint": null,
        "replyUrls": [],
        "servicePrincipalNames": [
            "32977d3b-ee0e-4614-9f50-f583a07842d2"
        ],
        "servicePrincipalType": "Application",
        "tags": [
            "WindowsAzureActiveDirectoryCustomSingleSignOnApplication",
            "WindowsAzureActiveDirectoryIntegratedApp"
        ],
        "tokenEncryptionKeyId": null,
        "samlSingleSignOnSettings": null,
        "addIns": [],
        "appRoles": [
            {
                "allowedMemberTypes": [
                    "User"
                ],
                "displayName": "User",
                "id": "18d14569-c3bd-439b-9a66-3a2aee01d14f",
                "isEnabled": true,
                "description": "User",
                "value": null,
                "origin": "Application"
            },
            {
                "allowedMemberTypes": [
                    "User"
                ],
                "displayName": "msiam_access",
                "id": "b9632174-c057-4f7e-951b-be3adc52bfe6",
                "isEnabled": true,
                "description": "msiam_access",
                "value": null,
                "origin": "Application"
            }
        ],
        "info": {
            "logoUrl": null,
            "marketingUrl": null,
            "privacyStatementUrl": null,
            "supportUrl": null,
            "termsOfServiceUrl": null
        },
        "keyCredentials": [],
        "oauth2PermissionScopes": [
            {
                "adminConsentDescription": "Allow the application to access Contoso IWA App on behalf of the signed-in user.",
                "adminConsentDisplayName": "Access Contoso IWA App",
                "id": "5cda2e1e-d9fd-4f69-b981-48fbc8a16be1",
                "isEnabled": true,
                "type": "User",
                "userConsentDescription": "Allow the application to access Contoso IWA App on your behalf.",
                "userConsentDisplayName": "Access Contoso IWA App",
                "value": "user_impersonation"
            }
        ],
        "passwordCredentials": [],
        "verifiedPublisher": {
            "displayName": null,
            "verifiedPublisherId": null,
            "addedDateTime": null
        }
    }
}
```

## Step 2: Configure application proxy

For the app that you created in Step 1, configure the URIs for the application. Assume that the app's internal URL is `https://contosoiwaapp.com` and the default domain for the external URL is `https://contosoiwaapp-contoso.msappproxy.net`. Add the external URL value to the **identifierUris**, **web>redirectUris** and **web>homePageUrl** properties.

Also, configure the **onPremisesPublishing** property to set the internal and external URLs, and other properties as needed. This property is only available in `beta` and can't be configured until you configure the URIs.

### Step 2.1: Configure the URIs

The following request uses the value of **appId** for the **identifierUris** property. You can also use any other identifier that matches the application id URI format expected by Microsoft Entra ID. The request returns a `204 No content` response.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/applications/bf21f7e9-9d25-4da2-82ab-7fdd85049f83
Content-type: application/json

{
    "identifierUris": [
        "api://32977d3b-ee0e-4614-9f50-f583a07842d2"
    ],
    "web": {
        "redirectUris": [
            "https://contosoiwaapp-contoso.msappproxy.net"
        ],
        "homePageUrl": "https://contosoiwaapp-contoso.msappproxy.net"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Application
{
	IdentifierUris = new List<string>
	{
		"api://32977d3b-ee0e-4614-9f50-f583a07842d2",
	},
	Web = new WebApplication
	{
		RedirectUris = new List<string>
		{
			"https://contosoiwaapp-contoso.msappproxy.net",
		},
		HomePageUrl = "https://contosoiwaapp-contoso.msappproxy.net",
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
identifierUris := []string {
	"api://32977d3b-ee0e-4614-9f50-f583a07842d2",
}
requestBody.SetIdentifierUris(identifierUris)
web := graphmodels.NewWebApplication()
redirectUris := []string {
	"https://contosoiwaapp-contoso.msappproxy.net",
}
web.SetRedirectUris(redirectUris)
homePageUrl := "https://contosoiwaapp-contoso.msappproxy.net"
web.SetHomePageUrl(&homePageUrl) 
requestBody.SetWeb(web)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
LinkedList<String> identifierUris = new LinkedList<String>();
identifierUris.add("api://32977d3b-ee0e-4614-9f50-f583a07842d2");
application.setIdentifierUris(identifierUris);
WebApplication web = new WebApplication();
LinkedList<String> redirectUris = new LinkedList<String>();
redirectUris.add("https://contosoiwaapp-contoso.msappproxy.net");
web.setRedirectUris(redirectUris);
web.setHomePageUrl("https://contosoiwaapp-contoso.msappproxy.net");
application.setWeb(web);
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
    identifierUris: [
        'api://32977d3b-ee0e-4614-9f50-f583a07842d2'
    ],
    web: {
        redirectUris: [
            'https://contosoiwaapp-contoso.msappproxy.net'
        ],
        homePageUrl: 'https://contosoiwaapp-contoso.msappproxy.net'
    }
};

await client.api('/applications/bf21f7e9-9d25-4da2-82ab-7fdd85049f83')
	.update(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Application;
use Microsoft\Graph\Generated\Models\WebApplication;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$requestBody->setIdentifierUris(['api://32977d3b-ee0e-4614-9f50-f583a07842d2', 	]);
$web = new WebApplication();
$web->setRedirectUris(['https://contosoiwaapp-contoso.msappproxy.net', 	]);
$web->setHomePageUrl('https://contosoiwaapp-contoso.msappproxy.net');
$requestBody->setWeb($web);

$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	identifierUris = @(
	"api://32977d3b-ee0e-4614-9f50-f583a07842d2"
)
web = @{
	redirectUris = @(
	"https://contosoiwaapp-contoso.msappproxy.net"
)
homePageUrl = "https://contosoiwaapp-contoso.msappproxy.net"
}
}

Update-MgApplication -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.application import Application
from msgraph.generated.models.web_application import WebApplication
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	identifier_uris = [
		"api://32977d3b-ee0e-4614-9f50-f583a07842d2",
	],
	web = WebApplication(
		redirect_uris = [
			"https://contosoiwaapp-contoso.msappproxy.net",
		],
		home_page_url = "https://contosoiwaapp-contoso.msappproxy.net",
	),
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Step 2.2: Configure the onPremisesPublishing property

The request returns a `204 No content` response.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
PATCH https://graph.microsoft.com/beta/applications/bf21f7e9-9d25-4da2-82ab-7fdd85049f83
Content-type: application/json

{
    "onPremisesPublishing": {
        "externalAuthenticationType": "aadPreAuthentication",
        "internalUrl": "https://contosoiwaapp.com",
        "externalUrl": "https://contosoiwaapp-contoso.msappproxy.net",
        "isHttpOnlyCookieEnabled": true,
        "isOnPremPublishingEnabled": true,
        "isPersistentCookieEnabled": true,
        "isSecureCookieEnabled": true,
        "isStateSessionEnabled": true,
        "isTranslateHostHeaderEnabled": true,
        "isTranslateLinksInBodyEnabled": true
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new Application
{
	OnPremisesPublishing = new OnPremisesPublishing
	{
		ExternalAuthenticationType = ExternalAuthenticationType.AadPreAuthentication,
		InternalUrl = "https://contosoiwaapp.com",
		ExternalUrl = "https://contosoiwaapp-contoso.msappproxy.net",
		IsHttpOnlyCookieEnabled = true,
		IsOnPremPublishingEnabled = true,
		IsPersistentCookieEnabled = true,
		IsSecureCookieEnabled = true,
		IsStateSessionEnabled = true,
		IsTranslateHostHeaderEnabled = true,
		IsTranslateLinksInBodyEnabled = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications["{application-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewApplication()
onPremisesPublishing := graphmodels.NewOnPremisesPublishing()
externalAuthenticationType := graphmodels.AADPREAUTHENTICATION_EXTERNALAUTHENTICATIONTYPE 
onPremisesPublishing.SetExternalAuthenticationType(&externalAuthenticationType) 
internalUrl := "https://contosoiwaapp.com"
onPremisesPublishing.SetInternalUrl(&internalUrl) 
externalUrl := "https://contosoiwaapp-contoso.msappproxy.net"
onPremisesPublishing.SetExternalUrl(&externalUrl) 
isHttpOnlyCookieEnabled := true
onPremisesPublishing.SetIsHttpOnlyCookieEnabled(&isHttpOnlyCookieEnabled) 
isOnPremPublishingEnabled := true
onPremisesPublishing.SetIsOnPremPublishingEnabled(&isOnPremPublishingEnabled) 
isPersistentCookieEnabled := true
onPremisesPublishing.SetIsPersistentCookieEnabled(&isPersistentCookieEnabled) 
isSecureCookieEnabled := true
onPremisesPublishing.SetIsSecureCookieEnabled(&isSecureCookieEnabled) 
isStateSessionEnabled := true
onPremisesPublishing.SetIsStateSessionEnabled(&isStateSessionEnabled) 
isTranslateHostHeaderEnabled := true
onPremisesPublishing.SetIsTranslateHostHeaderEnabled(&isTranslateHostHeaderEnabled) 
isTranslateLinksInBodyEnabled := true
onPremisesPublishing.SetIsTranslateLinksInBodyEnabled(&isTranslateLinksInBodyEnabled) 
requestBody.SetOnPremisesPublishing(onPremisesPublishing)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
OnPremisesPublishing onPremisesPublishing = new OnPremisesPublishing();
onPremisesPublishing.setExternalAuthenticationType(ExternalAuthenticationType.AadPreAuthentication);
onPremisesPublishing.setInternalUrl("https://contosoiwaapp.com");
onPremisesPublishing.setExternalUrl("https://contosoiwaapp-contoso.msappproxy.net");
onPremisesPublishing.setIsHttpOnlyCookieEnabled(true);
onPremisesPublishing.setIsOnPremPublishingEnabled(true);
onPremisesPublishing.setIsPersistentCookieEnabled(true);
onPremisesPublishing.setIsSecureCookieEnabled(true);
onPremisesPublishing.setIsStateSessionEnabled(true);
onPremisesPublishing.setIsTranslateHostHeaderEnabled(true);
onPremisesPublishing.setIsTranslateLinksInBodyEnabled(true);
application.setOnPremisesPublishing(onPremisesPublishing);
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
    onPremisesPublishing: {
        externalAuthenticationType: 'aadPreAuthentication',
        internalUrl: 'https://contosoiwaapp.com',
        externalUrl: 'https://contosoiwaapp-contoso.msappproxy.net',
        isHttpOnlyCookieEnabled: true,
        isOnPremPublishingEnabled: true,
        isPersistentCookieEnabled: true,
        isSecureCookieEnabled: true,
        isStateSessionEnabled: true,
        isTranslateHostHeaderEnabled: true,
        isTranslateLinksInBodyEnabled: true
    }
};

await client.api('/applications/bf21f7e9-9d25-4da2-82ab-7fdd85049f83')
	.version('beta')
	.update(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Application;
use Microsoft\Graph\Beta\Generated\Models\OnPremisesPublishing;
use Microsoft\Graph\Beta\Generated\Models\ExternalAuthenticationType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$onPremisesPublishing = new OnPremisesPublishing();
$onPremisesPublishing->setExternalAuthenticationType(new ExternalAuthenticationType('aadPreAuthentication'));
$onPremisesPublishing->setInternalUrl('https://contosoiwaapp.com');
$onPremisesPublishing->setExternalUrl('https://contosoiwaapp-contoso.msappproxy.net');
$onPremisesPublishing->setIsHttpOnlyCookieEnabled(true);
$onPremisesPublishing->setIsOnPremPublishingEnabled(true);
$onPremisesPublishing->setIsPersistentCookieEnabled(true);
$onPremisesPublishing->setIsSecureCookieEnabled(true);
$onPremisesPublishing->setIsStateSessionEnabled(true);
$onPremisesPublishing->setIsTranslateHostHeaderEnabled(true);
$onPremisesPublishing->setIsTranslateLinksInBodyEnabled(true);
$requestBody->setOnPremisesPublishing($onPremisesPublishing);

$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Applications

$params = @{
	onPremisesPublishing = @{
		externalAuthenticationType = "aadPreAuthentication"
		internalUrl = "https://contosoiwaapp.com"
		externalUrl = "https://contosoiwaapp-contoso.msappproxy.net"
		isHttpOnlyCookieEnabled = $true
		isOnPremPublishingEnabled = $true
		isPersistentCookieEnabled = $true
		isSecureCookieEnabled = $true
		isStateSessionEnabled = $true
		isTranslateHostHeaderEnabled = $true
		isTranslateLinksInBodyEnabled = $true
	}
}

Update-MgBetaApplication -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.application import Application
from msgraph_beta.generated.models.on_premises_publishing import OnPremisesPublishing
from msgraph_beta.generated.models.external_authentication_type import ExternalAuthenticationType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	on_premises_publishing = OnPremisesPublishing(
		external_authentication_type = ExternalAuthenticationType.AadPreAuthentication,
		internal_url = "https://contosoiwaapp.com",
		external_url = "https://contosoiwaapp-contoso.msappproxy.net",
		is_http_only_cookie_enabled = True,
		is_on_prem_publishing_enabled = True,
		is_persistent_cookie_enabled = True,
		is_secure_cookie_enabled = True,
		is_state_session_enabled = True,
		is_translate_host_header_enabled = True,
		is_translate_links_in_body_enabled = True,
	),
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Step 3: Assign a connector group to the application

### Step 3.1: Get connectors

Identify the connector that you want to assign to the connector group. Record its **id**.

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectors
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.OnPremisesPublishingProfiles["{onPremisesPublishingProfile-id}"].Connectors.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
connectors, err := graphClient.OnPremisesPublishingProfiles().ByOnPremisesPublishingProfileId("onPremisesPublishingProfile-id").Connectors().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConnectorCollectionResponse result = graphClient.onPremisesPublishingProfiles().byOnPremisesPublishingProfileId("{onPremisesPublishingProfile-id}").connectors().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let connectors = await client.api('/onPremisesPublishingProfiles/applicationProxy/connectors')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->onPremisesPublishingProfiles()->byOnPremisesPublishingProfileId('onPremisesPublishingProfile-id')->connectors()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Applications

Get-MgBetaOnPremisePublishingProfileConnector -OnPremisesPublishingProfileId $onPremisesPublishingProfileId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.on_premises_publishing_profiles.by_on_premises_publishing_profile_id('onPremisesPublishingProfile-id').connectors.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#onPremisesPublishingProfiles('applicationProxy')/connectors",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET onPremisesPublishingProfiles('<key>')/connectors?$select=externalIp,machineName",
    "value": [
    {
      "id": "d2b1e8e8-8511-49d6-a4ba-323cb083fbb0",
      "machineName": "connectorA.redmond.contoso.com"",
      "externalIp": "131.137.147.164",
      "status": "active"
    },
    {
      "id": "f2cab422-a1c8-4d70-a47e-2cb297a2e051",
      "machineName": "connectorB.contoso.com"",
      "externalIp": "68.0.191.210",
      "status": "active"
    }
  ]
}
```

### Step 3.2: Create a connectorGroup

Create a connectorGroup named `IWA Demo Connector Group` for the application. Record its **id**.

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
POST https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectorGroups
Content-type: application/json

{
  "name": "IWA Demo Connector Group"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ConnectorGroup
{
	Name = "IWA Demo Connector Group",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.OnPremisesPublishingProfiles["{onPremisesPublishingProfile-id}"].ConnectorGroups.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewConnectorGroup()
name := "IWA Demo Connector Group"
requestBody.SetName(&name) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
connectorGroups, err := graphClient.OnPremisesPublishingProfiles().ByOnPremisesPublishingProfileId("onPremisesPublishingProfile-id").ConnectorGroups().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConnectorGroup connectorGroup = new ConnectorGroup();
connectorGroup.setName("IWA Demo Connector Group");
ConnectorGroup result = graphClient.onPremisesPublishingProfiles().byOnPremisesPublishingProfileId("{onPremisesPublishingProfile-id}").connectorGroups().post(connectorGroup);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const connectorGroup = {
  name: 'IWA Demo Connector Group'
};

await client.api('/onPremisesPublishingProfiles/applicationProxy/connectorGroups')
	.version('beta')
	.post(connectorGroup);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ConnectorGroup;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConnectorGroup();
$requestBody->setName('IWA Demo Connector Group');

$result = $graphServiceClient->onPremisesPublishingProfiles()->byOnPremisesPublishingProfileId('onPremisesPublishingProfile-id')->connectorGroups()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Applications

$params = @{
	name = "IWA Demo Connector Group"
}

New-MgBetaOnPremisePublishingProfileConnectorGroup -OnPremisesPublishingProfileId $onPremisesPublishingProfileId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.connector_group import ConnectorGroup
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConnectorGroup(
	name = "IWA Demo Connector Group",
)

result = await graph_client.on_premises_publishing_profiles.by_on_premises_publishing_profile_id('onPremisesPublishingProfile-id').connector_groups.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#connectorGroups/$entity",
  "id": "3e6f4c35-a04b-4d03-b98a-66fff89b72e6",
  "name": "IWA Demo Connector Group",
  "connectorGroupType": "applicationProxy",
  "region": "eur",
  "isDefault": false
}
```

### Step 3.3: Assign a connector to the connectorGroup

The request returns a `204 No content` response.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectors/f2cab422-a1c8-4d70-a47e-2cb297a2e051/memberOf/$ref
Content-type: application/json

{
  "@odata.id":"https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ReferenceCreate
{
	OdataId = "https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.OnPremisesPublishingProfiles["{onPremisesPublishingProfile-id}"].Connectors["{connector-id}"].MemberOf.Ref.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewReferenceCreate()
odataId := "https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6"
requestBody.SetOdataId(&odataId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.OnPremisesPublishingProfiles().ByOnPremisesPublishingProfileId("onPremisesPublishingProfile-id").Connectors().ByConnectorId("connector-id").MemberOf().Ref().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.ReferenceCreate referenceCreate = new com.microsoft.graph.beta.models.ReferenceCreate();
referenceCreate.setOdataId("https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6");
graphClient.onPremisesPublishingProfiles().byOnPremisesPublishingProfileId("{onPremisesPublishingProfile-id}").connectors().byConnectorId("{connector-id}").memberOf().ref().post(referenceCreate);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const connectorGroup = {
  '@odata.id':'https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6'
};

await client.api('/onPremisesPublishingProfiles/applicationProxy/connectors/f2cab422-a1c8-4d70-a47e-2cb297a2e051/memberOf/$ref')
	.version('beta')
	.post(connectorGroup);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ReferenceCreate;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReferenceCreate();
$requestBody->setOdataId('https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6');

$graphServiceClient->onPremisesPublishingProfiles()->byOnPremisesPublishingProfileId('onPremisesPublishingProfile-id')->connectors()->byConnectorId('connector-id')->memberOf()->ref()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Applications

$params = @{
	"@odata.id" = "https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6"
}

New-MgBetaOnPremisePublishingProfileConnectorMemberOfByRef -OnPremisesPublishingProfileId $onPremisesPublishingProfileId -ConnectorId $connectorId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.reference_create import ReferenceCreate
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReferenceCreate(
	odata_id = "https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6",
)

await graph_client.on_premises_publishing_profiles.by_on_premises_publishing_profile_id('onPremisesPublishingProfile-id').connectors.by_connector_id('connector-id').member_of.ref.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Step 3.4: Assign the application to the connectorGroup

The request returns a `204 No content` response.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
PUT https://graph.microsoft.com/beta/applications/bf21f7e9-9d25-4da2-82ab-7fdd85049f83/connectorGroup/$ref
Content-type: application/json

{
  "@odata.id":"https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationproxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ReferenceUpdate
{
	OdataId = "https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationproxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Applications["{application-id}"].ConnectorGroup.Ref.PutAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewReferenceUpdate()
odataId := "https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationproxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6"
requestBody.SetOdataId(&odataId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Applications().ByApplicationId("application-id").ConnectorGroup().Ref().Put(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.ReferenceUpdate referenceUpdate = new com.microsoft.graph.beta.models.ReferenceUpdate();
referenceUpdate.setOdataId("https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationproxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6");
graphClient.applications().byApplicationId("{application-id}").connectorGroup().ref().put(referenceUpdate);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const connectorGroup = {
  '@odata.id':'https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationproxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6'
};

await client.api('/applications/bf21f7e9-9d25-4da2-82ab-7fdd85049f83/connectorGroup/$ref')
	.version('beta')
	.put(connectorGroup);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ReferenceUpdate;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReferenceUpdate();
$requestBody->setOdataId('https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationproxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6');

$graphServiceClient->applications()->byApplicationId('application-id')->connectorGroup()->ref()->put($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Applications

$params = @{
	"@odata.id" = "https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationproxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6"
}

Set-MgBetaApplicationConnectorGroupByRef -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.reference_update import ReferenceUpdate
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReferenceUpdate(
	odata_id = "https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationproxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6",
)

await graph_client.applications.by_application_id('application-id').connector_group.ref.put(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Step 4: Configure single sign-on \(SSO\)

In this step, you configure the **onPremisesPublishing > singleSignOnSettings** and **onPremisesPublishing > singleSignOnMode** properties for the application.

### Option 1: Configure IWA-based SSO

The following request shows how to configure Integrated Windows Authentication \(IWA\) for the application. The request returns a `204 No content` response.

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [CLI](#tabpanel_8_cli)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
PATCH https://graph.microsoft.com/beta/applications/bf21f7e9-9d25-4da2-82ab-7fdd85049f83
Content-type: appplication/json

{
  "onPremisesPublishing": {
    "singleSignOnSettings": {
      "kerberosSignOnSettings": {
        "kerberosServicePrincipalName": "HTTP/iwademo.contoso.com",
           "kerberosSignOnMappingAttributeType": "userPrincipalName"
      },
      "singleSignOnMode": "onPremisesKerberos"
    }
  } 
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Applications.Item;

var requestBody = new Application
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"onPremisesPublishing" , new 
			{
				SingleSignOnSettings = new 
				{
					KerberosSignOnSettings = new 
					{
						KerberosServicePrincipalName = "HTTP/iwademo.contoso.com",
						KerberosSignOnMappingAttributeType = "userPrincipalName",
					},
					SingleSignOnMode = "onPremisesKerberos",
				},
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Applications["{application-id}"].PatchAs{application-id}PatchResponseAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```bash

// THE CLI IS IN PREVIEW. NON-PRODUCTION USE ONLY
mgc-beta applications patch --application-id {application-id}
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphapplications "github.com/microsoftgraph/msgraph-beta-sdk-go/applications"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)


requestBody := graphapplications.NewApplication()
additionalData := map[string]interface{}{
onPremisesPublishing := graphmodels.New()
singleSignOnSettings := graphmodels.New()
kerberosSignOnSettings := graphmodels.New()
kerberosServicePrincipalName := "HTTP/iwademo.contoso.com"
kerberosSignOnSettings.SetKerberosServicePrincipalName(&kerberosServicePrincipalName) 
kerberosSignOnMappingAttributeType := "userPrincipalName"
kerberosSignOnSettings.SetKerberosSignOnMappingAttributeType(&kerberosSignOnMappingAttributeType) 
	singleSignOnSettings.SetKerberosSignOnSettings(kerberosSignOnSettings)
singleSignOnMode := "onPremisesKerberos"
singleSignOnSettings.SetSingleSignOnMode(&singleSignOnMode) 
	onPremisesPublishing.SetSingleSignOnSettings(singleSignOnSettings)
	requestBody.SetOnPremisesPublishing(onPremisesPublishing)
}
requestBody.SetAdditionalData(additionalData)

graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.applications.item.Application application = new com.microsoft.graph.beta.applications.item.Application();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 onPremisesPublishing = new ();
 singleSignOnSettings = new ();
 kerberosSignOnSettings = new ();
kerberosSignOnSettings.setKerberosServicePrincipalName("HTTP/iwademo.contoso.com");
kerberosSignOnSettings.setKerberosSignOnMappingAttributeType("userPrincipalName");
singleSignOnSettings.setKerberosSignOnSettings(kerberosSignOnSettings);
singleSignOnSettings.setSingleSignOnMode("onPremisesKerberos");
onPremisesPublishing.setSingleSignOnSettings(singleSignOnSettings);
additionalData.put("onPremisesPublishing", onPremisesPublishing);
application.setAdditionalData(additionalData);
graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
  onPremisesPublishing: {
    singleSignOnSettings: {
      kerberosSignOnSettings: {
        kerberosServicePrincipalName: 'HTTP/iwademo.contoso.com',
           kerberosSignOnMappingAttributeType: 'userPrincipalName'
      },
      singleSignOnMode: 'onPremisesKerberos'
    }
  } 
};

await client.api('/applications/bf21f7e9-9d25-4da2-82ab-7fdd85049f83')
	.version('beta')
	.update(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$additionalData = [
	'onPremisesPublishing' => [
		'singleSignOnSettings' => [
			'kerberosSignOnSettings' => [
				'kerberosServicePrincipalName' => 'HTTP/iwademo.contoso.com',
				'kerberosSignOnMappingAttributeType' => 'userPrincipalName',
			],
			'singleSignOnMode' => 'onPremisesKerberos',
		],
	],
];
$requestBody->setAdditionalData($additionalData);

$graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Applications

$applicationId = "bf21f7e9-9d25-4da2-82ab-7fdd85049f83"
$SSOMode = "onPremisesKerberos"
$SPN = "HTTP/iwademo.contoso.com"
$UserNameFormat = "userPrincipalName"
$params = @{
    onPremisesPublishing = @{
        singleSignOnSettings = @{
            singleSignOnMode = $SSOMode
            kerberosSignOnSettings = @ {
            kerberosServicePrincipalName = $SPN 
             kerberosSignOnMappingAttributeType = $UserNameFormat
          }
        }
    }
}
Update-MgBetaApplication -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

from msgraph import GraphServiceClient
from msgraph.generated.models.application import Application

graph_client = GraphServiceClient(credentials, scopes)

request_body = Application(
	additional_data = {
			"on_premises_publishing" : {
					"single_sign_on_settings" : {
							"kerberos_sign_on_settings" : {
									"kerberos_service_principal_name" : "HTTP/iwademo.contoso.com",
									"kerberos_sign_on_mapping_attribute_type" : "userPrincipalName",
							},
							"single_sign_on_mode" : "onPremisesKerberos",
					},
			},
	}
)

await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Option 2: Configure header-based SSO

The following request shows how to configure header-based SSO for the application. In this mode, the value of the **singleSignOnMode** property can be `aadHeaderBased`, `pingHeaderBased`, or `oAuthToken`. The request returns a `204 No content` response.

```http
PATCH https://graph.microsoft.com/beta/applications/bf21f7e9-9d25-4da2-82ab-7fdd85049f83
Content-type: appplication/json

{
  "onPremisesPublishing": {
    "singleSignOnSettings": {
      "kerberosSignOnSettings": {},
      "singleSignOnMode": "aadHeaderBased"
    }
  } 
}
```

## Step 5: Assign a user to the application

You want to assign a user to the application. From the service principal that you created in Step 1, record the ID of the default **User** role that's defined in the **appRoles** property. This value is `18d14569-c3bd-439b-9a66-3a2aee01d14f`.

In the request body, provide the following values:

- **principalId** - The ID of the user account that you created.
- **appRoleId** - The ID of the default `User` app role that you retrieved from the service principal.
- **resourceId** - The ID of the service principal.

### Request

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [CLI](#tabpanel_9_cli)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```http
POST https://graph.microsoft.com/beta/servicePrincipals/a8cac399-cde5-4516-a674-819503c61313/appRoleAssignments
Content-type: application/json

{
  "principalId": "2fe96d23-5dc6-4f35-8222-0426a8c115c8",
  "principalType": "User",
  "appRoleId":"18d14569-c3bd-439b-9a66-3a2aee01d14f",
  "resourceId":"a8cac399-cde5-4516-a674-819503c61313"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.ServicePrincipals.Item.AppRoleAssignments;

var requestBody = new AppRoleAssignmentsPostRequestBody
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"principalId" , "4628e7df-dff3-407c-a08f-75f08c0806dc"
		},
		{
			"principalType" , "User"
		},
		{
			"appRoleId" , "18d14569-c3bd-439b-9a66-3a2aee01d14f"
		},
		{
			"resourceId" , "a8cac399-cde5-4516-a674-819503c61313"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.ServicePrincipals["{servicePrincipal-id}"].AppRoleAssignments.PostAsAppRoleAssignmentsPostResponseAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```bash

// THE CLI IS IN PREVIEW. NON-PRODUCTION USE ONLY
mgc-beta service-principals app-role-assignments create --service-principal-id {servicePrincipal-id}
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-beta-sdk-go/serviceprincipals"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)


requestBody := graphserviceprincipals.NewAppRoleAssignmentsPostRequestBody()
additionalData := map[string]interface{}{
	"principalId" : "4628e7df-dff3-407c-a08f-75f08c0806dc", 
	"principalType" : "User", 
	"appRoleId" : "18d14569-c3bd-439b-9a66-3a2aee01d14f", 
	"resourceId" : "a8cac399-cde5-4516-a674-819503c61313", 
}
requestBody.SetAdditionalData(additionalData)

graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").AppRoleAssignments().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.serviceprincipals.item.approleassignments.AppRoleAssignmentsPostRequestBody appRoleAssignmentsPostRequestBody = new com.microsoft.graph.beta.serviceprincipals.item.approleassignments.AppRoleAssignmentsPostRequestBody();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("principalId", "4628e7df-dff3-407c-a08f-75f08c0806dc");
additionalData.put("principalType", "User");
additionalData.put("appRoleId", "18d14569-c3bd-439b-9a66-3a2aee01d14f");
additionalData.put("resourceId", "a8cac399-cde5-4516-a674-819503c61313");
appRoleAssignmentsPostRequestBody.setAdditionalData(additionalData);
graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").appRoleAssignments().post(appRoleAssignmentsPostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const appRoleAssignment = {
  principalId: '4628e7df-dff3-407c-a08f-75f08c0806dc',
  principalType: 'User',
  appRoleId: '18d14569-c3bd-439b-9a66-3a2aee01d14f',
  resourceId: 'a8cac399-cde5-4516-a674-819503c61313'
};

await client.api('/servicePrincipals/b00c693f-9658-4c06-bd1b-c402c4653dea/appRoleAssignments')
	.version('beta')
	.post(appRoleAssignment);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AppRoleAssignmentsPostRequestBody();
$additionalData = [
	'principalId' => '4628e7df-dff3-407c-a08f-75f08c0806dc',
	'principalType' => 'User',
	'appRoleId' => '18d14569-c3bd-439b-9a66-3a2aee01d14f',
	'resourceId' => 'a8cac399-cde5-4516-a674-819503c61313',
];
$requestBody->setAdditionalData($additionalData);

$graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->appRoleAssignments()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Applications

$userObjectId  = "2fe96d23-5dc6-4f35-8222-0426a8c115c8"

ServicePrincipalObjectId = Get-MgBetaServicePrincipal -Filter "DisplayName eq 'Contoso IWA App'" 

New-MgBetaUserAppRoleAssignment -UserId $userObjectId -PrincipalId $userObjectId -ResourceId $servicePrincipalObjectId.Id -AppRoleId "18d14569-c3bd-439b-9a66-3a2aee01d14f"
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

from msgraph import GraphServiceClient
from msgraph.generated.models.app_role_assignments_post_request_body import AppRoleAssignmentsPostRequestBody

graph_client = GraphServiceClient(credentials, scopes)

request_body = AppRoleAssignmentsPostRequestBody(
	additional_data = {
			"principal_id" : "4628e7df-dff3-407c-a08f-75f08c0806dc",
			"principal_type" : "User",
			"app_role_id" : "18d14569-c3bd-439b-9a66-3a2aee01d14f",
			"resource_id" : "a8cac399-cde5-4516-a674-819503c61313",
	}
)

await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').app_role_assignments.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#appRoleAssignments/$entity",
  "id": "I23pL8ZdNU-CIgQmqMEVyLJ0E6fx0ixEo92az8MnhtU",
  "creationTimestamp": "2020-06-09T00:06:07.5129268Z",
  "appRoleId": "18d14569-c3bd-439b-9a66-3a2aee01d14f",
  "principalDisplayName": "MyTestUser1",
  "principalId": "2fe96d23-5dc6-4f35-8222-0426a8c115c8",
  "principalType": "User",
  "resourceDisplayName": "Contoso IWA App",
  "resourceId": "a8cac399-cde5-4516-a674-819503c61313"
}
```

## Step 6: Test access to the application

Test the application by visiting the **externalUrl** configured for the app on your browser and then sign in with your test user. You should be able to sign into the app and access the application.

## Step 7: Clean up resources

In this step, remove the resources that you created and no longer need.

### Delete the user account

The request returns a `204 No content` response.

- [HTTP](#tabpanel_10_http)
- [C#](#tabpanel_10_csharp)
- [Go](#tabpanel_10_go)
- [Java](#tabpanel_10_java)
- [JavaScript](#tabpanel_10_javascript)
- [PHP](#tabpanel_10_php)
- [PowerShell](#tabpanel_10_powershell)
- [Python](#tabpanel_10_python)

```http
DELETE https://graph.microsoft.com/v1.0/users/4628e7df-dff3-407c-a08f-75f08c0806dc
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].DeleteAsync();
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
graphClient.Users().ByUserId("user-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.users().byUserId("{user-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/users/4628e7df-dff3-407c-a08f-75f08c0806dc')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->users()->byUserId('user-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Remove-MgUser -UserId $userId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.users.by_user_id('user-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Delete the application

When you delete the application, the service principal in your tenant is also deleted. This request returns a `204 No content` response.

- [HTTP](#tabpanel_11_http)
- [C#](#tabpanel_11_csharp)
- [Go](#tabpanel_11_go)
- [Java](#tabpanel_11_java)
- [JavaScript](#tabpanel_11_javascript)
- [PHP](#tabpanel_11_php)
- [PowerShell](#tabpanel_11_powershell)
- [Python](#tabpanel_11_python)

```http
DELETE https://graph.microsoft.com/v1.0/applications/bf21f7e9-9d25-4da2-82ab-7fdd85049f83
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Applications["{application-id}"].DeleteAsync();
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
graphClient.Applications().ByApplicationId("application-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.applications().byApplicationId("{application-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/applications/bf21f7e9-9d25-4da2-82ab-7fdd85049f83')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->applications()->byApplicationId('application-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

Remove-MgApplication -ApplicationId $applicationId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.applications.by_application_id('application-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Delete the connector group

The request returns a `204 No content` response.

- [HTTP](#tabpanel_12_http)
- [C#](#tabpanel_12_csharp)
- [CLI](#tabpanel_12_cli)
- [Go](#tabpanel_12_go)
- [Java](#tabpanel_12_java)
- [JavaScript](#tabpanel_12_javascript)
- [PHP](#tabpanel_12_php)
- [PowerShell](#tabpanel_12_powershell)
- [Python](#tabpanel_12_python)

```http
DELETE https://graph.microsoft.com/beta/onPremisesPublishingProfiles/applicationProxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.OnPremisesPublishingProfiles["{onPremisesPublishingProfile-id}"].ConnectorGroups["{connectorGroup-id}"].DeleteAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```bash

// THE CLI IS IN PREVIEW. NON-PRODUCTION USE ONLY
mgc-beta on-premises-publishing-profiles connector-groups delete --on-premises-publishing-profile-id {onPremisesPublishingProfile-id} --connector-group-id {connectorGroup-id}
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)



graphClient.OnPremisesPublishingProfiles().ByOnPremisesPublishingProfileId("onPremisesPublishingProfile-id").ConnectorGroups().ByConnectorGroupId("connectorGroup-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.onPremisesPublishingProfiles().byOnPremisesPublishingProfileId("{onPremisesPublishingProfile-id}").connectorGroups().byConnectorGroupId("{connectorGroup-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/onPremisesPublishingProfiles/applicationProxy/connectorGroups/3e6f4c35-a04b-4d03-b98a-66fff89b72e6')
	.version('beta')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->onPremisesPublishingProfiles()->byOnPremisesPublishingProfileId('onPremisesPublishingProfile-id')->connectorGroups()->byConnectorGroupId('connectorGroup-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Applications

Remove-MgBetaOnPremisePublishingProfileConnectorGroup -OnPremisesPublishingProfileId $onPremisesPublishingProfileId -ConnectorGroupId $connectorGroupId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

from msgraph import GraphServiceClient

graph_client = GraphServiceClient(credentials, scopes)


await graph_client.on_premises_publishing_profiles.by_on_premises_publishing_profile_id('onPremisesPublishingProfile-id').connector_groups.by_connector_group_id('connectorGroup-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Related content

- [Use Microsoft Entra application proxy to publish on-premises apps for remote users](https://learn.microsoft.com/en-us/entra/identity/app-proxy/overview-what-is-app-proxy).
- [On-premises publishing profiles](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishingprofile-root?view=graph-rest-beta&preserve-view=true).
