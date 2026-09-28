<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationassignmentsettings-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update educationAssignmentSettings

Namespace: microsoft.graph

Update the properties of an [educationAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0) object. Only teachers can update these settings.

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
PATCH /education/classes/{class-id}/assignmentSettings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [educationAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0) object.

The following table shows the properties that are required when you update the [educationAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| submissionAnimationDisabled | Boolean | Indicates whether to show the turn-in celebration animation. A value of `true` indicates to skip the animation. Default value is `false`. |

## Response

If successful, this method returns a `200 OK` response code and an updated [educationAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update submissionAnimationDisabled

#### Request

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
PATCH https://graph.microsoft.com/v1.0/education/classes/acdefc6b-2dc6-4e71-b1e9-6d9810ab1793/assignmentSettings
Content-Type: application/json

{
  "submissionAnimationDisabled": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationAssignmentSettings
{
	SubmissionAnimationDisabled = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].AssignmentSettings.PatchAsync(requestBody);
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

requestBody := graphmodels.NewEducationAssignmentSettings()
submissionAnimationDisabled := true
requestBody.SetSubmissionAnimationDisabled(&submissionAnimationDisabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentSettings, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").AssignmentSettings().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentSettings educationAssignmentSettings = new EducationAssignmentSettings();
educationAssignmentSettings.setSubmissionAnimationDisabled(true);
EducationAssignmentSettings result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignmentSettings().patch(educationAssignmentSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignmentSettings = {
  submissionAnimationDisabled: true
};

await client.api('/education/classes/acdefc6b-2dc6-4e71-b1e9-6d9810ab1793/assignmentSettings')
	.update(educationAssignmentSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignmentSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignmentSettings();
$requestBody->setSubmissionAnimationDisabled(true);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignmentSettings()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	submissionAnimationDisabled = $true
}

Update-MgEducationClassAssignmentSetting -EducationClassId $educationClassId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment_settings import EducationAssignmentSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignmentSettings(
	submission_animation_disabled = True,
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignment_settings.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "submissionAnimationDisabled": true
}
```

### Example 2: Create grading categories

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/assignmentSettings
Content-type: application/json

{
  "gradingCategories": [
        {           
            "displayName": "Lab",
            "percentageWeight": 10
        },
        {
            "displayName": "Homework",
            "percentageWeight": 80
        },
        {
            "displayName": "Test",
            "percentageWeight": 10
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationAssignmentSettings
{
	GradingCategories = new List<EducationGradingCategory>
	{
		new EducationGradingCategory
		{
			DisplayName = "Lab",
			PercentageWeight = 10,
		},
		new EducationGradingCategory
		{
			DisplayName = "Homework",
			PercentageWeight = 80,
		},
		new EducationGradingCategory
		{
			DisplayName = "Test",
			PercentageWeight = 10,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].AssignmentSettings.PatchAsync(requestBody);
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

requestBody := graphmodels.NewEducationAssignmentSettings()


educationGradingCategory := graphmodels.NewEducationGradingCategory()
displayName := "Lab"
educationGradingCategory.SetDisplayName(&displayName) 
percentageWeight := int32(10)
educationGradingCategory.SetPercentageWeight(&percentageWeight) 
educationGradingCategory1 := graphmodels.NewEducationGradingCategory()
displayName := "Homework"
educationGradingCategory1.SetDisplayName(&displayName) 
percentageWeight := int32(80)
educationGradingCategory1.SetPercentageWeight(&percentageWeight) 
educationGradingCategory2 := graphmodels.NewEducationGradingCategory()
displayName := "Test"
educationGradingCategory2.SetDisplayName(&displayName) 
percentageWeight := int32(10)
educationGradingCategory2.SetPercentageWeight(&percentageWeight) 

gradingCategories := []graphmodels.EducationGradingCategoryable {
	educationGradingCategory,
	educationGradingCategory1,
	educationGradingCategory2,
}
requestBody.SetGradingCategories(gradingCategories)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentSettings, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").AssignmentSettings().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentSettings educationAssignmentSettings = new EducationAssignmentSettings();
LinkedList<EducationGradingCategory> gradingCategories = new LinkedList<EducationGradingCategory>();
EducationGradingCategory educationGradingCategory = new EducationGradingCategory();
educationGradingCategory.setDisplayName("Lab");
educationGradingCategory.setPercentageWeight(10);
gradingCategories.add(educationGradingCategory);
EducationGradingCategory educationGradingCategory1 = new EducationGradingCategory();
educationGradingCategory1.setDisplayName("Homework");
educationGradingCategory1.setPercentageWeight(80);
gradingCategories.add(educationGradingCategory1);
EducationGradingCategory educationGradingCategory2 = new EducationGradingCategory();
educationGradingCategory2.setDisplayName("Test");
educationGradingCategory2.setPercentageWeight(10);
gradingCategories.add(educationGradingCategory2);
educationAssignmentSettings.setGradingCategories(gradingCategories);
EducationAssignmentSettings result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignmentSettings().patch(educationAssignmentSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignmentSettings = {
  gradingCategories: [
        {           
            displayName: 'Lab',
            percentageWeight: 10
        },
        {
            displayName: 'Homework',
            percentageWeight: 80
        },
        {
            displayName: 'Test',
            percentageWeight: 10
        }
    ]
};

await client.api('/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/assignmentSettings')
	.update(educationAssignmentSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignmentSettings;
use Microsoft\Graph\Generated\Models\EducationGradingCategory;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignmentSettings();
$gradingCategoriesEducationGradingCategory1 = new EducationGradingCategory();
$gradingCategoriesEducationGradingCategory1->setDisplayName('Lab');
$gradingCategoriesEducationGradingCategory1->setPercentageWeight(10);
$gradingCategoriesArray []= $gradingCategoriesEducationGradingCategory1;
$gradingCategoriesEducationGradingCategory2 = new EducationGradingCategory();
$gradingCategoriesEducationGradingCategory2->setDisplayName('Homework');
$gradingCategoriesEducationGradingCategory2->setPercentageWeight(80);
$gradingCategoriesArray []= $gradingCategoriesEducationGradingCategory2;
$gradingCategoriesEducationGradingCategory3 = new EducationGradingCategory();
$gradingCategoriesEducationGradingCategory3->setDisplayName('Test');
$gradingCategoriesEducationGradingCategory3->setPercentageWeight(10);
$gradingCategoriesArray []= $gradingCategoriesEducationGradingCategory3;
$requestBody->setGradingCategories($gradingCategoriesArray);


$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignmentSettings()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	gradingCategories = @(
		@{
			displayName = "Lab"
			percentageWeight = 10
		}
		@{
			displayName = "Homework"
			percentageWeight = 80
		}
		@{
			displayName = "Test"
			percentageWeight = 10
		}
	)
}

Update-MgEducationClassAssignmentSetting -EducationClassId $educationClassId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment_settings import EducationAssignmentSettings
from msgraph.generated.models.education_grading_category import EducationGradingCategory
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignmentSettings(
	grading_categories = [
		EducationGradingCategory(
			display_name = "Lab",
			percentage_weight = 10,
		),
		EducationGradingCategory(
			display_name = "Homework",
			percentage_weight = 80,
		),
		EducationGradingCategory(
			display_name = "Test",
			percentage_weight = 10,
		),
	],
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignment_settings.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('37d99af7-cfc5-4e3b-8566-f7d40e4a2070')/assignmentSettings/$entity",
    "submissionAnimationDisabled": true,
    "gradingCategories@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('37d99af7-cfc5-4e3b-8566-f7d40e4a2070')/assignmentSettings/gradingCategories",
    "gradingCategories": [
        {
            "id": "36bf5273-d3e3-4f83-a534-8c816c33cc3e",
            "displayName": "Lab",
            "percentageWeight": 10
        },
        {
            "id": "5ffdba4e-2d79-4fe5-87d0-9a2b4552d3c0",
            "displayName": "Homework",
            "percentageWeight": 80
        },
        {
            "id": "691579b1-cf38-40ba-8758-c6a27529a8b7",
            "displayName": "Test",
            "percentageWeight": 10
        }
    ]
}
```

### Example 3: Delta payload to delete, modify and add grading categories.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
PATCH https://graph.microsoft.com/v1.0/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/assignmentSettings
Content-type: application/json

{
    "gradingCategories@delta": [
        {
            // Change this grading category's name
            "id": "03bd9196-ce2e-41bd-902f-df9ae02de4db",
            "displayName": "Lab Updated"
        },
        {
            // Delete this grading category 
            "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#gradingCategories/$deletedEntity",
            "id": "109e5d73-3ef7-42a5-88d8-7e30cdb85f06",
            "reason": "deleted"
        },
        {
            // Add a new grading category 
            "displayName": "New Homework",
            "percentageWeight": 50
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new EducationAssignmentSettings
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"gradingCategories@delta" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"id", new UntypedString("03bd9196-ce2e-41bd-902f-df9ae02de4db")
					},
					{
						"displayName", new UntypedString("Lab Updated")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.context", new UntypedString("https://graph.microsoft.com/v1.0/$metadata#gradingCategories/$deletedEntity")
					},
					{
						"id", new UntypedString("109e5d73-3ef7-42a5-88d8-7e30cdb85f06")
					},
					{
						"reason", new UntypedString("deleted")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"displayName", new UntypedString("New Homework")
					},
					{
						"percentageWeight", new UntypedString("50")
					},
				}),
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].AssignmentSettings.PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentSettings educationAssignmentSettings = new EducationAssignmentSettings();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> gradingCategoriesDelta = new LinkedList<Object>();
 property = new ();
property.setId("03bd9196-ce2e-41bd-902f-df9ae02de4db");
property.setDisplayName("Lab Updated");
gradingCategoriesDelta.add(property);
 property1 = new ();
property1.setOdataContext("https://graph.microsoft.com/v1.0/$metadata#gradingCategories/$deletedEntity");
property1.setId("109e5d73-3ef7-42a5-88d8-7e30cdb85f06");
property1.setReason("deleted");
gradingCategoriesDelta.add(property1);
 property2 = new ();
property2.setDisplayName("New Homework");
property2.setPercentageWeight(50);
gradingCategoriesDelta.add(property2);
additionalData.put("gradingCategories@delta", gradingCategoriesDelta);
educationAssignmentSettings.setAdditionalData(additionalData);
EducationAssignmentSettings result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignmentSettings().patch(educationAssignmentSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignmentSettings = {
    'gradingCategories@delta': [
        {
            // Change this grading category\'s name
            id: '03bd9196-ce2e-41bd-902f-df9ae02de4db',
            displayName: 'Lab Updated'
        },
        {
            // Delete this grading category 
            '@odata.context': 'https://graph.microsoft.com/v1.0/$metadata#gradingCategories/$deletedEntity',
            id: '109e5d73-3ef7-42a5-88d8-7e30cdb85f06',
            reason: 'deleted'
        },
        {
            // Add a new grading category 
            displayName: 'New Homework',
            percentageWeight: 50
        }
    ]
};

await client.api('/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/assignmentSettings')
	.update(educationAssignmentSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignmentSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignmentSettings();
$additionalData = [
	'gradingCategories@delta' => [
			[
				'id' => '03bd9196-ce2e-41bd-902f-df9ae02de4db',
				'displayName' => 'Lab Updated',
			],
			[
				'@odata.context' => 'https://graph.microsoft.com/v1.0/$metadata#gradingCategories/$deletedEntity',
				'id' => '109e5d73-3ef7-42a5-88d8-7e30cdb85f06',
				'reason' => 'deleted',
			],
			[
				'displayName' => 'New Homework',
				'percentageWeight' => 50,
			],
		],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignmentSettings()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	"gradingCategories@delta" = @(
		@{
			id = "03bd9196-ce2e-41bd-902f-df9ae02de4db"
			displayName = "Lab Updated"
		}
		@{
			"@odata.context" = "https://graph.microsoft.com/v1.0/$metadata#gradingCategories/$deletedEntity"
			id = "109e5d73-3ef7-42a5-88d8-7e30cdb85f06"
			reason = "deleted"
		}
		@{
			displayName = "New Homework"
			percentageWeight = 
		}
	)
}

Update-MgEducationClassAssignmentSetting -EducationClassId $educationClassId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment_settings import EducationAssignmentSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignmentSettings(
	additional_data = {
			"grading_categories@delta" : [
				{
						"id" : "03bd9196-ce2e-41bd-902f-df9ae02de4db",
						"display_name" : "Lab Updated",
				},
				{
						"@odata_context" : "https://graph.microsoft.com/v1.0/$metadata#gradingCategories/$deletedEntity",
						"id" : "109e5d73-3ef7-42a5-88d8-7e30cdb85f06",
						"reason" : "deleted",
				},
				{
						"display_name" : "New Homework",
						"percentage_weight" : 50,
				},
			],
	}
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignment_settings.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

> **Note:** You don't need to include the comments that appear in the request body examples in your requests. They are there to clarify each operation for you.

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('37d99af7-cfc5-4e3b-8566-f7d40e4a2070')/assignmentSettings/$entity",
    "submissionAnimationDisabled": true,
    "gradingCategories@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('37d99af7-cfc5-4e3b-8566-f7d40e4a2070')/assignmentSettings/gradingCategories",
    "gradingCategories": [
        {
            "id": "a5ca6dda-f220-43ca-81e4-02396b99f398",
            "displayName": "Test",
            "percentageWeight": 30
        },
        {
            "id": "03bd9196-ce2e-41bd-902f-df9ae02de4db",
            "displayName": "Lab Updated",
            "percentageWeight": 20
        },
        {
            "id": "905b49a5-1639-49ab-9fbe-6a035def5ba3",
            "displayName": "New Homework",
            "percentageWeight": 50
        }
    ]
}
```
