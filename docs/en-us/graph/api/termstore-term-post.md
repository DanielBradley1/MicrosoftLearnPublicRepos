<!-- Source: https://learn.microsoft.com/en-us/graph/api/termstore-term-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create term

Namespace: microsoft.graph.termStore

Create a new [term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) object.

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
POST /sites/{site-id}/termStore/sets/{set-id}/children
POST /sites/{site-id}/termStore/sets/{set-id}/terms/{term-id}/children
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) object.

| Property | Type | Description |
| :--- | :--- | :--- |
| labels | [microsoft.graph.termStore.localizedLabel](https://learn.microsoft.com/en-us/graph/api/resources/termstore-localizedlabel?view=graph-rest-1.0) collection | Label for the term to be created. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/sites/microsoft.sharepoint.com,b9b0bc03-cbc4-40d2-aba9-2c9dd9821ddf,6a742cee-9216-4db5-8046-13a595684e74/termStore/sets/462bd0ae-30bb-4c58-845c-761ff6481ac1/children
Content-Type: application/json

{
  "labels": [
    {
      "languageTag" : "en-US",
      "name" : "Car",
      "isDefault" : true
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.TermStore;

var requestBody = new Term
{
	Labels = new List<LocalizedLabel>
	{
		new LocalizedLabel
		{
			LanguageTag = "en-US",
			Name = "Car",
			IsDefault = true,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].TermStore.Sets["{set-id}"].Children.PostAsync(requestBody);
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

requestBody := graphmodelstermstore.NewTerm()


localizedLabel := graphmodelstermstore.NewLocalizedLabel()
languageTag := "en-US"
localizedLabel.SetLanguageTag(&languageTag) 
name := "Car"
localizedLabel.SetName(&name) 
isDefault := true
localizedLabel.SetIsDefault(&isDefault) 

labels := []graphmodelstermstore.LocalizedLabelable {
	localizedLabel,
}
requestBody.SetLabels(labels)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
children, err := graphClient.Sites().BySiteId("site-id").TermStore().Sets().BySetId("set-id").Children().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.termstore.Term term = new com.microsoft.graph.models.termstore.Term();
LinkedList<com.microsoft.graph.models.termstore.LocalizedLabel> labels = new LinkedList<com.microsoft.graph.models.termstore.LocalizedLabel>();
com.microsoft.graph.models.termstore.LocalizedLabel localizedLabel = new com.microsoft.graph.models.termstore.LocalizedLabel();
localizedLabel.setLanguageTag("en-US");
localizedLabel.setName("Car");
localizedLabel.setIsDefault(true);
labels.add(localizedLabel);
term.setLabels(labels);
com.microsoft.graph.models.termstore.Term result = graphClient.sites().bySiteId("{site-id}").termStore().sets().bySetId("{set-id}").children().post(term);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const term = {
  labels: [
    {
      languageTag: 'en-US',
      name: 'Car',
      isDefault: true
    }
  ]
};

await client.api('/sites/microsoft.sharepoint.com,b9b0bc03-cbc4-40d2-aba9-2c9dd9821ddf,6a742cee-9216-4db5-8046-13a595684e74/termStore/sets/462bd0ae-30bb-4c58-845c-761ff6481ac1/children')
	.post(term);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TermStore\Term;
use Microsoft\Graph\Generated\Models\TermStore\LocalizedLabel;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Term();
$labelsLocalizedLabel1 = new LocalizedLabel();
$labelsLocalizedLabel1->setLanguageTag('en-US');
$labelsLocalizedLabel1->setName('Car');
$labelsLocalizedLabel1->setIsDefault(true);
$labelsArray []= $labelsLocalizedLabel1;
$requestBody->setLabels($labelsArray);


$result = $graphServiceClient->sites()->bySiteId('site-id')->termStore()->sets()->bySetId('set-id')->children()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	labels = @(
		@{
			languageTag = "en-US"
			name = "Car"
			isDefault = $true
		}
	)
}

New-MgSiteTermStoreSetChild -SiteId $siteId -SetId $setId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.term_store.term import Term
from msgraph.generated.models.term_store.localized_label import LocalizedLabel
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Term(
	labels = [
		LocalizedLabel(
			language_tag = "en-US",
			name = "Car",
			is_default = True,
		),
	],
)

result = await graph_client.sites.by_site_id('site-id').term_store.sets.by_set_id('set-id').children.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "createdDateTime": "2019-06-21T20:01:37Z",
  "id": "8ed8c9ea-7052-4c1d-a4d7-b9c10bffea6f",
  "labels" : [
      {
          "name" : "Car",
          "languageTag" : "en-US",
          "isDefault" : true
      }
  ],
  "lastModifiedDateTime": "2019-06-21T20:01:37Z"
}
```
