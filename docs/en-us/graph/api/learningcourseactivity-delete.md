<!-- Source: https://learn.microsoft.com/en-us/graph/api/learningcourseactivity-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Delete learningCourseActivity

Namespace: microsoft.graph

Delete a [learningCourseActivity](https://learn.microsoft.com/en-us/graph/api/resources/learningcourseactivity?view=graph-rest-1.0) object using the course activity ID of either an assignment or a self-initiated activity.

> **Note**: A provider can only manage Learning course activities when **isCourseAcitvitySyncEnabled** is set to `true`. To update the value, use the [Update learningProvider](https://learn.microsoft.com/en-us/graph/api/learningprovider-update?view=graph-rest-1.0) method.

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
| Application | LearningAssignedCourse.ReadWrite.All | LearningSelfInitiatedCourse.ReadWrite.All |

## HTTP request

```http
DELETE /employeeExperience/learningProviders/{registrationId}/learningCourseActivities/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

If unsuccessful, this method returns one of the responses below:

| Scenario | HTTP code | Code | Message |
| :--- | :--- | :--- | :--- |
| Method not supported for entity | 405 | methodNotAllowed | This method isn't supported for this entity type. See the Microsoft Graph documentation for the methods applicable to this entity. |
| User doesn't have the appropriate permissions scope | 403 | Forbidden | Your account doesn't have access to this report or data. Contact your administrator to request access. |
| Forbidden | 403 | Forbidden | You don't have an adequate service plan for this request. |
| Bad request | 400 | badRequest | This provider isn't enabled for the given tenant. |
| Bad request | 400 | badRequest | There was an issue with your request. Make sure the registrationId you entered is valid or registered for your tenant. |
| Bad request | 404 | notFound | The requested assignment ID doesn't exist. |
| Internal server error | 500 | internalServerError | Internal server error. |
| Request throttled | 429 | tooManyRequests | {"code": "tooManyRequests","message": "Retry after {noOfMinutes} minutes"}. |
| Service unavailable | 503 | serviceUnavailable | {"code": "serviceUnavailable","message": "Retry after {noOfMinutes} minutes"}. |

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
DELETE https://graph.microsoft.com/v1.0/employeeExperience/learningProviders/13727311-e7bb-470d-8b20-6a23d9030d70/learningCourseActivities/be2f4d76-e020-11ec-9d64-0242ac120002
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.EmployeeExperience.LearningProviders["{learningProvider-id}"].LearningCourseActivities["{learningCourseActivity-id}"].DeleteAsync();
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
graphClient.EmployeeExperience().LearningProviders().ByLearningProviderId("learningProvider-id").LearningCourseActivities().ByLearningCourseActivityId("learningCourseActivity-id").Delete(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.employeeExperience().learningProviders().byLearningProviderId("{learningProvider-id}").learningCourseActivities().byLearningCourseActivityId("{learningCourseActivity-id}").delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/employeeExperience/learningProviders/13727311-e7bb-470d-8b20-6a23d9030d70/learningCourseActivities/be2f4d76-e020-11ec-9d64-0242ac120002')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->employeeExperience()->learningProviders()->byLearningProviderId('learningProvider-id')->learningCourseActivities()->byLearningCourseActivityId('learningCourseActivity-id')->delete()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.employee_experience.learning_providers.by_learning_provider_id('learningProvider-id').learning_course_activities.by_learning_course_activity_id('learningCourseActivity-id').delete()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
