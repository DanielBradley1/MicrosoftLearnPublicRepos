<!-- Source: https://learn.microsoft.com/en-us/graph/api/contenttype-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update contentType

Namespace: microsoft.graph

Update a [content type](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0).

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
PATCH /sites/{site-id}/contentTypes/{contentType-id}
PATCH /sites/{site-id}/lists/{list-id}/contentTypes/{contentType-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) resource to update.

## Response

If successful, this method returns a `200 OK` response code and an updated [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) object in the response body.

## Example

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
PATCH https://graph.microsoft.com/v1.0/sites/{site-id}/contentTypes/{contentType-id}
Content-Type: application/json

{
    "name": "updatedCt",
	"documentSet": {
		"shouldPrefixNameToFile": true,
		"allowedContentTypes": [{
			"id": "0x0101",
			"name": "Document"
		}],
		"defaultContents": [{
				"fileName": "a.txt",
				"contentType": {
					"id": "0x0101"
				}
			},
			{
				"fileName": "b.txt",
				"contentType": {
					"id": "0x0101"
				}
			}
		],
		"sharedColumns": [{
				"name": "Description",
				"id": "cbb92da4-fd46-4c7d-af6c-3128c2a5576e"
			},
			{
				"name": "Address",
				"id": "fc2e188e-ba91-48c9-9dd3-16431afddd50"
			}
		],
		"welcomePageColumns": [{
			"name": "Address",
			"id": "fc2e188e-ba91-48c9-9dd3-16431afddd50"
		}]
	}
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ContentType
{
	Name = "updatedCt",
	DocumentSet = new DocumentSet
	{
		ShouldPrefixNameToFile = true,
		AllowedContentTypes = new List<ContentTypeInfo>
		{
			new ContentTypeInfo
			{
				Id = "0x0101",
				Name = "Document",
			},
		},
		DefaultContents = new List<DocumentSetContent>
		{
			new DocumentSetContent
			{
				FileName = "a.txt",
				ContentType = new ContentTypeInfo
				{
					Id = "0x0101",
				},
			},
			new DocumentSetContent
			{
				FileName = "b.txt",
				ContentType = new ContentTypeInfo
				{
					Id = "0x0101",
				},
			},
		},
		SharedColumns = new List<ColumnDefinition>
		{
			new ColumnDefinition
			{
				Name = "Description",
				Id = "cbb92da4-fd46-4c7d-af6c-3128c2a5576e",
			},
			new ColumnDefinition
			{
				Name = "Address",
				Id = "fc2e188e-ba91-48c9-9dd3-16431afddd50",
			},
		},
		WelcomePageColumns = new List<ColumnDefinition>
		{
			new ColumnDefinition
			{
				Name = "Address",
				Id = "fc2e188e-ba91-48c9-9dd3-16431afddd50",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].ContentTypes["{contentType-id}"].PatchAsync(requestBody);
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
name := "updatedCt"
requestBody.SetName(&name) 
documentSet := graphmodels.NewDocumentSet()
shouldPrefixNameToFile := true
documentSet.SetShouldPrefixNameToFile(&shouldPrefixNameToFile) 


contentTypeInfo := graphmodels.NewContentTypeInfo()
id := "0x0101"
contentTypeInfo.SetId(&id) 
name := "Document"
contentTypeInfo.SetName(&name) 

allowedContentTypes := []graphmodels.ContentTypeInfoable {
	contentTypeInfo,
}
documentSet.SetAllowedContentTypes(allowedContentTypes)


documentSetContent := graphmodels.NewDocumentSetContent()
fileName := "a.txt"
documentSetContent.SetFileName(&fileName) 
contentType := graphmodels.NewContentTypeInfo()
id := "0x0101"
contentType.SetId(&id) 
documentSetContent.SetContentType(contentType)
documentSetContent1 := graphmodels.NewDocumentSetContent()
fileName := "b.txt"
documentSetContent1.SetFileName(&fileName) 
contentType := graphmodels.NewContentTypeInfo()
id := "0x0101"
contentType.SetId(&id) 
documentSetContent1.SetContentType(contentType)

defaultContents := []graphmodels.DocumentSetContentable {
	documentSetContent,
	documentSetContent1,
}
documentSet.SetDefaultContents(defaultContents)


columnDefinition := graphmodels.NewColumnDefinition()
name := "Description"
columnDefinition.SetName(&name) 
id := "cbb92da4-fd46-4c7d-af6c-3128c2a5576e"
columnDefinition.SetId(&id) 
columnDefinition1 := graphmodels.NewColumnDefinition()
name := "Address"
columnDefinition1.SetName(&name) 
id := "fc2e188e-ba91-48c9-9dd3-16431afddd50"
columnDefinition1.SetId(&id) 

sharedColumns := []graphmodels.ColumnDefinitionable {
	columnDefinition,
	columnDefinition1,
}
documentSet.SetSharedColumns(sharedColumns)


columnDefinition := graphmodels.NewColumnDefinition()
name := "Address"
columnDefinition.SetName(&name) 
id := "fc2e188e-ba91-48c9-9dd3-16431afddd50"
columnDefinition.SetId(&id) 

welcomePageColumns := []graphmodels.ColumnDefinitionable {
	columnDefinition,
}
documentSet.SetWelcomePageColumns(welcomePageColumns)
requestBody.SetDocumentSet(documentSet)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
contentTypes, err := graphClient.Sites().BySiteId("site-id").ContentTypes().ByContentTypeId("contentType-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ContentType contentType = new ContentType();
contentType.setName("updatedCt");
DocumentSet documentSet = new DocumentSet();
documentSet.setShouldPrefixNameToFile(true);
LinkedList<ContentTypeInfo> allowedContentTypes = new LinkedList<ContentTypeInfo>();
ContentTypeInfo contentTypeInfo = new ContentTypeInfo();
contentTypeInfo.setId("0x0101");
contentTypeInfo.setName("Document");
allowedContentTypes.add(contentTypeInfo);
documentSet.setAllowedContentTypes(allowedContentTypes);
LinkedList<DocumentSetContent> defaultContents = new LinkedList<DocumentSetContent>();
DocumentSetContent documentSetContent = new DocumentSetContent();
documentSetContent.setFileName("a.txt");
ContentTypeInfo contentType1 = new ContentTypeInfo();
contentType1.setId("0x0101");
documentSetContent.setContentType(contentType1);
defaultContents.add(documentSetContent);
DocumentSetContent documentSetContent1 = new DocumentSetContent();
documentSetContent1.setFileName("b.txt");
ContentTypeInfo contentType2 = new ContentTypeInfo();
contentType2.setId("0x0101");
documentSetContent1.setContentType(contentType2);
defaultContents.add(documentSetContent1);
documentSet.setDefaultContents(defaultContents);
LinkedList<ColumnDefinition> sharedColumns = new LinkedList<ColumnDefinition>();
ColumnDefinition columnDefinition = new ColumnDefinition();
columnDefinition.setName("Description");
columnDefinition.setId("cbb92da4-fd46-4c7d-af6c-3128c2a5576e");
sharedColumns.add(columnDefinition);
ColumnDefinition columnDefinition1 = new ColumnDefinition();
columnDefinition1.setName("Address");
columnDefinition1.setId("fc2e188e-ba91-48c9-9dd3-16431afddd50");
sharedColumns.add(columnDefinition1);
documentSet.setSharedColumns(sharedColumns);
LinkedList<ColumnDefinition> welcomePageColumns = new LinkedList<ColumnDefinition>();
ColumnDefinition columnDefinition2 = new ColumnDefinition();
columnDefinition2.setName("Address");
columnDefinition2.setId("fc2e188e-ba91-48c9-9dd3-16431afddd50");
welcomePageColumns.add(columnDefinition2);
documentSet.setWelcomePageColumns(welcomePageColumns);
contentType.setDocumentSet(documentSet);
ContentType result = graphClient.sites().bySiteId("{site-id}").contentTypes().byContentTypeId("{contentType-id}").patch(contentType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const contentType = {
    name: 'updatedCt',
	documentSet: {
		shouldPrefixNameToFile: true,
		allowedContentTypes: [{
			id: '0x0101',
			name: 'Document'
		}],
		defaultContents: [{
				fileName: 'a.txt',
				contentType: {
					id: '0x0101'
				}
			},
			{
				fileName: 'b.txt',
				contentType: {
					id: '0x0101'
				}
			}
		],
		sharedColumns: [{
				name: 'Description',
				id: 'cbb92da4-fd46-4c7d-af6c-3128c2a5576e'
			},
			{
				name: 'Address',
				id: 'fc2e188e-ba91-48c9-9dd3-16431afddd50'
			}
		],
		welcomePageColumns: [{
			name: 'Address',
			id: 'fc2e188e-ba91-48c9-9dd3-16431afddd50'
		}]
	}
};

await client.api('/sites/{site-id}/contentTypes/{contentType-id}')
	.update(contentType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ContentType;
use Microsoft\Graph\Generated\Models\DocumentSet;
use Microsoft\Graph\Generated\Models\ContentTypeInfo;
use Microsoft\Graph\Generated\Models\DocumentSetContent;
use Microsoft\Graph\Generated\Models\ColumnDefinition;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ContentType();
$requestBody->setName('updatedCt');
$documentSet = new DocumentSet();
$documentSet->setShouldPrefixNameToFile(true);
$allowedContentTypesContentTypeInfo1 = new ContentTypeInfo();
$allowedContentTypesContentTypeInfo1->setId('0x0101');
$allowedContentTypesContentTypeInfo1->setName('Document');
$allowedContentTypesArray []= $allowedContentTypesContentTypeInfo1;
$documentSet->setAllowedContentTypes($allowedContentTypesArray);

$defaultContentsDocumentSetContent1 = new DocumentSetContent();
$defaultContentsDocumentSetContent1->setFileName('a.txt');
$defaultContentsDocumentSetContent1ContentType = new ContentTypeInfo();
$defaultContentsDocumentSetContent1ContentType->setId('0x0101');
$defaultContentsDocumentSetContent1->setContentType($defaultContentsDocumentSetContent1ContentType);
$defaultContentsArray []= $defaultContentsDocumentSetContent1;
$defaultContentsDocumentSetContent2 = new DocumentSetContent();
$defaultContentsDocumentSetContent2->setFileName('b.txt');
$defaultContentsDocumentSetContent2ContentType = new ContentTypeInfo();
$defaultContentsDocumentSetContent2ContentType->setId('0x0101');
$defaultContentsDocumentSetContent2->setContentType($defaultContentsDocumentSetContent2ContentType);
$defaultContentsArray []= $defaultContentsDocumentSetContent2;
$documentSet->setDefaultContents($defaultContentsArray);

$sharedColumnsColumnDefinition1 = new ColumnDefinition();
$sharedColumnsColumnDefinition1->setName('Description');
$sharedColumnsColumnDefinition1->setId('cbb92da4-fd46-4c7d-af6c-3128c2a5576e');
$sharedColumnsArray []= $sharedColumnsColumnDefinition1;
$sharedColumnsColumnDefinition2 = new ColumnDefinition();
$sharedColumnsColumnDefinition2->setName('Address');
$sharedColumnsColumnDefinition2->setId('fc2e188e-ba91-48c9-9dd3-16431afddd50');
$sharedColumnsArray []= $sharedColumnsColumnDefinition2;
$documentSet->setSharedColumns($sharedColumnsArray);

$welcomePageColumnsColumnDefinition1 = new ColumnDefinition();
$welcomePageColumnsColumnDefinition1->setName('Address');
$welcomePageColumnsColumnDefinition1->setId('fc2e188e-ba91-48c9-9dd3-16431afddd50');
$welcomePageColumnsArray []= $welcomePageColumnsColumnDefinition1;
$documentSet->setWelcomePageColumns($welcomePageColumnsArray);

$requestBody->setDocumentSet($documentSet);

$result = $graphServiceClient->sites()->bySiteId('site-id')->contentTypes()->byContentTypeId('contentType-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	name = "updatedCt"
	documentSet = @{
		shouldPrefixNameToFile = $true
		allowedContentTypes = @(
			@{
				id = "0x0101"
				name = "Document"
			}
		)
		defaultContents = @(
			@{
				fileName = "a.txt"
				contentType = @{
					id = "0x0101"
				}
			}
			@{
				fileName = "b.txt"
				contentType = @{
					id = "0x0101"
				}
			}
		)
		sharedColumns = @(
			@{
				name = "Description"
				id = "cbb92da4-fd46-4c7d-af6c-3128c2a5576e"
			}
			@{
				name = "Address"
				id = "fc2e188e-ba91-48c9-9dd3-16431afddd50"
			}
		)
		welcomePageColumns = @(
			@{
				name = "Address"
				id = "fc2e188e-ba91-48c9-9dd3-16431afddd50"
			}
		)
	}
}

Update-MgSiteContentType -SiteId $siteId -ContentTypeId $contentTypeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.content_type import ContentType
from msgraph.generated.models.document_set import DocumentSet
from msgraph.generated.models.content_type_info import ContentTypeInfo
from msgraph.generated.models.document_set_content import DocumentSetContent
from msgraph.generated.models.column_definition import ColumnDefinition
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ContentType(
	name = "updatedCt",
	document_set = DocumentSet(
		should_prefix_name_to_file = True,
		allowed_content_types = [
			ContentTypeInfo(
				id = "0x0101",
				name = "Document",
			),
		],
		default_contents = [
			DocumentSetContent(
				file_name = "a.txt",
				content_type = ContentTypeInfo(
					id = "0x0101",
				),
			),
			DocumentSetContent(
				file_name = "b.txt",
				content_type = ContentTypeInfo(
					id = "0x0101",
				),
			),
		],
		shared_columns = [
			ColumnDefinition(
				name = "Description",
				id = "cbb92da4-fd46-4c7d-af6c-3128c2a5576e",
			),
			ColumnDefinition(
				name = "Address",
				id = "fc2e188e-ba91-48c9-9dd3-16431afddd50",
			),
		],
		welcome_page_columns = [
			ColumnDefinition(
				name = "Address",
				id = "fc2e188e-ba91-48c9-9dd3-16431afddd50",
			),
		],
	),
)

result = await graph_client.sites.by_site_id('site-id').content_types.by_content_type_id('contentType-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "0x0101009B237E76EF94DC49B4E58139041E7C60",
    "description": "",
    "eTag": "\"7\"",
    "group": "Custom Content Types",
    "hidden": false,
    "name": "testdoc",
    "parentId": "0x0101",
    "base": {
        "id": "0x0101",
        "name": "Document"
    }
}
```
