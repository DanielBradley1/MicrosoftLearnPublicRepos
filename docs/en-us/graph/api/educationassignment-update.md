<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationassignment-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update educationassignment

Namespace: microsoft.graph

Update an [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) object.

Only teachers can perform this action.

Alternatively, request to change the status of an **assignment** with [publish](https://learn.microsoft.com/en-us/graph/api/educationassignment-publish?view=graph-rest-1.0) action. Don't use a PATCH operation for this purpose.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EduAssignments.ReadWriteBasic | EduAssignments.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EduAssignments.ReadWriteBasic.All | EduAssignments.ReadWrite.All |

## HTTP request

```http
PATCH /education/classes/{class-id}/assignments/{assignment-id}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply only the values of the fields you want to update.

Existing properties that aren't included in the request body maintains their previous values or be recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| addedStudentAction | String | Describes if the assignment should be distributed to students who are added after the assignment publication date. |
| addToCalendarAction | educationAddToCalendarOptions | Optional field to control the **assignment** behavior for adding **assignments** to students' and teachers' calendars when the **assignment** is published. The possible values are: `none`, `studentsAndPublisher`, `studentsAndTeamOwners`, `unknownFutureValue`, `studentsOnly`. Use the `Prefer: include - unknown -enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `studentsOnly`. Optional. |
| allowLateSubmissions | Boolean | Whether students can send submission after the due date. |
| allowStudentsToAddResourcesToSubmission | Boolean | Whether a student can add resources to a submission or not. Also, indicates whether all resources in the submission correspond to the assignment resource list. |
| assignDateTime | DateTimeOffset | Indicates the date to publish the assignment to students. Can't be edited when the assignment is published. |
| assignTo | [educationAssignmentRecipient](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentrecipient?view=graph-rest-1.0) | Students who get the assignment. |
| closeDateTime | DateTimeOffset | Date when the assignment is closed for submissions. This is an optional field that can be null if the assignment doesn't allowLateSubmissions or the closeDateTime is the same as the dueDateTime but if specified, it must be greater than or equal to the dueDateTime. |
| displayName | String | Name of assignment. |
| dueDateTime | DateTimeOffset | Date assignment is due. |
| grading | [educationAssignmentGradeType](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentgradetype?view=graph-rest-1.0) | How the assignment is graded. |
| instructions | itemBody | Instructions to be given to the students along with the assignment. |
| languageTag | String | Specifies the language in which UI notifications for the assignment are displayed. If **languageTag** isn't provided, the default language is `en-US`. Optional. |
| notificationChannelUrl | String | The channel to communicate notifications related to the assignment. To change the URL, set the `assignTo` value to [educationAssignmentClassRecipient](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentclassrecipient?view=graph-rest-1.0). The channel URL can't change after the publication of the assignment. |

## Response

If successful, this method returns a `200 OK` response code and an updated [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here's an example of the request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/4679bc1b-90c5-45af-ae1a-d5357672ed39
Content-type: application/json

{
    "displayName": "Reading and review test 09.03 #5",
    "instructions": {
        "contentType": "text",
        "content": "Read chapter 5 and write your review"
    },
    "dueDateTime": "2021-09-10T00:00:00Z",
    "addedStudentAction": "none"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationAssignment
{
	DisplayName = "Reading and review test 09.03 #5",
	Instructions = new EducationItemBody
	{
		ContentType = BodyType.Text,
		Content = "Read chapter 5 and write your review",
	},
	DueDateTime = DateTimeOffset.Parse("2021-09-10T00:00:00Z"),
	AddedStudentAction = EducationAddedStudentAction.None,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewEducationAssignment()
displayName := "Reading and review test 09.03 #5"
requestBody.SetDisplayName(&displayName) 
instructions := graphmodels.NewEducationItemBody()
contentType := graphmodels.TEXT_BODYTYPE 
instructions.SetContentType(&contentType) 
content := "Read chapter 5 and write your review"
instructions.SetContent(&content) 
requestBody.SetInstructions(instructions)
dueDateTime , err := time.Parse(time.RFC3339, "2021-09-10T00:00:00Z")
requestBody.SetDueDateTime(&dueDateTime) 
addedStudentAction := graphmodels.NONE_EDUCATIONADDEDSTUDENTACTION 
requestBody.SetAddedStudentAction(&addedStudentAction) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignments, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignment educationAssignment = new EducationAssignment();
educationAssignment.setDisplayName("Reading and review test 09.03 #5");
EducationItemBody instructions = new EducationItemBody();
instructions.setContentType(BodyType.Text);
instructions.setContent("Read chapter 5 and write your review");
educationAssignment.setInstructions(instructions);
OffsetDateTime dueDateTime = OffsetDateTime.parse("2021-09-10T00:00:00Z");
educationAssignment.setDueDateTime(dueDateTime);
educationAssignment.setAddedStudentAction(EducationAddedStudentAction.None);
EducationAssignment result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").patch(educationAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignment = {
    displayName: 'Reading and review test 09.03 #5',
    instructions: {
        contentType: 'text',
        content: 'Read chapter 5 and write your review'
    },
    dueDateTime: '2021-09-10T00:00:00Z',
    addedStudentAction: 'none'
};

await client.api('/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/4679bc1b-90c5-45af-ae1a-d5357672ed39')
	.update(educationAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignment;
use Microsoft\Graph\Generated\Models\EducationItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\EducationAddedStudentAction;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignment();
$requestBody->setDisplayName('Reading and review test 09.03 #5');
$instructions = new EducationItemBody();
$instructions->setContentType(new BodyType('text'));
$instructions->setContent('Read chapter 5 and write your review');
$requestBody->setInstructions($instructions);
$requestBody->setDueDateTime(new \DateTime('2021-09-10T00:00:00Z'));
$requestBody->setAddedStudentAction(new EducationAddedStudentAction('none'));

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	displayName = "Reading and review test 09.03 #5"
	instructions = @{
		contentType = "text"
		content = "Read chapter 5 and write your review"
	}
	dueDateTime = [System.DateTime]::Parse("2021-09-10T00:00:00Z")
	addedStudentAction = "none"
}

Update-MgEducationClassAssignment -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment import EducationAssignment
from msgraph.generated.models.education_item_body import EducationItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.education_added_student_action import EducationAddedStudentAction
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignment(
	display_name = "Reading and review test 09.03 #5",
	instructions = EducationItemBody(
		content_type = BodyType.Text,
		content = "Read chapter 5 and write your review",
	),
	due_date_time = "2021-09-10T00:00:00Z",
	added_student_action = EducationAddedStudentAction.None,
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

Here's an example of the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('72a7baec-c3e9-4213-a850-f62de0adad5f')/assignments/$entity",
    "classId": "72a7baec-c3e9-4213-a850-f62de0adad5f",
    "displayName": "Reading and review test 09.03 #5",
    "closeDateTime": null,
    "dueDateTime": "2021-09-10T00:00:00Z",
    "assignDateTime": null,
    "assignedDateTime": null,
    "allowLateSubmissions": true,
    "resourcesFolderUrl": null,
    "createdDateTime": "2021-09-03T23:57:14.6088791Z",
    "lastModifiedDateTime": "2021-09-04T15:01:35.3361649Z",
    "allowStudentsToAddResourcesToSubmission": true,
    "status": "draft",
    "notificationChannelUrl": null,
    "webUrl": "https://teams.microsoft.com/l/entity/66aeee93-507d-479a-a3ef-8f494af43945/classroom?context=%7B%22subEntityId%22%3A%22%7B%5C%22version%5C%22%3A%5C%221.0%5C%22,%5C%22config%5C%22%3A%7B%5C%22classes%5C%22%3A%5B%7B%5C%22id%5C%22%3A%5C%2272a7baec-c3e9-4213-a850-f62de0adad5f%5C%22,%5C%22displayName%5C%22%3Anull,%5C%22assignmentIds%5C%22%3A%5B%5C%224679bc1b-90c5-45af-ae1a-d5357672ed39%5C%22%5D%7D%5D%7D,%5C%22action%5C%22%3A%5C%22navigate%5C%22,%5C%22view%5C%22%3A%5C%22assignment-viewer%5C%22%7D%22,%22channelId%22%3Anull%7D",
    "addedStudentAction": "none",
    "languageTag": "pt-BR",
    "id": "4679bc1b-90c5-45af-ae1a-d5357672ed39",
    "instructions": {
        "content": "Read chapter 5 and write your review",
        "contentType": "text"
    },
    "grading": {
        "@odata.type": "#microsoft.graph.educationAssignmentPointsGradeType",
        "maxPoints": 50
    },
    "assignTo": {
        "@odata.type": "#microsoft.graph.educationAssignmentClassRecipient"
    },
    "createdBy": {
        "application": null,
        "device": null,
        "user": {
            "id": "f3a5344e-dbde-48b0-be24-b5b62a243836",
            "displayName": null
        }
    },
    "lastModifiedBy": {
        "application": null,
        "device": null,
        "user": {
            "id": "f3a5344e-dbde-48b0-be24-b5b62a243836",
            "displayName": null
        }
    }
}
```

## Related content

- [Status, transitions, and limitations for assignments and submissions](https://learn.microsoft.com/en-us/graph/assignments-submissions-status-transition)
- [Specify the default channel for education assignment notifications](https://learn.microsoft.com/en-us/graph/education-build-notificationchannelurl)
