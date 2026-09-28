<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-tags?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# Create tags

Namespace: microsoft.graph.security

Create a new [ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.Read.All | eDiscovery.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.Read.All | eDiscovery.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Purview role](https://learn.microsoft.com/en-us/purview/edisc-permissions) through one of the following options:

- **eDiscovery Manager**. Allows members to access review sets in eDiscovery cases they create and are members of. **This is the least privileged option for accessing review sets in their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to access review sets in all eDiscovery cases in the organization.
- **Reviewer**. Provides read-only access to review sets within eDiscovery cases where the user is a member. Reviewers can view and tag documents but cannot perform other case management tasks.

The Review role allows users to access review sets in eDiscovery cases they are members of. Users can view and tag documents in review sets but cannot preview search results or perform other search or case management tasks.

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
POST /security/cases/ediscoveryCases/{ediscoveryCaseId}/tags
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) object.

You can specify the following properties when you create an **ediscoveryReviewTag**. The **parent** relationship can also be specified.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the tag. Required. |
| description | String | Description of the tag. Optional. |
| childSelectability | microsoft.graph.security.childSelectability | This value controls whether the UX presents the tags as checkboxes or a radio button group. The possible values are: `One`, `Many`. Required. |

## Response

If successful, this method returns a `201 Created` response code and an [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a tag

#### Request

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/58399dff-cebe-478f-b1af-d3227f1fd645/tags

{
    "displayName": "My tag API",
    "description": "Use Graph API to create tags",
    "childSelectability": "Many",
	"parent@odata.bind":
	"https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/{ediscoveryCaseID}/tags/{parentTagID}"
	
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new EdiscoveryReviewTag
{
	DisplayName = "My tag API",
	Description = "Use Graph API to create tags",
	ChildSelectability = ChildSelectability.Many,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"parent@odata.bind" , "https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/{ediscoveryCaseID}/tags/{parentTagID}"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Tags.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewEdiscoveryReviewTag()
displayName := "My tag API"
requestBody.SetDisplayName(&displayName) 
description := "Use Graph API to create tags"
requestBody.SetDescription(&description) 
childSelectability := graphmodels.MANY_CHILDSELECTABILITY 
requestBody.SetChildSelectability(&childSelectability) 
additionalData := map[string]interface{}{
	"parent@odata.bind" : "https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/{ediscoveryCaseID}/tags/{parentTagID}", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tags, err := graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Tags().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.EdiscoveryReviewTag ediscoveryReviewTag = new com.microsoft.graph.models.security.EdiscoveryReviewTag();
ediscoveryReviewTag.setDisplayName("My tag API");
ediscoveryReviewTag.setDescription("Use Graph API to create tags");
ediscoveryReviewTag.setChildSelectability(com.microsoft.graph.models.security.ChildSelectability.Many);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("parent@odata.bind", "https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/{ediscoveryCaseID}/tags/{parentTagID}");
ediscoveryReviewTag.setAdditionalData(additionalData);
com.microsoft.graph.models.security.EdiscoveryReviewTag result = graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").tags().post(ediscoveryReviewTag);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ediscoveryReviewTag = {
    displayName: 'My tag API',
    description: 'Use Graph API to create tags',
    childSelectability: 'Many',
	'parent@odata.bind':
	'https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/{ediscoveryCaseID}/tags/{parentTagID}'
	
};

await client.api('/security/cases/ediscoveryCases/58399dff-cebe-478f-b1af-d3227f1fd645/tags')
	.post(ediscoveryReviewTag);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\EdiscoveryReviewTag;
use Microsoft\Graph\Generated\Models\Security\ChildSelectability;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EdiscoveryReviewTag();
$requestBody->setDisplayName('My tag API');
$requestBody->setDescription('Use Graph API to create tags');
$requestBody->setChildSelectability(new ChildSelectability('many'));
$additionalData = [
	'parent@odata.bind' => 'https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/{ediscoveryCaseID}/tags/{parentTagID}',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->tags()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "My tag API"
	description = "Use Graph API to create tags"
	childSelectability = "Many"
	"parent@odata.bind" = "https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/{ediscoveryCaseID}/tags/{parentTagID}"
}

New-MgSecurityCaseEdiscoveryCaseTag -EdiscoveryCaseId $ediscoveryCaseId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.ediscovery_review_tag import EdiscoveryReviewTag
from msgraph.generated.models.child_selectability import ChildSelectability
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EdiscoveryReviewTag(
	display_name = "My tag API",
	description = "Use Graph API to create tags",
	child_selectability = ChildSelectability.Many,
	additional_data = {
			"parent@odata_bind" : "https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/{ediscoveryCaseID}/tags/{parentTagID}",
	}
)

result = await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').tags.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('58399dff-cebe-478f-b1af-d3227f1fd645')/tags/$entity",
    "displayName": "My tag API",
    "description": "Use Graph API to create tags",
    "lastModifiedDateTime": "2022-05-23T19:58:26.1573076Z",
    "childSelectability": "Many",
    "id": "7c6cc351-fb90-431f-8562-1b607a3144a4",
    "createdBy": {
        "user": {
            "id": "c25c3914-f9f7-43ee-9cba-a25377e0cec6",
            "displayName": "MOD Administrator",
            "userPrincipalName": "admin@contoso.com"
        },
        "application": {
            "id": "de8bc8b5-d9f9-48b1-a8ad-b748da725064",
            "displayName": "Graph Explorer"
        }
    }
}
```

### Example 2: Create a tag with a parent

#### Request

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/58399dff-cebe-478f-b1af-d3227f1fd645/tags

{
    "displayName": "My tag API",
    "description": "Use Graph API to create tags",
    "childSelectability": "Many",
    "parent@odata.bind":""
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new EdiscoveryReviewTag
{
	DisplayName = "My tag API",
	Description = "Use Graph API to create tags",
	ChildSelectability = ChildSelectability.Many,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"parent@odata.bind" , ""
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].Tags.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewEdiscoveryReviewTag()
displayName := "My tag API"
requestBody.SetDisplayName(&displayName) 
description := "Use Graph API to create tags"
requestBody.SetDescription(&description) 
childSelectability := graphmodels.MANY_CHILDSELECTABILITY 
requestBody.SetChildSelectability(&childSelectability) 
additionalData := map[string]interface{}{
	"parent@odata.bind" : "", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tags, err := graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").Tags().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.EdiscoveryReviewTag ediscoveryReviewTag = new com.microsoft.graph.models.security.EdiscoveryReviewTag();
ediscoveryReviewTag.setDisplayName("My tag API");
ediscoveryReviewTag.setDescription("Use Graph API to create tags");
ediscoveryReviewTag.setChildSelectability(com.microsoft.graph.models.security.ChildSelectability.Many);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("parent@odata.bind", "");
ediscoveryReviewTag.setAdditionalData(additionalData);
com.microsoft.graph.models.security.EdiscoveryReviewTag result = graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").tags().post(ediscoveryReviewTag);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ediscoveryReviewTag = {
    displayName: 'My tag API',
    description: 'Use Graph API to create tags',
    childSelectability: 'Many',
    'parent@odata.bind':''
};

await client.api('/security/cases/ediscoveryCases/58399dff-cebe-478f-b1af-d3227f1fd645/tags')
	.post(ediscoveryReviewTag);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\EdiscoveryReviewTag;
use Microsoft\Graph\Generated\Models\Security\ChildSelectability;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EdiscoveryReviewTag();
$requestBody->setDisplayName('My tag API');
$requestBody->setDescription('Use Graph API to create tags');
$requestBody->setChildSelectability(new ChildSelectability('many'));
$additionalData = [
	'parent@odata.bind' => '',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->tags()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	displayName = "My tag API"
	description = "Use Graph API to create tags"
	childSelectability = "Many"
	"parent@odata.bind" = ""
}

New-MgSecurityCaseEdiscoveryCaseTag -EdiscoveryCaseId $ediscoveryCaseId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.ediscovery_review_tag import EdiscoveryReviewTag
from msgraph.generated.models.child_selectability import ChildSelectability
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EdiscoveryReviewTag(
	display_name = "My tag API",
	description = "Use Graph API to create tags",
	child_selectability = ChildSelectability.Many,
	additional_data = {
			"parent@odata_bind" : "",
	}
)

result = await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').tags.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('58399dff-cebe-478f-b1af-d3227f1fd645')/tags/$entity",
    "displayName": "My tag API",
    "description": "Use Graph API to create tags",
    "lastModifiedDateTime": "2022-05-23T19:58:26.1573076Z",
    "childSelectability": "Many",
    "id": "7c6cc351-fb90-431f-8562-1b607a3144a4",
    "createdBy": {
        "user": {
            "id": "c25c3914-f9f7-43ee-9cba-a25377e0cec6",
            "displayName": "MOD Administrator",
            "userPrincipalName": "admin@contoso.com"
        },
        "application": {
            "id": "de8bc8b5-d9f9-48b1-a8ad-b748da725064",
            "displayName": "Graph Explorer"
        }
    }
}
```
