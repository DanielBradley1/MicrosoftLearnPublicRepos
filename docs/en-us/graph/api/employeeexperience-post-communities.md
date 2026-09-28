<!-- Source: https://learn.microsoft.com/en-us/graph/api/employeeexperience-post-communities?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create community

Namespace: microsoft.graph

Create a new [community](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0) in Viva Engage.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Community.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Community.ReadWrite.All | Not available. |

## HTTP request

```http
POST /employeeExperience/communities
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [community](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0) object.

You can specify the following properties when you create a **community**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the community. Maximum length is 1,024 characters. |
| displayName | String | The name of the community. Maximum length is 255 characters. |
| privacy | [communityPrivacy](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0#communityprivacy-values) | Defines the privacy level of the community. The possible values are: `public`, `private`, `unknownFutureValue`. |

## Response

If successful, this method returns a `202 Accepted` response code. The response also contains an `Operation-Location` header with a link to the [engagementAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/engagementasyncoperation?view=graph-rest-1.0). You can poll the `Operation-Location` endpoint for status update on the creation operation.

## Examples

### Example 1: Delegated permissions

#### Request

The following example shows a request with delegated permissions. When the **owners** property isn't specified in the request body, the calling user is automatically assigned as the community owner.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/employeeExperience/communities
Content-Type: application/json

{
  "displayName": "Financial Advice for Software Engineers",
  "description": "A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.",
  "privacy": "public"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Community
{
	DisplayName = "Financial Advice for Software Engineers",
	Description = "A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.",
	Privacy = CommunityPrivacy.Public,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.Communities.PostAsync(requestBody);
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

requestBody := graphmodels.NewCommunity()
displayName := "Financial Advice for Software Engineers"
requestBody.SetDisplayName(&displayName) 
description := "A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients."
requestBody.SetDescription(&description) 
privacy := graphmodels.PUBLIC_COMMUNITYPRIVACY 
requestBody.SetPrivacy(&privacy) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
communities, err := graphClient.EmployeeExperience().Communities().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Community community = new Community();
community.setDisplayName("Financial Advice for Software Engineers");
community.setDescription("A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.");
community.setPrivacy(CommunityPrivacy.Public);
Community result = graphClient.employeeExperience().communities().post(community);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const community = {
  displayName: 'Financial Advice for Software Engineers',
  description: 'A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.',
  privacy: 'public'
};

await client.api('/employeeExperience/communities')
	.post(community);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Community;
use Microsoft\Graph\Generated\Models\CommunityPrivacy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Community();
$requestBody->setDisplayName('Financial Advice for Software Engineers');
$requestBody->setDescription('A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.');
$requestBody->setPrivacy(new CommunityPrivacy('public'));

$result = $graphServiceClient->employeeExperience()->communities()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.community import Community
from msgraph.generated.models.community_privacy import CommunityPrivacy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Community(
	display_name = "Financial Advice for Software Engineers",
	description = "A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.",
	privacy = CommunityPrivacy.Public,
)

result = await graph_client.employee_experience.communities.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: https://graph.microsoft.com/v1.0/employeeExperience/engagementAsyncOperations('3a6fdce1-c261-48bc-89de-1cfef658c0d5')
```

### Example 2: Application permissions

#### Request

The following example shows a minimal request that requires application permissions. If the **owners** property isn't specified in the request body, the request fails.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/employeeExperience/communities
Content-Type: application/json

{
  "displayName": "Financial Advice for Software Engineers",
  "description": "A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.",
  "privacy": "public",
  "owners@odata.bind": [
    "https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Community
{
	DisplayName = "Financial Advice for Software Engineers",
	Description = "A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.",
	Privacy = CommunityPrivacy.Public,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"owners@odata.bind" , new List<string>
			{
				"https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2",
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.Communities.PostAsync(requestBody);
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

requestBody := graphmodels.NewCommunity()
displayName := "Financial Advice for Software Engineers"
requestBody.SetDisplayName(&displayName) 
description := "A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients."
requestBody.SetDescription(&description) 
privacy := graphmodels.PUBLIC_COMMUNITYPRIVACY 
requestBody.SetPrivacy(&privacy) 
additionalData := map[string]interface{}{
	odataBind := []string {
		"https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2",
	}
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
communities, err := graphClient.EmployeeExperience().Communities().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Community community = new Community();
community.setDisplayName("Financial Advice for Software Engineers");
community.setDescription("A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.");
community.setPrivacy(CommunityPrivacy.Public);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<String> ownersOdataBind = new LinkedList<String>();
ownersOdataBind.add("https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2");
additionalData.put("owners@odata.bind", ownersOdataBind);
community.setAdditionalData(additionalData);
Community result = graphClient.employeeExperience().communities().post(community);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const community = {
  displayName: 'Financial Advice for Software Engineers',
  description: 'A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.',
  privacy: 'public',
  'owners@odata.bind': [
    'https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2'
  ]
};

await client.api('/employeeExperience/communities')
	.post(community);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Community;
use Microsoft\Graph\Generated\Models\CommunityPrivacy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Community();
$requestBody->setDisplayName('Financial Advice for Software Engineers');
$requestBody->setDescription('A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.');
$requestBody->setPrivacy(new CommunityPrivacy('public'));
$additionalData = [
	'owners@odata.bind' => [
'https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2', ],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->employeeExperience()->communities()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.community import Community
from msgraph.generated.models.community_privacy import CommunityPrivacy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Community(
	display_name = "Financial Advice for Software Engineers",
	description = "A community where financial advisors who represent customers from software engineering profession can discuss advice and suggestions for their clients.",
	privacy = CommunityPrivacy.Public,
	additional_data = {
			"owners@odata_bind" : [
				"https://graph.microsoft.com/v1.0/users/26be1845-4119-4801-a799-aea79d09f1a2",
			],
	}
)

result = await graph_client.employee_experience.communities.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: https://graph.microsoft.com/v1.0/employeeExperience/engagementAsyncOperations('3a6fdce1-c261-48bc-89de-1cfef658c0d5')
```
