<!-- Source: https://learn.microsoft.com/en-us/graph/api/termstore-set-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create termStore set

Namespace: microsoft.graph.termStore

Create a new [set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TermStore.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /sites/{site-id}/termStore/sets
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) object.

| Property | Type | Description |
| :--- | :--- | :--- |
| localizedNames | [microsoft.graph.termStore.localizedName](https://learn.microsoft.com/en-us/graph/api/resources/termstore-localizedname?view=graph-rest-1.0) collection | Name of the set to be created. |
| parentGroup | [microsoft.graph.termStore.group](https://learn.microsoft.com/en-us/graph/api/resources/termstore-group?view=graph-rest-1.0) | termstore-group under which the set needs to be created. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.termStore.set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/sites/6a742cee-9216-4db5-8046-13a595684e74/termStore/sets
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.termStore.set",
  "parentGroup":{
      "id": "fc733b51-10f1-40fd-b784-dc6d1e42804b"
   },
   "localizedNames" : [
      {
        "languageTag" : "en-US",
        "name" : "Department"
      }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.TermStore;

var requestBody = new Set
{
	OdataType = "#microsoft.graph.termStore.set",
	ParentGroup = new Group
	{
		Id = "fc733b51-10f1-40fd-b784-dc6d1e42804b",
	},
	LocalizedNames = new List<LocalizedName>
	{
		new LocalizedName
		{
			LanguageTag = "en-US",
			Name = "Department",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].TermStore.Sets.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelstermstore "github.com/microsoftgraph/msgraph-sdk-go/models/termstore"
	  //other-imports
)

requestBody := graphmodelstermstore.NewSet()
parentGroup := graphmodelstermstore.NewGroup()
id := "fc733b51-10f1-40fd-b784-dc6d1e42804b"
parentGroup.SetId(&id) 
requestBody.SetParentGroup(parentGroup)


localizedName := graphmodelstermstore.NewLocalizedName()
languageTag := "en-US"
localizedName.SetLanguageTag(&languageTag) 
name := "Department"
localizedName.SetName(&name) 

localizedNames := []graphmodelstermstore.LocalizedNameable {
	localizedName,
}
requestBody.SetLocalizedNames(localizedNames)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sets, err := graphClient.Sites().BySiteId("site-id").TermStore().Sets().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.termstore.Set set = new com.microsoft.graph.models.termstore.Set();
set.setOdataType("#microsoft.graph.termStore.set");
com.microsoft.graph.models.termstore.Group parentGroup = new com.microsoft.graph.models.termstore.Group();
parentGroup.setId("fc733b51-10f1-40fd-b784-dc6d1e42804b");
set.setParentGroup(parentGroup);
LinkedList<com.microsoft.graph.models.termstore.LocalizedName> localizedNames = new LinkedList<com.microsoft.graph.models.termstore.LocalizedName>();
com.microsoft.graph.models.termstore.LocalizedName localizedName = new com.microsoft.graph.models.termstore.LocalizedName();
localizedName.setLanguageTag("en-US");
localizedName.setName("Department");
localizedNames.add(localizedName);
set.setLocalizedNames(localizedNames);
com.microsoft.graph.models.termstore.Set result = graphClient.sites().bySiteId("{site-id}").termStore().sets().post(set);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const set = {
  '@odata.type': '#microsoft.graph.termStore.set',
  parentGroup: {
      id: 'fc733b51-10f1-40fd-b784-dc6d1e42804b'
   },
   localizedNames: [
      {
        languageTag: 'en-US',
        name: 'Department'
      }
  ]
};

await client.api('/sites/6a742cee-9216-4db5-8046-13a595684e74/termStore/sets')
	.post(set);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TermStore\Set;
use Microsoft\Graph\Generated\Models\TermStore\Group;
use Microsoft\Graph\Generated\Models\TermStore\LocalizedName;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Set();
$requestBody->setOdataType('#microsoft.graph.termStore.set');
$parentGroup = new Group();
$parentGroup->setId('fc733b51-10f1-40fd-b784-dc6d1e42804b');
$requestBody->setParentGroup($parentGroup);
$localizedNamesLocalizedName1 = new LocalizedName();
$localizedNamesLocalizedName1->setLanguageTag('en-US');
$localizedNamesLocalizedName1->setName('Department');
$localizedNamesArray []= $localizedNamesLocalizedName1;
$requestBody->setLocalizedNames($localizedNamesArray);


$result = $graphServiceClient->sites()->bySiteId('site-id')->termStore()->sets()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	"@odata.type" = "#microsoft.graph.termStore.set"
	parentGroup = @{
		id = "fc733b51-10f1-40fd-b784-dc6d1e42804b"
	}
	localizedNames = @(
		@{
			languageTag = "en-US"
			name = "Department"
		}
	)
}

New-MgSiteTermStoreSet -SiteId $siteId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.term_store.set import Set
from msgraph.generated.models.term_store.group import Group
from msgraph.generated.models.term_store.localized_name import LocalizedName
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Set(
	odata_type = "#microsoft.graph.termStore.set",
	parent_group = Group(
		id = "fc733b51-10f1-40fd-b784-dc6d1e42804b",
	),
	localized_names = [
		LocalizedName(
			language_tag = "en-US",
			name = "Department",
		),
	],
)

result = await graph_client.sites.by_site_id('site-id').term_store.sets.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.termStore.set",
  "id": "3607e9f9-e9f9-3607-f9e9-0736f9e90736",
  "localizedNames" : [
      {
        "languageTag" : "en-US",
        "name" : "Department"
      }
  ]
}
```
