<!-- Source: https://learn.microsoft.com/en-us/graph/api/reportsroot-list-readingcoachpassages?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List readingCoachPassages

Namespace: microsoft.graph

Get a list of [Reading Coach passages](https://learn.microsoft.com/en-us/graph/api/resources/readingcoachpassage?view=graph-rest-1.0) that were practiced by a student.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EduReports-Reading.ReadAnonymous.All | EduReports-Reading.Read.All |

## HTTP request

```http
GET /education/reports/readingCoachPassages
```

## Optional query parameters

This method supports the `$top`, `$filter`, `$count`, `$skipToken`, and `$select` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [readingCoachPassage](https://learn.microsoft.com/en-us/graph/api/resources/readingcoachpassage?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Get a list of the Reading Coach passages from the last 24 hours

The following example shows how to get a list of the Reading Coach passages from the last 24 hours.

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

```msgraph
GET https://graph.microsoft.com/v1.0/education/reports/readingCoachPassages
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Reports.ReadingCoachPassages.GetAsync();
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
readingCoachPassages, err := graphClient.Education().Reports().ReadingCoachPassages().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ReadingCoachPassageCollectionResponse result = graphClient.education().reports().readingCoachPassages().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let readingCoachPassages = await client.api('/education/reports/readingCoachPassages')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->education()->reports()->readingCoachPassages()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationReportReadingCoachPassage
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.education.reports.reading_coach_passages.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the default response from the last 24 hours.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/reports/readingCoachPassages",
  "value": [
    {
      "practicedAtDateTime": "2025-06-25T14:51:31.0663974Z",
      "studentId": "27a9716d-05aa-4aaa-ae18-9fc10318a03d",
      "practiceWords": [
        "science",
        "experiment",
        "laboratory",
        "hypothesis",
        "observation"
      ],
      "wordsPerMinute": 55.5,
      "wordsAccuracyPercentage": 92.0,
      "timeSpentReadingInSeconds": 165.75,
      "languageTag": "en-US",
      "storyType": "userProvided",
      "isReadingCompleted": true
    },
    {
      "practicedAtDateTime": "2025-06-25T12:51:31.0663974Z",
      "studentId": "27a9716d-05aa-4aaa-ae18-9fc10318a03d",
      "practiceWords": [
        "tortoise",
        "experiment"
      ],
      "wordsPerMinute": 52.5,
      "wordsAccuracyPercentage": 94.5,
      "timeSpentReadingInSeconds": 180.5,
      "languageTag": "en-US",
      "storyType": "aiGenerated",
      "isReadingCompleted": true
    }
  ]
}
```

### Example 2: Get a list of the Reading Coach passages for a specific date using $filter

The following example shows how to get the Reading Coach passages for a specific date using the `$filter` query parameter. The requested time range must be 24 hours or shorter.

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

```msgraph
GET https://graph.microsoft.com/v1.0/education/reports/readingCoachPassages?$filter=practicedAtDateTime gt 2025-06-22T00:00:00Z and practicedAtDateTime lt 2025-06-23T00:00:00Z
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Reports.ReadingCoachPassages.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "practicedAtDateTime gt 2025-06-22T00:00:00Z and practicedAtDateTime lt 2025-06-23T00:00:00Z";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  grapheducation "github.com/microsoftgraph/msgraph-sdk-go/education"
	  //other-imports
)


requestFilter := "practicedAtDateTime gt 2025-06-22T00:00:00Z and practicedAtDateTime lt 2025-06-23T00:00:00Z"

requestParameters := &grapheducation.ReportsReadingCoachPassagesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &grapheducation.ReportsReadingCoachPassagesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
readingCoachPassages, err := graphClient.Education().Reports().ReadingCoachPassages().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ReadingCoachPassageCollectionResponse result = graphClient.education().reports().readingCoachPassages().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "practicedAtDateTime gt 2025-06-22T00:00:00Z and practicedAtDateTime lt 2025-06-23T00:00:00Z";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let readingCoachPassages = await client.api('/education/reports/readingCoachPassages')
	.filter('practicedAtDateTime gt 2025-06-22T00:00:00Z and practicedAtDateTime lt 2025-06-23T00:00:00Z')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Education\Reports\ReadingCoachPassages\ReadingCoachPassagesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ReadingCoachPassagesRequestBuilderGetRequestConfiguration();
$queryParameters = ReadingCoachPassagesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "practicedAtDateTime gt 2025-06-22T00:00:00Z and practicedAtDateTime lt 2025-06-23T00:00:00Z";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->education()->reports()->readingCoachPassages()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationReportReadingCoachPassage -Filter "practicedAtDateTime gt 2025-06-22T00:00:00Z and practicedAtDateTime lt 2025-06-23T00:00:00Z" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.education.reports.reading_coach_passages.reading_coach_passages_request_builder import ReadingCoachPassagesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ReadingCoachPassagesRequestBuilder.ReadingCoachPassagesRequestBuilderGetQueryParameters(
		filter = "practicedAtDateTime gt 2025-06-22T00:00:00Z and practicedAtDateTime lt 2025-06-23T00:00:00Z",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.education.reports.reading_coach_passages.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/reports/readingCoachPassages",
  "value": [
    {
      "practicedAtDateTime": "2025-06-22T14:51:31.0663974Z",
      "studentId": "27a9716d-05aa-4aaa-ae18-9fc10318a03d",
      "practiceWords": [
        "science",
        "experiment",
        "laboratory",
        "hypothesis",
        "observation"
      ],
      "wordsPerMinute": 55.5,
      "wordsAccuracyPercentage": 92.0,
      "timeSpentReadingInSeconds": 165.75,
      "languageTag": "en-US",
      "storyType": "userProvided",
      "isReadingCompleted": true
    },
    {
      "practicedAtDateTime": "2025-06-22T12:51:31.0663974Z",
      "studentId": "27a9716d-05aa-4aaa-ae18-9fc10318a03d",
      "practiceWords": [
        "tortoise",
        "experiment"
      ],
      "wordsPerMinute": 52.5,
      "wordsAccuracyPercentage": 94.5,
      "timeSpentReadingInSeconds": 180.5,
      "languageTag": "en-US",
      "storyType": "aiGenerated",
      "isReadingCompleted": true
    }
  ]
}
```
