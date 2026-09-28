<!-- Source: https://learn.microsoft.com/en-us/graph/api/engagementasyncoperation-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-27 -->

# Get engagementAsyncOperation

Namespace: microsoft.graph

Get an [engagementAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/engagementasyncoperation?view=graph-rest-1.0) to track a long-running operation request.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Community.Read.All | Community.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Community.Read.All | Community.ReadWrite.All, EngagementConversation.Migration.All |

## HTTP request

```http
GET /employeeExperience/engagementAsyncOperations/{engagementAsyncOperationId}
```

## Optional query parameters

This method supports the `$select` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [engagementAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/engagementasyncoperation?view=graph-rest-1.0) object in the response body.

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

```http
GET https://graph.microsoft.com/v1.0/employeeExperience/engagementAsyncOperations/a6fdce1-c261-48bc-89de-1cfef658c0d5
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.EngagementAsyncOperations["{engagementAsyncOperation-id}"].GetAsync();
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
engagementAsyncOperations, err := graphClient.EmployeeExperience().EngagementAsyncOperations().ByEngagementAsyncOperationId("engagementAsyncOperation-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EngagementAsyncOperation result = graphClient.employeeExperience().engagementAsyncOperations().byEngagementAsyncOperationId("{engagementAsyncOperation-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let engagementAsyncOperation = await client.api('/employeeExperience/engagementAsyncOperations/a6fdce1-c261-48bc-89de-1cfef658c0d5')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->employeeExperience()->engagementAsyncOperations()->byEngagementAsyncOperationId('engagementAsyncOperation-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.employee_experience.engagement_async_operations.by_engagement_async_operation_id('engagementAsyncOperation-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/employeeExperience/engagementAsyncOperations/$entity",
  "id": "eyJfdHlwZSI6IkxvbmdSdW5uaW5nT3BlcmF0aW9uIiwiaWQiOiI0ZmVhMjE5Ni0yZTRjLTQ4MzctYTlhNi1iMTVjOTBhNTM2ODkiLCJvcGVyYXRpb24iOiJDcmVhdGVDb21tdW5pdHkifQ",
  "createdDateTime": "2023-12-06T09:42:54.367629-08:00", 
  "lastActionDateTime": "2023-12-06T09:42:54.367663-08:00",
  "status": "succeeded",
  "statusDetail": null,
  "resourceLocation": "https://graph.microsoft.com/v1.0/employeeExperience/communities('eyXxdHlwZSI6Ikdyb3VwIiwiaABCDiI4MzIxMjc1In0')",
  "operationType": "createCommunity",
  "resourceId": "eyXxdHlwZSI6Ikdyb3VwIiwiaABCDiI4MzIxMjc1In0"
}
```
