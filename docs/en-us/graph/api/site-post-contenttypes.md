<!-- Source: https://learn.microsoft.com/en-us/graph/api/site-post-contenttypes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create a content type

Namespace: microsoft.graph

Create a new [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Manage.All | Sites.FullControl.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Manage.All | Sites.FullControl.All |

## HTTP request

```http
POST /sites/{site-id}/contentTypes
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) resource to create.

## Response

If successful, this method returns a `201 Created` response code and a [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) object in the response body.

## Example

The following example shows how to create a new generic content type.

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
POST https://graph.microsoft.com/v1.0/sites/{id}/contentTypes
Content-Type: application/json

{
    "name": "docSet",
    "description": "custom docset",
    "base": {
        "name": "Document Set",
        "id": "0x0120D520"
    },
    "group": "Document Set Content Types" 
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ContentType
{
	Name = "docSet",
	Description = "custom docset",
	Base = new ContentType
	{
		Name = "Document Set",
		Id = "0x0120D520",
	},
	Group = "Document Set Content Types",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].ContentTypes.PostAsync(requestBody);
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

requestBody := graphmodels.NewContentType()
name := "docSet"
requestBody.SetName(&name) 
description := "custom docset"
requestBody.SetDescription(&description) 
base := graphmodels.NewContentType()
name := "Document Set"
base.SetName(&name) 
id := "0x0120D520"
base.SetId(&id) 
requestBody.SetBase(base)
group := "Document Set Content Types"
requestBody.SetGroup(&group) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
contentTypes, err := graphClient.Sites().BySiteId("site-id").ContentTypes().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ContentType contentType = new ContentType();
contentType.setName("docSet");
contentType.setDescription("custom docset");
ContentType base = new ContentType();
base.setName("Document Set");
base.setId("0x0120D520");
contentType.setBase(base);
contentType.setGroup("Document Set Content Types");
ContentType result = graphClient.sites().bySiteId("{site-id}").contentTypes().post(contentType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const contentType = {
    name: 'docSet',
    description: 'custom docset',
    base: {
        name: 'Document Set',
        id: '0x0120D520'
    },
    group: 'Document Set Content Types' 
};

await client.api('/sites/{id}/contentTypes')
	.post(contentType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ContentType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ContentType();
$requestBody->setName('docSet');
$requestBody->setDescription('custom docset');
$base = new ContentType();
$base->setName('Document Set');
$base->setId('0x0120D520');
$requestBody->setBase($base);
$requestBody->setGroup('Document Set Content Types');

$result = $graphServiceClient->sites()->bySiteId('site-id')->contentTypes()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	name = "docSet"
	description = "custom docset"
	base = @{
		name = "Document Set"
		id = "0x0120D520"
	}
	group = "Document Set Content Types"
}

New-MgSiteContentType -SiteId $siteId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.content_type import ContentType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ContentType(
	name = "docSet",
	description = "custom docset",
	base = ContentType(
		name = "Document Set",
		id = "0x0120D520",
	),
	group = "Document Set Content Types",
)

result = await graph_client.sites.by_site_id('site-id').content_types.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "0x01002A2479FF33DD4BC3B1533A012B653717",
  "name": "docSet",
  "group":"Document Set Content Types",
  "description" : "custom docset",
  "base": {
        "name": "Document Set",
        "id": "0x0120D520"
   }
}
```
