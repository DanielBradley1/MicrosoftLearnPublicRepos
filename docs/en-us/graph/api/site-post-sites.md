<!-- Source: https://learn.microsoft.com/en-us/graph/api/site-post-sites?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-29 -->

# Create site

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new SharePoint [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Create.All | Sites.FullControl.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Create.All | Sites.FullControl.All |

## HTTP request

```http
POST /sites
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-beta) object.

You can specify the following properties when you create a **site**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The descriptive text for the site. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-beta). |
| locale | String | The language settings of the site. |
| name | String | The name of the site. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-beta). Optional. |
| ownerIdentityToResolve | [identityInput](https://learn.microsoft.com/en-us/graph/api/resources/identityinput?view=graph-rest-beta) | The site owner to be provided at the time of site creation only. Optional. |
| shareByEmailEnabled | Boolean | Determines whether the site and its content can be shared via email. Optional. |
| template | siteTemplateType | Specifies the template applied to the site. The possible values are: `sitepagepublishing`, `sts`, `unknownFutureValue`. Optional. |
| webUrl | String | The URL for the site that can only be provided at the time of site creation. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-beta). Optional. |

## Response

If successful, this method returns a `202 Accepted` response code and a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-beta) object in the response body. The response also contains a `Location` header, which contains the location of the [getOperationStatus](https://learn.microsoft.com/en-us/graph/api/site-getoperationstatus?view=graph-rest-beta) that was created to handle the site creation operation. Check the status of the creation operation by making a GET request to this location.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/sites
Content-Type: application/json

{
  "name": "Communication Site Test",
  "webUrl": "https://contoso.sharepoint.com/sites/commsite1",
  "locale": "en-US",
  "shareByEmailEnabled": false,
  "description": "Test Site Description",
  "template": "sitepagepublishing",
  "ownerIdentityToResolve": {
    "email": "ryan@contoso.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new Site
{
	Name = "Communication Site Test",
	WebUrl = "https://contoso.sharepoint.com/sites/commsite1",
	Locale = "en-US",
	ShareByEmailEnabled = false,
	Description = "Test Site Description",
	Template = SiteTemplateType.Sitepagepublishing,
	OwnerIdentityToResolve = new IdentityInput
	{
		Email = "ryan@contoso.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSite()
name := "Communication Site Test"
requestBody.SetName(&name) 
webUrl := "https://contoso.sharepoint.com/sites/commsite1"
requestBody.SetWebUrl(&webUrl) 
locale := "en-US"
requestBody.SetLocale(&locale) 
shareByEmailEnabled := false
requestBody.SetShareByEmailEnabled(&shareByEmailEnabled) 
description := "Test Site Description"
requestBody.SetDescription(&description) 
template := graphmodels.SITEPAGEPUBLISHING_SITETEMPLATETYPE 
requestBody.SetTemplate(&template) 
ownerIdentityToResolve := graphmodels.NewIdentityInput()
email := "ryan@contoso.com"
ownerIdentityToResolve.SetEmail(&email) 
requestBody.SetOwnerIdentityToResolve(ownerIdentityToResolve)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sites, err := graphClient.Sites().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Site site = new Site();
site.setName("Communication Site Test");
site.setWebUrl("https://contoso.sharepoint.com/sites/commsite1");
site.setLocale("en-US");
site.setShareByEmailEnabled(false);
site.setDescription("Test Site Description");
site.setTemplate(SiteTemplateType.Sitepagepublishing);
IdentityInput ownerIdentityToResolve = new IdentityInput();
ownerIdentityToResolve.setEmail("ryan@contoso.com");
site.setOwnerIdentityToResolve(ownerIdentityToResolve);
Site result = graphClient.sites().post(site);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const site = {
  name: 'Communication Site Test',
  webUrl: 'https://contoso.sharepoint.com/sites/commsite1',
  locale: 'en-US',
  shareByEmailEnabled: false,
  description: 'Test Site Description',
  template: 'sitepagepublishing',
  ownerIdentityToResolve: {
    email: 'ryan@contoso.com'
  }
};

await client.api('/sites')
	.version('beta')
	.post(site);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Site;
use Microsoft\Graph\Beta\Generated\Models\SiteTemplateType;
use Microsoft\Graph\Beta\Generated\Models\IdentityInput;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Site();
$requestBody->setName('Communication Site Test');
$requestBody->setWebUrl('https://contoso.sharepoint.com/sites/commsite1');
$requestBody->setLocale('en-US');
$requestBody->setShareByEmailEnabled(false);
$requestBody->setDescription('Test Site Description');
$requestBody->setTemplate(new SiteTemplateType('sitepagepublishing'));
$ownerIdentityToResolve = new IdentityInput();
$ownerIdentityToResolve->setEmail('ryan@contoso.com');
$requestBody->setOwnerIdentityToResolve($ownerIdentityToResolve);

$result = $graphServiceClient->sites()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.site import Site
from msgraph_beta.generated.models.site_template_type import SiteTemplateType
from msgraph_beta.generated.models.identity_input import IdentityInput
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Site(
	name = "Communication Site Test",
	web_url = "https://contoso.sharepoint.com/sites/commsite1",
	locale = "en-US",
	share_by_email_enabled = False,
	description = "Test Site Description",
	template = SiteTemplateType.Sitepagepublishing,
	owner_identity_to_resolve = IdentityInput(
		email = "ryan@contoso.com",
	),
)

result = await graph_client.sites.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Location: https://graph.microsoft.com/beta/sites/getOperationStatus(operationId='JXMnaHR0cHMlM0ElMkYlMkZncmFwaC5taWNyb3NvZnQuY29tJTJGc2l0ZXMlMkZ0ZWFtc2l0ZTE=')
```
