<!-- Source: https://learn.microsoft.com/en-us/graph/api/learningcourseactivity-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update learningCourseActivity

Namespace: microsoft.graph

Update the properties of a [learningCourseActivity](https://learn.microsoft.com/en-us/graph/api/resources/learningcourseactivity?view=graph-rest-1.0) object.

> **Note**: Learning course activities can be managed by a provider only when **isCourseAcitvitySyncEnabled** is set to `true`. To update the value, use the [Update learningProvider](https://learn.microsoft.com/en-us/graph/api/learningprovider-update?view=graph-rest-1.0) method.

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
PATCH /employeeExperience/learningProviders/{registrationId}/learningCourseActivities/{learningCourseActivityId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, use @odata.type to specify the type of [learningCourseActivity](https://learn.microsoft.com/en-us/graph/api/resources/learningcourseactivity?view=graph-rest-1.0) resource \([learningAssignment](https://learn.microsoft.com/en-us/graph/api/resources/learningassignment?view=graph-rest-1.0) or [learningSelfInitiated](https://learn.microsoft.com/en-us/graph/api/resources/learningselfinitiatedcourse?view=graph-rest-1.0)\), and include the properties of that type to update.

The following table lists the properties you can change for an assigned learning course activity \(**learningAssignment**\).

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedDateTime | DateTimeOffset | Assigned date for the course activity. Optional. |
| completedDateTime | DateTimeOffset | Date and time when the assignment was completed. Optional. |
| completionPercentage | Int32 | The percentage of the course the user completes. If a value is provided, it must be between `0` and `100` \(inclusive\). Optional. |
| dueDateTime | DateTimeOffset | The due date for the course activity. Optional. |
| notes | String | Notes for the course activity. Optional. |
| status | courseStatus | The status of the course activity. Possible values are `notStarted`, `inProgress`, `completed`. Required. |

The following table lists the properties you can change for a self-initiated learning course activity \(**learningSelfInitiated**\).

| Property | Type | Description |
| :--- | :--- | :--- |
| completedDateTime | DateTimeOffset | Date and time when the assignment was completed. Optional. |
| completionPercentage | Int32 | The percentage of the course completed by the user. If a value is provided, it must be between `0` and `100` \(inclusive\). Optional. |
| status | courseStatus | The status of the course activity. The possible values are: `inProgress`, `completed`. Required. |
| startedDateTime | DateTimeOffset | The date and time when the learner started the self-initiated course. |

## Response

If successful, this method returns a `204 No Content` response code.

If unsuccessful, this method returns one of the responses below:

| Scenario | HTTP code | Code | Message | Details |
| :--- | :--- | :--- | :--- | :--- |
| Method not supported for entity | 405 | methodNotAllowed | This method isn't supported for this entity type. See the Microsoft Graph documentation for the methods applicable to this entity. |  |
| User doesn't have appropriate permission scope | 403 | Forbidden | Your account doesn't have access to this report or data. Contact your administrator to request access. |  |
| Forbidden | 403 | Forbidden | You don't have an adequate service plan for this request. |  |
| Bad request | 400 | badRequest | This provider isn't enabled for the given tenant. |  |
| Bad request | 400 | badRequest | There was an issue with your request. Make sure the registrationId you entered is valid or registered for your tenant. |  |
| Bad request | 404 | notFound | The assignment ID requested doesn’t exist. |  |
| Internal server error | 500 | internalServerError | Internal server error. |  |
| Request throttled | 429 | tooManyRequests | {"code": "tooManyRequests","message": "Retry after {noOfMinutes} minutes".} |  |
| Service unavailable | 503 | serviceUnavailable | {"code": "serviceUnavailable","message": "Retry after {noOfMinutes} minutes"}. |  |
| Bad request | 400 | badRequest | Required fields are missing | {"code": "badRequest","message": "Input field {fieldName} is required"}. |
| Bad request | 400 | badRequest | Input fields are invalid | {"code": "badRequest","message": "Input field {fieldName} is invalid"}. |
| Bad request | 400 | badRequest | badRequest | {"code": "badRequest","message": "Input field {fieldName} shouldn't be empty"}. |
| Forbidden | 403 | Forbidden | The provider isn't valid to create course activity for the given learning content | When the registrationId/learningProviderId doesn't match with the provider with which the learningContent is created. |
| Forbidden | 403 | Forbidden | The user license is not valid to perform the operation | When the user for which the assignment is being created doesn't have a premium license. |

## Examples

### Example 1: Update an assigned learning course activity

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/employeeExperience/learningProviders/01e8f81b-3060-4dec-acf0-0389665a0a38/learningCourseActivities/8ba2228a-e020-11ec-9d64-0242ac120003
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.learningAssignment",
  "assignedDateTime": "2021-05-11T22:57:17+00:00",
  "assignmentType": "required",
  "assignerUserId": "cea1684d-57dc-438d-a9d1-e666ec1a7f3d",
  "completedDateTime": null,
  "completionPercentage": 20,
  "learningProviderId": "01e8f81b-3060-4dec-acf0-0389665a0a38",
  "dueDateTime": {
    "dateTime": "2022-09-22T16:05:00.0000000",
    "timeZone": "UTC"
  },
  "externalCourseActivityId": "12a2228a-e020-11ec-9d64-0242ac120002",
  "learningContentId": "57baf9dc-e020-11ec-9d64-0242ac120002",
  "learnerUserId": "7ba2228a-e020-11ec-9d64-0242ac120002",
  "notes": {
    "contentType": "text",
    "content": "required assignment added for user"
  },
  "status": "inProgress"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new LearningAssignment
{
	OdataType = "#microsoft.graph.learningAssignment",
	AssignedDateTime = DateTimeOffset.Parse("2021-05-11T22:57:17+00:00"),
	AssignmentType = AssignmentType.Required,
	AssignerUserId = "cea1684d-57dc-438d-a9d1-e666ec1a7f3d",
	CompletedDateTime = null,
	CompletionPercentage = 20,
	LearningProviderId = "01e8f81b-3060-4dec-acf0-0389665a0a38",
	DueDateTime = new DateTimeTimeZone
	{
		DateTime = "2022-09-22T16:05:00.0000000",
		TimeZone = "UTC",
	},
	ExternalCourseActivityId = "12a2228a-e020-11ec-9d64-0242ac120002",
	LearningContentId = "57baf9dc-e020-11ec-9d64-0242ac120002",
	LearnerUserId = "7ba2228a-e020-11ec-9d64-0242ac120002",
	Notes = new ItemBody
	{
		ContentType = BodyType.Text,
		Content = "required assignment added for user",
	},
	Status = CourseStatus.InProgress,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.LearningProviders["{learningProvider-id}"].LearningCourseActivities["{learningCourseActivity-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewLearningCourseActivity()
assignedDateTime , err := time.Parse(time.RFC3339, "2021-05-11T22:57:17+00:00")
requestBody.SetAssignedDateTime(&assignedDateTime) 
assignmentType := graphmodels.REQUIRED_ASSIGNMENTTYPE 
requestBody.SetAssignmentType(&assignmentType) 
assignerUserId := "cea1684d-57dc-438d-a9d1-e666ec1a7f3d"
requestBody.SetAssignerUserId(&assignerUserId) 
completedDateTime := null
requestBody.SetCompletedDateTime(&completedDateTime) 
completionPercentage := int32(20)
requestBody.SetCompletionPercentage(&completionPercentage) 
learningProviderId := "01e8f81b-3060-4dec-acf0-0389665a0a38"
requestBody.SetLearningProviderId(&learningProviderId) 
dueDateTime := graphmodels.NewDateTimeTimeZone()
dateTime := "2022-09-22T16:05:00.0000000"
dueDateTime.SetDateTime(&dateTime) 
timeZone := "UTC"
dueDateTime.SetTimeZone(&timeZone) 
requestBody.SetDueDateTime(dueDateTime)
externalCourseActivityId := "12a2228a-e020-11ec-9d64-0242ac120002"
requestBody.SetExternalCourseActivityId(&externalCourseActivityId) 
learningContentId := "57baf9dc-e020-11ec-9d64-0242ac120002"
requestBody.SetLearningContentId(&learningContentId) 
learnerUserId := "7ba2228a-e020-11ec-9d64-0242ac120002"
requestBody.SetLearnerUserId(&learnerUserId) 
notes := graphmodels.NewItemBody()
contentType := graphmodels.TEXT_BODYTYPE 
notes.SetContentType(&contentType) 
content := "required assignment added for user"
notes.SetContent(&content) 
requestBody.SetNotes(notes)
status := graphmodels.INPROGRESS_COURSESTATUS 
requestBody.SetStatus(&status) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
learningCourseActivities, err := graphClient.EmployeeExperience().LearningProviders().ByLearningProviderId("learningProvider-id").LearningCourseActivities().ByLearningCourseActivityId("learningCourseActivity-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LearningAssignment learningCourseActivity = new LearningAssignment();
learningCourseActivity.setOdataType("#microsoft.graph.learningAssignment");
OffsetDateTime assignedDateTime = OffsetDateTime.parse("2021-05-11T22:57:17+00:00");
learningCourseActivity.setAssignedDateTime(assignedDateTime);
learningCourseActivity.setAssignmentType(AssignmentType.Required);
learningCourseActivity.setAssignerUserId("cea1684d-57dc-438d-a9d1-e666ec1a7f3d");
learningCourseActivity.setCompletedDateTime(null);
learningCourseActivity.setCompletionPercentage(20);
learningCourseActivity.setLearningProviderId("01e8f81b-3060-4dec-acf0-0389665a0a38");
DateTimeTimeZone dueDateTime = new DateTimeTimeZone();
dueDateTime.setDateTime("2022-09-22T16:05:00.0000000");
dueDateTime.setTimeZone("UTC");
learningCourseActivity.setDueDateTime(dueDateTime);
learningCourseActivity.setExternalCourseActivityId("12a2228a-e020-11ec-9d64-0242ac120002");
learningCourseActivity.setLearningContentId("57baf9dc-e020-11ec-9d64-0242ac120002");
learningCourseActivity.setLearnerUserId("7ba2228a-e020-11ec-9d64-0242ac120002");
ItemBody notes = new ItemBody();
notes.setContentType(BodyType.Text);
notes.setContent("required assignment added for user");
learningCourseActivity.setNotes(notes);
learningCourseActivity.setStatus(CourseStatus.InProgress);
LearningCourseActivity result = graphClient.employeeExperience().learningProviders().byLearningProviderId("{learningProvider-id}").learningCourseActivities().byLearningCourseActivityId("{learningCourseActivity-id}").patch(learningCourseActivity);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const learningCourseActivity = {
  '@odata.type': '#microsoft.graph.learningAssignment',
  assignedDateTime: '2021-05-11T22:57:17+00:00',
  assignmentType: 'required',
  assignerUserId: 'cea1684d-57dc-438d-a9d1-e666ec1a7f3d',
  completedDateTime: null,
  completionPercentage: 20,
  learningProviderId: '01e8f81b-3060-4dec-acf0-0389665a0a38',
  dueDateTime: {
    dateTime: '2022-09-22T16:05:00.0000000',
    timeZone: 'UTC'
  },
  externalCourseActivityId: '12a2228a-e020-11ec-9d64-0242ac120002',
  learningContentId: '57baf9dc-e020-11ec-9d64-0242ac120002',
  learnerUserId: '7ba2228a-e020-11ec-9d64-0242ac120002',
  notes: {
    contentType: 'text',
    content: 'required assignment added for user'
  },
  status: 'inProgress'
};

await client.api('/employeeExperience/learningProviders/01e8f81b-3060-4dec-acf0-0389665a0a38/learningCourseActivities/8ba2228a-e020-11ec-9d64-0242ac120003')
	.update(learningCourseActivity);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\LearningAssignment;
use Microsoft\Graph\Generated\Models\AssignmentType;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\CourseStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new LearningAssignment();
$requestBody->setOdataType('#microsoft.graph.learningAssignment');
$requestBody->setAssignedDateTime(new \DateTime('2021-05-11T22:57:17+00:00'));
$requestBody->setAssignmentType(new AssignmentType('required'));
$requestBody->setAssignerUserId('cea1684d-57dc-438d-a9d1-e666ec1a7f3d');
$requestBody->setCompletedDateTime(null);
$requestBody->setCompletionPercentage(20);
$requestBody->setLearningProviderId('01e8f81b-3060-4dec-acf0-0389665a0a38');
$dueDateTime = new DateTimeTimeZone();
$dueDateTime->setDateTime('2022-09-22T16:05:00.0000000');
$dueDateTime->setTimeZone('UTC');
$requestBody->setDueDateTime($dueDateTime);
$requestBody->setExternalCourseActivityId('12a2228a-e020-11ec-9d64-0242ac120002');
$requestBody->setLearningContentId('57baf9dc-e020-11ec-9d64-0242ac120002');
$requestBody->setLearnerUserId('7ba2228a-e020-11ec-9d64-0242ac120002');
$notes = new ItemBody();
$notes->setContentType(new BodyType('text'));
$notes->setContent('required assignment added for user');
$requestBody->setNotes($notes);
$requestBody->setStatus(new CourseStatus('inProgress'));

$result = $graphServiceClient->employeeExperience()->learningProviders()->byLearningProviderId('learningProvider-id')->learningCourseActivities()->byLearningCourseActivityId('learningCourseActivity-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.learning_assignment import LearningAssignment
from msgraph.generated.models.assignment_type import AssignmentType
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.course_status import CourseStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = LearningAssignment(
	odata_type = "#microsoft.graph.learningAssignment",
	assigned_date_time = "2021-05-11T22:57:17+00:00",
	assignment_type = AssignmentType.Required,
	assigner_user_id = "cea1684d-57dc-438d-a9d1-e666ec1a7f3d",
	completed_date_time = None,
	completion_percentage = 20,
	learning_provider_id = "01e8f81b-3060-4dec-acf0-0389665a0a38",
	due_date_time = DateTimeTimeZone(
		date_time = "2022-09-22T16:05:00.0000000",
		time_zone = "UTC",
	),
	external_course_activity_id = "12a2228a-e020-11ec-9d64-0242ac120002",
	learning_content_id = "57baf9dc-e020-11ec-9d64-0242ac120002",
	learner_user_id = "7ba2228a-e020-11ec-9d64-0242ac120002",
	notes = ItemBody(
		content_type = BodyType.Text,
		content = "required assignment added for user",
	),
	status = CourseStatus.InProgress,
)

result = await graph_client.employee_experience.learning_providers.by_learning_provider_id('learningProvider-id').learning_course_activities.by_learning_course_activity_id('learningCourseActivity-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Update a self-initiated learning course activity

### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/employeeExperience/learningProviders/01e8f81b-3060-4dec-acf0-0389665a0a38/learningCourseActivities/8ba2228a-e020-11ec-9d64-0242ac120003
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.learningSelfInitiatedCourse",
  "completedDateTime": null,
  "completionPercentage": 30,
  "externalCourseActivityId": "12a2228a-e020-11ec-9d64-0242ac120002",
  "learningContentId": "57baf9dc-e020-11ec-9d64-0242ac120002",
  "learningProviderId": "01e8f81b-3060-4dec-acf0-0389665a0a38",
  "startedDateTime": "2021-05-11T22:57:17+00:00",
  "status": "inProgress"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new LearningSelfInitiatedCourse
{
	OdataType = "#microsoft.graph.learningSelfInitiatedCourse",
	CompletedDateTime = null,
	CompletionPercentage = 30,
	ExternalCourseActivityId = "12a2228a-e020-11ec-9d64-0242ac120002",
	LearningContentId = "57baf9dc-e020-11ec-9d64-0242ac120002",
	LearningProviderId = "01e8f81b-3060-4dec-acf0-0389665a0a38",
	StartedDateTime = DateTimeOffset.Parse("2021-05-11T22:57:17+00:00"),
	Status = CourseStatus.InProgress,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.LearningProviders["{learningProvider-id}"].LearningCourseActivities["{learningCourseActivity-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewLearningCourseActivity()
completedDateTime := null
requestBody.SetCompletedDateTime(&completedDateTime) 
completionPercentage := int32(30)
requestBody.SetCompletionPercentage(&completionPercentage) 
externalCourseActivityId := "12a2228a-e020-11ec-9d64-0242ac120002"
requestBody.SetExternalCourseActivityId(&externalCourseActivityId) 
learningContentId := "57baf9dc-e020-11ec-9d64-0242ac120002"
requestBody.SetLearningContentId(&learningContentId) 
learningProviderId := "01e8f81b-3060-4dec-acf0-0389665a0a38"
requestBody.SetLearningProviderId(&learningProviderId) 
startedDateTime , err := time.Parse(time.RFC3339, "2021-05-11T22:57:17+00:00")
requestBody.SetStartedDateTime(&startedDateTime) 
status := graphmodels.INPROGRESS_COURSESTATUS 
requestBody.SetStatus(&status) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
learningCourseActivities, err := graphClient.EmployeeExperience().LearningProviders().ByLearningProviderId("learningProvider-id").LearningCourseActivities().ByLearningCourseActivityId("learningCourseActivity-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LearningSelfInitiatedCourse learningCourseActivity = new LearningSelfInitiatedCourse();
learningCourseActivity.setOdataType("#microsoft.graph.learningSelfInitiatedCourse");
learningCourseActivity.setCompletedDateTime(null);
learningCourseActivity.setCompletionPercentage(30);
learningCourseActivity.setExternalCourseActivityId("12a2228a-e020-11ec-9d64-0242ac120002");
learningCourseActivity.setLearningContentId("57baf9dc-e020-11ec-9d64-0242ac120002");
learningCourseActivity.setLearningProviderId("01e8f81b-3060-4dec-acf0-0389665a0a38");
OffsetDateTime startedDateTime = OffsetDateTime.parse("2021-05-11T22:57:17+00:00");
learningCourseActivity.setStartedDateTime(startedDateTime);
learningCourseActivity.setStatus(CourseStatus.InProgress);
LearningCourseActivity result = graphClient.employeeExperience().learningProviders().byLearningProviderId("{learningProvider-id}").learningCourseActivities().byLearningCourseActivityId("{learningCourseActivity-id}").patch(learningCourseActivity);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const learningCourseActivity = {
  '@odata.type': '#microsoft.graph.learningSelfInitiatedCourse',
  completedDateTime: null,
  completionPercentage: 30,
  externalCourseActivityId: '12a2228a-e020-11ec-9d64-0242ac120002',
  learningContentId: '57baf9dc-e020-11ec-9d64-0242ac120002',
  learningProviderId: '01e8f81b-3060-4dec-acf0-0389665a0a38',
  startedDateTime: '2021-05-11T22:57:17+00:00',
  status: 'inProgress'
};

await client.api('/employeeExperience/learningProviders/01e8f81b-3060-4dec-acf0-0389665a0a38/learningCourseActivities/8ba2228a-e020-11ec-9d64-0242ac120003')
	.update(learningCourseActivity);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\LearningSelfInitiatedCourse;
use Microsoft\Graph\Generated\Models\CourseStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new LearningSelfInitiatedCourse();
$requestBody->setOdataType('#microsoft.graph.learningSelfInitiatedCourse');
$requestBody->setCompletedDateTime(null);
$requestBody->setCompletionPercentage(30);
$requestBody->setExternalCourseActivityId('12a2228a-e020-11ec-9d64-0242ac120002');
$requestBody->setLearningContentId('57baf9dc-e020-11ec-9d64-0242ac120002');
$requestBody->setLearningProviderId('01e8f81b-3060-4dec-acf0-0389665a0a38');
$requestBody->setStartedDateTime(new \DateTime('2021-05-11T22:57:17+00:00'));
$requestBody->setStatus(new CourseStatus('inProgress'));

$result = $graphServiceClient->employeeExperience()->learningProviders()->byLearningProviderId('learningProvider-id')->learningCourseActivities()->byLearningCourseActivityId('learningCourseActivity-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.learning_self_initiated_course import LearningSelfInitiatedCourse
from msgraph.generated.models.course_status import CourseStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = LearningSelfInitiatedCourse(
	odata_type = "#microsoft.graph.learningSelfInitiatedCourse",
	completed_date_time = None,
	completion_percentage = 30,
	external_course_activity_id = "12a2228a-e020-11ec-9d64-0242ac120002",
	learning_content_id = "57baf9dc-e020-11ec-9d64-0242ac120002",
	learning_provider_id = "01e8f81b-3060-4dec-acf0-0389665a0a38",
	started_date_time = "2021-05-11T22:57:17+00:00",
	status = CourseStatus.InProgress,
)

result = await graph_client.employee_experience.learning_providers.by_learning_provider_id('learningProvider-id').learning_course_activities.by_learning_course_activity_id('learningCourseActivity-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
