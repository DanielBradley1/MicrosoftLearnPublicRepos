<!-- Source: https://learn.microsoft.com/en-us/graph/api/reportsroot-list-speakerassignmentsubmissions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List speakerAssignmentSubmissions

Namespace: microsoft.graph

Get a list of [speaker assignments](https://learn.microsoft.com/en-us/graph/api/resources/speakerassignmentsubmission?view=graph-rest-1.0) that were submitted by a student.

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
GET /education/reports/speakerAssignmentSubmissions
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

If successful, this method returns a `200 OK` response code and a collection of [speakerAssignmentSubmission](https://learn.microsoft.com/en-us/graph/api/resources/speakerassignmentsubmission?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Get a list of the speaker assignment submissions from the last 24 hours

The following example shows how to get a list of the speaker assignment submissions from the last 24 hours.

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
GET https://graph.microsoft.com/v1.0/education/reports/speakerAssignmentSubmissions
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Reports.SpeakerAssignmentSubmissions.GetAsync();
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
speakerAssignmentSubmissions, err := graphClient.Education().Reports().SpeakerAssignmentSubmissions().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SpeakerAssignmentSubmissionCollectionResponse result = graphClient.education().reports().speakerAssignmentSubmissions().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let speakerAssignmentSubmissions = await client.api('/education/reports/speakerAssignmentSubmissions')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->education()->reports()->speakerAssignmentSubmissions()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationReportSpeakerAssignmentSubmission
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.education.reports.speaker_assignment_submissions.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the default response from the last 24 hours.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/reports/speakerAssignmentSubmissions",
  "value": [
    {
      "assignmentId": "f2a0074a-eca7-4563-9de2-17fa0a274ed1",
      "classId": "36957e6c-2716-4794-b88b-5983e2502d7d",
      "submissionId": "3d292db5-189e-468b-8ca1-23ec6f74a8c2",
      "studentId": "6ade364a-ea37-4a58-82df-1814fb617618",
      "submissionDateTime": "2025-05-28T14:51:31.0663974Z",
      "lengthOfSubmissionInSeconds": 310.25,
      "wordsSpokenCount": 580,
      "monotoneOccurrencesCount": 5,
      "averageWordsPerMinutePace": 115,
      "fillerWordsOccurrencesCount": 9,
      "topFillerWords": [
        "so",
        "umm",
        "kind of"
      ],
      "topMispronouncedWords": [
        "prerequisites",
        "anonymous",
        "miscellaneous"
      ],
      "nonInclusiveLanguageOccurrencesCount": 1,
      "topNonInclusiveWordsAndPhrases": [
        "you guys"
      ],
      "repetitiveLanguageOccurrencesCount": 4,
      "topRepetitiveWordsAndPhrases": [
        "just",
        "right",
        "okay"
      ],
      "lostEyeContactOccurrencesCount": 3,
      "incorrectCameraDistanceOccurrencesCount": 0,
      "obstructedViewOccurrencesCount": 0
    },
    {
      "assignmentId": "1d468582-009d-42cb-9e32-172806ea5349",
      "classId": "4e9fef60-58a3-423d-9f38-fc0425bb91ca",
      "submissionId": "7058d2c1-9e3e-4dae-9932-970b8b45e87b",
      "studentId": "28e10270-0566-46ef-80ab-435608609047",
      "submissionDateTime": "2025-05-28T16:11:31.066402Z",
      "lengthOfSubmissionInSeconds": 198.5,
      "wordsSpokenCount": 380,
      "monotoneOccurrencesCount": 3,
      "averageWordsPerMinutePace": 135,
      "fillerWordsOccurrencesCount": 7,
      "topFillerWords": [
        "um",
        "actually"
      ],
      "topMispronouncedWords": [
        "specific",
        "particularly"
      ],
      "nonInclusiveLanguageOccurrencesCount": 0,
      "topNonInclusiveWordsAndPhrases": [],
      "repetitiveLanguageOccurrencesCount": 3,
      "topRepetitiveWordsAndPhrases": [
        "just"
      ],
      "lostEyeContactOccurrencesCount": null,
      "incorrectCameraDistanceOccurrencesCount": null,
      "obstructedViewOccurrencesCount": null
    }
  ]
}
```

### Example 2: Get a list of the speaker assignment submissions for a specific date using $filter

The following example shows how to get a list of the speaker assignment submissions for a specific date using the `$filter` query parameter. The requested time range must be 24 hours or shorter.

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
GET https://graph.microsoft.com/v1.0/education/reports/speakerAssignmentSubmissions?$filter=submissionDateTime gt 2025-05-28T00:00:00Z and submissionDateTime lt 2025-05-29T00:00:00Z
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Reports.SpeakerAssignmentSubmissions.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "submissionDateTime gt 2025-05-28T00:00:00Z and submissionDateTime lt 2025-05-29T00:00:00Z";
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


requestFilter := "submissionDateTime gt 2025-05-28T00:00:00Z and submissionDateTime lt 2025-05-29T00:00:00Z"

requestParameters := &grapheducation.ReportsSpeakerAssignmentSubmissionsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &grapheducation.ReportsSpeakerAssignmentSubmissionsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
speakerAssignmentSubmissions, err := graphClient.Education().Reports().SpeakerAssignmentSubmissions().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SpeakerAssignmentSubmissionCollectionResponse result = graphClient.education().reports().speakerAssignmentSubmissions().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "submissionDateTime gt 2025-05-28T00:00:00Z and submissionDateTime lt 2025-05-29T00:00:00Z";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let speakerAssignmentSubmissions = await client.api('/education/reports/speakerAssignmentSubmissions')
	.filter('submissionDateTime gt 2025-05-28T00:00:00Z and submissionDateTime lt 2025-05-29T00:00:00Z')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Education\Reports\SpeakerAssignmentSubmissions\SpeakerAssignmentSubmissionsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new SpeakerAssignmentSubmissionsRequestBuilderGetRequestConfiguration();
$queryParameters = SpeakerAssignmentSubmissionsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "submissionDateTime gt 2025-05-28T00:00:00Z and submissionDateTime lt 2025-05-29T00:00:00Z";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->education()->reports()->speakerAssignmentSubmissions()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationReportSpeakerAssignmentSubmission -Filter "submissionDateTime gt 2025-05-28T00:00:00Z and submissionDateTime lt 2025-05-29T00:00:00Z" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.education.reports.speaker_assignment_submissions.speaker_assignment_submissions_request_builder import SpeakerAssignmentSubmissionsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = SpeakerAssignmentSubmissionsRequestBuilder.SpeakerAssignmentSubmissionsRequestBuilderGetQueryParameters(
		filter = "submissionDateTime gt 2025-05-28T00:00:00Z and submissionDateTime lt 2025-05-29T00:00:00Z",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.education.reports.speaker_assignment_submissions.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/reports/speakerAssignmentSubmissions",
  "value": [
    {
      "assignmentId": "3221a41a-6cdc-4deb-ad50-27a7e179ec27",
      "classId": "4e9e40aa-b9ac-4af6-8a1d-4c44c27080da",
      "submissionId": "3d292db5-189e-468b-8ca1-23ec6f74a8c2",
      "studentId": "6ade364a-ea37-4a58-82df-1814fb617618",
      "submissionDateTime": "2025-05-28T01:27:42.5458886Z",
      "lengthOfSubmissionInSeconds": 185.5,
      "wordsSpokenCount": 350,
      "monotoneOccurrencesCount": 8,
      "averageWordsPerMinutePace": 120,
      "fillerWordsOccurrencesCount": 14,
      "topFillerWords": [
        "um",
        "like",
        "you know",
        "actually"
      ],
      "topMispronouncedWords": [
        "particularly",
        "subsequently",
        "statistics"
      ],
      "nonInclusiveLanguageOccurrencesCount": 2,
      "topNonInclusiveWordsAndPhrases": [
        "you guys",
        "chairman"
      ],
      "repetitiveLanguageOccurrencesCount": 6,
      "topRepetitiveWordsAndPhrases": [
        "basically",
        "essentially",
        "so"
      ],
      "lostEyeContactOccurrencesCount": 5,
      "incorrectCameraDistanceOccurrencesCount": null,
      "obstructedViewOccurrencesCount": 0
    },
    {
      "assignmentId": "f88c2e12-2277-4e5a-bc19-207278e820c5",
      "classId": "39aeb453-fe67-4d19-95b9-e588095cb13e",
      "submissionId": "c0d9706a-23a8-4d27-ba9e-5c97a4cede34",
      "studentId": "27a9716d-05aa-4aaa-ae18-9fc10318a03d",
      "submissionDateTime": "2025-05-28T16:27:42.5458933Z",
      "lengthOfSubmissionInSeconds": 240.75,
      "wordsSpokenCount": 420,
      "monotoneOccurrencesCount": null,
      "averageWordsPerMinutePace": 105,
      "fillerWordsOccurrencesCount": 18,
      "topFillerWords": [
        "um",
        "uh",
        "like",
        "sort of"
      ],
      "topMispronouncedWords": [
        "necessarily",
        "specifically",
        "phenomenon"
      ],
      "nonInclusiveLanguageOccurrencesCount": 0,
      "topNonInclusiveWordsAndPhrases": [],
      "repetitiveLanguageOccurrencesCount": 9,
      "topRepetitiveWordsAndPhrases": [
        "literally",
        "actually",
        "basically"
      ],
      "lostEyeContactOccurrencesCount": 7,
      "incorrectCameraDistanceOccurrencesCount": 2,
      "obstructedViewOccurrencesCount": 1
    },
    {
      "assignmentId": "3ed5169c-ea75-4a3f-ae4e-6abe401064b0",
      "classId": "00bc1413-d329-4a52-a92a-51971c0a3cf3",
      "submissionId": "6e43da78-9d50-4fa7-b707-8fbd05c04e67",
      "studentId": "02bcca3c-70cf-437b-813d-dd2bc32bef02",
      "submissionDateTime": "2025-05-28T18:27:42.5458952Z",
      "lengthOfSubmissionInSeconds": 275.85,
      "wordsSpokenCount": 530,
      "monotoneOccurrencesCount": 15,
      "averageWordsPerMinutePace": 125,
      "fillerWordsOccurrencesCount": 22,
      "topFillerWords": [
        "like",
        "you know",
        "uh",
        "um",
        "I mean"
      ],
      "topMispronouncedWords": [
        "entrepreneur",
        "hierarchy",
        "infrastructure"
      ],
      "nonInclusiveLanguageOccurrencesCount": 3,
      "topNonInclusiveWordsAndPhrases": [
        "mankind",
        "guys",
        "manpower"
      ],
      "repetitiveLanguageOccurrencesCount": 11,
      "topRepetitiveWordsAndPhrases": [
        "basically",
        "sort of",
        "kind of",
        "so"
      ],
      "lostEyeContactOccurrencesCount": 8,
      "incorrectCameraDistanceOccurrencesCount": 3,
      "obstructedViewOccurrencesCount": 2
    }
  ]
}
```
