<!-- Source: https://learn.microsoft.com/en-us/graph/search-concept-answers -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Set up administrative search answers for users in an organization

Microsoft Search lets administrators associate search terms with meanings or web pages that are specific to their organizations and include these associations as search answers. For example, users in an organization might run into an unfamiliar acronym that represents an internal project name, or a team name that is associated with a team web page. Administrators can set up [acronyms](https://learn.microsoft.com/en-us/microsoftsearch/manage-acronyms), [bookmarks](https://learn.microsoft.com/en-us/microsoftsearch/manage-bookmarks), or [QnAs](https://learn.microsoft.com/en-us/microsoftsearch/manage-qas) in the [Microsoft 365 admin center](https://admin.microsoft.com/), under **Search & intelligence**. This enables users to use search to navigate and get familiarized with their work.

Administrators can also use the Microsoft Search API in Microsoft Graph to [programmatically manage administrative search answers](https://learn.microsoft.com/en-us/graph/api/resources/search-api-answers-overview) in the organization. These answers are displayed in Microsoft Search results when triggered by an acronym or keyword defined in the available search answer resource types: [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym), [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark), and [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna) resources.

When triggered by a defined acronym or keyword, these search answers appear at the top of the search results page in your organization.

## Example 1: Create a new acronym

The following request creates a new acronym that displays on the search results page when a user searches for it.

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
POST https://graph.microsoft.com/v1.0/search/acronyms
Content-Type: application/json

{
  "displayName": "GDPR",
  "standsFor": "General Data Protection Regulation",
  "description": "A European Union (EU) regulation on data protection and privacy in the EU and the European Economic Area (EEA) that enhances individuals' control and rights over their personal data, simplifies the regulatory environment for international business, and addresses the transfer of personal data outside the EU and EEA areas.",
  "webUrl": "http://contoso.com/GDPR",
  "state": "published"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Search;

var requestBody = new Acronym
{
	DisplayName = "GDPR",
	StandsFor = "General Data Protection Regulation",
	Description = "A European Union (EU) regulation on data protection and privacy in the EU and the European Economic Area (EEA) that enhances individuals' control and rights over their personal data, simplifies the regulatory environment for international business, and addresses the transfer of personal data outside the EU and EEA areas.",
	WebUrl = "http://contoso.com/GDPR",
	State = AnswerState.Published,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Search.Acronyms.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssearch "github.com/microsoftgraph/msgraph-sdk-go/models/search"
	  //other-imports
)

requestBody := graphmodelssearch.NewAcronym()
displayName := "GDPR"
requestBody.SetDisplayName(&displayName) 
standsFor := "General Data Protection Regulation"
requestBody.SetStandsFor(&standsFor) 
description := "A European Union (EU) regulation on data protection and privacy in the EU and the European Economic Area (EEA) that enhances individuals' control and rights over their personal data, simplifies the regulatory environment for international business, and addresses the transfer of personal data outside the EU and EEA areas."
requestBody.SetDescription(&description) 
webUrl := "http://contoso.com/GDPR"
requestBody.SetWebUrl(&webUrl) 
state := graphmodels.PUBLISHED_ANSWERSTATE 
requestBody.SetState(&state) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
acronyms, err := graphClient.Search().Acronyms().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.search.Acronym acronym = new com.microsoft.graph.models.search.Acronym();
acronym.setDisplayName("GDPR");
acronym.setStandsFor("General Data Protection Regulation");
acronym.setDescription("A European Union (EU) regulation on data protection and privacy in the EU and the European Economic Area (EEA) that enhances individuals' control and rights over their personal data, simplifies the regulatory environment for international business, and addresses the transfer of personal data outside the EU and EEA areas.");
acronym.setWebUrl("http://contoso.com/GDPR");
acronym.setState(com.microsoft.graph.models.search.AnswerState.Published);
com.microsoft.graph.models.search.Acronym result = graphClient.search().acronyms().post(acronym);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const acronym = {
  displayName: 'GDPR',
  standsFor: 'General Data Protection Regulation',
  description: 'A European Union (EU) regulation on data protection and privacy in the EU and the European Economic Area (EEA) that enhances individuals\' control and rights over their personal data, simplifies the regulatory environment for international business, and addresses the transfer of personal data outside the EU and EEA areas.',
  webUrl: 'http://contoso.com/GDPR',
  state: 'published'
};

await client.api('/search/acronyms')
	.post(acronym);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Search\Acronym;
use Microsoft\Graph\Generated\Models\Search\AnswerState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Acronym();
$requestBody->setDisplayName('GDPR');
$requestBody->setStandsFor('General Data Protection Regulation');
$requestBody->setDescription('A European Union (EU) regulation on data protection and privacy in the EU and the European Economic Area (EEA) that enhances individuals\' control and rights over their personal data, simplifies the regulatory environment for international business, and addresses the transfer of personal data outside the EU and EEA areas.');
$requestBody->setWebUrl('http://contoso.com/GDPR');
$requestBody->setState(new AnswerState('published'));

$result = $graphServiceClient->search()->acronyms()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	displayName = "GDPR"
	standsFor = "General Data Protection Regulation"
	description = "A European Union (EU) regulation on data protection and privacy in the EU and the European Economic Area (EEA) that enhances individuals' control and rights over their personal data, simplifies the regulatory environment for international business, and addresses the transfer of personal data outside the EU and EEA areas."
	webUrl = "http://contoso.com/GDPR"
	state = "published"
}

New-MgSearchAcronym -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.search.acronym import Acronym
from msgraph.generated.models.answer_state import AnswerState
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Acronym(
	display_name = "GDPR",
	stands_for = "General Data Protection Regulation",
	description = "A European Union (EU) regulation on data protection and privacy in the EU and the European Economic Area (EEA) that enhances individuals' control and rights over their personal data, simplifies the regulatory environment for international business, and addresses the transfer of personal data outside the EU and EEA areas.",
	web_url = "http://contoso.com/GDPR",
	state = AnswerState.Published,
)

result = await graph_client.search.acronyms.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "733b26d5-af76-4eea-ac69-1a0ce8716897"
}
```

## Example 2: Create a new bookmark

The following request creates a new bookmark that displays on the search results page when a user searches for at least one of its keywords.

### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/search/bookmarks
Content-Type: application/json

{
  "displayName": "Contoso Install Site",
  "webUrl": "http://www.contoso.com/",
  "description": "Try or buy Contoso for Home or Business and view product information",
  "keywords":  {
    "keywords": ["Contoso", "install"],
    "reservedKeywords": ["Contoso"],
    "matchSimilarKeywords": true
  },
  "state": "published"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Search;

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
			"Contoso",
		},
		MatchSimilarKeywords = true,
	},
	State = AnswerState.Published,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Search.Bookmarks.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssearch "github.com/microsoftgraph/msgraph-sdk-go/models/search"
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
	"Contoso",
}
keywords.SetReservedKeywords(reservedKeywords)
matchSimilarKeywords := true
keywords.SetMatchSimilarKeywords(&matchSimilarKeywords) 
requestBody.SetKeywords(keywords)
state := graphmodels.PUBLISHED_ANSWERSTATE 
requestBody.SetState(&state) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
bookmarks, err := graphClient.Search().Bookmarks().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
reservedKeywords.add("Contoso");
keywords.setReservedKeywords(reservedKeywords);
keywords.setMatchSimilarKeywords(true);
bookmark.setKeywords(keywords);
bookmark.setState(com.microsoft.graph.models.search.AnswerState.Published);
com.microsoft.graph.models.search.Bookmark result = graphClient.search().bookmarks().post(bookmark);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
    reservedKeywords: ['Contoso'],
    matchSimilarKeywords: true
  },
  state: 'published'
};

await client.api('/search/bookmarks')
	.post(bookmark);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Search\Bookmark;
use Microsoft\Graph\Generated\Models\Search\AnswerKeyword;
use Microsoft\Graph\Generated\Models\Search\AnswerState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Bookmark();
$requestBody->setDisplayName('Contoso Install Site');
$requestBody->setWebUrl('http://www.contoso.com/');
$requestBody->setDescription('Try or buy Contoso for Home or Business and view product information');
$keywords = new AnswerKeyword();
$keywords->setKeywords(['Contoso', 'install', 	]);
$keywords->setReservedKeywords(['Contoso', 	]);
$keywords->setMatchSimilarKeywords(true);
$requestBody->setKeywords($keywords);
$requestBody->setState(new AnswerState('published'));

$result = $graphServiceClient->search()->bookmarks()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
"Contoso"
)
matchSimilarKeywords = $true
}
state = "published"
}

New-MgSearchBookmark -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.search.bookmark import Bookmark
from msgraph.generated.models.search.answer_keyword import AnswerKeyword
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
			"Contoso",
		],
		match_similar_keywords = True,
	),
	state = AnswerState.Published,
)

result = await graph_client.search.bookmarks.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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

## Next steps

- Be familiar with the Search API scenarios and capabilities: [Microsoft Search API overview](https://learn.microsoft.com/en-us/graph/search-concept-overview).
- Explore the search APIs in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
- [Use the Microsoft Search API to manage administrative answers](https://learn.microsoft.com/en-us/graph/api/resources/search-api-answers-overview).
