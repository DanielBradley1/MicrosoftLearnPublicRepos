<!-- Source: https://learn.microsoft.com/en-us/graph/api/search-bookmark-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-22 -->

# Update bookmark

Namespace: microsoft.graph.search

Update the properties of a [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) object.

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
PATCH /search/bookmarks/{bookmarksId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

> **Note:** Any updates to the properties of a collection, such as keywords or categories, replace the entire collection.

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
| platforms | microsoft.graph.devicePlatformType collection | List of devices and operating systems that are able to view this bookmark. The possible values are: `android`, `androidForWork`, `ios`, `macOS`, `windowsPhone81`, `windowsPhone81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidASOP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`. |
| powerAppIds | String collection | List of Power Apps associated with this bookmark. If users add existing Power Apps to a bookmark, they can complete tasks directly on the search results page, such as entering vacation time or reporting expenses. |
| state | microsoft.graph.search.answerState | State of the bookmark. The possible values are: `published`, `draft`, `excluded`, `unknownFutureValue`. |
| targetedVariations | [microsoft.graph.search.answerVariant](https://learn.microsoft.com/en-us/graph/api/resources/search-answervariant?view=graph-rest-1.0) collection | Variations of a bookmark for different countries/regions or devices. Use when you need to show different content to users based on their device, country/region, or both. The date and group settings apply to all variations. |
| webUrl | String | The URL link for the bookmark. When users select this bookmark from the search results, they are directed to the specified URL. Inherited from [searchAnswer](https://learn.microsoft.com/en-us/graph/api/resources/search-searchanswer?view=graph-rest-1.0). |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/v1.0/search/bookmarks/733b26d5-af76-4eea-ac69-1a0ce8716897
Content-Type: application/json

{
  "description": "Book a fancy vacation in Tuscany or browse museums in Florence."
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Search;

var requestBody = new Bookmark
{
	Description = "Book a fancy vacation in Tuscany or browse museums in Florence.",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Search.Bookmarks["{bookmark-id}"].PatchAsync(requestBody);
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

requestBody := graphmodelssearch.NewBookmark()
description := "Book a fancy vacation in Tuscany or browse museums in Florence."
requestBody.SetDescription(&description) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
bookmarks, err := graphClient.Search().Bookmarks().ByBookmarkId("bookmark-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.search.Bookmark bookmark = new com.microsoft.graph.models.search.Bookmark();
bookmark.setDescription("Book a fancy vacation in Tuscany or browse museums in Florence.");
com.microsoft.graph.models.search.Bookmark result = graphClient.search().bookmarks().byBookmarkId("{bookmark-id}").patch(bookmark);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const bookmark = {
  description: 'Book a fancy vacation in Tuscany or browse museums in Florence.'
};

await client.api('/search/bookmarks/733b26d5-af76-4eea-ac69-1a0ce8716897')
	.update(bookmark);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Search\Bookmark;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Bookmark();
$requestBody->setDescription('Book a fancy vacation in Tuscany or browse museums in Florence.');

$result = $graphServiceClient->search()->bookmarks()->byBookmarkId('bookmark-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	description = "Book a fancy vacation in Tuscany or browse museums in Florence."
}

Update-MgSearchBookmark -BookmarkId $bookmarkId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.search.bookmark import Bookmark
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Bookmark(
	description = "Book a fancy vacation in Tuscany or browse museums in Florence.",
)

result = await graph_client.search.bookmarks.by_bookmark_id('bookmark-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
