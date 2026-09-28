<!-- Source: https://learn.microsoft.com/en-us/graph/api/learningcourseactivity-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get learningCourseActivity

Namespace: microsoft.graph

Get the specified [learningCourseActivity](https://learn.microsoft.com/en-us/graph/api/resources/learningcourseactivity?view=graph-rest-1.0) object using either an ID or an **externalCourseActivityId** of the learning provider, or a **courseActivityId** of a user.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LearningAssignedCourse.Read | LearningSelfInitiatedCourse.Read |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LearningAssignedCourse.Read.All | LearningAssignedCourse.ReadWrite.All, LearningSelfInitiatedCourse.Read.All, LearningSelfInitiatedCourse.ReadWrite.All |

## HTTP request

To get a specific learning course activity based on its ID \(primary key\):

```http
GET /employeeExperience/learningCourseActivities/{Id}
```

To get a specific learning course activity based on its **externalCourseActivityId** \(secondary key\):

```http
GET /employeeExperience/learningProviders/{registrationId}/learningCourseActivities(externalCourseActivityId='{externalCourseActivityId}')
```

To get the details of a learning course activity for a user:

```http
GET users/{user-id}/employeeExperience/learningCourseActivities/{id}
```

To get the details of a learning course activity for the signed-in user:

```http
GET me/employeeExperience/learningCourseActivities/{id}
```

## Optional query parameters

This method supports the `$select` and other OData query parameters to customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [learningCourseActivity](https://learn.microsoft.com/en-us/graph/api/resources/learningcourseactivity?view=graph-rest-1.0) object in the response body.

If unsuccessful, this method returns one of the responses below:

| Scenario | HTTP code | Code | Message |
| :--- | :--- | :--- | :--- |
| Method not supported for entity | 405 | methodNotAllowed | This method isn't supported for this entity type. See the Microsoft Graph documentation for the methods applicable to this entity. |
| User doesn't have appropriate permission scope | 403 | Forbidden | Your account doesn't have access to this report or data. Contact your administrator to request access. |
| Forbidden | 403 | Forbidden | You don't have an adequate service plan for this request. |
| Bad request | 400 | badRequest | This provider isn't enabled for the given tenant. |
| Bad request | 400 | badRequest | There was an issue with your request. Make sure the registrationId you entered is valid or registered for your tenant. |
| Bad request | 404 | notFound | The requested assignment ID doesn’t exist. |
| Internal server error | 500 | internalServerError | Internal server error. |
| Request throttled | 429 | tooManyRequests | {"code": "tooManyRequests","message": "Retry after {noOfMinutes} minutes"}. |
| Service unavailable | 503 | serviceUnavailable | {"code": "serviceUnavailable","message": "Retry after {noOfMinutes} minutes"}. |

## Examples

### Example 1: Get a learning course activity based on its ID

#### Request

The following examples show a request to get a learning course activity using an ID.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/employeeExperience/learningCourseActivities/8ba2228a-e020-11ec-9d64-0242ac120003
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.LearningCourseActivities["{learningCourseActivity-id}"].GetAsync();
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
learningCourseActivities, err := graphClient.EmployeeExperience().LearningCourseActivities().ByLearningCourseActivityId("learningCourseActivity-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LearningCourseActivity result = graphClient.employeeExperience().learningCourseActivities().byLearningCourseActivityId("{learningCourseActivity-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let learningCourseActivity = await client.api('/employeeExperience/learningCourseActivities/8ba2228a-e020-11ec-9d64-0242ac120003')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->employeeExperience()->learningCourseActivities()->byLearningCourseActivityId('learningCourseActivity-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.employee_experience.learning_course_activities.by_learning_course_activity_id('learningCourseActivity-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.learningAssignment",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningCourseActivities('7ba2228a-e020-11ec-9d64-0242ac120002')$entity",
  "assignedDateTime": "2021-05-11T22:57:17+00:00",
  "assignmentType": "required",
  "assignerUserId": "cea1684d-57dc-438d-a9d1-e666ec1a7f3d",
  "completedDateTime": null,
  "completionPercentage": null,
  "dueDateTime": {
    "dateTime": "2022-09-22T16:05:00.0000000",
    "timeZone": "UTC"
  },
  "externalCourseActivityId": "12a2228a-e020-11ec-9d64-0242ac120002",
  "id": "8ba2228a-e020-11ec-9d64-0242ac120003",
  "learningContentId": "57baf9dc-e020-11ec-9d64-0242ac120002",
  "learningProviderId": "13727311-e7bb-470d-8b20-6a23d9030d70",
  "learnerUserId": "7ba2228a-e020-11ec-9d64-0242ac120002",
  "notes": {
    "contentType": "text",
    "content": "required assignment added for user"
  },
  "status": "notStarted"
}
```

### Example 2: Get a learning course activity based on the externalCourseActivityId of the learning provider

#### Request

The following example shows a request to get the details of a learning course activity using an external course activity ID.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/employeeExperience/learningProviders/01e8f81b-3060-4dec-acf0-0389665a0a38/learningCourseActivities(externalCourseActivityId='12a2228a-e020-11ec-9d64-0242ac120002')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.LearningProviders["{learningProvider-id}"].LearningCourseActivitiesWithExternalcourseActivityId("{externalcourseActivityId}").GetAsync();
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
externalcourseActivityId := "{externalcourseActivityId}"
learningCourseActivities, err := graphClient.EmployeeExperience().LearningProviders().ByLearningProviderId("learningProvider-id").LearningCourseActivitiesWithExternalcourseActivityId(&externalcourseActivityId).Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LearningCourseActivity result = graphClient.employeeExperience().learningProviders().byLearningProviderId("{learningProvider-id}").learningCourseActivitiesWithExternalcourseActivityId("{externalcourseActivityId}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->employeeExperience()->learningProviders()->byLearningProviderId('learningProvider-id')->learningCourseActivitiesWithExternalcourseActivityId('{externalcourseActivityId}', )->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.employee_experience.learning_providers.by_learning_provider_id('learningProvider-id').learning_course_activities_with_externalcourse_activity_id("{externalcourseActivityId}").get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.learningAssignment",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('01e8f81b-3060-4dec-acf0-0389665a0a38')/learningCourseActivities('8ba2228a-e020-11ec-9d64-0242ac120003')$entity",
  "assignedDateTime": "2021-05-11T22:57:17+00:00",
  "assignerUserId": "cea1684d-57dc-438d-a9d1-e666ec1a7f3d",
  "assignmentType": "required",
  "completedDateTime": null,
  "completionPercentage": null,
  "externalCourseActivityId": "12a2228a-e020-11ec-9d64-0242ac120002",
  "id": "8ba2228a-e020-11ec-9d64-0242ac120003",
  "dueDateTime": {
    "dateTime": "2022-09-22T16:05:00.0000000",
    "timeZone": "UTC"
  },
  "learningContentId": "57baf9dc-e020-11ec-9d64-0242ac120002",
  "learningProviderId": "01e8f81b-3060-4dec-acf0-0389665a0a38",
  "learnerUserId": "7ba2228a-e020-11ec-9d64-0242ac120002",
  "notes": {
    "contentType": "text",
    "content": "required assignment added for user"
  },
  "status": "notStarted"
}
```

### Example 3: Get the details of a learning course activity for a user

#### Request

The following example shows a request to get the details of a learning course activity for a user.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users/7ba2228a-e020-11ec-9d64-0242ac120002/employeeExperience/learningCourseActivities/8ba2228a-e020-11ec-9d64-0242ac120003
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].EmployeeExperience.LearningCourseActivities["{learningCourseActivity-id}"].GetAsync();
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
learningCourseActivities, err := graphClient.Users().ByUserId("user-id").EmployeeExperience().LearningCourseActivities().ByLearningCourseActivityId("learningCourseActivity-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LearningCourseActivity result = graphClient.users().byUserId("{user-id}").employeeExperience().learningCourseActivities().byLearningCourseActivityId("{learningCourseActivity-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let learningCourseActivity = await client.api('/users/7ba2228a-e020-11ec-9d64-0242ac120002/employeeExperience/learningCourseActivities/8ba2228a-e020-11ec-9d64-0242ac120003')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->employeeExperience()->learningCourseActivities()->byLearningCourseActivityId('learningCourseActivity-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').employee_experience.learning_course_activities.by_learning_course_activity_id('learningCourseActivity-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.learningAssignment",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningCourseActivities('8ba2228a-e020-11ec-9d64-0242ac120003')$entity",
  "assignedDateTime": "2021-05-11T22:57:17+00:00",
  "assignmentType": "required",
  "assignerUserId": "cea1684d-57dc-438d-a9d1-e666ec1a7f3d",
  "completedDateTime": null,
  "completionPercentage": 20,
  "externalCourseActivityId": "12a2228a-e020-11ec-9d64-0242ac120002",
  "id": "8ba2228a-e020-11ec-9d64-0242ac120003",
  "dueDateTime": {
    "dateTime": "2022-09-22T16:05:00.0000000",
    "timeZone": "UTC"
  },
  "learningContentId": "57baf9dc-e020-11ec-9d64-0242ac120002",
  "learningProviderId": "13727311-e7bb-470d-8b20-6a23d9030d70",
  "learnerUserId": "7ba2228a-e020-11ec-9d64-0242ac120002",
  "notes": {
    "contentType": "text",
    "content": "required assignment added for user"
  },
  "status": "notStarted"
}
```
