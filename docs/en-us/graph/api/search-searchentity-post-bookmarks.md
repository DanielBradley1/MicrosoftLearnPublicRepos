<!-- Source: https://learn.microsoft.com/en-us/graph/api/search-searchentity-post-bookmarks?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Create bookmark

Namespace: microsoft.graph.search

Create a new [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SearchConfiguration.Read.All | SearchConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SearchConfiguration.Read.All | SearchConfiguration.ReadWrite.All |

## HTTP request

```http
POST /search/bookmarks
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) object.

The following table shows the properties that are available when you create a [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| availabilityEndDateTime | DateTimeOffset | Date and time when the bookmark stops appearing as a search result. Set as `null` for always available. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| availabilityStartDateTime | DateTimeOffset | Date and time when the bookmark starts to appear as a search result. Set as `null` for always available. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| categories | String collection | Categories commonly used to describe this bookmark. For example, `IT` and `HR`. |
| description | String | The bookmark description that is shown on the search results page. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| displayName | String | The bookmark name that is displayed in search results. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| groupIds | String collection | The list of security groups that are able to view this bookmark. |
| keywords | [microsoft.graph.search.answerKeyword](https://learn.microsoft.com/en-us/graph/api/resources/search-answerkeyword?view=graph-rest-1.0) | Keywords that trigger this bookmark to appear in search results. |
| languageTags | String collection | A list of geographically specific language names in which this bookmark can be viewed. Each language tag value follows the pattern {language}-{region}. For example, `en-us` is English as used in the United States. For the list of possible values, see [Supported language tags](https://learn.microsoft.com/en-us/graph/api/resources/search-api-answers-overview?view=graph-rest-1.0#supported-language-tags). |
| platforms | microsoft.graph.devicePlatformType collection | List of devices and operating systems that are able to view this bookmark. The possible values are: `android`, `windows`, `ios`, `unknown`, `macOs`. |
| powerAppIds | String collection | List of Power Apps associated with this bookmark. If users add existing Power Apps to a bookmark, they can complete tasks directly on the search results page, such as entering vacation time or reporting expenses. |
| state | microsoft.graph.search.answerState | State of the bookmark. The possible values are: `published`, `draft`, `excluded`, `unknownFutureValue`. |
| targetedVariations | [microsoft.graph.search.answerVariant](https://learn.microsoft.com/en-us/graph/api/resources/search-answervariant?view=graph-rest-1.0) collection | Variations of a bookmark for different countries/regions or devices. Use when you need to show different content to users based on their device, country/region, or both. The date and group settings apply to all variations. |
| webUrl | String | The URL link for the bookmark. When users select this bookmark from the search results, they're directed to the specified URL. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |

## Response

If successful, this method returns a `201 Created` response code with the ID of the bookmark created.

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
POST https://graph.microsoft.com/v1.0/search/bookmarks
Content-Type: application/json

{
  "displayName": "Contoso Install Site",
  "webUrl": "http://www.contoso.com/",
  "description": "Try or buy Contoso for Home or Business and view product information",
  "keywords":  {
    "keywords": ["Contoso", "install"],
    "reservedKeywords": ["Unique keyword"],
    "matchSimilarKeywords": true
  },
  "availabilityStartDateTime": null,
  "availabilityEndDateTime": null,
  "platforms": ["windows"],
  "targetedVariations": [
    {
      "languageTag": "es-es",
      "displayName": "Sitio de instalación Contoso",
      "description": "Pruebe o compre Contoso hogar o negocios y vea la información del producto"
    }
  ],
  "state": "published"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Search;
using Microsoft.Graph.Models;

var requestBody = new Bookmark
{
	DisplayName = "Contoso Install Site",
	WebUrl = "http://www.contoso.com/",
	Description = "Try or buy Contoso for Home or Business and view product information",
	Keywords = new AnswerKeyword
	{
		Keywords = new List<string>
		{
			"Contoso",
			"install",
		},
		ReservedKeywords = new List<string>
		{
			"Unique keyword",
		},
		MatchSimilarKeywords = true,
	},
	AvailabilityStartDateTime = null,
	AvailabilityEndDateTime = null,
	Platforms = new List<DevicePlatformType?>
	{
		DevicePlatformType.Android,
	},
	TargetedVariations = new List<AnswerVariant>
	{
		new AnswerVariant
		{
			LanguageTag = "es-es",
			DisplayName = "Sitio de instalación Contoso",
			Description = "Pruebe o compre Contoso hogar o negocios y vea la información del producto",
		},
	},
	State = AnswerState.Published,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Search.Bookmarks.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssearch "github.com/microsoftgraph/msgraph-sdk-go/models/search"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodelssearch.NewBookmark()
displayName := "Contoso Install Site"
requestBody.SetDisplayName(&displayName) 
webUrl := "http://www.contoso.com/"
requestBody.SetWebUrl(&webUrl) 
description := "Try or buy Contoso for Home or Business and view product information"
requestBody.SetDescription(&description) 
keywords := graphmodelssearch.NewAnswerKeyword()
keywords := []string {
	"Contoso",
	"install",
}
keywords.SetKeywords(keywords)
reservedKeywords := []string {
	"Unique keyword",
}
keywords.SetReservedKeywords(reservedKeywords)
matchSimilarKeywords := true
keywords.SetMatchSimilarKeywords(&matchSimilarKeywords) 
requestBody.SetKeywords(keywords)
availabilityStartDateTime := null
requestBody.SetAvailabilityStartDateTime(&availabilityStartDateTime) 
availabilityEndDateTime := null
requestBody.SetAvailabilityEndDateTime(&availabilityEndDateTime) 
platforms := []graphmodels.DevicePlatformTypeable {
	devicePlatformType := graphmodels.WINDOWS_DEVICEPLATFORMTYPE 
	requestBody.SetDevicePlatformType(&devicePlatformType)
}
requestBody.SetPlatforms(platforms)


answerVariant := graphmodelssearch.NewAnswerVariant()
languageTag := "es-es"
answerVariant.SetLanguageTag(&languageTag) 
displayName := "Sitio de instalación Contoso"
answerVariant.SetDisplayName(&displayName) 
description := "Pruebe o compre Contoso hogar o negocios y vea la información del producto"
answerVariant.SetDescription(&description) 

targetedVariations := []graphmodelssearch.AnswerVariantable {
	answerVariant,
}
requestBody.SetTargetedVariations(targetedVariations)
state := graphmodels.PUBLISHED_ANSWERSTATE 
requestBody.SetState(&state) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
bookmarks, err := graphClient.Search().Bookmarks().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.search.Bookmark bookmark = new com.microsoft.graph.models.search.Bookmark();
bookmark.setDisplayName("Contoso Install Site");
bookmark.setWebUrl("http://www.contoso.com/");
bookmark.setDescription("Try or buy Contoso for Home or Business and view product information");
com.microsoft.graph.models.search.AnswerKeyword keywords = new com.microsoft.graph.models.search.AnswerKeyword();
LinkedList<String> keywords1 = new LinkedList<String>();
keywords1.add("Contoso");
keywords1.add("install");
keywords.setKeywords(keywords1);
LinkedList<String> reservedKeywords = new LinkedList<String>();
reservedKeywords.add("Unique keyword");
keywords.setReservedKeywords(reservedKeywords);
keywords.setMatchSimilarKeywords(true);
bookmark.setKeywords(keywords);
bookmark.setAvailabilityStartDateTime(null);
bookmark.setAvailabilityEndDateTime(null);
LinkedList<DevicePlatformType> platforms = new LinkedList<DevicePlatformType>();
platforms.add(DevicePlatformType.Android);
bookmark.setPlatforms(platforms);
LinkedList<com.microsoft.graph.models.search.AnswerVariant> targetedVariations = new LinkedList<com.microsoft.graph.models.search.AnswerVariant>();
com.microsoft.graph.models.search.AnswerVariant answerVariant = new com.microsoft.graph.models.search.AnswerVariant();
answerVariant.setLanguageTag("es-es");
answerVariant.setDisplayName("Sitio de instalación Contoso");
answerVariant.setDescription("Pruebe o compre Contoso hogar o negocios y vea la información del producto");
targetedVariations.add(answerVariant);
bookmark.setTargetedVariations(targetedVariations);
bookmark.setState(com.microsoft.graph.models.search.AnswerState.Published);
com.microsoft.graph.models.search.Bookmark result = graphClient.search().bookmarks().post(bookmark);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const bookmark = {
  displayName: 'Contoso Install Site',
  webUrl: 'http://www.contoso.com/',
  description: 'Try or buy Contoso for Home or Business and view product information',
  keywords: {
    keywords: ['Contoso', 'install'],
    reservedKeywords: ['Unique keyword'],
    matchSimilarKeywords: true
  },
  availabilityStartDateTime: null,
  availabilityEndDateTime: null,
  platforms: ['windows'],
  targetedVariations: [
    {
      languageTag: 'es-es',
      displayName: 'Sitio de instalación Contoso',
      description: 'Pruebe o compre Contoso hogar o negocios y vea la información del producto'
    }
  ],
  state: 'published'
};

await client.api('/search/bookmarks')
	.post(bookmark);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Search\Bookmark;
use Microsoft\Graph\Generated\Models\Search\AnswerKeyword;
use Microsoft\Graph\Generated\Models\DevicePlatformType;
use Microsoft\Graph\Generated\Models\Search\AnswerVariant;
use Microsoft\Graph\Generated\Models\Search\AnswerState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Bookmark();
$requestBody->setDisplayName('Contoso Install Site');
$requestBody->setWebUrl('http://www.contoso.com/');
$requestBody->setDescription('Try or buy Contoso for Home or Business and view product information');
$keywords = new AnswerKeyword();
$keywords->setKeywords(['Contoso', 'install', 	]);
$keywords->setReservedKeywords(['Unique keyword', 	]);
$keywords->setMatchSimilarKeywords(true);
$requestBody->setKeywords($keywords);
$requestBody->setAvailabilityStartDateTime(null);
$requestBody->setAvailabilityEndDateTime(null);
$requestBody->setPlatforms([new DevicePlatformType('windows'),	]);
$targetedVariationsAnswerVariant1 = new AnswerVariant();
$targetedVariationsAnswerVariant1->setLanguageTag('es-es');
$targetedVariationsAnswerVariant1->setDisplayName('Sitio de instalación Contoso');
$targetedVariationsAnswerVariant1->setDescription('Pruebe o compre Contoso hogar o negocios y vea la información del producto');
$targetedVariationsArray []= $targetedVariationsAnswerVariant1;
$requestBody->setTargetedVariations($targetedVariationsArray);

$requestBody->setState(new AnswerState('published'));

$result = $graphServiceClient->search()->bookmarks()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	displayName = "Contoso Install Site"
	webUrl = "http://www.contoso.com/"
	description = "Try or buy Contoso for Home or Business and view product information"
	keywords = @{
		keywords = @(
		"Contoso"
	"install"
)
reservedKeywords = @(
"Unique keyword"
)
matchSimilarKeywords = $true
}
availabilityStartDateTime = $null
availabilityEndDateTime = $null
platforms = @(
"windows"
)
targetedVariations = @(
@{
languageTag = "es-es"
displayName = "Sitio de instalación Contoso"
description = "Pruebe o compre Contoso hogar o negocios y vea la información del producto"
}
)
state = "published"
}

New-MgSearchBookmark -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.search.bookmark import Bookmark
from msgraph.generated.models.search.answer_keyword import AnswerKeyword
from msgraph.generated.models.device_platform_type import DevicePlatformType
from msgraph.generated.models.search.answer_variant import AnswerVariant
from msgraph.generated.models.answer_state import AnswerState
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Bookmark(
	display_name = "Contoso Install Site",
	web_url = "http://www.contoso.com/",
	description = "Try or buy Contoso for Home or Business and view product information",
	keywords = AnswerKeyword(
		keywords = [
			"Contoso",
			"install",
		],
		reserved_keywords = [
			"Unique keyword",
		],
		match_similar_keywords = True,
	),
	availability_start_date_time = None,
	availability_end_date_time = None,
	platforms = [
		DevicePlatformType.Android,
	],
	targeted_variations = [
		AnswerVariant(
			language_tag = "es-es",
			display_name = "Sitio de instalación Contoso",
			description = "Pruebe o compre Contoso hogar o negocios y vea la información del producto",
		),
	],
	state = AnswerState.Published,
)

result = await graph_client.search.bookmarks.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Location: /733b26d5-af76-4eea-ac69-1a0ce8716897
Content-Type: application/json

{
  "id": "733b26d5-af76-4eea-ac69-1a0ce8716897"
}
```
