<!-- Source: https://learn.microsoft.com/en-us/graph/api/search-searchentity-post-qnas?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Create qna

Namespace: microsoft.graph.search

Create a new [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) object.

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
POST /search/qnas
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) object.

The following table shows the properties that are available when you create a [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| availabilityEndDateTime | DateTimeOffset | Date and time when the QnA stops appearing as a search result. Set as `null` for always available. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| availabilityStartDateTime | DateTimeOffset | Date and time when the QnA starts to appear as a search result. Set as `null` for always available. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | Answer that is displayed in search results. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| displayName | String | Question that is displayed in search results. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| groupIds | String collection | The list of security groups that are able to view this QnA. |
| keywords | [microsoft.graph.search.answerKeyword](https://learn.microsoft.com/en-us/graph/api/resources/search-answerkeyword?view=graph-rest-1.0) | Keywords that trigger this QnA to appear in search results. |
| languageTags | String collection | A list of geographically specific language names in which this QnA can be viewed. Each language tag value follows the pattern {language}-{region}. For example, `en-us` is English as used in the United States. For the list of possible values, see [Supported language tags](https://learn.microsoft.com/en-us/graph/api/resources/search-api-answers-overview?view=graph-rest-1.0#supported-language-tags). |
| platforms | microsoft.graph.devicePlatformType collection | List of devices and operating systems that are able to view this QnA. The possible values are: `android`, `androidForWork`, `ios`, `macOS`, `windowsPhone81`, `windowsPhone81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidASOP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`. |
| state | microsoft.graph.search.answerState | State of the QnA. The possible values are: `published`, `draft`, `excluded`, `unknownFutureValue`. |
| targetedVariations | [microsoft.graph.search.answerVariant](https://learn.microsoft.com/en-us/graph/api/resources/search-answervariant?view=graph-rest-1.0) collection | Variations of a QnA for different countries/regions or devices. Use when you need to show different content to users based on their device, country/region, or both. The date and group settings apply to all variations. |
| webUrl | String | The URL link for the QnA. When users select this QnA from the search results, they're directed to the specified URL. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |

## Response

If successful, this method returns a `201 Created` response code with the ID of the question and answer created.

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
POST https://graph.microsoft.com/v1.0/search/qnas
Content-Type: application/json

{
  "displayName": "Global Country Holidays",
  "webUrl": "http://www.contoso.com/",
  "description": "The dates that Contoso offices will be closed to observe holidays. These dates may differ from the actual date of the holiday in cases where the holiday falls on a weekend.    <table>    <thead>    <tr>    <td><strong>2021 Dates</strong></td>    <td><strong>Holiday</strong></td>    </tr>    </thead>    <tbody>    <tr>        <td>January 1, 2021</td>        <td>New Year's Day</td>    </tr>        <tr>        <td>January 18, 2021</td>        <td>Martin Luther King Day</td>    </tr>        <tr>        <td>February 15, 2021</td>        <td>Presidents Day</td>    </tr>        <tr>        <td>May 31, 2021</td>        <td>Memorial Day</td>    </tr>        <tr>        <td>July 5, 2021</td>        <td>Independence Day</td>    </tr>        <tr>        <td>September 6, 2021</td>        <td>Labor Day</td>    </tr>        <tr>        <td>November 25, 2021 - November 26, 2021</td>        <td>Thanksgiving Day and Day after Thanksgiving</td>    </tr>    <tr>        <td>December 23, 2021 - December 24, 2021</td>        <td>Christmas Eve and Christmas Day</td>    </tr>    </tbody>    </table>",
  "keywords":  {
    "keywords": ["new years day", "martin luther king day", "presidents day", "memorial day", "independence day", "labor day", "thanksgiving", "christmas"],
    "reservedKeywords": ["holidays", "paid days off"],
    "matchSimilarKeywords": true
  },
  "availabilityStartDateTime": "2020-09-21T20:01:37Z",
  "availabilityEndDateTime": "2021-12-31T20:01:37Z",
  "languageTags": ["en-us"],
  "platforms": ["ios"],
  "state": "published"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Search;
using Microsoft.Graph.Models;

var requestBody = new Qna
{
	DisplayName = "Global Country Holidays",
	WebUrl = "http://www.contoso.com/",
	Description = "The dates that Contoso offices will be closed to observe holidays. These dates may differ from the actual date of the holiday in cases where the holiday falls on a weekend.    <table>    <thead>    <tr>    <td><strong>2021 Dates</strong></td>    <td><strong>Holiday</strong></td>    </tr>    </thead>    <tbody>    <tr>        <td>January 1, 2021</td>        <td>New Year's Day</td>    </tr>        <tr>        <td>January 18, 2021</td>        <td>Martin Luther King Day</td>    </tr>        <tr>        <td>February 15, 2021</td>        <td>Presidents Day</td>    </tr>        <tr>        <td>May 31, 2021</td>        <td>Memorial Day</td>    </tr>        <tr>        <td>July 5, 2021</td>        <td>Independence Day</td>    </tr>        <tr>        <td>September 6, 2021</td>        <td>Labor Day</td>    </tr>        <tr>        <td>November 25, 2021 - November 26, 2021</td>        <td>Thanksgiving Day and Day after Thanksgiving</td>    </tr>    <tr>        <td>December 23, 2021 - December 24, 2021</td>        <td>Christmas Eve and Christmas Day</td>    </tr>    </tbody>    </table>",
	Keywords = new AnswerKeyword
	{
		Keywords = new List<string>
		{
			"new years day",
			"martin luther king day",
			"presidents day",
			"memorial day",
			"independence day",
			"labor day",
			"thanksgiving",
			"christmas",
		},
		ReservedKeywords = new List<string>
		{
			"holidays",
			"paid days off",
		},
		MatchSimilarKeywords = true,
	},
	AvailabilityStartDateTime = DateTimeOffset.Parse("2020-09-21T20:01:37Z"),
	AvailabilityEndDateTime = DateTimeOffset.Parse("2021-12-31T20:01:37Z"),
	LanguageTags = new List<string>
	{
		"en-us",
	},
	Platforms = new List<DevicePlatformType?>
	{
		DevicePlatformType.IOS,
	},
	State = AnswerState.Published,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Search.Qnas.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssearch "github.com/microsoftgraph/msgraph-sdk-go/models/search"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodelssearch.NewQna()
displayName := "Global Country Holidays"
requestBody.SetDisplayName(&displayName) 
webUrl := "http://www.contoso.com/"
requestBody.SetWebUrl(&webUrl) 
description := "The dates that Contoso offices will be closed to observe holidays. These dates may differ from the actual date of the holiday in cases where the holiday falls on a weekend.    <table>    <thead>    <tr>    <td><strong>2021 Dates</strong></td>    <td><strong>Holiday</strong></td>    </tr>    </thead>    <tbody>    <tr>        <td>January 1, 2021</td>        <td>New Year's Day</td>    </tr>        <tr>        <td>January 18, 2021</td>        <td>Martin Luther King Day</td>    </tr>        <tr>        <td>February 15, 2021</td>        <td>Presidents Day</td>    </tr>        <tr>        <td>May 31, 2021</td>        <td>Memorial Day</td>    </tr>        <tr>        <td>July 5, 2021</td>        <td>Independence Day</td>    </tr>        <tr>        <td>September 6, 2021</td>        <td>Labor Day</td>    </tr>        <tr>        <td>November 25, 2021 - November 26, 2021</td>        <td>Thanksgiving Day and Day after Thanksgiving</td>    </tr>    <tr>        <td>December 23, 2021 - December 24, 2021</td>        <td>Christmas Eve and Christmas Day</td>    </tr>    </tbody>    </table>"
requestBody.SetDescription(&description) 
keywords := graphmodelssearch.NewAnswerKeyword()
keywords := []string {
	"new years day",
	"martin luther king day",
	"presidents day",
	"memorial day",
	"independence day",
	"labor day",
	"thanksgiving",
	"christmas",
}
keywords.SetKeywords(keywords)
reservedKeywords := []string {
	"holidays",
	"paid days off",
}
keywords.SetReservedKeywords(reservedKeywords)
matchSimilarKeywords := true
keywords.SetMatchSimilarKeywords(&matchSimilarKeywords) 
requestBody.SetKeywords(keywords)
availabilityStartDateTime , err := time.Parse(time.RFC3339, "2020-09-21T20:01:37Z")
requestBody.SetAvailabilityStartDateTime(&availabilityStartDateTime) 
availabilityEndDateTime , err := time.Parse(time.RFC3339, "2021-12-31T20:01:37Z")
requestBody.SetAvailabilityEndDateTime(&availabilityEndDateTime) 
languageTags := []string {
	"en-us",
}
requestBody.SetLanguageTags(languageTags)
platforms := []graphmodels.DevicePlatformTypeable {
	devicePlatformType := graphmodels.IOS_DEVICEPLATFORMTYPE 
	requestBody.SetDevicePlatformType(&devicePlatformType)
}
requestBody.SetPlatforms(platforms)
state := graphmodels.PUBLISHED_ANSWERSTATE 
requestBody.SetState(&state) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
qnas, err := graphClient.Search().Qnas().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.search.Qna qna = new com.microsoft.graph.models.search.Qna();
qna.setDisplayName("Global Country Holidays");
qna.setWebUrl("http://www.contoso.com/");
qna.setDescription("The dates that Contoso offices will be closed to observe holidays. These dates may differ from the actual date of the holiday in cases where the holiday falls on a weekend.    <table>    <thead>    <tr>    <td><strong>2021 Dates</strong></td>    <td><strong>Holiday</strong></td>    </tr>    </thead>    <tbody>    <tr>        <td>January 1, 2021</td>        <td>New Year's Day</td>    </tr>        <tr>        <td>January 18, 2021</td>        <td>Martin Luther King Day</td>    </tr>        <tr>        <td>February 15, 2021</td>        <td>Presidents Day</td>    </tr>        <tr>        <td>May 31, 2021</td>        <td>Memorial Day</td>    </tr>        <tr>        <td>July 5, 2021</td>        <td>Independence Day</td>    </tr>        <tr>        <td>September 6, 2021</td>        <td>Labor Day</td>    </tr>        <tr>        <td>November 25, 2021 - November 26, 2021</td>        <td>Thanksgiving Day and Day after Thanksgiving</td>    </tr>    <tr>        <td>December 23, 2021 - December 24, 2021</td>        <td>Christmas Eve and Christmas Day</td>    </tr>    </tbody>    </table>");
com.microsoft.graph.models.search.AnswerKeyword keywords = new com.microsoft.graph.models.search.AnswerKeyword();
LinkedList<String> keywords1 = new LinkedList<String>();
keywords1.add("new years day");
keywords1.add("martin luther king day");
keywords1.add("presidents day");
keywords1.add("memorial day");
keywords1.add("independence day");
keywords1.add("labor day");
keywords1.add("thanksgiving");
keywords1.add("christmas");
keywords.setKeywords(keywords1);
LinkedList<String> reservedKeywords = new LinkedList<String>();
reservedKeywords.add("holidays");
reservedKeywords.add("paid days off");
keywords.setReservedKeywords(reservedKeywords);
keywords.setMatchSimilarKeywords(true);
qna.setKeywords(keywords);
OffsetDateTime availabilityStartDateTime = OffsetDateTime.parse("2020-09-21T20:01:37Z");
qna.setAvailabilityStartDateTime(availabilityStartDateTime);
OffsetDateTime availabilityEndDateTime = OffsetDateTime.parse("2021-12-31T20:01:37Z");
qna.setAvailabilityEndDateTime(availabilityEndDateTime);
LinkedList<String> languageTags = new LinkedList<String>();
languageTags.add("en-us");
qna.setLanguageTags(languageTags);
LinkedList<DevicePlatformType> platforms = new LinkedList<DevicePlatformType>();
platforms.add(DevicePlatformType.IOS);
qna.setPlatforms(platforms);
qna.setState(com.microsoft.graph.models.search.AnswerState.Published);
com.microsoft.graph.models.search.Qna result = graphClient.search().qnas().post(qna);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const qna = {
  displayName: 'Global Country Holidays',
  webUrl: 'http://www.contoso.com/',
  description: 'The dates that Contoso offices will be closed to observe holidays. These dates may differ from the actual date of the holiday in cases where the holiday falls on a weekend.    <table>    <thead>    <tr>    <td><strong>2021 Dates</strong></td>    <td><strong>Holiday</strong></td>    </tr>    </thead>    <tbody>    <tr>        <td>January 1, 2021</td>        <td>New Year\'s Day</td>    </tr>        <tr>        <td>January 18, 2021</td>        <td>Martin Luther King Day</td>    </tr>        <tr>        <td>February 15, 2021</td>        <td>Presidents Day</td>    </tr>        <tr>        <td>May 31, 2021</td>        <td>Memorial Day</td>    </tr>        <tr>        <td>July 5, 2021</td>        <td>Independence Day</td>    </tr>        <tr>        <td>September 6, 2021</td>        <td>Labor Day</td>    </tr>        <tr>        <td>November 25, 2021 - November 26, 2021</td>        <td>Thanksgiving Day and Day after Thanksgiving</td>    </tr>    <tr>        <td>December 23, 2021 - December 24, 2021</td>        <td>Christmas Eve and Christmas Day</td>    </tr>    </tbody>    </table>',
  keywords: {
    keywords: ['new years day', 'martin luther king day', 'presidents day', 'memorial day', 'independence day', 'labor day', 'thanksgiving', 'christmas'],
    reservedKeywords: ['holidays', 'paid days off'],
    matchSimilarKeywords: true
  },
  availabilityStartDateTime: '2020-09-21T20:01:37Z',
  availabilityEndDateTime: '2021-12-31T20:01:37Z',
  languageTags: ['en-us'],
  platforms: ['ios'],
  state: 'published'
};

await client.api('/search/qnas')
	.post(qna);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Search\Qna;
use Microsoft\Graph\Generated\Models\Search\AnswerKeyword;
use Microsoft\Graph\Generated\Models\DevicePlatformType;
use Microsoft\Graph\Generated\Models\Search\AnswerState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Qna();
$requestBody->setDisplayName('Global Country Holidays');
$requestBody->setWebUrl('http://www.contoso.com/');
$requestBody->setDescription('The dates that Contoso offices will be closed to observe holidays. These dates may differ from the actual date of the holiday in cases where the holiday falls on a weekend.    <table>    <thead>    <tr>    <td><strong>2021 Dates</strong></td>    <td><strong>Holiday</strong></td>    </tr>    </thead>    <tbody>    <tr>        <td>January 1, 2021</td>        <td>New Year\'s Day</td>    </tr>        <tr>        <td>January 18, 2021</td>        <td>Martin Luther King Day</td>    </tr>        <tr>        <td>February 15, 2021</td>        <td>Presidents Day</td>    </tr>        <tr>        <td>May 31, 2021</td>        <td>Memorial Day</td>    </tr>        <tr>        <td>July 5, 2021</td>        <td>Independence Day</td>    </tr>        <tr>        <td>September 6, 2021</td>        <td>Labor Day</td>    </tr>        <tr>        <td>November 25, 2021 - November 26, 2021</td>        <td>Thanksgiving Day and Day after Thanksgiving</td>    </tr>    <tr>        <td>December 23, 2021 - December 24, 2021</td>        <td>Christmas Eve and Christmas Day</td>    </tr>    </tbody>    </table>');
$keywords = new AnswerKeyword();
$keywords->setKeywords(['new years day', 'martin luther king day', 'presidents day', 'memorial day', 'independence day', 'labor day', 'thanksgiving', 'christmas', 	]);
$keywords->setReservedKeywords(['holidays', 'paid days off', 	]);
$keywords->setMatchSimilarKeywords(true);
$requestBody->setKeywords($keywords);
$requestBody->setAvailabilityStartDateTime(new \DateTime('2020-09-21T20:01:37Z'));
$requestBody->setAvailabilityEndDateTime(new \DateTime('2021-12-31T20:01:37Z'));
$requestBody->setLanguageTags(['en-us', 	]);
$requestBody->setPlatforms([new DevicePlatformType('ios'),	]);
$requestBody->setState(new AnswerState('published'));

$result = $graphServiceClient->search()->qnas()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	displayName = "Global Country Holidays"
	webUrl = "http://www.contoso.com/"
	description = "The dates that Contoso offices will be closed to observe holidays. These dates may differ from the actual date of the holiday in cases where the holiday falls on a weekend.    <table>    <thead>    <tr>    <td><strong>2021 Dates</strong></td>    <td><strong>Holiday</strong></td>    </tr>    </thead>    <tbody>    <tr>        <td>January 1, 2021</td>        <td>New Year's Day</td>    </tr>        <tr>        <td>January 18, 2021</td>        <td>Martin Luther King Day</td>    </tr>        <tr>        <td>February 15, 2021</td>        <td>Presidents Day</td>    </tr>        <tr>        <td>May 31, 2021</td>        <td>Memorial Day</td>    </tr>        <tr>        <td>July 5, 2021</td>        <td>Independence Day</td>    </tr>        <tr>        <td>September 6, 2021</td>        <td>Labor Day</td>    </tr>        <tr>        <td>November 25, 2021 - November 26, 2021</td>        <td>Thanksgiving Day and Day after Thanksgiving</td>    </tr>    <tr>        <td>December 23, 2021 - December 24, 2021</td>        <td>Christmas Eve and Christmas Day</td>    </tr>    </tbody>    </table>"
	keywords = @{
		keywords = @(
		"new years day"
	"martin luther king day"
"presidents day"
"memorial day"
"independence day"
"labor day"
"thanksgiving"
"christmas"
)
reservedKeywords = @(
"holidays"
"paid days off"
)
matchSimilarKeywords = $true
}
availabilityStartDateTime = [System.DateTime]::Parse("2020-09-21T20:01:37Z")
availabilityEndDateTime = [System.DateTime]::Parse("2021-12-31T20:01:37Z")
languageTags = @(
"en-us"
)
platforms = @(
"ios"
)
state = "published"
}

New-MgSearchQna -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.search.qna import Qna
from msgraph.generated.models.search.answer_keyword import AnswerKeyword
from msgraph.generated.models.device_platform_type import DevicePlatformType
from msgraph.generated.models.answer_state import AnswerState
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Qna(
	display_name = "Global Country Holidays",
	web_url = "http://www.contoso.com/",
	description = "The dates that Contoso offices will be closed to observe holidays. These dates may differ from the actual date of the holiday in cases where the holiday falls on a weekend.    <table>    <thead>    <tr>    <td><strong>2021 Dates</strong></td>    <td><strong>Holiday</strong></td>    </tr>    </thead>    <tbody>    <tr>        <td>January 1, 2021</td>        <td>New Year's Day</td>    </tr>        <tr>        <td>January 18, 2021</td>        <td>Martin Luther King Day</td>    </tr>        <tr>        <td>February 15, 2021</td>        <td>Presidents Day</td>    </tr>        <tr>        <td>May 31, 2021</td>        <td>Memorial Day</td>    </tr>        <tr>        <td>July 5, 2021</td>        <td>Independence Day</td>    </tr>        <tr>        <td>September 6, 2021</td>        <td>Labor Day</td>    </tr>        <tr>        <td>November 25, 2021 - November 26, 2021</td>        <td>Thanksgiving Day and Day after Thanksgiving</td>    </tr>    <tr>        <td>December 23, 2021 - December 24, 2021</td>        <td>Christmas Eve and Christmas Day</td>    </tr>    </tbody>    </table>",
	keywords = AnswerKeyword(
		keywords = [
			"new years day",
			"martin luther king day",
			"presidents day",
			"memorial day",
			"independence day",
			"labor day",
			"thanksgiving",
			"christmas",
		],
		reserved_keywords = [
			"holidays",
			"paid days off",
		],
		match_similar_keywords = True,
	),
	availability_start_date_time = "2020-09-21T20:01:37Z",
	availability_end_date_time = "2021-12-31T20:01:37Z",
	language_tags = [
		"en-us",
	],
	platforms = [
		DevicePlatformType.IOS,
	],
	state = AnswerState.Published,
)

result = await graph_client.search.qnas.post(request_body)
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
