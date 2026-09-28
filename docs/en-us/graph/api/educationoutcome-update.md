<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationoutcome-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-20 -->

# Update educationOutcome

Namespace: microsoft.graph

Update the properties of an [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) object. Only teachers can perform this operation.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EduAssignments.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EduAssignments.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /education/classes/{class-id}/assignments/{assignment-id}/submissions/{submission-id}/outcomes/{outcome-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply only the values of the fields you want to update.

Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

The **educationOutcome** object will be one of the following derived types: **educationPointsOutcome**, **educationFeedbackOutcome**, or **educationRubricOutcome**. Supply the specific properties relevant to the type of outcome you're updating.

All derived outcome types have a regular and a "published" property appropriate to that type of outcome; for example, **points** and **publishedPoints**, **feedback** and **publishedFeedback**. Don't update the "published" property; it is for internal use. For example, to assign points to an **educationPointsOutcome**, update the **points** property, but don't update **publishedPoints**.

## Response

If successful, this method returns a `200 OK` response code and an updated [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) object in the response body.

If **pointsGradeType** and **points** are updated to a negative or infinite value, the method returns a `400` error message.

```http
HTTP/1.1 400 Bad Request
Content-type: application/json

{
	"error": {
		"code": "badRequest",
		"message": "Bad request.",
		"innerError": {
			"code": "invalidGrading",
			"message": "Points must be less than 9999999 when using PointsGradeType."
		}
	}
}
```

If an invalid outcome ID is specified, a `404 Not Found` error is returned.

```http
HTTP/1.1 404 Not Found
Content-type: application/json

{
	"error": {
		"code": "20241",
		"message": "Entity not found. Outcome id: 05d0f76c-1dfa-4442-926c-1b094828b505"
	}
}
```

## Examples

### Example 1: Update a feedback outcome

#### Request

The following example shows a request to update a feedback outcome.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/education/classes/acdefc6b-2dc6-4e71-b1e9-6d9810ab1793/assignments/cf6005fc-9e13-44a2-a6ac-a53322006454/submissions/d1bee293-d8bb-48d4-af3e-c8cb0e3c7fe7/outcomes/9c0f2850-ff8f-4fd6-b3ac-e23077b59141
Content-type: application/json

{
    "@odata.type":"#microsoft.graph.educationFeedbackOutcome",
    "feedback":{
        "text":{
            "content":"This is feedback for the assignment as a whole.",
            "contentType":"text"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationFeedbackOutcome
{
	OdataType = "#microsoft.graph.educationFeedbackOutcome",
	Feedback = new EducationFeedback
	{
		Text = new EducationItemBody
		{
			Content = "This is feedback for the assignment as a whole.",
			ContentType = BodyType.Text,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Submissions["{educationSubmission-id}"].Outcomes["{educationOutcome-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewEducationOutcome()
feedback := graphmodels.NewEducationFeedback()
text := graphmodels.NewEducationItemBody()
content := "This is feedback for the assignment as a whole."
text.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
text.SetContentType(&contentType) 
feedback.SetText(text)
requestBody.SetFeedback(feedback)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
outcomes, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Submissions().ByEducationSubmissionId("educationSubmission-id").Outcomes().ByEducationOutcomeId("educationOutcome-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationFeedbackOutcome educationOutcome = new EducationFeedbackOutcome();
educationOutcome.setOdataType("#microsoft.graph.educationFeedbackOutcome");
EducationFeedback feedback = new EducationFeedback();
EducationItemBody text = new EducationItemBody();
text.setContent("This is feedback for the assignment as a whole.");
text.setContentType(BodyType.Text);
feedback.setText(text);
educationOutcome.setFeedback(feedback);
EducationOutcome result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").submissions().byEducationSubmissionId("{educationSubmission-id}").outcomes().byEducationOutcomeId("{educationOutcome-id}").patch(educationOutcome);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationOutcome = {
    '@odata.type':'#microsoft.graph.educationFeedbackOutcome',
    feedback: {
        text: {
            content: 'This is feedback for the assignment as a whole.',
            contentType: 'text'
        }
    }
};

await client.api('/education/classes/acdefc6b-2dc6-4e71-b1e9-6d9810ab1793/assignments/cf6005fc-9e13-44a2-a6ac-a53322006454/submissions/d1bee293-d8bb-48d4-af3e-c8cb0e3c7fe7/outcomes/9c0f2850-ff8f-4fd6-b3ac-e23077b59141')
	.update(educationOutcome);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationFeedbackOutcome;
use Microsoft\Graph\Generated\Models\EducationFeedback;
use Microsoft\Graph\Generated\Models\EducationItemBody;
use Microsoft\Graph\Generated\Models\BodyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationFeedbackOutcome();
$requestBody->setOdataType('#microsoft.graph.educationFeedbackOutcome');
$feedback = new EducationFeedback();
$feedbackText = new EducationItemBody();
$feedbackText->setContent('This is feedback for the assignment as a whole.');
$feedbackText->setContentType(new BodyType('text'));
$feedback->setText($feedbackText);
$requestBody->setFeedback($feedback);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->submissions()->byEducationSubmissionId('educationSubmission-id')->outcomes()->byEducationOutcomeId('educationOutcome-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	"@odata.type" = "#microsoft.graph.educationFeedbackOutcome"
	feedback = @{
		text = @{
			content = "This is feedback for the assignment as a whole."
			contentType = "text"
		}
	}
}

Update-MgEducationClassAssignmentSubmissionOutcome -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -EducationSubmissionId $educationSubmissionId -EducationOutcomeId $educationOutcomeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_feedback_outcome import EducationFeedbackOutcome
from msgraph.generated.models.education_feedback import EducationFeedback
from msgraph.generated.models.education_item_body import EducationItemBody
from msgraph.generated.models.body_type import BodyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationFeedbackOutcome(
	odata_type = "#microsoft.graph.educationFeedbackOutcome",
	feedback = EducationFeedback(
		text = EducationItemBody(
			content = "This is feedback for the assignment as a whole.",
			content_type = BodyType.Text,
		),
	),
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').submissions.by_education_submission_id('educationSubmission-id').outcomes.by_education_outcome_id('educationOutcome-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.educationFeedbackOutcome",
    "id": "ca05367a-b292-42d5-aff7-5d279feeace8",
    "lastModifiedBy": {
        "user": {
            "id": "9391878d-903c-406c-bb1c-0f17d00fd878"
        }
    },
    "feedback": {
        "feedbackDateTime": "2019-07-31T21:10:30.3231461Z",
        "text": {
            "content": "This is feedback for the assignment as a whole.",
            "contentType": "text"
        },
        "feedbackBy": {
            "user": {
                "id": "9391878d-903c-406c-bb1c-0f17d00fd878",
            }
        }
    }
}
```

### Example 2: Update a points outcome

#### Request

The following example shows a request to update a points outcome.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/education/classes/acdefc6b-2dc6-4e71-b1e9-6d9810ab1793/assignments/cf6005fc-9e13-44a2-a6ac-a53322006454/submissions/d1bee293-d8bb-48d4-af3e-c8cb0e3c7fe7/outcomes/9c0f2850-ff8f-4fd6-b3ac-e23077b59141
Content-type: application/json

{
    "@odata.type":"#microsoft.graph.educationPointsOutcome",
    "points":{
        "@odata.type":"#microsoft.graph.educationAssignmentPointsGrade",
        "points":85.0
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationPointsOutcome
{
	OdataType = "#microsoft.graph.educationPointsOutcome",
	Points = new EducationAssignmentPointsGrade
	{
		OdataType = "#microsoft.graph.educationAssignmentPointsGrade",
		Points = 85.0f,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Submissions["{educationSubmission-id}"].Outcomes["{educationOutcome-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewEducationOutcome()
points := graphmodels.NewEducationAssignmentPointsGrade()
points := float32(85.0)
points.SetPoints(&points) 
requestBody.SetPoints(points)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
outcomes, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Submissions().ByEducationSubmissionId("educationSubmission-id").Outcomes().ByEducationOutcomeId("educationOutcome-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationPointsOutcome educationOutcome = new EducationPointsOutcome();
educationOutcome.setOdataType("#microsoft.graph.educationPointsOutcome");
EducationAssignmentPointsGrade points = new EducationAssignmentPointsGrade();
points.setOdataType("#microsoft.graph.educationAssignmentPointsGrade");
points.setPoints(85.0f);
educationOutcome.setPoints(points);
EducationOutcome result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").submissions().byEducationSubmissionId("{educationSubmission-id}").outcomes().byEducationOutcomeId("{educationOutcome-id}").patch(educationOutcome);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationOutcome = {
    '@odata.type':'#microsoft.graph.educationPointsOutcome',
    points: {
        '@odata.type':'#microsoft.graph.educationAssignmentPointsGrade',
        points: 85.0
    }
};

await client.api('/education/classes/acdefc6b-2dc6-4e71-b1e9-6d9810ab1793/assignments/cf6005fc-9e13-44a2-a6ac-a53322006454/submissions/d1bee293-d8bb-48d4-af3e-c8cb0e3c7fe7/outcomes/9c0f2850-ff8f-4fd6-b3ac-e23077b59141')
	.update(educationOutcome);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationPointsOutcome;
use Microsoft\Graph\Generated\Models\EducationAssignmentPointsGrade;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationPointsOutcome();
$requestBody->setOdataType('#microsoft.graph.educationPointsOutcome');
$points = new EducationAssignmentPointsGrade();
$points->setOdataType('#microsoft.graph.educationAssignmentPointsGrade');
$points->setPoints(85.0);
$requestBody->setPoints($points);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->submissions()->byEducationSubmissionId('educationSubmission-id')->outcomes()->byEducationOutcomeId('educationOutcome-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	"@odata.type" = "#microsoft.graph.educationPointsOutcome"
	points = @{
		"@odata.type" = "#microsoft.graph.educationAssignmentPointsGrade"
		points = 
	}
}

Update-MgEducationClassAssignmentSubmissionOutcome -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -EducationSubmissionId $educationSubmissionId -EducationOutcomeId $educationOutcomeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_points_outcome import EducationPointsOutcome
from msgraph.generated.models.education_assignment_points_grade import EducationAssignmentPointsGrade
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationPointsOutcome(
	odata_type = "#microsoft.graph.educationPointsOutcome",
	points = EducationAssignmentPointsGrade(
		odata_type = "#microsoft.graph.educationAssignmentPointsGrade",
		points = 85.0,
	),
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').submissions.by_education_submission_id('educationSubmission-id').outcomes.by_education_outcome_id('educationOutcome-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.type":"#microsoft.graph.educationPointsOutcome",
    "id":"ea1351f6-ba33-4940-b2cb-6a7254af2dc8",
    "lastModifiedBy":{
        "user":{
            "id":"9391878d-903c-406c-bb1c-0f17d00fd878"
        }
    },
    "points":{
        "gradedDateTime":"2019-07-15T22:35:48.2429387Z",
        "points":85.0,
        "gradedBy":{
            "user":{
                "id":"9391878d-903c-406c-bb1c-0f17d00fd878"
            }
        }
    }
}
```

### Example 3: Update a rubric outcome

#### Request

The following example shows a request to update a rubric outcome.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
PATCH https://graph.microsoft.com/v1.0/education/classes/acdefc6b-2dc6-4e71-b1e9-6d9810ab1793/assignments/cf6005fc-9e13-44a2-a6ac-a53322006454/submissions/d1bee293-d8bb-48d4-af3e-c8cb0e3c7fe7/outcomes/9c0f2850-ff8f-4fd6-b3ac-e23077b59141
Content-type: application/json

{
    "@odata.type":"#microsoft.graph.educationRubricOutcome",
    "rubricQualityFeedback":[
        {
            "qualityId":"9a145aa8-f3d9-43a1-8f77-5387ff0693f2",
            "feedback":{
                "content":"This is feedback specific to the first quality of the rubric.",
                "contentType":"text"
            }
        },
        {
            "qualityId":"d2331fb2-2761-402e-8de6-93e0afaa076e",
            "feedback":{
                "content":"This is feedback specific to the second quality of the rubric.",
                "contentType":"text"
            }
        }
    ],
    "rubricQualitySelectedLevels":[
        {
            "qualityId":"9a145aa8-f3d9-43a1-8f77-5387ff0693f2",
            "columnId":"4fb17a1d-5681-46c2-a295-4e305c3eae23"
        },
        {
            "qualityId":"d2331fb2-2761-402e-8de6-93e0afaa076e",
            "columnId":"aac076bf-51ba-48c5-a2e0-ee235b0b9740"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationRubricOutcome
{
	OdataType = "#microsoft.graph.educationRubricOutcome",
	RubricQualityFeedback = new List<RubricQualityFeedbackModel>
	{
		new RubricQualityFeedbackModel
		{
			QualityId = "9a145aa8-f3d9-43a1-8f77-5387ff0693f2",
			Feedback = new EducationItemBody
			{
				Content = "This is feedback specific to the first quality of the rubric.",
				ContentType = BodyType.Text,
			},
		},
		new RubricQualityFeedbackModel
		{
			QualityId = "d2331fb2-2761-402e-8de6-93e0afaa076e",
			Feedback = new EducationItemBody
			{
				Content = "This is feedback specific to the second quality of the rubric.",
				ContentType = BodyType.Text,
			},
		},
	},
	RubricQualitySelectedLevels = new List<RubricQualitySelectedColumnModel>
	{
		new RubricQualitySelectedColumnModel
		{
			QualityId = "9a145aa8-f3d9-43a1-8f77-5387ff0693f2",
			ColumnId = "4fb17a1d-5681-46c2-a295-4e305c3eae23",
		},
		new RubricQualitySelectedColumnModel
		{
			QualityId = "d2331fb2-2761-402e-8de6-93e0afaa076e",
			ColumnId = "aac076bf-51ba-48c5-a2e0-ee235b0b9740",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Submissions["{educationSubmission-id}"].Outcomes["{educationOutcome-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewEducationOutcome()


rubricQualityFeedbackModel := graphmodels.NewRubricQualityFeedbackModel()
qualityId := "9a145aa8-f3d9-43a1-8f77-5387ff0693f2"
rubricQualityFeedbackModel.SetQualityId(&qualityId) 
feedback := graphmodels.NewEducationItemBody()
content := "This is feedback specific to the first quality of the rubric."
feedback.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
feedback.SetContentType(&contentType) 
rubricQualityFeedbackModel.SetFeedback(feedback)
rubricQualityFeedbackModel1 := graphmodels.NewRubricQualityFeedbackModel()
qualityId := "d2331fb2-2761-402e-8de6-93e0afaa076e"
rubricQualityFeedbackModel1.SetQualityId(&qualityId) 
feedback := graphmodels.NewEducationItemBody()
content := "This is feedback specific to the second quality of the rubric."
feedback.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
feedback.SetContentType(&contentType) 
rubricQualityFeedbackModel1.SetFeedback(feedback)

rubricQualityFeedback := []graphmodels.RubricQualityFeedbackModelable {
	rubricQualityFeedbackModel,
	rubricQualityFeedbackModel1,
}
requestBody.SetRubricQualityFeedback(rubricQualityFeedback)


rubricQualitySelectedColumnModel := graphmodels.NewRubricQualitySelectedColumnModel()
qualityId := "9a145aa8-f3d9-43a1-8f77-5387ff0693f2"
rubricQualitySelectedColumnModel.SetQualityId(&qualityId) 
columnId := "4fb17a1d-5681-46c2-a295-4e305c3eae23"
rubricQualitySelectedColumnModel.SetColumnId(&columnId) 
rubricQualitySelectedColumnModel1 := graphmodels.NewRubricQualitySelectedColumnModel()
qualityId := "d2331fb2-2761-402e-8de6-93e0afaa076e"
rubricQualitySelectedColumnModel1.SetQualityId(&qualityId) 
columnId := "aac076bf-51ba-48c5-a2e0-ee235b0b9740"
rubricQualitySelectedColumnModel1.SetColumnId(&columnId) 

rubricQualitySelectedLevels := []graphmodels.RubricQualitySelectedColumnModelable {
	rubricQualitySelectedColumnModel,
	rubricQualitySelectedColumnModel1,
}
requestBody.SetRubricQualitySelectedLevels(rubricQualitySelectedLevels)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
outcomes, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Submissions().ByEducationSubmissionId("educationSubmission-id").Outcomes().ByEducationOutcomeId("educationOutcome-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationRubricOutcome educationOutcome = new EducationRubricOutcome();
educationOutcome.setOdataType("#microsoft.graph.educationRubricOutcome");
LinkedList<RubricQualityFeedbackModel> rubricQualityFeedback = new LinkedList<RubricQualityFeedbackModel>();
RubricQualityFeedbackModel rubricQualityFeedbackModel = new RubricQualityFeedbackModel();
rubricQualityFeedbackModel.setQualityId("9a145aa8-f3d9-43a1-8f77-5387ff0693f2");
EducationItemBody feedback = new EducationItemBody();
feedback.setContent("This is feedback specific to the first quality of the rubric.");
feedback.setContentType(BodyType.Text);
rubricQualityFeedbackModel.setFeedback(feedback);
rubricQualityFeedback.add(rubricQualityFeedbackModel);
RubricQualityFeedbackModel rubricQualityFeedbackModel1 = new RubricQualityFeedbackModel();
rubricQualityFeedbackModel1.setQualityId("d2331fb2-2761-402e-8de6-93e0afaa076e");
EducationItemBody feedback1 = new EducationItemBody();
feedback1.setContent("This is feedback specific to the second quality of the rubric.");
feedback1.setContentType(BodyType.Text);
rubricQualityFeedbackModel1.setFeedback(feedback1);
rubricQualityFeedback.add(rubricQualityFeedbackModel1);
educationOutcome.setRubricQualityFeedback(rubricQualityFeedback);
LinkedList<RubricQualitySelectedColumnModel> rubricQualitySelectedLevels = new LinkedList<RubricQualitySelectedColumnModel>();
RubricQualitySelectedColumnModel rubricQualitySelectedColumnModel = new RubricQualitySelectedColumnModel();
rubricQualitySelectedColumnModel.setQualityId("9a145aa8-f3d9-43a1-8f77-5387ff0693f2");
rubricQualitySelectedColumnModel.setColumnId("4fb17a1d-5681-46c2-a295-4e305c3eae23");
rubricQualitySelectedLevels.add(rubricQualitySelectedColumnModel);
RubricQualitySelectedColumnModel rubricQualitySelectedColumnModel1 = new RubricQualitySelectedColumnModel();
rubricQualitySelectedColumnModel1.setQualityId("d2331fb2-2761-402e-8de6-93e0afaa076e");
rubricQualitySelectedColumnModel1.setColumnId("aac076bf-51ba-48c5-a2e0-ee235b0b9740");
rubricQualitySelectedLevels.add(rubricQualitySelectedColumnModel1);
educationOutcome.setRubricQualitySelectedLevels(rubricQualitySelectedLevels);
EducationOutcome result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").submissions().byEducationSubmissionId("{educationSubmission-id}").outcomes().byEducationOutcomeId("{educationOutcome-id}").patch(educationOutcome);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationOutcome = {
    '@odata.type':'#microsoft.graph.educationRubricOutcome',
    rubricQualityFeedback: [
        {
            qualityId: '9a145aa8-f3d9-43a1-8f77-5387ff0693f2',
            feedback: {
                content: 'This is feedback specific to the first quality of the rubric.',
                contentType: 'text'
            }
        },
        {
            qualityId: 'd2331fb2-2761-402e-8de6-93e0afaa076e',
            feedback: {
                content: 'This is feedback specific to the second quality of the rubric.',
                contentType: 'text'
            }
        }
    ],
    rubricQualitySelectedLevels: [
        {
            qualityId: '9a145aa8-f3d9-43a1-8f77-5387ff0693f2',
            columnId: '4fb17a1d-5681-46c2-a295-4e305c3eae23'
        },
        {
            qualityId: 'd2331fb2-2761-402e-8de6-93e0afaa076e',
            columnId: 'aac076bf-51ba-48c5-a2e0-ee235b0b9740'
        }
    ]
};

await client.api('/education/classes/acdefc6b-2dc6-4e71-b1e9-6d9810ab1793/assignments/cf6005fc-9e13-44a2-a6ac-a53322006454/submissions/d1bee293-d8bb-48d4-af3e-c8cb0e3c7fe7/outcomes/9c0f2850-ff8f-4fd6-b3ac-e23077b59141')
	.update(educationOutcome);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationRubricOutcome;
use Microsoft\Graph\Generated\Models\RubricQualityFeedbackModel;
use Microsoft\Graph\Generated\Models\EducationItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\RubricQualitySelectedColumnModel;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationRubricOutcome();
$requestBody->setOdataType('#microsoft.graph.educationRubricOutcome');
$rubricQualityFeedbackRubricQualityFeedbackModel1 = new RubricQualityFeedbackModel();
$rubricQualityFeedbackRubricQualityFeedbackModel1->setQualityId('9a145aa8-f3d9-43a1-8f77-5387ff0693f2');
$rubricQualityFeedbackRubricQualityFeedbackModel1Feedback = new EducationItemBody();
$rubricQualityFeedbackRubricQualityFeedbackModel1Feedback->setContent('This is feedback specific to the first quality of the rubric.');
$rubricQualityFeedbackRubricQualityFeedbackModel1Feedback->setContentType(new BodyType('text'));
$rubricQualityFeedbackRubricQualityFeedbackModel1->setFeedback($rubricQualityFeedbackRubricQualityFeedbackModel1Feedback);
$rubricQualityFeedbackArray []= $rubricQualityFeedbackRubricQualityFeedbackModel1;
$rubricQualityFeedbackRubricQualityFeedbackModel2 = new RubricQualityFeedbackModel();
$rubricQualityFeedbackRubricQualityFeedbackModel2->setQualityId('d2331fb2-2761-402e-8de6-93e0afaa076e');
$rubricQualityFeedbackRubricQualityFeedbackModel2Feedback = new EducationItemBody();
$rubricQualityFeedbackRubricQualityFeedbackModel2Feedback->setContent('This is feedback specific to the second quality of the rubric.');
$rubricQualityFeedbackRubricQualityFeedbackModel2Feedback->setContentType(new BodyType('text'));
$rubricQualityFeedbackRubricQualityFeedbackModel2->setFeedback($rubricQualityFeedbackRubricQualityFeedbackModel2Feedback);
$rubricQualityFeedbackArray []= $rubricQualityFeedbackRubricQualityFeedbackModel2;
$requestBody->setRubricQualityFeedback($rubricQualityFeedbackArray);

$rubricQualitySelectedLevelsRubricQualitySelectedColumnModel1 = new RubricQualitySelectedColumnModel();
$rubricQualitySelectedLevelsRubricQualitySelectedColumnModel1->setQualityId('9a145aa8-f3d9-43a1-8f77-5387ff0693f2');
$rubricQualitySelectedLevelsRubricQualitySelectedColumnModel1->setColumnId('4fb17a1d-5681-46c2-a295-4e305c3eae23');
$rubricQualitySelectedLevelsArray []= $rubricQualitySelectedLevelsRubricQualitySelectedColumnModel1;
$rubricQualitySelectedLevelsRubricQualitySelectedColumnModel2 = new RubricQualitySelectedColumnModel();
$rubricQualitySelectedLevelsRubricQualitySelectedColumnModel2->setQualityId('d2331fb2-2761-402e-8de6-93e0afaa076e');
$rubricQualitySelectedLevelsRubricQualitySelectedColumnModel2->setColumnId('aac076bf-51ba-48c5-a2e0-ee235b0b9740');
$rubricQualitySelectedLevelsArray []= $rubricQualitySelectedLevelsRubricQualitySelectedColumnModel2;
$requestBody->setRubricQualitySelectedLevels($rubricQualitySelectedLevelsArray);


$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->submissions()->byEducationSubmissionId('educationSubmission-id')->outcomes()->byEducationOutcomeId('educationOutcome-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	"@odata.type" = "#microsoft.graph.educationRubricOutcome"
	rubricQualityFeedback = @(
		@{
			qualityId = "9a145aa8-f3d9-43a1-8f77-5387ff0693f2"
			feedback = @{
				content = "This is feedback specific to the first quality of the rubric."
				contentType = "text"
			}
		}
		@{
			qualityId = "d2331fb2-2761-402e-8de6-93e0afaa076e"
			feedback = @{
				content = "This is feedback specific to the second quality of the rubric."
				contentType = "text"
			}
		}
	)
	rubricQualitySelectedLevels = @(
		@{
			qualityId = "9a145aa8-f3d9-43a1-8f77-5387ff0693f2"
			columnId = "4fb17a1d-5681-46c2-a295-4e305c3eae23"
		}
		@{
			qualityId = "d2331fb2-2761-402e-8de6-93e0afaa076e"
			columnId = "aac076bf-51ba-48c5-a2e0-ee235b0b9740"
		}
	)
}

Update-MgEducationClassAssignmentSubmissionOutcome -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -EducationSubmissionId $educationSubmissionId -EducationOutcomeId $educationOutcomeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_rubric_outcome import EducationRubricOutcome
from msgraph.generated.models.rubric_quality_feedback_model import RubricQualityFeedbackModel
from msgraph.generated.models.education_item_body import EducationItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.rubric_quality_selected_column_model import RubricQualitySelectedColumnModel
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationRubricOutcome(
	odata_type = "#microsoft.graph.educationRubricOutcome",
	rubric_quality_feedback = [
		RubricQualityFeedbackModel(
			quality_id = "9a145aa8-f3d9-43a1-8f77-5387ff0693f2",
			feedback = EducationItemBody(
				content = "This is feedback specific to the first quality of the rubric.",
				content_type = BodyType.Text,
			),
		),
		RubricQualityFeedbackModel(
			quality_id = "d2331fb2-2761-402e-8de6-93e0afaa076e",
			feedback = EducationItemBody(
				content = "This is feedback specific to the second quality of the rubric.",
				content_type = BodyType.Text,
			),
		),
	],
	rubric_quality_selected_levels = [
		RubricQualitySelectedColumnModel(
			quality_id = "9a145aa8-f3d9-43a1-8f77-5387ff0693f2",
			column_id = "4fb17a1d-5681-46c2-a295-4e305c3eae23",
		),
		RubricQualitySelectedColumnModel(
			quality_id = "d2331fb2-2761-402e-8de6-93e0afaa076e",
			column_id = "aac076bf-51ba-48c5-a2e0-ee235b0b9740",
		),
	],
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').submissions.by_education_submission_id('educationSubmission-id').outcomes.by_education_outcome_id('educationOutcome-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json


{
    "@odata.type": "#microsoft.graph.educationRubricOutcome",
    "id": "65a46d78-1a2b-4a7e-bcf8-78a22ac2611b",
    "rubricQualityFeedback": [
        {
            "qualityId": "9a145aa8-f3d9-43a1-8f77-5387ff0693f2",
            "feedback": {
                "content": "This is feedback specific to the first quality of the rubric.",
                "contentType": "text"
            }
        },
        {
            "qualityId": "d2331fb2-2761-402e-8de6-93e0afaa076e",
            "feedback": {
                "content": "This is feedback specific to the second quality of the rubric.",
                "contentType": "text"
            }
        }
    ],
    "rubricQualitySelectedLevels": [
        {
            "qualityId": "9a145aa8-f3d9-43a1-8f77-5387ff0693f2",
            "columnId": "4fb17a1d-5681-46c2-a295-4e305c3eae23"
        },
        {
            "qualityId": "d2331fb2-2761-402e-8de6-93e0afaa076e",
            "columnId": "aac076bf-51ba-48c5-a2e0-ee235b0b9740"
        }
    ]
}
```
