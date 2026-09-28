<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationassignmentsettings-post-gradingschemes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create educationGradingScheme

Namespace: microsoft.graph

Create a new [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) on an [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0). Only teachers can perform this operation.

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
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /education/classes/{id}/assignmentSettings/gradingSchemes
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of an [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and an [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows the request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/education/classes/de45722a-c202-43a9-9dd5-d82c45bcef91/assignmentSettings/gradingSchemes
Content-Type: application/json
 
{
  "displayName": "PassFailScheme",
  "grades": [
    {
      "displayName": "Pass",
      "minPercentage": 70,
      "defaultPercentage": 90
    },
    {
      "displayName": "Fail",
      "minPercentage": 0,
      "defaultPercentage": 50
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationGradingScheme
{
	DisplayName = "PassFailScheme",
	Grades = new List<EducationGradingSchemeGrade>
	{
		new EducationGradingSchemeGrade
		{
			DisplayName = "Pass",
			MinPercentage = 70f,
			DefaultPercentage = 90f,
		},
		new EducationGradingSchemeGrade
		{
			DisplayName = "Fail",
			MinPercentage = 0f,
			DefaultPercentage = 50f,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].AssignmentSettings.GradingSchemes.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationGradingScheme()
displayName := "PassFailScheme"
requestBody.SetDisplayName(&displayName) 


educationGradingSchemeGrade := graphmodels.NewEducationGradingSchemeGrade()
displayName := "Pass"
educationGradingSchemeGrade.SetDisplayName(&displayName) 
minPercentage := float32(70)
educationGradingSchemeGrade.SetMinPercentage(&minPercentage) 
defaultPercentage := float32(90)
educationGradingSchemeGrade.SetDefaultPercentage(&defaultPercentage) 
educationGradingSchemeGrade1 := graphmodels.NewEducationGradingSchemeGrade()
displayName := "Fail"
educationGradingSchemeGrade1.SetDisplayName(&displayName) 
minPercentage := float32(0)
educationGradingSchemeGrade1.SetMinPercentage(&minPercentage) 
defaultPercentage := float32(50)
educationGradingSchemeGrade1.SetDefaultPercentage(&defaultPercentage) 

grades := []graphmodels.EducationGradingSchemeGradeable {
	educationGradingSchemeGrade,
	educationGradingSchemeGrade1,
}
requestBody.SetGrades(grades)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
gradingSchemes, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").AssignmentSettings().GradingSchemes().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationGradingScheme educationGradingScheme = new EducationGradingScheme();
educationGradingScheme.setDisplayName("PassFailScheme");
LinkedList<EducationGradingSchemeGrade> grades = new LinkedList<EducationGradingSchemeGrade>();
EducationGradingSchemeGrade educationGradingSchemeGrade = new EducationGradingSchemeGrade();
educationGradingSchemeGrade.setDisplayName("Pass");
educationGradingSchemeGrade.setMinPercentage(70f);
educationGradingSchemeGrade.setDefaultPercentage(90f);
grades.add(educationGradingSchemeGrade);
EducationGradingSchemeGrade educationGradingSchemeGrade1 = new EducationGradingSchemeGrade();
educationGradingSchemeGrade1.setDisplayName("Fail");
educationGradingSchemeGrade1.setMinPercentage(0f);
educationGradingSchemeGrade1.setDefaultPercentage(50f);
grades.add(educationGradingSchemeGrade1);
educationGradingScheme.setGrades(grades);
EducationGradingScheme result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignmentSettings().gradingSchemes().post(educationGradingScheme);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationGradingScheme = {
  displayName: 'PassFailScheme',
  grades: [
    {
      displayName: 'Pass',
      minPercentage: 70,
      defaultPercentage: 90
    },
    {
      displayName: 'Fail',
      minPercentage: 0,
      defaultPercentage: 50
    }
  ]
};

await client.api('/education/classes/de45722a-c202-43a9-9dd5-d82c45bcef91/assignmentSettings/gradingSchemes')
	.post(educationGradingScheme);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationGradingScheme;
use Microsoft\Graph\Generated\Models\EducationGradingSchemeGrade;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationGradingScheme();
$requestBody->setDisplayName('PassFailScheme');
$gradesEducationGradingSchemeGrade1 = new EducationGradingSchemeGrade();
$gradesEducationGradingSchemeGrade1->setDisplayName('Pass');
$gradesEducationGradingSchemeGrade1->setMinPercentage(70);
$gradesEducationGradingSchemeGrade1->setDefaultPercentage(90);
$gradesArray []= $gradesEducationGradingSchemeGrade1;
$gradesEducationGradingSchemeGrade2 = new EducationGradingSchemeGrade();
$gradesEducationGradingSchemeGrade2->setDisplayName('Fail');
$gradesEducationGradingSchemeGrade2->setMinPercentage(0);
$gradesEducationGradingSchemeGrade2->setDefaultPercentage(50);
$gradesArray []= $gradesEducationGradingSchemeGrade2;
$requestBody->setGrades($gradesArray);


$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignmentSettings()->gradingSchemes()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	displayName = "PassFailScheme"
	grades = @(
		@{
			displayName = "Pass"
			minPercentage = 70
			defaultPercentage = 90
		}
		@{
			displayName = "Fail"
			minPercentage = 0
			defaultPercentage = 50
		}
	)
}

New-MgEducationClassAssignmentSettingGradingScheme -EducationClassId $educationClassId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_grading_scheme import EducationGradingScheme
from msgraph.generated.models.education_grading_scheme_grade import EducationGradingSchemeGrade
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationGradingScheme(
	display_name = "PassFailScheme",
	grades = [
		EducationGradingSchemeGrade(
			display_name = "Pass",
			min_percentage = 70,
			default_percentage = 90,
		),
		EducationGradingSchemeGrade(
			display_name = "Fail",
			min_percentage = 0,
			default_percentage = 50,
		),
	],
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignment_settings.grading_schemes.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('de45722a-c202-43a9-9dd5-d82c45bcef91')/assignmentSettings/gradingSchemes/$entity",
  "id": "acdbd23c-004e-4965-8e57-fa08c7d2020d",
  "displayName": "PassFailScheme",
  "hidePointsDuringGrading": false,
  "grades": [
    {
      "displayName": "Pass",
      "minPercentage": 70,
      "defaultPercentage": 90
    },
    {
      "displayName": "Fail",
      "minPercentage": 0,
      "defaultPercentage": 50
    }
  ]
}
```
