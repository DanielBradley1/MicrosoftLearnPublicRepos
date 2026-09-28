<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationclass-post-assignments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create educationAssignment

Namespace: microsoft.graph

Create a new assignment.

Only teachers in a class can create an assignment. Assignments start in draft status, which means that students can't see the assignment until it's published.

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
POST /education/classes/{class-id}/assignments
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of an [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and an [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments
Content-type: application/json

{
    "dueDateTime": "2022-09-16T00:00:00Z",
    "displayName": "Reading test 09.14",
    "languageTag": "es-MX",
    "instructions": {
        "contentType": "text",
        "content": "Read chapter 4"
    },
    "grading": {
        "@odata.type": "#microsoft.graph.educationAssignmentPointsGradeType",
        "maxPoints": 50
    },
    "assignTo": {
        "@odata.type": "#microsoft.graph.educationAssignmentClassRecipient"
    },
    "status": "draft",
    "allowStudentsToAddResourcesToSubmission": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationAssignment
{
	DueDateTime = DateTimeOffset.Parse("2022-09-16T00:00:00Z"),
	DisplayName = "Reading test 09.14",
	LanguageTag = "es-MX",
	Instructions = new EducationItemBody
	{
		ContentType = BodyType.Text,
		Content = "Read chapter 4",
	},
	Grading = new EducationAssignmentPointsGradeType
	{
		OdataType = "#microsoft.graph.educationAssignmentPointsGradeType",
		MaxPoints = 50f,
	},
	AssignTo = new EducationAssignmentClassRecipient
	{
		OdataType = "#microsoft.graph.educationAssignmentClassRecipient",
	},
	Status = EducationAssignmentStatus.Draft,
	AllowStudentsToAddResourcesToSubmission = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments.PostAsync(requestBody);
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
dueDateTime , err := time.Parse(time.RFC3339, "2022-09-16T00:00:00Z")
requestBody.SetDueDateTime(&dueDateTime) 
displayName := "Reading test 09.14"
requestBody.SetDisplayName(&displayName) 
languageTag := "es-MX"
requestBody.SetLanguageTag(&languageTag) 
instructions := graphmodels.NewEducationItemBody()
contentType := graphmodels.TEXT_BODYTYPE 
instructions.SetContentType(&contentType) 
content := "Read chapter 4"
instructions.SetContent(&content) 
requestBody.SetInstructions(instructions)
grading := graphmodels.NewEducationAssignmentPointsGradeType()
maxPoints := float32(50)
grading.SetMaxPoints(&maxPoints) 
requestBody.SetGrading(grading)
assignTo := graphmodels.NewEducationAssignmentClassRecipient()
requestBody.SetAssignTo(assignTo)
status := graphmodels.DRAFT_EDUCATIONASSIGNMENTSTATUS 
requestBody.SetStatus(&status) 
allowStudentsToAddResourcesToSubmission := true
requestBody.SetAllowStudentsToAddResourcesToSubmission(&allowStudentsToAddResourcesToSubmission) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignments, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignment educationAssignment = new EducationAssignment();
OffsetDateTime dueDateTime = OffsetDateTime.parse("2022-09-16T00:00:00Z");
educationAssignment.setDueDateTime(dueDateTime);
educationAssignment.setDisplayName("Reading test 09.14");
educationAssignment.setLanguageTag("es-MX");
EducationItemBody instructions = new EducationItemBody();
instructions.setContentType(BodyType.Text);
instructions.setContent("Read chapter 4");
educationAssignment.setInstructions(instructions);
EducationAssignmentPointsGradeType grading = new EducationAssignmentPointsGradeType();
grading.setOdataType("#microsoft.graph.educationAssignmentPointsGradeType");
grading.setMaxPoints(50f);
educationAssignment.setGrading(grading);
EducationAssignmentClassRecipient assignTo = new EducationAssignmentClassRecipient();
assignTo.setOdataType("#microsoft.graph.educationAssignmentClassRecipient");
educationAssignment.setAssignTo(assignTo);
educationAssignment.setStatus(EducationAssignmentStatus.Draft);
educationAssignment.setAllowStudentsToAddResourcesToSubmission(true);
EducationAssignment result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().post(educationAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignment = {
    dueDateTime: '2022-09-16T00:00:00Z',
    displayName: 'Reading test 09.14',
    languageTag: 'es-MX',
    instructions: {
        contentType: 'text',
        content: 'Read chapter 4'
    },
    grading: {
        '@odata.type': '#microsoft.graph.educationAssignmentPointsGradeType',
        maxPoints: 50
    },
    assignTo: {
        '@odata.type': '#microsoft.graph.educationAssignmentClassRecipient'
    },
    status: 'draft',
    allowStudentsToAddResourcesToSubmission: true
};

await client.api('/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments')
	.post(educationAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignment;
use Microsoft\Graph\Generated\Models\EducationItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\EducationAssignmentPointsGradeType;
use Microsoft\Graph\Generated\Models\EducationAssignmentClassRecipient;
use Microsoft\Graph\Generated\Models\EducationAssignmentStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignment();
$requestBody->setDueDateTime(new \DateTime('2022-09-16T00:00:00Z'));
$requestBody->setDisplayName('Reading test 09.14');
$requestBody->setLanguageTag('es-MX');
$instructions = new EducationItemBody();
$instructions->setContentType(new BodyType('text'));
$instructions->setContent('Read chapter 4');
$requestBody->setInstructions($instructions);
$grading = new EducationAssignmentPointsGradeType();
$grading->setOdataType('#microsoft.graph.educationAssignmentPointsGradeType');
$grading->setMaxPoints(50);
$requestBody->setGrading($grading);
$assignTo = new EducationAssignmentClassRecipient();
$assignTo->setOdataType('#microsoft.graph.educationAssignmentClassRecipient');
$requestBody->setAssignTo($assignTo);
$requestBody->setStatus(new EducationAssignmentStatus('draft'));
$requestBody->setAllowStudentsToAddResourcesToSubmission(true);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	dueDateTime = [System.DateTime]::Parse("2022-09-16T00:00:00Z")
	displayName = "Reading test 09.14"
	languageTag = "es-MX"
	instructions = @{
		contentType = "text"
		content = "Read chapter 4"
	}
	grading = @{
		"@odata.type" = "#microsoft.graph.educationAssignmentPointsGradeType"
		maxPoints = 
	}
	assignTo = @{
		"@odata.type" = "#microsoft.graph.educationAssignmentClassRecipient"
	}
	status = "draft"
	allowStudentsToAddResourcesToSubmission = $true
}

New-MgEducationClassAssignment -EducationClassId $educationClassId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment import EducationAssignment
from msgraph.generated.models.education_item_body import EducationItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.education_assignment_points_grade_type import EducationAssignmentPointsGradeType
from msgraph.generated.models.education_assignment_class_recipient import EducationAssignmentClassRecipient
from msgraph.generated.models.education_assignment_status import EducationAssignmentStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignment(
	due_date_time = "2022-09-16T00:00:00Z",
	display_name = "Reading test 09.14",
	language_tag = "es-MX",
	instructions = EducationItemBody(
		content_type = BodyType.Text,
		content = "Read chapter 4",
	),
	grading = EducationAssignmentPointsGradeType(
		odata_type = "#microsoft.graph.educationAssignmentPointsGradeType",
		max_points = 50,
	),
	assign_to = EducationAssignmentClassRecipient(
		odata_type = "#microsoft.graph.educationAssignmentClassRecipient",
	),
	status = EducationAssignmentStatus.Draft,
	allow_students_to_add_resources_to_submission = True,
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

In the request body, supply a JSON representation of an [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) object.

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('f4a941ff-9da6-4707-ba5b-0eae93cad0b4')/assignments/$entity",
    "classId": "f4a941ff-9da6-4707-ba5b-0eae93cad0b4",
    "displayName": "Reading test 09.14",
    "closeDateTime": null,
    "dueDateTime": "2022-09-16T00:00:00Z",
    "assignDateTime": null,
    "assignedDateTime": null,
    "allowLateSubmissions": true,
    "resourcesFolderUrl": null,
    "createdDateTime": "2022-09-14T21:23:17.8898549Z",
    "lastModifiedDateTime": "2022-09-14T21:23:17.9055807Z",
    "allowStudentsToAddResourcesToSubmission": true,
    "status": "draft",
    "notificationChannelUrl": null,
    "webUrl": "https://teams.microsoft.com/l/entity/66aeee93-507d-479a-a3ef-8f494af43945/classroom?context=%7B%22subEntityId%22%3A%22%7B%5C%22version%5C%22%3A%5C%221.0%5C%22,%5C%22config%5C%22%3A%7B%5C%22classes%5C%22%3A%5B%7B%5C%22id%5C%22%3A%5C%22f4a941ff-9da6-4707-ba5b-0eae93cad0b4%5C%22,%5C%22displayName%5C%22%3Anull,%5C%22assignmentIds%5C%22%3A%5B%5C%22ea77e1dd-1e04-4051-967e-09129d42290f%5C%22%5D,%5C%22submissionId%5C%22%3Anull%7D%5D%7D,%5C%22action%5C%22%3A%5C%22navigate%5C%22,%5C%22view%5C%22%3A%5C%22assignment-viewer%5C%22%7D%22,%22channelId%22%3Anull%7D",
    "addToCalendarAction": "none",
    "addedStudentAction": "none",
    "id": "ea77e1dd-1e04-4051-967e-09129d42290f",
    "instructions": {
        "content": "Read chapter 4",
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
