<!-- Source: https://learn.microsoft.com/en-us/graph/api/subjectrightsrequest-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List subjectRightsRequests

Namespace: microsoft.graph

Get a list of [subjectRightsRequest](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequest?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SubjectRightsRequest.Read.All | SubjectRightsRequest.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

Caution

The subject rights request API under the `/privacy` node is deprecated and will stop returning data on March 30, 2025. Please use the new path under `/security`.

```http
GET /security/subjectRightsRequests
GET /privacy/subjectRightsRequests
```

## Optional query parameters

This method doesn't support the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [subjectRightsRequest](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequest?view=graph-rest-1.0) objects in the response body.

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

```msgraph
GET https://graph.microsoft.com/v1.0/privacy/subjectRightsRequests
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Privacy.SubjectRightsRequests.GetAsync();
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
subjectRightsRequests, err := graphClient.Privacy().SubjectRightsRequests().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SubjectRightsRequestCollectionResponse result = graphClient.privacy().subjectRightsRequests().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let subjectRightsRequests = await client.api('/privacy/subjectRightsRequests')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->privacy()->subjectRightsRequests()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Compliance

Get-MgPrivacySubjectRightsRequest
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.privacy.subject_rights_requests.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "type": "export",
      "dataSubjectType": "customer",
      "regulations": [
        "GDPR"
      ],
      "displayName": "Export request for Monica Thompson",
      "description": "This is a export request",
      "status": "active",
      "internalDueDateTime": "2022-06-20T22:42:28Z",
      "lastModifiedDateTime": "2022-04-20T22:42:28Z",
      "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
      "createdDateTime": "2022-04-19T22:42:28Z",
      "stages": [
        {
          "stage": "contentRetrieval",
          "status": "notStarted",
          "error": null
        },
        {
          "stage": "contentReview",
          "status": "notStarted",
          "error": null
        },
        {
          "stage": "generateReport",
          "status": "notStarted",
          "error": null
        },
        {
          "stage": "caseResolved",
          "status": "notStarted",
          "error": null
        }
      ],
      "createdBy": {
        "user": {
          "id": "1B761ED2-AA7E-4D82-9CF5-C09D737B6167",
          "displayName": "srradmin@contoso.com"
        }
      },
      "lastModifiedBy": {
        "user": {
          "id": "1B761ED2-AA7E-4D82-9CF5-C09D737B6167",
          "displayName": "srradmin@contoso.com"
        }
      },
      "dataSubject": {
        "firstName": "Monica",
        "lastName": "Thompson",
        "email": "Monica.Thompson@contoso.com",
        "residency": "USA"
      },
      "team": {
        "id": "5484809c-fb5b-415a-afc6-da7ff601034e",
        "webUrl": "https://teams.contoso.com/teams/teamid"
      },
      "includeAllVersions": false,
      "pauseAfterEstimate": true,
      "includeAuthoredContent": true,
      "externalId": null,
      "contentQuery": "(('Monica Thompson' OR 'Monica.Thompson@contoso.com') OR (participants=Monica.Thompson@contoso.com))",
      "mailboxLocations": null,
      "siteLocations": {
        "@odata.type": "microsoft.graph.subjectRightsRequestAllSiteLocation"
      }
    },
    {
      "type": "export",
      "dataSubjectType": "customer",
      "regulations": [
        "GDPR"
      ],
      "displayName": "Export request for Alex.Wilber",
      "description": "This is a export request",
      "status": "active",
      "internalDueDateTime": "2022-06-20T22:42:28Z",
      "lastModifiedDateTime": "2022-04-20T22:42:28Z",
      "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
      "createdDateTime": "2022-04-19T22:42:28Z",
      "stages": [
        {
          "stage": "contentRetrieval",
          "status": "notStarted",
          "error": null
        },
        {
          "stage": "contentReview",
          "status": "notStarted",
          "error": null
        },
        {
          "stage": "generateReport",
          "status": "notStarted",
          "error": null
        },
        {
          "stage": "caseResolved",
          "status": "notStarted",
          "error": null
        }
      ],
      "createdBy": {
        "user": {
          "id": "1B761ED2-AA7E-4D82-9CF5-C09D737B6167",
          "displayName": "srradmin@contoso.com"
        }
      },
      "lastModifiedBy": {
        "user": {
          "id": "1B761ED2-AA7E-4D82-9CF5-C09D737B6167",
          "displayName": "srradmin@contoso.com"
        }
      },
      "dataSubject": {
        "firstName": "Alex",
        "lastName": "Wilber",
        "email": "Alex.Wilber@contoso.com"
      },
      "team": {
        "id": "5484809c-fb5b-415a-afc6-da7ff601034e",
        "webUrl": "https://teams.contoso.com/teams/teamid"
      },
      "includeAllVersions": false,
      "pauseAfterEstimate": true,
      "includeAuthoredContent": true,
      "externalId": null,
      "contentQuery": "(('Alex Wilber' OR 'Alex.Wilber@contoso.com') OR (participants=Alex.Wilber@contoso.com))",
      "mailboxLocations": {
        "@odata.type": "microsoft.graph.subjectRightsRequestAllMailBoxLocation"
      },
      "siteLocations": {
        "@odata.type": "microsoft.graph.subjectRightsRequestAllSiteLocation"
      }
    }
  ]
}
```
