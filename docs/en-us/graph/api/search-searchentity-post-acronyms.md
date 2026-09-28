<!-- Source: https://learn.microsoft.com/en-us/graph/api/search-searchentity-post-acronyms?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create acronym

Namespace: microsoft.graph.search

Create a new [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) object.

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
POST /search/acronyms
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) object.

The following table shows the properties that are available when you create an [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A brief description of the acronym that gives users more information about the acronym and what it stands for. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| displayName | String | The actual short form or acronym. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |
| standsFor | String | What the acronym stands for. |
| state | microsoft.graph.search.answerState | State of the acronym. The possible values are: `published`, `draft`, `excluded`, `unknownFutureValue`. |
| webUrl | String | The URL of the page or website where users can go for more information about the acronym. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |

## Response

If successful, this method returns a `201 Created` response code with the ID of the acronym created.

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
POST https://graph.microsoft.com/v1.0/search/acronyms
Content-Type: application/json

{
  "displayName": "DNN",
  "standsFor": "Deep Neural Network",
  "description": "A deep neural network is a neural network with a certain level of complexity, a neural network with more than two layers.",
  "webUrl": "http://microsoft.com/deep-neural-network",
  "state": "draft"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Search;

var requestBody = new Acronym
{
	DisplayName = "DNN",
	StandsFor = "Deep Neural Network",
	Description = "A deep neural network is a neural network with a certain level of complexity, a neural network with more than two layers.",
	WebUrl = "http://microsoft.com/deep-neural-network",
	State = AnswerState.Draft,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Search.Acronyms.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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
displayName := "DNN"
requestBody.SetDisplayName(&displayName) 
standsFor := "Deep Neural Network"
requestBody.SetStandsFor(&standsFor) 
description := "A deep neural network is a neural network with a certain level of complexity, a neural network with more than two layers."
requestBody.SetDescription(&description) 
webUrl := "http://microsoft.com/deep-neural-network"
requestBody.SetWebUrl(&webUrl) 
state := graphmodels.DRAFT_ANSWERSTATE 
requestBody.SetState(&state) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
acronyms, err := graphClient.Search().Acronyms().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.search.Acronym acronym = new com.microsoft.graph.models.search.Acronym();
acronym.setDisplayName("DNN");
acronym.setStandsFor("Deep Neural Network");
acronym.setDescription("A deep neural network is a neural network with a certain level of complexity, a neural network with more than two layers.");
acronym.setWebUrl("http://microsoft.com/deep-neural-network");
acronym.setState(com.microsoft.graph.models.search.AnswerState.Draft);
com.microsoft.graph.models.search.Acronym result = graphClient.search().acronyms().post(acronym);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const acronym = {
  displayName: 'DNN',
  standsFor: 'Deep Neural Network',
  description: 'A deep neural network is a neural network with a certain level of complexity, a neural network with more than two layers.',
  webUrl: 'http://microsoft.com/deep-neural-network',
  state: 'draft'
};

await client.api('/search/acronyms')
	.post(acronym);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Search\Acronym;
use Microsoft\Graph\Generated\Models\Search\AnswerState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Acronym();
$requestBody->setDisplayName('DNN');
$requestBody->setStandsFor('Deep Neural Network');
$requestBody->setDescription('A deep neural network is a neural network with a certain level of complexity, a neural network with more than two layers.');
$requestBody->setWebUrl('http://microsoft.com/deep-neural-network');
$requestBody->setState(new AnswerState('draft'));

$result = $graphServiceClient->search()->acronyms()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	displayName = "DNN"
	standsFor = "Deep Neural Network"
	description = "A deep neural network is a neural network with a certain level of complexity, a neural network with more than two layers."
	webUrl = "http://microsoft.com/deep-neural-network"
	state = "draft"
}

New-MgSearchAcronym -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.search.acronym import Acronym
from msgraph.generated.models.answer_state import AnswerState
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Acronym(
	display_name = "DNN",
	stands_for = "Deep Neural Network",
	description = "A deep neural network is a neural network with a certain level of complexity, a neural network with more than two layers.",
	web_url = "http://microsoft.com/deep-neural-network",
	state = AnswerState.Draft,
)

result = await graph_client.search.acronyms.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "733b26d5-af76-4eea-ac69-1a0ce8716897"
}
```
