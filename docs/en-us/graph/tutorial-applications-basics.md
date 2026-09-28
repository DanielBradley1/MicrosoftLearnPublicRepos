<!-- Source: https://learn.microsoft.com/en-us/graph/tutorial-applications-basics -->
<!-- Sitemap-Last-Modified: 2025-07-04 -->

# Manage Microsoft Entra applications using Microsoft Graph

Microsoft Entra applications enable secure access to resources in the Microsoft cloud. Microsoft Graph provides a unified API endpoint that lets you programmatically create, configure, and manage these applications and their associated service principals. This article shows you how for automating common app management tasks with Microsoft Graph, including registering apps, updating properties, assigning permissions, and managing credentials.

## Prerequisites

- To test the API operations, sign in to [Graph Explorer](https://aka.ms/ge) with an account that lets you create and manage applications in your tenant.

## Register an application with Microsoft Entra ID

Create an app by specifying the required **displayName** property. The request uses default values for other properties.

Least privileged delegated permission: `Application.ReadWrite.All`.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
POST https://graph.microsoft.com/v1.0/applications
Content-type: application/json

{
  "displayName": "My application"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Application
{
	DisplayName = "My application",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications.PostAsync(requestBody);
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
displayName := "My application"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
application.setDisplayName("My application");
Application result = graphClient.applications().post(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
  displayName: 'My application'
};

await client.api('/applications')
	.post(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Application;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$requestBody->setDisplayName('My application');

$result = $graphServiceClient->applications()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	displayName = "My application"
}

New-MgApplication -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.application import Application
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	display_name = "My application",
)

result = await graph_client.applications.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The request returns a `201 Created` response with the application object in the response body. The application gets an **id** that's unique for apps in the tenant, and an **appId** that's globally unique in the Microsoft Entra ID ecosystem.

## Create a service principal for an application

Least privileged delegated permission: `Application.ReadWrite.All`.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals
Content-type: application/json

{
  "appId": "fc876dd1-6bcb-4304-b9b6-18ddf1526b62"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ServicePrincipal
{
	AppId = "fc876dd1-6bcb-4304-b9b6-18ddf1526b62",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals.PostAsync(requestBody);
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

requestBody := graphmodels.NewServicePrincipal()
appId := "fc876dd1-6bcb-4304-b9b6-18ddf1526b62"
requestBody.SetAppId(&appId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
servicePrincipals, err := graphClient.ServicePrincipals().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ServicePrincipal servicePrincipal = new ServicePrincipal();
servicePrincipal.setAppId("fc876dd1-6bcb-4304-b9b6-18ddf1526b62");
ServicePrincipal result = graphClient.servicePrincipals().post(servicePrincipal);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const servicePrincipal = {
  appId: 'fc876dd1-6bcb-4304-b9b6-18ddf1526b62'
};

await client.api('/servicePrincipals')
	.post(servicePrincipal);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ServicePrincipal;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ServicePrincipal();
$requestBody->setAppId('fc876dd1-6bcb-4304-b9b6-18ddf1526b62');

$result = $graphServiceClient->servicePrincipals()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	appId = "fc876dd1-6bcb-4304-b9b6-18ddf1526b62"
}

New-MgServicePrincipal -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.service_principal import ServicePrincipal
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ServicePrincipal(
	app_id = "fc876dd1-6bcb-4304-b9b6-18ddf1526b62",
)

result = await graph_client.service_principals.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The request returns a `201 Created` response that includes the service principal object in the response body.

## Addressing an application or a service principal object

Reference an application or a service principal by its ID. This syntax supports the GET, PATCH, and DELETE HTTP methods.

```http
https://graph.microsoft.com/v1.0/applications/{applicationObjectId}
https://graph.microsoft.com/v1.0/servicePrincipals/{servicePrincipalObjectId}
```

Reference an application or a service principal by its `appId`. This syntax supports the GET, PATCH, and DELETE HTTP methods.

```http
https://graph.microsoft.com/v1.0/applications(appId='appId')
https://graph.microsoft.com/v1.0/servicePrincipals(appId='appId')
```

Address an application object by its **uniqueName** using the PATCH method. Use this property to create an application with the unique name if it doesn't exist, or update it if it exists. This operation is called *Upsert*.

```http
PATCH https://graph.microsoft.com/v1.0/applications(uniqueName='{uniqueName}')
Content-Type: application/json
Prefer: create-if-missing

{
  "displayName": "Display name"
}
```

## Configure other basic properties for your app

Least privileged delegated permission: `Application.ReadWrite.All`.

Set up these basic properties for your app:

- Add tags for categorization \(use `HideApp` to hide the app from My Apps and the Microsoft 365 Launcher\)
- Add a logo, terms of service, and privacy statement
- Store contact information

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
PATCH https://graph.microsoft.com/v1.0/applications/0d0021e2-eaab-4b9f-a5ad-38c55337d63e/
Content-type: application/json

{
  "tags": [
      "HR",
      "Payroll",
      "HideApp"
  ],
  "info": {
      "logoUrl": "https://cdn.contoso.com/photo/2016/03/21/23/25/link-1271843_1280.png",
      "marketingUrl": "https://www.contoso.com/app/marketing",
      "privacyStatementUrl": "https://www.contoso.com/app/privacy",
      "supportUrl": "https://www.contoso.com/app/support",
      "termsOfServiceUrl": "https://www.contoso.com/app/termsofservice"
  },
  "web": {
      "homePageUrl": "https://www.contoso.com/",
      "logoutUrl": "https://www.contoso.com/frontchannel_logout",
      "redirectUris": [
          "https://localhost"
      ]
  },
  "serviceManagementReference": "Owners aliases: Finance @ contosofinance@contoso.com; The Phone Company HR consulting @ hronsite@thephone-company.com;"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Application
{
	Tags = new List<string>
	{
		"HR",
		"Payroll",
		"HideApp",
	},
	Info = new InformationalUrl
	{
		LogoUrl = "https://cdn.contoso.com/photo/2016/03/21/23/25/link-1271843_1280.png",
		MarketingUrl = "https://www.contoso.com/app/marketing",
		PrivacyStatementUrl = "https://www.contoso.com/app/privacy",
		SupportUrl = "https://www.contoso.com/app/support",
		TermsOfServiceUrl = "https://www.contoso.com/app/termsofservice",
	},
	Web = new WebApplication
	{
		HomePageUrl = "https://www.contoso.com/",
		LogoutUrl = "https://www.contoso.com/frontchannel_logout",
		RedirectUris = new List<string>
		{
			"https://localhost",
		},
	},
	ServiceManagementReference = "Owners aliases: Finance @ contosofinance@contoso.com; The Phone Company HR consulting @ hronsite@thephone-company.com;",
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
tags := []string {
	"HR",
	"Payroll",
	"HideApp",
}
requestBody.SetTags(tags)
info := graphmodels.NewInformationalUrl()
logoUrl := "https://cdn.contoso.com/photo/2016/03/21/23/25/link-1271843_1280.png"
info.SetLogoUrl(&logoUrl) 
marketingUrl := "https://www.contoso.com/app/marketing"
info.SetMarketingUrl(&marketingUrl) 
privacyStatementUrl := "https://www.contoso.com/app/privacy"
info.SetPrivacyStatementUrl(&privacyStatementUrl) 
supportUrl := "https://www.contoso.com/app/support"
info.SetSupportUrl(&supportUrl) 
termsOfServiceUrl := "https://www.contoso.com/app/termsofservice"
info.SetTermsOfServiceUrl(&termsOfServiceUrl) 
requestBody.SetInfo(info)
web := graphmodels.NewWebApplication()
homePageUrl := "https://www.contoso.com/"
web.SetHomePageUrl(&homePageUrl) 
logoutUrl := "https://www.contoso.com/frontchannel_logout"
web.SetLogoutUrl(&logoutUrl) 
redirectUris := []string {
	"https://localhost",
}
web.SetRedirectUris(redirectUris)
requestBody.SetWeb(web)
serviceManagementReference := "Owners aliases: Finance @ contosofinance@contoso.com; The Phone Company HR consulting @ hronsite@thephone-company.com;"
requestBody.SetServiceManagementReference(&serviceManagementReference) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
LinkedList<String> tags = new LinkedList<String>();
tags.add("HR");
tags.add("Payroll");
tags.add("HideApp");
application.setTags(tags);
InformationalUrl info = new InformationalUrl();
info.setLogoUrl("https://cdn.contoso.com/photo/2016/03/21/23/25/link-1271843_1280.png");
info.setMarketingUrl("https://www.contoso.com/app/marketing");
info.setPrivacyStatementUrl("https://www.contoso.com/app/privacy");
info.setSupportUrl("https://www.contoso.com/app/support");
info.setTermsOfServiceUrl("https://www.contoso.com/app/termsofservice");
application.setInfo(info);
WebApplication web = new WebApplication();
web.setHomePageUrl("https://www.contoso.com/");
web.setLogoutUrl("https://www.contoso.com/frontchannel_logout");
LinkedList<String> redirectUris = new LinkedList<String>();
redirectUris.add("https://localhost");
web.setRedirectUris(redirectUris);
application.setWeb(web);
application.setServiceManagementReference("Owners aliases: Finance @ contosofinance@contoso.com; The Phone Company HR consulting @ hronsite@thephone-company.com;");
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
  tags: [
      'HR',
      'Payroll',
      'HideApp'
  ],
  info: {
      logoUrl: 'https://cdn.contoso.com/photo/2016/03/21/23/25/link-1271843_1280.png',
      marketingUrl: 'https://www.contoso.com/app/marketing',
      privacyStatementUrl: 'https://www.contoso.com/app/privacy',
      supportUrl: 'https://www.contoso.com/app/support',
      termsOfServiceUrl: 'https://www.contoso.com/app/termsofservice'
  },
  web: {
      homePageUrl: 'https://www.contoso.com/',
      logoutUrl: 'https://www.contoso.com/frontchannel_logout',
      redirectUris: [
          'https://localhost'
      ]
  },
  serviceManagementReference: 'Owners aliases: Finance @ contosofinance@contoso.com; The Phone Company HR consulting @ hronsite@thephone-company.com;'
};

await client.api('/applications/0d0021e2-eaab-4b9f-a5ad-38c55337d63e/')
	.update(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Application;
use Microsoft\Graph\Generated\Models\InformationalUrl;
use Microsoft\Graph\Generated\Models\WebApplication;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$requestBody->setTags(['HR', 'Payroll', 'HideApp', 	]);
$info = new InformationalUrl();
$info->setLogoUrl('https://cdn.contoso.com/photo/2016/03/21/23/25/link-1271843_1280.png');
$info->setMarketingUrl('https://www.contoso.com/app/marketing');
$info->setPrivacyStatementUrl('https://www.contoso.com/app/privacy');
$info->setSupportUrl('https://www.contoso.com/app/support');
$info->setTermsOfServiceUrl('https://www.contoso.com/app/termsofservice');
$requestBody->setInfo($info);
$web = new WebApplication();
$web->setHomePageUrl('https://www.contoso.com/');
$web->setLogoutUrl('https://www.contoso.com/frontchannel_logout');
$web->setRedirectUris(['https://localhost', 	]);
$requestBody->setWeb($web);
$requestBody->setServiceManagementReference('Owners aliases: Finance @ contosofinance@contoso.com; The Phone Company HR consulting @ hronsite@thephone-company.com;');

$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	tags = @(
	"HR"
"Payroll"
"HideApp"
)
info = @{
logoUrl = "https://cdn.contoso.com/photo/2016/03/21/23/25/link-1271843_1280.png"
marketingUrl = "https://www.contoso.com/app/marketing"
privacyStatementUrl = "https://www.contoso.com/app/privacy"
supportUrl = "https://www.contoso.com/app/support"
termsOfServiceUrl = "https://www.contoso.com/app/termsofservice"
}
web = @{
homePageUrl = "https://www.contoso.com/"
logoutUrl = "https://www.contoso.com/frontchannel_logout"
redirectUris = @(
"https://localhost"
)
}
serviceManagementReference = "Owners aliases: Finance @ contosofinance@contoso.com; The Phone Company HR consulting @ hronsite@thephone-company.com;"
}

Update-MgApplication -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.application import Application
from msgraph.generated.models.informational_url import InformationalUrl
from msgraph.generated.models.web_application import WebApplication
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	tags = [
		"HR",
		"Payroll",
		"HideApp",
	],
	info = InformationalUrl(
		logo_url = "https://cdn.contoso.com/photo/2016/03/21/23/25/link-1271843_1280.png",
		marketing_url = "https://www.contoso.com/app/marketing",
		privacy_statement_url = "https://www.contoso.com/app/privacy",
		support_url = "https://www.contoso.com/app/support",
		terms_of_service_url = "https://www.contoso.com/app/termsofservice",
	),
	web = WebApplication(
		home_page_url = "https://www.contoso.com/",
		logout_url = "https://www.contoso.com/frontchannel_logout",
		redirect_uris = [
			"https://localhost",
		],
	),
	service_management_reference = "Owners aliases: Finance @ contosofinance@contoso.com; The Phone Company HR consulting @ hronsite@thephone-company.com;",
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Restrict sign-in to only users assigned all roles on the app.

Least privileged delegated permission: `Application.ReadWrite.All`.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
PATCH https://graph.microsoft.com/v1.0/servicePrincipals/89473e09-0737-41a1-a0c3-1418d6908bcd

{
    "appRoleAssignmentRequired": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ServicePrincipal
{
	AppRoleAssignmentRequired = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewServicePrincipal()
appRoleAssignmentRequired := true
requestBody.SetAppRoleAssignmentRequired(&appRoleAssignmentRequired) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
servicePrincipals, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ServicePrincipal servicePrincipal = new ServicePrincipal();
servicePrincipal.setAppRoleAssignmentRequired(true);
ServicePrincipal result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").patch(servicePrincipal);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const servicePrincipal = {
    appRoleAssignmentRequired: true
};

await client.api('/servicePrincipals/89473e09-0737-41a1-a0c3-1418d6908bcd')
	.update(servicePrincipal);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ServicePrincipal;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ServicePrincipal();
$requestBody->setAppRoleAssignmentRequired(true);

$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	appRoleAssignmentRequired = $true
}

Update-MgServicePrincipal -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.service_principal import ServicePrincipal
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ServicePrincipal(
	app_role_assignment_required = True,
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Assign permissions to an app

Assign permissions through Microsoft Graph by updating the **requiredResourceAccess** property of the app object. This method is a programmatic alternative to using the Microsoft Entra admin center. Include both existing and new permissions to avoid removing permissions that are assigned but not granted.

*Assigning* permissions doesn't *grant* them. Grant admin consent in the Microsoft Entra admin center or [programmatically using Microsoft Graph APIs](https://learn.microsoft.com/en-us/graph/permissions-grant-via-msgraph).

Least privileged delegated permission: `Application.ReadWrite.All`.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
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

## Create app roles

### Create app roles on an application object

To add or update app roles, include all existing roles in your request. If you omit existing roles, they're removed.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
PATCH https://graph.microsoft.com/v1.0/applications/bbd46130-e957-4c38-a116-d4d02afd1057
Content-Type: application/json

{
  "appRoles": [
    {
      "allowedMemberTypes": [
          "User",
          "Application"
      ],
      "description": "Survey.Read",
      "displayName": "Survey.Read",
      "id": "7a9ddfc4-cc8a-48ea-8275-8ecbffffd5a0",
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
			Id = Guid.Parse("7a9ddfc4-cc8a-48ea-8275-8ecbffffd5a0"),
			IsEnabled = false,
			Origin = "Application",
			Value = "Survey.Read",
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
id := uuid.MustParse("7a9ddfc4-cc8a-48ea-8275-8ecbffffd5a0")
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

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
appRole.setId(UUID.fromString("7a9ddfc4-cc8a-48ea-8275-8ecbffffd5a0"));
appRole.setIsEnabled(false);
appRole.setOrigin("Application");
appRole.setValue("Survey.Read");
appRoles.add(appRole);
application.setAppRoles(appRoles);
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
      id: '7a9ddfc4-cc8a-48ea-8275-8ecbffffd5a0',
      isEnabled: false,
      origin: 'Application',
      value: 'Survey.Read'
    }
  ]
};

await client.api('/applications/bbd46130-e957-4c38-a116-d4d02afd1057')
	.update(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
$appRolesAppRole1->setId('7a9ddfc4-cc8a-48ea-8275-8ecbffffd5a0');
$appRolesAppRole1->setIsEnabled(false);
$appRolesAppRole1->setOrigin('Application');
$appRolesAppRole1->setValue('Survey.Read');
$appRolesArray []= $appRolesAppRole1;
$requestBody->setAppRoles($appRolesArray);


$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
	id = "7a9ddfc4-cc8a-48ea-8275-8ecbffffd5a0"
	isEnabled = $false
	origin = "Application"
	value = "Survey.Read"
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
			id = UUID("7a9ddfc4-cc8a-48ea-8275-8ecbffffd5a0"),
			is_enabled = False,
			origin = "Application",
			value = "Survey.Read",
		),
	],
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Manage owners

### Identify ownerless service principals or those with only one owner

Least privileged delegated permission: `Application.ReadWrite.All`.

This request requires the **ConsistencyLevel** header set to `eventual` because `$count` is in the request. For more information about the use of **ConsistencyLevel** and `$count`, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

This request also returns the count of the apps that match the filter condition.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```msgraph
GET https://graph.microsoft.com/v1.0/servicePrincipals?$filter=owners/$count eq 0 or owners/$count eq 1&$count=true
ConsistencyLevel: eventual
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "owners/$count eq 0 or owners/$count eq 1";
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.Headers.Add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-sdk-go/serviceprincipals"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("ConsistencyLevel", "eventual")


requestFilter := "owners/$count eq 0 or owners/$count eq 1"
requestCount := true

requestParameters := &graphserviceprincipals.ServicePrincipalsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Count: &requestCount,
}
configuration := &graphserviceprincipals.ServicePrincipalsRequestBuilderGetRequestConfiguration{
	Headers: headers,
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
	requestConfiguration.queryParameters.filter = "owners/$count eq 0 or owners/$count eq 1";
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.headers.add("ConsistencyLevel", "eventual");
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let servicePrincipals = await client.api('/servicePrincipals')
	.header('ConsistencyLevel','eventual')
	.filter('owners/$count eq 0 or owners/$count eq 1')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ServicePrincipals\ServicePrincipalsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ServicePrincipalsRequestBuilderGetRequestConfiguration();
$headers = [
		'ConsistencyLevel' => 'eventual',
	];
$requestConfiguration->headers = $headers;

$queryParameters = ServicePrincipalsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "owners/\$count eq 0 or owners/\$count eq 1";
$queryParameters->count = true;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->servicePrincipals()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgServicePrincipal -Filter "owners/`$count eq 0 or owners/`$count eq 1" -CountVariable CountVar  -ConsistencyLevel eventual 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.service_principals.service_principals_request_builder import ServicePrincipalsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ServicePrincipalsRequestBuilder.ServicePrincipalsRequestBuilderGetQueryParameters(
		filter = "owners/$count eq 0 or owners/$count eq 1",
		count = True,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("ConsistencyLevel", "eventual")


result = await graph_client.service_principals.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Assign an owner to an app

Least privileged delegated permission: `Application.ReadWrite.All`.

In the following request, `8afc02cb-4d62-4dba-b536-9f6d73e9be26` is the object ID for a user or service principal.

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
POST https://graph.microsoft.com/v1.0/applications/7b45cf6d-9083-4eb2-92c4-a7e090f1fc40/owners/$ref
Content-Type: application/json

{
    "@odata.id": "https://graph.microsoft.com/v1.0/directoryObjects/8afc02cb-4d62-4dba-b536-9f6d73e9be26"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ReferenceCreate
{
	OdataId = "https://graph.microsoft.com/v1.0/directoryObjects/8afc02cb-4d62-4dba-b536-9f6d73e9be26",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Applications["{application-id}"].Owners.Ref.PostAsync(requestBody);
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

requestBody := graphmodels.NewReferenceCreate()
odataId := "https://graph.microsoft.com/v1.0/directoryObjects/8afc02cb-4d62-4dba-b536-9f6d73e9be26"
requestBody.SetOdataId(&odataId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Applications().ByApplicationId("application-id").Owners().Ref().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.ReferenceCreate referenceCreate = new com.microsoft.graph.models.ReferenceCreate();
referenceCreate.setOdataId("https://graph.microsoft.com/v1.0/directoryObjects/8afc02cb-4d62-4dba-b536-9f6d73e9be26");
graphClient.applications().byApplicationId("{application-id}").owners().ref().post(referenceCreate);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const directoryObject = {
    '@odata.id': 'https://graph.microsoft.com/v1.0/directoryObjects/8afc02cb-4d62-4dba-b536-9f6d73e9be26'
};

await client.api('/applications/7b45cf6d-9083-4eb2-92c4-a7e090f1fc40/owners/$ref')
	.post(directoryObject);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ReferenceCreate;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReferenceCreate();
$requestBody->setOdataId('https://graph.microsoft.com/v1.0/directoryObjects/8afc02cb-4d62-4dba-b536-9f6d73e9be26');

$graphServiceClient->applications()->byApplicationId('application-id')->owners()->ref()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	"@odata.id" = "https://graph.microsoft.com/v1.0/directoryObjects/8afc02cb-4d62-4dba-b536-9f6d73e9be26"
}

New-MgApplicationOwnerByRef -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.reference_create import ReferenceCreate
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReferenceCreate(
	odata_id = "https://graph.microsoft.com/v1.0/directoryObjects/8afc02cb-4d62-4dba-b536-9f6d73e9be26",
)

await graph_client.applications.by_application_id('application-id').owners.ref.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Assign an owner to a service principal

Least privileged delegated permission: `Application.ReadWrite.All`.

The following request references the service principal using its **appId**. You can alternatively reference it using the object ID in the pattern `../servicePrincipals/{object ID}/owners/$ref`. `dddddddd-9999-0000-1111-eeeeeeeeeeee` is the object ID for a user or service principal.

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals(appId='00001111-aaaa-2222-bbbb-3333cccc4444')/owners/$ref
Content-Type: application/json

{
    "@odata.id": "https://graph.microsoft.com/v1.0/directoryObjects/dddddddd-9999-0000-1111-eeeeeeeeeeee"
}
```

## Lock sensitive properties for service principals

Use the app instance lock feature to protect sensitive properties of service principals from unauthorized changes. Yo can lock the following properties:

- **keyCredentials** where the usage type is `Sign` or `Verify`.
- **passwordCredentials** where the usage type is `Sign` or `Verify`.
- **tokenEncryptionKeyId** property.

You manage the app instance lock feature through the **servicePrincipalLockConfiguration** property of the [application](https://learn.microsoft.com/en-us/graph/api/resources/application) object of the multitenant app.

#### To lock all sensitive properties of a service principal

When **isEnabled** and **allProperties** is set to `true`, even if other properties of the servicePrincipalLockConfiguration object are `null`, then all sensitive properties of the service principal are locked.

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```http
PATCH https://graph.microsoft.com/beta/applications/a0b7f39e-3139-48aa-9397-f46fb63102f7

{
    "servicePrincipalLockConfiguration": {
        "isEnabled": true,
        "allProperties": true
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new Application
{
	ServicePrincipalLockConfiguration = new ServicePrincipalLockConfiguration
	{
		IsEnabled = true,
		AllProperties = true,
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
servicePrincipalLockConfiguration := graphmodels.NewServicePrincipalLockConfiguration()
isEnabled := true
servicePrincipalLockConfiguration.SetIsEnabled(&isEnabled) 
allProperties := true
servicePrincipalLockConfiguration.SetAllProperties(&allProperties) 
requestBody.SetServicePrincipalLockConfiguration(servicePrincipalLockConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
ServicePrincipalLockConfiguration servicePrincipalLockConfiguration = new ServicePrincipalLockConfiguration();
servicePrincipalLockConfiguration.setIsEnabled(true);
servicePrincipalLockConfiguration.setAllProperties(true);
application.setServicePrincipalLockConfiguration(servicePrincipalLockConfiguration);
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
    servicePrincipalLockConfiguration: {
        isEnabled: true,
        allProperties: true
    }
};

await client.api('/applications/a0b7f39e-3139-48aa-9397-f46fb63102f7')
	.version('beta')
	.update(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Application;
use Microsoft\Graph\Beta\Generated\Models\ServicePrincipalLockConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$servicePrincipalLockConfiguration = new ServicePrincipalLockConfiguration();
$servicePrincipalLockConfiguration->setIsEnabled(true);
$servicePrincipalLockConfiguration->setAllProperties(true);
$requestBody->setServicePrincipalLockConfiguration($servicePrincipalLockConfiguration);

$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Applications

$params = @{
	servicePrincipalLockConfiguration = @{
		isEnabled = $true
		allProperties = $true
	}
}

Update-MgBetaApplication -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.application import Application
from msgraph_beta.generated.models.service_principal_lock_configuration import ServicePrincipalLockConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	service_principal_lock_configuration = ServicePrincipalLockConfiguration(
		is_enabled = True,
		all_properties = True,
	),
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### To lock specific sensitive properties of a service principal

The following example locks the **keyCredentials** and **passwordCredentials** properties of the service principal and enables the app instance lock feature.

- [HTTP](#tabpanel_10_http)
- [C#](#tabpanel_10_csharp)
- [Go](#tabpanel_10_go)
- [Java](#tabpanel_10_java)
- [JavaScript](#tabpanel_10_javascript)
- [PHP](#tabpanel_10_php)
- [PowerShell](#tabpanel_10_powershell)
- [Python](#tabpanel_10_python)

```http
PATCH https://graph.microsoft.com/beta/applications/a0b7f39e-3139-48aa-9397-f46fb63102f7

{
    "servicePrincipalLockConfiguration": {
        "isEnabled": true,
        "credentialsWithUsageSign": true,
        "credentialsWithUsageVerify": true
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new Application
{
	ServicePrincipalLockConfiguration = new ServicePrincipalLockConfiguration
	{
		IsEnabled = true,
		CredentialsWithUsageSign = true,
		CredentialsWithUsageVerify = true,
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
servicePrincipalLockConfiguration := graphmodels.NewServicePrincipalLockConfiguration()
isEnabled := true
servicePrincipalLockConfiguration.SetIsEnabled(&isEnabled) 
credentialsWithUsageSign := true
servicePrincipalLockConfiguration.SetCredentialsWithUsageSign(&credentialsWithUsageSign) 
credentialsWithUsageVerify := true
servicePrincipalLockConfiguration.SetCredentialsWithUsageVerify(&credentialsWithUsageVerify) 
requestBody.SetServicePrincipalLockConfiguration(servicePrincipalLockConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
ServicePrincipalLockConfiguration servicePrincipalLockConfiguration = new ServicePrincipalLockConfiguration();
servicePrincipalLockConfiguration.setIsEnabled(true);
servicePrincipalLockConfiguration.setCredentialsWithUsageSign(true);
servicePrincipalLockConfiguration.setCredentialsWithUsageVerify(true);
application.setServicePrincipalLockConfiguration(servicePrincipalLockConfiguration);
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
    servicePrincipalLockConfiguration: {
        isEnabled: true,
        credentialsWithUsageSign: true,
        credentialsWithUsageVerify: true
    }
};

await client.api('/applications/a0b7f39e-3139-48aa-9397-f46fb63102f7')
	.version('beta')
	.update(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Application;
use Microsoft\Graph\Beta\Generated\Models\ServicePrincipalLockConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$servicePrincipalLockConfiguration = new ServicePrincipalLockConfiguration();
$servicePrincipalLockConfiguration->setIsEnabled(true);
$servicePrincipalLockConfiguration->setCredentialsWithUsageSign(true);
$servicePrincipalLockConfiguration->setCredentialsWithUsageVerify(true);
$requestBody->setServicePrincipalLockConfiguration($servicePrincipalLockConfiguration);

$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Applications

$params = @{
	servicePrincipalLockConfiguration = @{
		isEnabled = $true
		credentialsWithUsageSign = $true
		credentialsWithUsageVerify = $true
	}
}

Update-MgBetaApplication -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.application import Application
from msgraph_beta.generated.models.service_principal_lock_configuration import ServicePrincipalLockConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	service_principal_lock_configuration = ServicePrincipalLockConfiguration(
		is_enabled = True,
		credentials_with_usage_sign = True,
		credentials_with_usage_verify = True,
	),
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Configure trusted certificate authorities for apps

You can restrict certificate credential usage for apps in your tenant to only the certificates issued by trusted certificate authorities. This policy is enforced when you add a certificate to an app and doesn't affect existing certificates unless they're rotated. When an app tries to rotate its certificate credentials, it goes through the policy evaluation to ensure the credentials being added comply with the trusted certificate authority restriction.

### Step 1: Create a certificate chain of trust

Least privileged delegated permission: `AppCertTrustConfiguration.Read.All` Least privileged Microsoft Entra role: `Application Administrator`

- [HTTP](#tabpanel_11_http)
- [C#](#tabpanel_11_csharp)
- [Go](#tabpanel_11_go)
- [Java](#tabpanel_11_java)
- [JavaScript](#tabpanel_11_javascript)
- [PHP](#tabpanel_11_php)
- [PowerShell](#tabpanel_11_powershell)
- [Python](#tabpanel_11_python)

```http
POST https://graph.microsoft.com/beta/certificateAuthorities/certificateBasedApplicationConfigurations

{
    "displayName": "Trusted Certificate Chain of Trust for Contoso",
    "description": "The Trusted Certificate Chain of Trust containing a certificate chain used by app policy, to only allow application certificates from selected issuer.",
    "trustedCertificateAuthorities": [
        {
            "isRootAuthority": true,
            "certificate": "MIIFVjCCAz6gAwIBAgIQJdrL...UyNDIyNTcwM1owPDE …="
        },
        {
            "isRootAuthority": false,
            "certificate": QAAAAAAWjABAQsFADA8M...UyNDIyNTcwM1o …="
        }
    ]
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

const certificateBasedApplicationConfiguration = {
    displayName: 'Trusted Certificate Chain of Trust for Contoso',
    description: 'The Trusted Certificate Chain of Trust containing a certificate chain used by app policy, to only allow application certificates from selected issuer.',
    trustedCertificateAuthorities: [
        {
            isRootAuthority: true,
            certificate: 'MIIFVjCCAz6gAwIBAgIQJdrL...UyNDIyNTcwM1owPDE …='
        },
        {
            isRootAuthority: false,
            certificate: QAAAAAAWjABAQsFADA8M...UyNDIyNTcwM1o …="
        }
    ]
};

await client.api('/certificateAuthorities/certificateBasedApplicationConfigurations')
	.version('beta')
	.post(certificateBasedApplicationConfiguration);
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

The request returns a `200 OK` response object. The response includes the ID of the certificate chain of trust object. Assume that the ID is `eec5ba11-2fc0-4113-83a2-ed986ed13743` used in Step 2.

### Step 2: Assign the certificate chain of trust to an application management policy

The following sample sets up a policy to ensure that only certificates issued by the intermediate certificate authority defined in the previous step can be added to apps in the tenant. The **applicationRestrictions** > **keyCredentials** object defines a **restrictionType** with the value `trustedCertificateAuthority`, which references the ID that was created. Because this policy is applied to the default tenant-level app management policy, it's enforced for all apps created in the tenant and rejects attempts to add noncompliant certificates as part of an app's certificate credentials.

This policy ensures that only certificates from the specified intermediate certificate authority can be added to apps. The **applicationRestrictions** > **keyCredentials** object sets a **restrictionType** to `trustedCertificateAuthority`, referencing the created ID. This policy applies to all apps in the tenant, rejecting any noncompliant certificates.

Least privileged delegated permission: `Policy.Read.ApplicationConfiguration` Least privileged Microsoft Entra role: `Security Administrator`

- [HTTP](#tabpanel_12_http)
- [C#](#tabpanel_12_csharp)
- [Go](#tabpanel_12_go)
- [Java](#tabpanel_12_java)
- [JavaScript](#tabpanel_12_javascript)
- [PHP](#tabpanel_12_php)
- [PowerShell](#tabpanel_12_powershell)
- [Python](#tabpanel_12_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/defaultAppManagementPolicy

{
  "id": "d015220e-9789-4e8e-bbcc-270fe419229d",
  "description": "Lorem ipsum",
  "displayName": "Credential management policy",
  "isEnabled": true,
  "applicationRestrictions": {
    "passwordCredentials": [
      {
        "restrictionType": "passwordLifetime",
        "maxLifetime": "P14D",
        "restrictForAppsCreatedAfterDateTime": "2020-01-01T07:00:00Z"
      }
    ],
    "keyCredentials": [
      {
        "restrictionType": "certificateLifetime",
        "restrictForAppsCreatedAfterDateTime": "2020-01-01T10:37:00Z",
        "maxLifetime": "P90D"
      },
      {
        "restrictionType": "trustedCertificateAuthority",
        "certificateBasedApplicationConfigurationIds": [
          "eec5ba11-2fc0-4113-83a2-ed986ed13743"
        ],
        "restrictForAppsCreatedAfterDateTime": "2019-10-19T10:37:00Z"
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new TenantAppManagementPolicy
{
	Id = "d015220e-9789-4e8e-bbcc-270fe419229d",
	Description = "Lorem ipsum",
	DisplayName = "Credential management policy",
	IsEnabled = true,
	ApplicationRestrictions = new AppManagementApplicationConfiguration
	{
		PasswordCredentials = new List<PasswordCredentialConfiguration>
		{
			new PasswordCredentialConfiguration
			{
				RestrictionType = AppCredentialRestrictionType.PasswordLifetime,
				MaxLifetime = TimeSpan.Parse("P14D"),
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2020-01-01T07:00:00Z"),
			},
		},
		KeyCredentials = new List<KeyCredentialConfiguration>
		{
			new KeyCredentialConfiguration
			{
				RestrictionType = AppKeyCredentialRestrictionType.AsymmetricKeyLifetime,
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2020-01-01T10:37:00Z"),
				MaxLifetime = TimeSpan.Parse("P90D"),
			},
			new KeyCredentialConfiguration
			{
				RestrictionType = AppKeyCredentialRestrictionType.AsymmetricKeyLifetime,
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2019-10-19T10:37:00Z"),
				AdditionalData = new Dictionary<string, object>
				{
					{
						"certificateBasedApplicationConfigurationIds" , new List<string>
						{
							"eec5ba11-2fc0-4113-83a2-ed986ed13743",
						}
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.DefaultAppManagementPolicy.PatchAsync(requestBody);
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

requestBody := graphmodels.NewTenantAppManagementPolicy()
id := "d015220e-9789-4e8e-bbcc-270fe419229d"
requestBody.SetId(&id) 
description := "Lorem ipsum"
requestBody.SetDescription(&description) 
displayName := "Credential management policy"
requestBody.SetDisplayName(&displayName) 
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
applicationRestrictions := graphmodels.NewAppManagementApplicationConfiguration()


passwordCredentialConfiguration := graphmodels.NewPasswordCredentialConfiguration()
restrictionType := graphmodels.PASSWORDLIFETIME_APPCREDENTIALRESTRICTIONTYPE 
passwordCredentialConfiguration.SetRestrictionType(&restrictionType) 
maxLifetime , err := abstractions.ParseISODuration("P14D")
passwordCredentialConfiguration.SetMaxLifetime(&maxLifetime) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2020-01-01T07:00:00Z")
passwordCredentialConfiguration.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 

passwordCredentials := []graphmodels.PasswordCredentialConfigurationable {
	passwordCredentialConfiguration,
}
applicationRestrictions.SetPasswordCredentials(passwordCredentials)


keyCredentialConfiguration := graphmodels.NewKeyCredentialConfiguration()
restrictionType := graphmodels.CERTIFICATELIFETIME_APPKEYCREDENTIALRESTRICTIONTYPE 
keyCredentialConfiguration.SetRestrictionType(&restrictionType) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2020-01-01T10:37:00Z")
keyCredentialConfiguration.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 
maxLifetime , err := abstractions.ParseISODuration("P90D")
keyCredentialConfiguration.SetMaxLifetime(&maxLifetime) 
keyCredentialConfiguration1 := graphmodels.NewKeyCredentialConfiguration()
restrictionType := graphmodels.TRUSTEDCERTIFICATEAUTHORITY_APPKEYCREDENTIALRESTRICTIONTYPE 
keyCredentialConfiguration1.SetRestrictionType(&restrictionType) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2019-10-19T10:37:00Z")
keyCredentialConfiguration1.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 
additionalData := map[string]interface{}{
	certificateBasedApplicationConfigurationIds := []string {
		"eec5ba11-2fc0-4113-83a2-ed986ed13743",
	}
}
keyCredentialConfiguration1.SetAdditionalData(additionalData)

keyCredentials := []graphmodels.KeyCredentialConfigurationable {
	keyCredentialConfiguration,
	keyCredentialConfiguration1,
}
applicationRestrictions.SetKeyCredentials(keyCredentials)
requestBody.SetApplicationRestrictions(applicationRestrictions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
defaultAppManagementPolicy, err := graphClient.Policies().DefaultAppManagementPolicy().Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TenantAppManagementPolicy tenantAppManagementPolicy = new TenantAppManagementPolicy();
tenantAppManagementPolicy.setId("d015220e-9789-4e8e-bbcc-270fe419229d");
tenantAppManagementPolicy.setDescription("Lorem ipsum");
tenantAppManagementPolicy.setDisplayName("Credential management policy");
tenantAppManagementPolicy.setIsEnabled(true);
AppManagementApplicationConfiguration applicationRestrictions = new AppManagementApplicationConfiguration();
LinkedList<PasswordCredentialConfiguration> passwordCredentials = new LinkedList<PasswordCredentialConfiguration>();
PasswordCredentialConfiguration passwordCredentialConfiguration = new PasswordCredentialConfiguration();
passwordCredentialConfiguration.setRestrictionType(AppCredentialRestrictionType.PasswordLifetime);
PeriodAndDuration maxLifetime = PeriodAndDuration.ofDuration(Duration.parse("P14D"));
passwordCredentialConfiguration.setMaxLifetime(maxLifetime);
OffsetDateTime restrictForAppsCreatedAfterDateTime = OffsetDateTime.parse("2020-01-01T07:00:00Z");
passwordCredentialConfiguration.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime);
passwordCredentials.add(passwordCredentialConfiguration);
applicationRestrictions.setPasswordCredentials(passwordCredentials);
LinkedList<KeyCredentialConfiguration> keyCredentials = new LinkedList<KeyCredentialConfiguration>();
KeyCredentialConfiguration keyCredentialConfiguration = new KeyCredentialConfiguration();
keyCredentialConfiguration.setRestrictionType(AppKeyCredentialRestrictionType.AsymmetricKeyLifetime);
OffsetDateTime restrictForAppsCreatedAfterDateTime1 = OffsetDateTime.parse("2020-01-01T10:37:00Z");
keyCredentialConfiguration.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime1);
PeriodAndDuration maxLifetime1 = PeriodAndDuration.ofDuration(Duration.parse("P90D"));
keyCredentialConfiguration.setMaxLifetime(maxLifetime1);
keyCredentials.add(keyCredentialConfiguration);
KeyCredentialConfiguration keyCredentialConfiguration1 = new KeyCredentialConfiguration();
keyCredentialConfiguration1.setRestrictionType(AppKeyCredentialRestrictionType.AsymmetricKeyLifetime);
OffsetDateTime restrictForAppsCreatedAfterDateTime2 = OffsetDateTime.parse("2019-10-19T10:37:00Z");
keyCredentialConfiguration1.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime2);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<String> certificateBasedApplicationConfigurationIds = new LinkedList<String>();
certificateBasedApplicationConfigurationIds.add("eec5ba11-2fc0-4113-83a2-ed986ed13743");
additionalData.put("certificateBasedApplicationConfigurationIds", certificateBasedApplicationConfigurationIds);
keyCredentialConfiguration1.setAdditionalData(additionalData);
keyCredentials.add(keyCredentialConfiguration1);
applicationRestrictions.setKeyCredentials(keyCredentials);
tenantAppManagementPolicy.setApplicationRestrictions(applicationRestrictions);
TenantAppManagementPolicy result = graphClient.policies().defaultAppManagementPolicy().patch(tenantAppManagementPolicy);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const tenantAppManagementPolicy = {
  id: 'd015220e-9789-4e8e-bbcc-270fe419229d',
  description: 'Lorem ipsum',
  displayName: 'Credential management policy',
  isEnabled: true,
  applicationRestrictions: {
    passwordCredentials: [
      {
        restrictionType: 'passwordLifetime',
        maxLifetime: 'P14D',
        restrictForAppsCreatedAfterDateTime: '2020-01-01T07:00:00Z'
      }
    ],
    keyCredentials: [
      {
        restrictionType: 'certificateLifetime',
        restrictForAppsCreatedAfterDateTime: '2020-01-01T10:37:00Z',
        maxLifetime: 'P90D'
      },
      {
        restrictionType: 'trustedCertificateAuthority',
        certificateBasedApplicationConfigurationIds: [
          'eec5ba11-2fc0-4113-83a2-ed986ed13743'
        ],
        restrictForAppsCreatedAfterDateTime: '2019-10-19T10:37:00Z'
      }
    ]
  }
};

await client.api('/policies/defaultAppManagementPolicy')
	.update(tenantAppManagementPolicy);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TenantAppManagementPolicy;
use Microsoft\Graph\Generated\Models\AppManagementApplicationConfiguration;
use Microsoft\Graph\Generated\Models\PasswordCredentialConfiguration;
use Microsoft\Graph\Generated\Models\AppCredentialRestrictionType;
use Microsoft\Graph\Generated\Models\KeyCredentialConfiguration;
use Microsoft\Graph\Generated\Models\AppKeyCredentialRestrictionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TenantAppManagementPolicy();
$requestBody->setId('d015220e-9789-4e8e-bbcc-270fe419229d');
$requestBody->setDescription('Lorem ipsum');
$requestBody->setDisplayName('Credential management policy');
$requestBody->setIsEnabled(true);
$applicationRestrictions = new AppManagementApplicationConfiguration();
$passwordCredentialsPasswordCredentialConfiguration1 = new PasswordCredentialConfiguration();
$passwordCredentialsPasswordCredentialConfiguration1->setRestrictionType(new AppCredentialRestrictionType('passwordLifetime'));
$passwordCredentialsPasswordCredentialConfiguration1->setMaxLifetime(new \DateInterval('P14D'));
$passwordCredentialsPasswordCredentialConfiguration1->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2020-01-01T07:00:00Z'));
$passwordCredentialsArray []= $passwordCredentialsPasswordCredentialConfiguration1;
$applicationRestrictions->setPasswordCredentials($passwordCredentialsArray);

$keyCredentialsKeyCredentialConfiguration1 = new KeyCredentialConfiguration();
$keyCredentialsKeyCredentialConfiguration1->setRestrictionType(new AppKeyCredentialRestrictionType('certificateLifetime'));
$keyCredentialsKeyCredentialConfiguration1->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2020-01-01T10:37:00Z'));
$keyCredentialsKeyCredentialConfiguration1->setMaxLifetime(new \DateInterval('P90D'));
$keyCredentialsArray []= $keyCredentialsKeyCredentialConfiguration1;
$keyCredentialsKeyCredentialConfiguration2 = new KeyCredentialConfiguration();
$keyCredentialsKeyCredentialConfiguration2->setRestrictionType(new AppKeyCredentialRestrictionType('trustedCertificateAuthority'));
$keyCredentialsKeyCredentialConfiguration2->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2019-10-19T10:37:00Z'));
$additionalData = [
'certificateBasedApplicationConfigurationIds' => [
'eec5ba11-2fc0-4113-83a2-ed986ed13743', ],
];
$keyCredentialsKeyCredentialConfiguration2->setAdditionalData($additionalData);
$keyCredentialsArray []= $keyCredentialsKeyCredentialConfiguration2;
$applicationRestrictions->setKeyCredentials($keyCredentialsArray);

$requestBody->setApplicationRestrictions($applicationRestrictions);

$result = $graphServiceClient->policies()->defaultAppManagementPolicy()->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	id = "d015220e-9789-4e8e-bbcc-270fe419229d"
	description = "Lorem ipsum"
	displayName = "Credential management policy"
	isEnabled = $true
	applicationRestrictions = @{
		passwordCredentials = @(
			@{
				restrictionType = "passwordLifetime"
				maxLifetime = "P14D"
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2020-01-01T07:00:00Z")
			}
		)
		keyCredentials = @(
			@{
				restrictionType = "certificateLifetime"
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2020-01-01T10:37:00Z")
				maxLifetime = "P90D"
			}
			@{
				restrictionType = "trustedCertificateAuthority"
				certificateBasedApplicationConfigurationIds = @(
				"eec5ba11-2fc0-4113-83a2-ed986ed13743"
			)
			restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2019-10-19T10:37:00Z")
		}
	)
}
}

Update-MgPolicyDefaultAppManagementPolicy -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.tenant_app_management_policy import TenantAppManagementPolicy
from msgraph.generated.models.app_management_application_configuration import AppManagementApplicationConfiguration
from msgraph.generated.models.password_credential_configuration import PasswordCredentialConfiguration
from msgraph.generated.models.app_credential_restriction_type import AppCredentialRestrictionType
from msgraph.generated.models.key_credential_configuration import KeyCredentialConfiguration
from msgraph.generated.models.app_key_credential_restriction_type import AppKeyCredentialRestrictionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TenantAppManagementPolicy(
	id = "d015220e-9789-4e8e-bbcc-270fe419229d",
	description = "Lorem ipsum",
	display_name = "Credential management policy",
	is_enabled = True,
	application_restrictions = AppManagementApplicationConfiguration(
		password_credentials = [
			PasswordCredentialConfiguration(
				restriction_type = AppCredentialRestrictionType.PasswordLifetime,
				max_lifetime = "P14D",
				restrict_for_apps_created_after_date_time = "2020-01-01T07:00:00Z",
			),
		],
		key_credentials = [
			KeyCredentialConfiguration(
				restriction_type = AppKeyCredentialRestrictionType.AsymmetricKeyLifetime,
				restrict_for_apps_created_after_date_time = "2020-01-01T10:37:00Z",
				max_lifetime = "P90D",
			),
			KeyCredentialConfiguration(
				restriction_type = AppKeyCredentialRestrictionType.AsymmetricKeyLifetime,
				restrict_for_apps_created_after_date_time = "2019-10-19T10:37:00Z",
				additional_data = {
						"certificate_based_application_configuration_ids" : [
							"eec5ba11-2fc0-4113-83a2-ed986ed13743",
						],
				}
			),
		],
	),
)

result = await graph_client.policies.default_app_management_policy.patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Related content

- [The Microsoft Entra app manifest](https://learn.microsoft.com/en-us/entra/identity-platform/reference-app-manifest)
- [Properties of an enterprise application \(service principal\)](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/application-properties)
- [Add a certificate to an app using Microsoft Graph](https://learn.microsoft.com/en-us/graph/applications-how-to-add-certificate)
