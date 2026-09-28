<!-- Source: https://learn.microsoft.com/en-us/graph/api/learningcourseactivity-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-30 -->

# List learningCourseActivities

Namespace: microsoft.graph

Get a list of the [learningCourseActivity](https://learn.microsoft.com/en-us/graph/api/resources/learningcourseactivity?view=graph-rest-1.0) objects \(assigned or self-initiated\) for a user.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LearningAssignedCourse.Read.All | LearningSelfInitiatedCourse.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

To retrieve the course activity list for a signed-in user:

```http
GET /me/employeeExperience/learningCourseActivities
```

To retrieve the course activity list for a user:

```http
GET /users/{user-id}/employeeExperience/learningCourseActivities
```

## Optional query parameters

This method supports the `$skip`, `$top`, `$count`, and `$select` OData query parameters. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Prefer | include-unknown-enum-members. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [learningCourseActivity](https://learn.microsoft.com/en-us/graph/api/resources/learningcourseactivity?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows how to retrieve all the course activities for a given user.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users/7ba2228a-e020-11ec-9d64-0242ac120002/employeeExperience/learningCourseActivities
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].EmployeeExperience.LearningCourseActivities.GetAsync();
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
learningCourseActivities, err := graphClient.Users().ByUserId("user-id").EmployeeExperience().LearningCourseActivities().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LearningCourseActivityCollectionResponse result = graphClient.users().byUserId("{user-id}").employeeExperience().learningCourseActivities().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let learningCourseActivities = await client.api('/users/7ba2228a-e020-11ec-9d64-0242ac120002/employeeExperience/learningCourseActivities')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->employeeExperience()->learningCourseActivities()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').employee_experience.learning_course_activities.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#me/employeeExperience/learningCourseActivities$entity",
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/$metadata#me/employeeExperience/learningCourseActivities?$skip=10",
  "value": [
    {
      "@odata.type": "#microsoft.graph.learningAssignment",
      "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningCourseActivities('8ba2228a-e020-11ec-9d64-0242ac120003')$entity",
      "assignedDateTime": "2021-05-11T22:57:17+00:00",
      "assignmentType": "required",
      "assignerUserId": "cea1684d-57dc-438d-a9d1-e666ec1a7f3d",
      "completedDateTime": null,
      "completionPercentage": null,
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
    },
    {
      "@odata.type": "#microsoft.graph.learningAssignment",
      "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningCourseActivities('8ba2228a-e020-11ec-9d64-0242ac120003')$entity",
      "assignedDateTime": "2021-05-11T22:57:17+00:00",
      "assignmentType": "unknownFutureValue",
      "assignerUserId": "cea1684d-57dc-438d-a9d1-e666ec1a7f3d",
      "completedDateTime": null,
      "completionPercentage": null,
      "externalCourseActivityId": null,
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
    },
    {
      "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningCourseActivities('be2f4d76-e020-11ec-9d64-0242ac120002')$entity",
      "@odata.type": "#microsoft.graph.learningSelfInitiatedCourse",
      "completedDateTime": null,
      "completionPercentage": 20,
      "externalCourseActivityId": "12a2228a-e020-11ec-9d64-0242ac120002",
      "id": "be2f4d76-e020-11ec-9d64-0242ac120002",
      "learningContentId": "57baf9dc-e020-11ec-9d64-0242ac120002",
      "learningProviderId": "13727311-e7bb-470d-8b20-6a23d9030d70",
      "learnerUserId": "7ba2228a-e020-11ec-9d64-0242ac120002",
      "startedDateTime": "2021-05-21T22:57:17+00:00",
      "status": "inProgress"
    }
  ]
}
```

### Request

The following example shows how to retrieve all the course activities for a given user when `Prefer: include-unknown-enum-members` is provided in the request header.

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#me/employeeExperience/learningCourseActivities$entity",
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/$metadata#me/employeeExperience/learningCourseActivities?$skip=10",
  "value": [
    {
      "@odata.type": "#microsoft.graph.learningAssignment",
      "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningCourseActivities('8ba2228a-e020-11ec-9d64-0242ac120003')$entity",
      "assignedDateTime": "2021-05-11T22:57:17+00:00",
      "assignmentType": "required",
      "assignerUserId": "cea1684d-57dc-438d-a9d1-e666ec1a7f3d",
      "completedDateTime": null,
      "completionPercentage": null,
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
    },
    {
      "@odata.type": "#microsoft.graph.learningAssignment",
      "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningCourseActivities('8ba2228a-e020-11ec-9d64-0242ac120003')$entity",
      "assignedDateTime": "2021-05-11T22:57:17+00:00",
      "assignmentType": "peerRecommended",
      "assignerUserId": "cea1684d-57dc-438d-a9d1-e666ec1a7f3d",
      "completedDateTime": null,
      "completionPercentage": null,
      "externalCourseActivityId": null,
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
    },
    {
      "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningCourseActivities('be2f4d76-e020-11ec-9d64-0242ac120002')$entity",
      "@odata.type": "#microsoft.graph.learningSelfInitiatedCourse",
      "completedDateTime": null,
      "completionPercentage": 20,
      "externalCourseActivityId": "12a2228a-e020-11ec-9d64-0242ac120002",
      "id": "be2f4d76-e020-11ec-9d64-0242ac120002",
      "learningContentId": "57baf9dc-e020-11ec-9d64-0242ac120002",
      "learningProviderId": "13727311-e7bb-470d-8b20-6a23d9030d70",
      "learnerUserId": "7ba2228a-e020-11ec-9d64-0242ac120002",
      "startedDateTime": "2021-05-21T22:57:17+00:00",
      "status": "inProgress"
    }
  ]
}
```
