<!-- Source: https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-post-profilepropertysettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# Create profilePropertySetting

Namespace: microsoft.graph

Create a new [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PeopleSettings.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PeopleSettings.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). *People Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /admin/people/profilePropertySettings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) object.

You can specify the following properties when creating a **profilePropertySetting**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the property-level setting. Optional. |
| name | String | Other name of the property-level setting. For backward compatibility. Optional. |
| prioritizedSourceUrls | String collection | A collection of prioritized profile source URLs ordered by data precedence within an organization. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [profilePropertySetting](https://learn.microsoft.com/en-us/graph/api/resources/profilepropertysetting?view=graph-rest-1.0) object in the response body.

## Examples

### Request

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
POST https://graph.microsoft.com/v1.0/admin/people/profilePropertySettings
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.profilePropertySetting",
  "displayName": "Profile priority config",
  "name": "Profile priority config",
  "prioritizedSourceUrls": [
    "https://graph.microsoft.com/v1.0/admin/people/profileSources(sourceId='contosohr1')"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ProfilePropertySetting
{
	OdataType = "#microsoft.graph.profilePropertySetting",
	DisplayName = "Profile priority config",
	Name = "Profile priority config",
	PrioritizedSourceUrls = new List<string>
	{
		"https://graph.microsoft.com/v1.0/admin/people/profileSources(sourceId='contosohr1')",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.People.ProfilePropertySettings.PostAsync(requestBody);
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

requestBody := graphmodels.NewProfilePropertySetting()
displayName := "Profile priority config"
requestBody.SetDisplayName(&displayName) 
name := "Profile priority config"
requestBody.SetName(&name) 
prioritizedSourceUrls := []string {
	"https://graph.microsoft.com/v1.0/admin/people/profileSources(sourceId='contosohr1')",
}
requestBody.SetPrioritizedSourceUrls(prioritizedSourceUrls)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
profilePropertySettings, err := graphClient.Admin().People().ProfilePropertySettings().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ProfilePropertySetting profilePropertySetting = new ProfilePropertySetting();
profilePropertySetting.setOdataType("#microsoft.graph.profilePropertySetting");
profilePropertySetting.setDisplayName("Profile priority config");
profilePropertySetting.setName("Profile priority config");
LinkedList<String> prioritizedSourceUrls = new LinkedList<String>();
prioritizedSourceUrls.add("https://graph.microsoft.com/v1.0/admin/people/profileSources(sourceId='contosohr1')");
profilePropertySetting.setPrioritizedSourceUrls(prioritizedSourceUrls);
ProfilePropertySetting result = graphClient.admin().people().profilePropertySettings().post(profilePropertySetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const profilePropertySetting = {
  '@odata.type': '#microsoft.graph.profilePropertySetting',
  displayName: 'Profile priority config',
  name: 'Profile priority config',
  prioritizedSourceUrls: [
    'https://graph.microsoft.com/v1.0/admin/people/profileSources(sourceId=\'contosohr1\')'
  ]
};

await client.api('/admin/people/profilePropertySettings')
	.post(profilePropertySetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ProfilePropertySetting;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ProfilePropertySetting();
$requestBody->setOdataType('#microsoft.graph.profilePropertySetting');
$requestBody->setDisplayName('Profile priority config');
$requestBody->setName('Profile priority config');
$requestBody->setPrioritizedSourceUrls(['https://graph.microsoft.com/v1.0/admin/people/profileSources(sourceId=\'contosohr1\')', 	]);

$result = $graphServiceClient->admin()->people()->profilePropertySettings()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	"@odata.type" = "#microsoft.graph.profilePropertySetting"
	displayName = "Profile priority config"
	name = "Profile priority config"
	prioritizedSourceUrls = @(
	"https://graph.microsoft.com/v1.0/admin/people/profileSources(sourceId='contosohr1')"
)
}

New-MgAdminPeopleProfilePropertySetting -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.profile_property_setting import ProfilePropertySetting
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ProfilePropertySetting(
	odata_type = "#microsoft.graph.profilePropertySetting",
	display_name = "Profile priority config",
	name = "Profile priority config",
	prioritized_source_urls = [
		"https://graph.microsoft.com/v1.0/admin/people/profileSources(sourceId='contosohr1')",
	],
)

result = await graph_client.admin.people.profile_property_settings.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.profilePropertySetting",
  "id": "00000000-0000-0000-0000-000000000001",
  "displayName": "Profile priority config",
  "name": "Profile priority config",
  "prioritizedSourceUrls": [
    "https://graph.microsoft.com/v1.0/admin/people/profileSources(sourceId='contosohr1')",
    "https://graph.microsoft.com/v1.0/admin/people/profileSources(sourceId='4ce763dd-9214-4eff-af7c-da491cc3782d')"
  ]
}
```
