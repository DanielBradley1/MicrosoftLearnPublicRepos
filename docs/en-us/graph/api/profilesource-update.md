<!-- Source: https://learn.microsoft.com/en-us/graph/api/profilesource-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# Update profileSource

Namespace: microsoft.graph

Update the properties of a [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) object.

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
PATCH /admin/people/profileSources(sourceId='{sourceId}')
```

## Function parameters

In the request URL, provide the following parameter with a valid value.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| sourceId | String | Profile source identifier used as an [alternate key](https://github.com/microsoft/api-guidelines/blob/vNext/graph/patterns/alternate-key.md). Required. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

> **Note:** To avoid encoding issues that malform the payload, use `Content-Type: application/json; charset=utf-8`.

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the profile source intended to inform users about the profile source name. |
| kind | String | Type of the profile source. |
| localizations | [profileSourceLocalization](https://learn.microsoft.com/en-us/graph/api/resources/profilesourcelocalization?view=graph-rest-1.0) collection | Alternative localized labels specified by an administrator. |
| sourceId | String | Profile source identifier used as an alternate key. |
| webUrl | String | Web URL of the profile source that directs users to the page view of the profile data. |

## Response

If successful, this method returns a `200 OK` response code and an updated [profileSource](https://learn.microsoft.com/en-us/graph/api/resources/profilesource?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/admin/people/profileSources(sourceId='bamboohr1')
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.profileSource",
  "sourceId": "bamboohr1",
  "kind": "BambooHR",
  "displayName": "BambooHR Updated",
  "webUrl": "https://bamboohr.contoso.com/login",
  "localizations": [
    {
      "displayName": "HR-Platform",
      "webUrl": "http://bamboohr.contoso.com/en-us/login",
      "languageTag": "en-us"
    },
    {
      "displayName": "HR-Plattform",
      "webUrl": "http://bamboohr.contoso.com/de/login",
      "languageTag": "de"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ProfileSource
{
	OdataType = "#microsoft.graph.profileSource",
	SourceId = "bamboohr1",
	Kind = "BambooHR",
	DisplayName = "BambooHR Updated",
	WebUrl = "https://bamboohr.contoso.com/login",
	Localizations = new List<ProfileSourceLocalization>
	{
		new ProfileSourceLocalization
		{
			DisplayName = "HR-Platform",
			WebUrl = "http://bamboohr.contoso.com/en-us/login",
			LanguageTag = "en-us",
		},
		new ProfileSourceLocalization
		{
			DisplayName = "HR-Plattform",
			WebUrl = "http://bamboohr.contoso.com/de/login",
			LanguageTag = "de",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.People.ProfileSourcesWithSourceId("{sourceId}").PatchAsync(requestBody);
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

requestBody := graphmodels.NewProfileSource()
sourceId := "bamboohr1"
requestBody.SetSourceId(&sourceId) 
kind := "BambooHR"
requestBody.SetKind(&kind) 
displayName := "BambooHR Updated"
requestBody.SetDisplayName(&displayName) 
webUrl := "https://bamboohr.contoso.com/login"
requestBody.SetWebUrl(&webUrl) 


profileSourceLocalization := graphmodels.NewProfileSourceLocalization()
displayName := "HR-Platform"
profileSourceLocalization.SetDisplayName(&displayName) 
webUrl := "http://bamboohr.contoso.com/en-us/login"
profileSourceLocalization.SetWebUrl(&webUrl) 
languageTag := "en-us"
profileSourceLocalization.SetLanguageTag(&languageTag) 
profileSourceLocalization1 := graphmodels.NewProfileSourceLocalization()
displayName := "HR-Plattform"
profileSourceLocalization1.SetDisplayName(&displayName) 
webUrl := "http://bamboohr.contoso.com/de/login"
profileSourceLocalization1.SetWebUrl(&webUrl) 
languageTag := "de"
profileSourceLocalization1.SetLanguageTag(&languageTag) 

localizations := []graphmodels.ProfileSourceLocalizationable {
	profileSourceLocalization,
	profileSourceLocalization1,
}
requestBody.SetLocalizations(localizations)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sourceId := "{sourceId}"
profileSources, err := graphClient.Admin().People().ProfileSourcesWithSourceId(&sourceId).Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ProfileSource profileSource = new ProfileSource();
profileSource.setOdataType("#microsoft.graph.profileSource");
profileSource.setSourceId("bamboohr1");
profileSource.setKind("BambooHR");
profileSource.setDisplayName("BambooHR Updated");
profileSource.setWebUrl("https://bamboohr.contoso.com/login");
LinkedList<ProfileSourceLocalization> localizations = new LinkedList<ProfileSourceLocalization>();
ProfileSourceLocalization profileSourceLocalization = new ProfileSourceLocalization();
profileSourceLocalization.setDisplayName("HR-Platform");
profileSourceLocalization.setWebUrl("http://bamboohr.contoso.com/en-us/login");
profileSourceLocalization.setLanguageTag("en-us");
localizations.add(profileSourceLocalization);
ProfileSourceLocalization profileSourceLocalization1 = new ProfileSourceLocalization();
profileSourceLocalization1.setDisplayName("HR-Plattform");
profileSourceLocalization1.setWebUrl("http://bamboohr.contoso.com/de/login");
profileSourceLocalization1.setLanguageTag("de");
localizations.add(profileSourceLocalization1);
profileSource.setLocalizations(localizations);
ProfileSource result = graphClient.admin().people().profileSourcesWithSourceId("{sourceId}").patch(profileSource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ProfileSource;
use Microsoft\Graph\Generated\Models\ProfileSourceLocalization;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ProfileSource();
$requestBody->setOdataType('#microsoft.graph.profileSource');
$requestBody->setSourceId('bamboohr1');
$requestBody->setKind('BambooHR');
$requestBody->setDisplayName('BambooHR Updated');
$requestBody->setWebUrl('https://bamboohr.contoso.com/login');
$localizationsProfileSourceLocalization1 = new ProfileSourceLocalization();
$localizationsProfileSourceLocalization1->setDisplayName('HR-Platform');
$localizationsProfileSourceLocalization1->setWebUrl('http://bamboohr.contoso.com/en-us/login');
$localizationsProfileSourceLocalization1->setLanguageTag('en-us');
$localizationsArray []= $localizationsProfileSourceLocalization1;
$localizationsProfileSourceLocalization2 = new ProfileSourceLocalization();
$localizationsProfileSourceLocalization2->setDisplayName('HR-Plattform');
$localizationsProfileSourceLocalization2->setWebUrl('http://bamboohr.contoso.com/de/login');
$localizationsProfileSourceLocalization2->setLanguageTag('de');
$localizationsArray []= $localizationsProfileSourceLocalization2;
$requestBody->setLocalizations($localizationsArray);


$result = $graphServiceClient->admin()->people()->profileSourcesWithSourceId('{sourceId}', )->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	"@odata.type" = "#microsoft.graph.profileSource"
	sourceId = "bamboohr1"
	kind = "BambooHR"
	displayName = "BambooHR Updated"
	webUrl = "https://bamboohr.contoso.com/login"
	localizations = @(
		@{
			displayName = "HR-Platform"
			webUrl = "http://bamboohr.contoso.com/en-us/login"
			languageTag = "en-us"
		}
		@{
			displayName = "HR-Plattform"
			webUrl = "http://bamboohr.contoso.com/de/login"
			languageTag = "de"
		}
	)
}

Update-MgAdminPeopleProfileSourceBySourceId -BodyParameter $params -SourceId $sourceIdId 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.profile_source import ProfileSource
from msgraph.generated.models.profile_source_localization import ProfileSourceLocalization
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ProfileSource(
	odata_type = "#microsoft.graph.profileSource",
	source_id = "bamboohr1",
	kind = "BambooHR",
	display_name = "BambooHR Updated",
	web_url = "https://bamboohr.contoso.com/login",
	localizations = [
		ProfileSourceLocalization(
			display_name = "HR-Platform",
			web_url = "http://bamboohr.contoso.com/en-us/login",
			language_tag = "en-us",
		),
		ProfileSourceLocalization(
			display_name = "HR-Plattform",
			web_url = "http://bamboohr.contoso.com/de/login",
			language_tag = "de",
		),
	],
)

result = await graph_client.admin.people.profile_sources_with_source_id("{sourceId}").patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.profileSource",
  "id": "27f1af7b-b166-4f5b-b994-ae135a581547",
  "sourceId": "bamboohr1",
  "kind": "BambooHR",
  "displayName": "BambooHR Updated",
  "webUrl": "https://bamboohr.contoso.com/login",
  "localizations": [
    {
      "displayName": "HR-Platform",
      "webUrl": "http://bamboohr.contoso.com/en-us/login",
      "languageTag": "en-us"
    },
    {
      "displayName": "HR-Plattform",
      "webUrl": "http://bamboohr.contoso.com/de/login",
      "languageTag": "de"
    }
  ]
}
```
