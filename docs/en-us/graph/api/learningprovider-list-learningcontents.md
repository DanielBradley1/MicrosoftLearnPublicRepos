<!-- Source: https://learn.microsoft.com/en-us/graph/api/learningprovider-list-learningcontents?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-30 -->

# List learningContents

Namespace: microsoft.graph

Get a list of the [learningContent](https://learn.microsoft.com/en-us/graph/api/resources/learningcontent?view=graph-rest-1.0) resources and their properties.

This list represents the metadata of the specified provider's content in Viva Learning.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LearningContent.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LearningContent.Read.All | LearningContent.ReadWrite.All |

## HTTP request

```http
GET /employeeExperience/learningProviders/{learningProviderId}/learningContents
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [learningContent](https://learn.microsoft.com/en-us/graph/api/resources/learningcontent?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/employeeExperience/learningProviders/13727311-e7bb-470d-8b20-6a23d9030d70/learningContents
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.LearningProviders["{learningProvider-id}"].LearningContents.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
learningContents, err := graphClient.EmployeeExperience().LearningProviders().ByLearningProviderId("learningProvider-id").LearningContents().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LearningContentCollectionResponse result = graphClient.employeeExperience().learningProviders().byLearningProviderId("{learningProvider-id}").learningContents().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let learningContents = await client.api('/employeeExperience/learningProviders/13727311-e7bb-470d-8b20-6a23d9030d70/learningContents')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->employeeExperience()->learningProviders()->byLearningProviderId('learningProvider-id')->learningContents()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.employee_experience.learning_providers.by_learning_provider_id('learningProvider-id').learning_contents.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningContents",
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningContents?skip=2&top=2",
    "@odata.count": 10,
    "value": [
        {
            "id": "99029577-a660-46b6-ba58-3ce4d21d5f50",
            "externalId": "LP4771",
            "title": "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle",
            "description": "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.",
            "contentWebUrl": "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/",
            "sourceName": "MSLibrary",
            "thumbnailWebUrl": "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF",
            "languageTag": "en-us",
            "numberOfPages": 10,
            "duration": "PDT1H",
            "format": "Book",
            "createdDateTime": "2018-01-01T00:00:00",
            "lastModifiedDateTime": "2021-04-01T04:26:06.1995367Z",
            "contributors": [
                "Lina Wagner",
                "Lisa Richter"
            ], 
            "additionalTags": [
                "Create private or public teams",
                "Add members to teams"
            ],
            "skillTags": [
                "Create teams",
                "Teams channels",
                "Teams members"
            ],
            "isActive": true,
            "isPremium": false,
            "isSearchable": false
        },
        {
            "id": "77029588-a660-46b6-ba58-3ce4d21d5678",
            "externalId": "LP4772",
            "title": "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle",
            "description": "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.",
            "contentWebUrl": "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/",
            "sourceName": "MSLibrary",
            "thumbnailWebUrl": "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF",
            "languageTag": "en-us",
            "numberOfPages": 10,
            "duration": "PDT1H",
            "format": "Book",
            "createdDateTime": "2018-01-01T00:00:00",
            "lastModifiedDateTime": "2021-04-01T04:26:06.1995367Z",
            "contributors": [
                "Lina Wagner",
                "Lisa Richter"
            ], 
            "additionalTags": [
                "Create private or public teams",
                "Add members to teams"
            ],
            "skillTags": [
                "Create teams",
                "Teams channels",
                "Teams members"
            ],
            "isActive": true,
            "isPremium": false,
            "isSearchable": false
        }
    ]
}
```
