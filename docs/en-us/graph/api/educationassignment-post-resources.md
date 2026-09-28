<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationassignment-post-resources?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-19 -->

# Create educationAssignmentResource

Namespace: microsoft.graph

Create an [assignment resource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0). Only teachers can perform this operation.

You can create the following types of assignment resources:

- [educationFileResource](https://learn.microsoft.com/en-us/graph/api/resources/educationfileresource?view=graph-rest-1.0)
- [educationExcelResource](https://learn.microsoft.com/en-us/graph/api/resources/educationexcelresource?view=graph-rest-1.0)
- [educationWordResource](https://learn.microsoft.com/en-us/graph/api/resources/educationwordresource?view=graph-rest-1.0)
- [educationLinkResource](https://learn.microsoft.com/en-us/graph/api/resources/educationlinkresource?view=graph-rest-1.0)
- [educationPowerPointResource](https://learn.microsoft.com/en-us/graph/api/resources/educationpowerpointresource?view=graph-rest-1.0)
- [educationMediaResource](https://learn.microsoft.com/en-us/graph/api/resources/educationmediaresource?view=graph-rest-1.0)
- [educationTeamsAppResource](https://learn.microsoft.com/en-us/graph/api/resources/educationteamsappresource?view=graph-rest-1.0)
- [educationSpeakerProgressResource](https://learn.microsoft.com/en-us/graph/api/resources/educationspeakerprogressresource?view=graph-rest-1.0)

Every resource has an **@odata.type** property to indicate which type of resource is being created.

Important

Before you can upload an assignment resource, you must [set up the resources folder](https://learn.microsoft.com/en-us/graph/api/educationassignment-setupresourcesfolder?view=graph-rest-1.0) for the [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) to upload the files to.

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
POST /education/classes/{class-id}/assignments/{assignment-id}/resources
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of one of the following resource types:

- [educationFileResource](https://learn.microsoft.com/en-us/graph/api/resources/educationfileresource?view=graph-rest-1.0)
- [educationExcelResource](https://learn.microsoft.com/en-us/graph/api/resources/educationexcelresource?view=graph-rest-1.0)
- [educationWordResource](https://learn.microsoft.com/en-us/graph/api/resources/educationwordresource?view=graph-rest-1.0)
- [educationLinkResource](https://learn.microsoft.com/en-us/graph/api/resources/educationlinkresource?view=graph-rest-1.0)
- [educationPowerPointResource](https://learn.microsoft.com/en-us/graph/api/resources/educationpowerpointresource?view=graph-rest-1.0)
- [educationMediaResource](https://learn.microsoft.com/en-us/graph/api/resources/educationmediaresource?view=graph-rest-1.0)
- [educationTeamsAppResource](https://learn.microsoft.com/en-us/graph/api/resources/educationteamsappresource?view=graph-rest-1.0)

> **Note:** You can't use this operation to create an [educationExternalResource](https://learn.microsoft.com/en-us/graph/api/resources/educationexternalresource?view=graph-rest-1.0).

## Response

If successful, this method returns a `201 Created` response code and an [educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) object in the response body.

This method also returns a `400 Bad Request` response code when an invalid request body is provided for the **educationSpeakerProgressResource** assignment resource in the following scenarios:

- The distributable resource attach limit is exceeded.
- No speaker coach setting or AI feedback is enabled.
- AI feedback is enabled, but the AI feedback criteria are null.
- AI feedback is enabled, but no settings are enabled in the AI feedback criteria.
- AI feedback is enabled, but **aiFeedbackCriteria.speechType** has an invalid value.
- AI feedback criteria have settings enabled, but AI feedback isn't enabled.
- **aiFeedbackCriteria.speechType** is set, but AI feedback isn't enabled.
- **recordingTimeLimitInMinutes** isn't between 1 and 10 \(inclusive\).
- **maxRecordingAttempts** isn't between 0 and 10 \(inclusive\).

## Examples

### Example 1: Create an educationLinkResource

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
POST https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources
Content-type: application/json

{
	"distributeForStudentWork": false,
	"resource": {
		"displayName": "Where the Wonders of Learning Never Cease | Wonderopolis",
		"link": "https://wonderopolis.org/",
		"thumbnailPreviewUrl": null,
		"@odata.type": "#microsoft.graph.educationLinkResource"
	}
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationAssignmentResource
{
	DistributeForStudentWork = false,
	Resource = new EducationLinkResource
	{
		DisplayName = "Where the Wonders of Learning Never Cease | Wonderopolis",
		Link = "https://wonderopolis.org/",
		OdataType = "#microsoft.graph.educationLinkResource",
		AdditionalData = new Dictionary<string, object>
		{
			{
				"thumbnailPreviewUrl" , null
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Resources.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationAssignmentResource()
distributeForStudentWork := false
requestBody.SetDistributeForStudentWork(&distributeForStudentWork) 
resource := graphmodels.NewEducationLinkResource()
displayName := "Where the Wonders of Learning Never Cease | Wonderopolis"
resource.SetDisplayName(&displayName) 
link := "https://wonderopolis.org/"
resource.SetLink(&link) 
additionalData := map[string]interface{}{
	thumbnailPreviewUrl := null
resource.SetThumbnailPreviewUrl(&thumbnailPreviewUrl) 
}
resource.SetAdditionalData(additionalData)
requestBody.SetResource(resource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Resources().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentResource educationAssignmentResource = new EducationAssignmentResource();
educationAssignmentResource.setDistributeForStudentWork(false);
EducationLinkResource resource = new EducationLinkResource();
resource.setDisplayName("Where the Wonders of Learning Never Cease | Wonderopolis");
resource.setLink("https://wonderopolis.org/");
resource.setOdataType("#microsoft.graph.educationLinkResource");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("thumbnailPreviewUrl", null);
resource.setAdditionalData(additionalData);
educationAssignmentResource.setResource(resource);
EducationAssignmentResource result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").resources().post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignmentResource = {
	distributeForStudentWork: false,
	resource: {
		displayName: 'Where the Wonders of Learning Never Cease | Wonderopolis',
		link: 'https://wonderopolis.org/',
		thumbnailPreviewUrl: null,
		'@odata.type': '#microsoft.graph.educationLinkResource'
	}
};

await client.api('/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources')
	.post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignmentResource;
use Microsoft\Graph\Generated\Models\EducationLinkResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignmentResource();
$requestBody->setDistributeForStudentWork(false);
$resource = new EducationLinkResource();
$resource->setDisplayName('Where the Wonders of Learning Never Cease | Wonderopolis');
$resource->setLink('https://wonderopolis.org/');
$resource->setOdataType('#microsoft.graph.educationLinkResource');
$additionalData = [
	'thumbnailPreviewUrl' => null,
];
$resource->setAdditionalData($additionalData);
$requestBody->setResource($resource);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->resources()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	distributeForStudentWork = $false
	resource = @{
		displayName = "Where the Wonders of Learning Never Cease | Wonderopolis"
		link = "https://wonderopolis.org/"
		thumbnailPreviewUrl = $null
		"@odata.type" = "#microsoft.graph.educationLinkResource"
	}
}

New-MgEducationClassAssignmentResource -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment_resource import EducationAssignmentResource
from msgraph.generated.models.education_link_resource import EducationLinkResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignmentResource(
	distribute_for_student_work = False,
	resource = EducationLinkResource(
		display_name = "Where the Wonders of Learning Never Cease | Wonderopolis",
		link = "https://wonderopolis.org/",
		odata_type = "#microsoft.graph.educationLinkResource",
		additional_data = {
				"thumbnail_preview_url" : None,
		}
	),
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').resources.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
	"@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('72a7baec-c3e9-4213-a850-f62de0adad5f')/assignments('1618dfb0-3ff2-4edf-8d5c-b8f81df00e80')/resources/$entity",
  "assignmentResourceUrl": null,  
	"id": "a2f95693-aea2-4d5e-a936-11ef390f8f20",
	"resource": {
		"@odata.type": "#microsoft.graph.educationLinkResource",
		"displayName": "Where the Wonders of Learning Never Cease | Wonderopolis",
		"createdDateTime": "2021-09-13T15:50:39.0017937Z",
		"lastModifiedDateTime": "2021-09-13T15:50:39.0017937Z",
		"link": "https://wonderopolis.org/",
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
}
```

### Example 2: Create an educationWordResource

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
POST https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources
Content-type: application/json

{
    "distributeForStudentWork":false,
    "resource": {
        "@odata.type": "microsoft.graph.educationWordResource",
        "displayName": "Issues and PR in guthub.docx",
        "fileUrl": "https://graph.microsoft.com/v1.0/drives/b!DPA6q59Tw0mtgmyXRUmrQRqBZTesG-lMkl1cBmvvMeUEWrOk89nKRpUEr4ZhNYBc/items/016XPCQEELISJB7NVNVBAK7V4UIF6Q27U2"
										  
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationAssignmentResource
{
	DistributeForStudentWork = false,
	Resource = new EducationWordResource
	{
		OdataType = "microsoft.graph.educationWordResource",
		DisplayName = "Issues and PR in guthub.docx",
		FileUrl = "https://graph.microsoft.com/v1.0/drives/b!DPA6q59Tw0mtgmyXRUmrQRqBZTesG-lMkl1cBmvvMeUEWrOk89nKRpUEr4ZhNYBc/items/016XPCQEELISJB7NVNVBAK7V4UIF6Q27U2",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Resources.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationAssignmentResource()
distributeForStudentWork := false
requestBody.SetDistributeForStudentWork(&distributeForStudentWork) 
resource := graphmodels.NewEducationWordResource()
displayName := "Issues and PR in guthub.docx"
resource.SetDisplayName(&displayName) 
fileUrl := "https://graph.microsoft.com/v1.0/drives/b!DPA6q59Tw0mtgmyXRUmrQRqBZTesG-lMkl1cBmvvMeUEWrOk89nKRpUEr4ZhNYBc/items/016XPCQEELISJB7NVNVBAK7V4UIF6Q27U2"
resource.SetFileUrl(&fileUrl) 
requestBody.SetResource(resource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Resources().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentResource educationAssignmentResource = new EducationAssignmentResource();
educationAssignmentResource.setDistributeForStudentWork(false);
EducationWordResource resource = new EducationWordResource();
resource.setOdataType("microsoft.graph.educationWordResource");
resource.setDisplayName("Issues and PR in guthub.docx");
resource.setFileUrl("https://graph.microsoft.com/v1.0/drives/b!DPA6q59Tw0mtgmyXRUmrQRqBZTesG-lMkl1cBmvvMeUEWrOk89nKRpUEr4ZhNYBc/items/016XPCQEELISJB7NVNVBAK7V4UIF6Q27U2");
educationAssignmentResource.setResource(resource);
EducationAssignmentResource result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").resources().post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignmentResource = {
    distributeForStudentWork: false,
    resource: {
        '@odata.type': 'microsoft.graph.educationWordResource',
        displayName: 'Issues and PR in guthub.docx',
        fileUrl: 'https://graph.microsoft.com/v1.0/drives/b!DPA6q59Tw0mtgmyXRUmrQRqBZTesG-lMkl1cBmvvMeUEWrOk89nKRpUEr4ZhNYBc/items/016XPCQEELISJB7NVNVBAK7V4UIF6Q27U2'
										  
    }
};

await client.api('/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources')
	.post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignmentResource;
use Microsoft\Graph\Generated\Models\EducationWordResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignmentResource();
$requestBody->setDistributeForStudentWork(false);
$resource = new EducationWordResource();
$resource->setOdataType('microsoft.graph.educationWordResource');
$resource->setDisplayName('Issues and PR in guthub.docx');
$resource->setFileUrl('https://graph.microsoft.com/v1.0/drives/b!DPA6q59Tw0mtgmyXRUmrQRqBZTesG-lMkl1cBmvvMeUEWrOk89nKRpUEr4ZhNYBc/items/016XPCQEELISJB7NVNVBAK7V4UIF6Q27U2');
$requestBody->setResource($resource);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->resources()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	distributeForStudentWork = $false
	resource = @{
		"@odata.type" = "microsoft.graph.educationWordResource"
		displayName = "Issues and PR in guthub.docx"
		fileUrl = "https://graph.microsoft.com/v1.0/drives/b!DPA6q59Tw0mtgmyXRUmrQRqBZTesG-lMkl1cBmvvMeUEWrOk89nKRpUEr4ZhNYBc/items/016XPCQEELISJB7NVNVBAK7V4UIF6Q27U2"
	}
}

New-MgEducationClassAssignmentResource -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment_resource import EducationAssignmentResource
from msgraph.generated.models.education_word_resource import EducationWordResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignmentResource(
	distribute_for_student_work = False,
	resource = EducationWordResource(
		odata_type = "microsoft.graph.educationWordResource",
		display_name = "Issues and PR in guthub.docx",
		file_url = "https://graph.microsoft.com/v1.0/drives/b!DPA6q59Tw0mtgmyXRUmrQRqBZTesG-lMkl1cBmvvMeUEWrOk89nKRpUEr4ZhNYBc/items/016XPCQEELISJB7NVNVBAK7V4UIF6Q27U2",
	),
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').resources.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('72a7baec-c3e9-4213-a850-f62de0adad5f')/assignments('1618dfb0-3ff2-4edf-8d5c-b8f81df00e80')/resources/$entity",
    "assignmentResourceUrl": null,
    "id": "d835503f-fd00-4840-b69c-7230d10e18b8",
    "resource": {
        "@odata.type": "#microsoft.graph.educationWordResource",
        "displayName": "Issues and PR in guthub.docx",
        "createdDateTime": "2021-08-04T00:23:08.6269586Z",
        "lastModifiedDateTime": "2021-08-04T00:23:08.6269586Z",
        "fileUrl": "https://graph.microsoft.com/v1.0/drives/b!DPA6q59Tw0mtgmyXRUmrQRqBZTesG-lMkl1cBmvvMeUEWrOk89nKRpUEr4ZhNYBc/items/016XPCQEELISJB7NVNVBAK7V4UIF6Q27U2",
        "createdBy": {
            "application": null,
            "device": null,
            "user": {
                "id": "80cefd93-8d88-40e2-b5d3-67898383e226",
                "displayName": null
            }
        },
        "lastModifiedBy": {
            "application": null,
            "device": null,
            "user": {
                "id": "80cefd93-8d88-40e2-b5d3-67898383e226",
                "displayName": null
            }
        }
    }
}
```

### Example 3: Create an educationFileResource

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
POST https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources
Content-type: application/json

{
	"distributeForStudentWork":false,
	"resource": {
		"displayName": "article.pdf",
		"file": {
			"odataid": "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RPHKSP6THE4ORD2RQAR6MQLF26G"
		},
		"@odata.type": "#microsoft.graph.educationFileResource"
	}
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new EducationAssignmentResource
{
	DistributeForStudentWork = false,
	Resource = new EducationFileResource
	{
		DisplayName = "article.pdf",
		OdataType = "#microsoft.graph.educationFileResource",
		AdditionalData = new Dictionary<string, object>
		{
			{
				"file" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"odataid", new UntypedString("https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RPHKSP6THE4ORD2RQAR6MQLF26G")
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Resources.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationAssignmentResource()
distributeForStudentWork := false
requestBody.SetDistributeForStudentWork(&distributeForStudentWork) 
resource := graphmodels.NewEducationFileResource()
displayName := "article.pdf"
resource.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
file := graph.New()
odataid := "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RPHKSP6THE4ORD2RQAR6MQLF26G"
file.SetOdataid(&odataid) 
	resource.SetFile(file)
}
resource.SetAdditionalData(additionalData)
requestBody.SetResource(resource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Resources().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentResource educationAssignmentResource = new EducationAssignmentResource();
educationAssignmentResource.setDistributeForStudentWork(false);
EducationFileResource resource = new EducationFileResource();
resource.setDisplayName("article.pdf");
resource.setOdataType("#microsoft.graph.educationFileResource");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 file = new ();
file.setOdataid("https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RPHKSP6THE4ORD2RQAR6MQLF26G");
additionalData.put("file", file);
resource.setAdditionalData(additionalData);
educationAssignmentResource.setResource(resource);
EducationAssignmentResource result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").resources().post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignmentResource = {
	distributeForStudentWork: false,
	resource: {
		displayName: 'article.pdf',
		file: {
			odataid: 'https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RPHKSP6THE4ORD2RQAR6MQLF26G'
		},
		'@odata.type': '#microsoft.graph.educationFileResource'
	}
};

await client.api('/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources')
	.post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignmentResource;
use Microsoft\Graph\Generated\Models\EducationFileResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignmentResource();
$requestBody->setDistributeForStudentWork(false);
$resource = new EducationFileResource();
$resource->setDisplayName('article.pdf');
$resource->setOdataType('#microsoft.graph.educationFileResource');
$additionalData = [
	'file' => [
		'odataid' => 'https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RPHKSP6THE4ORD2RQAR6MQLF26G',
	],
];
$resource->setAdditionalData($additionalData);
$requestBody->setResource($resource);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->resources()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	distributeForStudentWork = $false
	resource = @{
		displayName = "article.pdf"
		file = @{
			odataid = "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RPHKSP6THE4ORD2RQAR6MQLF26G"
		}
		"@odata.type" = "#microsoft.graph.educationFileResource"
	}
}

New-MgEducationClassAssignmentResource -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment_resource import EducationAssignmentResource
from msgraph.generated.models.education_file_resource import EducationFileResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignmentResource(
	distribute_for_student_work = False,
	resource = EducationFileResource(
		display_name = "article.pdf",
		odata_type = "#microsoft.graph.educationFileResource",
		additional_data = {
				"file" : {
						"odataid" : "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RPHKSP6THE4ORD2RQAR6MQLF26G",
				},
		}
	),
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').resources.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('72a7baec-c3e9-4213-a850-f62de0adad5f')/assignments('1618dfb0-3ff2-4edf-8d5c-b8f81df00e80')/resources/$entity",
    "distributeForStudentWork": false,
    "id": "eec7f642-9d9a-406f-bbae-4b3b2c12e273",
    "resource": {
        "@odata.type": "#microsoft.graph.educationFileResource",
        "displayName": "article.pdf",
        "createdDateTime": "2021-07-16T23:41:53.9378423Z",
        "lastModifiedDateTime": "2021-07-16T23:41:53.9378423Z",
        "fileUrl": "https://graph.microsoft.com/v1.0/drives/b!DPA6q59Tw0mtgmyXRUmrQRqBZTesG-lMkl1cBmvvMeU6BLWBcGc_R6UgCKyYyTin/items/016XPCQEA5VVDIMU4BSFG3VBI37MPHZ3OE",
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
}
```

### Example 4: Create an educationExcelResource

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources
Content-type: application/json

{
    "distributeForStudentWork":false,
    "resource": {
        "@odata.type": "microsoft.graph.educationExcelResource",
        "displayName":"Graph Doc pages.xlsx",
        "fileUrl": "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RIR7PSV4JJSFJHKNPUVUWGPW4O2"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationAssignmentResource
{
	DistributeForStudentWork = false,
	Resource = new EducationExcelResource
	{
		OdataType = "microsoft.graph.educationExcelResource",
		DisplayName = "Graph Doc pages.xlsx",
		FileUrl = "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RIR7PSV4JJSFJHKNPUVUWGPW4O2",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Resources.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationAssignmentResource()
distributeForStudentWork := false
requestBody.SetDistributeForStudentWork(&distributeForStudentWork) 
resource := graphmodels.NewEducationExcelResource()
displayName := "Graph Doc pages.xlsx"
resource.SetDisplayName(&displayName) 
fileUrl := "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RIR7PSV4JJSFJHKNPUVUWGPW4O2"
resource.SetFileUrl(&fileUrl) 
requestBody.SetResource(resource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Resources().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentResource educationAssignmentResource = new EducationAssignmentResource();
educationAssignmentResource.setDistributeForStudentWork(false);
EducationExcelResource resource = new EducationExcelResource();
resource.setOdataType("microsoft.graph.educationExcelResource");
resource.setDisplayName("Graph Doc pages.xlsx");
resource.setFileUrl("https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RIR7PSV4JJSFJHKNPUVUWGPW4O2");
educationAssignmentResource.setResource(resource);
EducationAssignmentResource result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").resources().post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignmentResource = {
    distributeForStudentWork: false,
    resource: {
        '@odata.type': 'microsoft.graph.educationExcelResource',
        displayName: 'Graph Doc pages.xlsx',
        fileUrl: 'https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RIR7PSV4JJSFJHKNPUVUWGPW4O2'
    }
};

await client.api('/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources')
	.post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignmentResource;
use Microsoft\Graph\Generated\Models\EducationExcelResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignmentResource();
$requestBody->setDistributeForStudentWork(false);
$resource = new EducationExcelResource();
$resource->setOdataType('microsoft.graph.educationExcelResource');
$resource->setDisplayName('Graph Doc pages.xlsx');
$resource->setFileUrl('https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RIR7PSV4JJSFJHKNPUVUWGPW4O2');
$requestBody->setResource($resource);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->resources()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	distributeForStudentWork = $false
	resource = @{
		"@odata.type" = "microsoft.graph.educationExcelResource"
		displayName = "Graph Doc pages.xlsx"
		fileUrl = "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RIR7PSV4JJSFJHKNPUVUWGPW4O2"
	}
}

New-MgEducationClassAssignmentResource -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment_resource import EducationAssignmentResource
from msgraph.generated.models.education_excel_resource import EducationExcelResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignmentResource(
	distribute_for_student_work = False,
	resource = EducationExcelResource(
		odata_type = "microsoft.graph.educationExcelResource",
		display_name = "Graph Doc pages.xlsx",
		file_url = "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RIR7PSV4JJSFJHKNPUVUWGPW4O2",
	),
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').resources.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('72a7baec-c3e9-4213-a850-f62de0adad5f')/assignments('1618dfb0-3ff2-4edf-8d5c-b8f81df00e80')/resources/$entity",
    "assignmentResourceUrl": null,
	"id": "517b36a6-9ca2-4e7b-9748-3af25f5cd4fd",
	"resource": {
		"@odata.type": "#microsoft.graph.educationExcelResource",
		"displayName": "Graph Doc pages.xlsx",
		"createdDateTime": "2021-09-13T15:50:49.7107759Z",
		"lastModifiedDateTime": "2021-09-13T15:50:49.7107759Z",
		"fileUrl": "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RIR7PSV4JJSFJHKNPUVUWGPW4O2",
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
}
```

### Example 5: Create an educationPowerPointResource

#### Request

The following example shows a request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources
Content-type: application/json

{
    "distributeForStudentWork":false,
    "resource": {
        "@odata.type": "microsoft.graph.educationPowerPointResource",
        "displayName":"state diagram.pptx",
        "fileUrl": "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RN327OXRN6EVFE2Q5FRJZTN5EOJ"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationAssignmentResource
{
	DistributeForStudentWork = false,
	Resource = new EducationPowerPointResource
	{
		OdataType = "microsoft.graph.educationPowerPointResource",
		DisplayName = "state diagram.pptx",
		FileUrl = "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RN327OXRN6EVFE2Q5FRJZTN5EOJ",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Resources.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationAssignmentResource()
distributeForStudentWork := false
requestBody.SetDistributeForStudentWork(&distributeForStudentWork) 
resource := graphmodels.NewEducationPowerPointResource()
displayName := "state diagram.pptx"
resource.SetDisplayName(&displayName) 
fileUrl := "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RN327OXRN6EVFE2Q5FRJZTN5EOJ"
resource.SetFileUrl(&fileUrl) 
requestBody.SetResource(resource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Resources().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentResource educationAssignmentResource = new EducationAssignmentResource();
educationAssignmentResource.setDistributeForStudentWork(false);
EducationPowerPointResource resource = new EducationPowerPointResource();
resource.setOdataType("microsoft.graph.educationPowerPointResource");
resource.setDisplayName("state diagram.pptx");
resource.setFileUrl("https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RN327OXRN6EVFE2Q5FRJZTN5EOJ");
educationAssignmentResource.setResource(resource);
EducationAssignmentResource result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").resources().post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignmentResource = {
    distributeForStudentWork: false,
    resource: {
        '@odata.type': 'microsoft.graph.educationPowerPointResource',
        displayName: 'state diagram.pptx',
        fileUrl: 'https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RN327OXRN6EVFE2Q5FRJZTN5EOJ'
    }
};

await client.api('/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources')
	.post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignmentResource;
use Microsoft\Graph\Generated\Models\EducationPowerPointResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignmentResource();
$requestBody->setDistributeForStudentWork(false);
$resource = new EducationPowerPointResource();
$resource->setOdataType('microsoft.graph.educationPowerPointResource');
$resource->setDisplayName('state diagram.pptx');
$resource->setFileUrl('https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RN327OXRN6EVFE2Q5FRJZTN5EOJ');
$requestBody->setResource($resource);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->resources()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	distributeForStudentWork = $false
	resource = @{
		"@odata.type" = "microsoft.graph.educationPowerPointResource"
		displayName = "state diagram.pptx"
		fileUrl = "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RN327OXRN6EVFE2Q5FRJZTN5EOJ"
	}
}

New-MgEducationClassAssignmentResource -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment_resource import EducationAssignmentResource
from msgraph.generated.models.education_power_point_resource import EducationPowerPointResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignmentResource(
	distribute_for_student_work = False,
	resource = EducationPowerPointResource(
		odata_type = "microsoft.graph.educationPowerPointResource",
		display_name = "state diagram.pptx",
		file_url = "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RN327OXRN6EVFE2Q5FRJZTN5EOJ",
	),
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').resources.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('72a7baec-c3e9-4213-a850-f62de0adad5f')/assignments('1618dfb0-3ff2-4edf-8d5c-b8f81df00e80')/resources/$entity",
  "assignmentResourceUrl": null,
	"id": "3cb7968b-082f-4756-bdfb-782b4538cc0a",
	"resource": {
		"@odata.type": "#microsoft.graph.educationPowerPointResource",
    "displayName": "state diagram.pptx",
		"createdDateTime": "2021-09-13T15:50:58.5428117Z",
		"lastModifiedDateTime": "2021-09-13T15:50:58.5428117Z",
		"fileUrl": "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RN327OXRN6EVFE2Q5FRJZTN5EOJ",
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
}
```

### Example 6: Create an educationMediaResource

#### Request

The following example shows a request.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/v1.0/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources
Content-type: application/json

{
    "distributeForStudentWork":false,
    "resource": {
        "@odata.type": "microsoft.graph.educationMediaResource",
        "displayName":"homework example.PNG",
        "fileUrl": "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RMUWOKAGSJZ6BHINJVKNMOOJABF"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationAssignmentResource
{
	DistributeForStudentWork = false,
	Resource = new EducationMediaResource
	{
		OdataType = "microsoft.graph.educationMediaResource",
		DisplayName = "homework example.PNG",
		FileUrl = "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RMUWOKAGSJZ6BHINJVKNMOOJABF",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Resources.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationAssignmentResource()
distributeForStudentWork := false
requestBody.SetDistributeForStudentWork(&distributeForStudentWork) 
resource := graphmodels.NewEducationMediaResource()
displayName := "homework example.PNG"
resource.SetDisplayName(&displayName) 
fileUrl := "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RMUWOKAGSJZ6BHINJVKNMOOJABF"
resource.SetFileUrl(&fileUrl) 
requestBody.SetResource(resource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Resources().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentResource educationAssignmentResource = new EducationAssignmentResource();
educationAssignmentResource.setDistributeForStudentWork(false);
EducationMediaResource resource = new EducationMediaResource();
resource.setOdataType("microsoft.graph.educationMediaResource");
resource.setDisplayName("homework example.PNG");
resource.setFileUrl("https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RMUWOKAGSJZ6BHINJVKNMOOJABF");
educationAssignmentResource.setResource(resource);
EducationAssignmentResource result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").resources().post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignmentResource = {
    distributeForStudentWork: false,
    resource: {
        '@odata.type': 'microsoft.graph.educationMediaResource',
        displayName: 'homework example.PNG',
        fileUrl: 'https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RMUWOKAGSJZ6BHINJVKNMOOJABF'
    }
};

await client.api('/education/classes/72a7baec-c3e9-4213-a850-f62de0adad5f/assignments/1618dfb0-3ff2-4edf-8d5c-b8f81df00e80/resources')
	.post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignmentResource;
use Microsoft\Graph\Generated\Models\EducationMediaResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignmentResource();
$requestBody->setDistributeForStudentWork(false);
$resource = new EducationMediaResource();
$resource->setOdataType('microsoft.graph.educationMediaResource');
$resource->setDisplayName('homework example.PNG');
$resource->setFileUrl('https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RMUWOKAGSJZ6BHINJVKNMOOJABF');
$requestBody->setResource($resource);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->resources()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	distributeForStudentWork = $false
	resource = @{
		"@odata.type" = "microsoft.graph.educationMediaResource"
		displayName = "homework example.PNG"
		fileUrl = "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RMUWOKAGSJZ6BHINJVKNMOOJABF"
	}
}

New-MgEducationClassAssignmentResource -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment_resource import EducationAssignmentResource
from msgraph.generated.models.education_media_resource import EducationMediaResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignmentResource(
	distribute_for_student_work = False,
	resource = EducationMediaResource(
		odata_type = "microsoft.graph.educationMediaResource",
		display_name = "homework example.PNG",
		file_url = "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RMUWOKAGSJZ6BHINJVKNMOOJABF",
	),
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').resources.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('72a7baec-c3e9-4213-a850-f62de0adad5f')/assignments('1618dfb0-3ff2-4edf-8d5c-b8f81df00e80')/resources/$entity",
    "distributeForStudentWork": false,
    "id": "30495bfd-c912-49d5-b3e1-92b60db3142a",
    "resource": {
        "@odata.type": "#microsoft.graph.educationMediaResource",
        "displayName": "homework example.PNG",
        "createdDateTime": "2021-09-16T00:09:32.2133895Z",
        "lastModifiedDateTime": "2021-09-16T00:09:32.2133895Z",
        "fileUrl": "https://graph.microsoft.com/v1.0/drives/b!OPmUsPgnBUiMIXMxWcj3neC1xck6I5NIsnFxfrLdmXoOOmEQNO79QpIMPdOmY3nf/items/01QTY63RMUWOKAGSJZ6BHINJVKNMOOJABF",
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
}
```

### Example 7: Create an educationTeamsAppResource

#### Request

The following example shows a request.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
POST https://graph.microsoft.com/v1.0/education/classes/2003c52e-807a-4186-9b49-60c573095461/assignments/820371a1-4589-4a4a-8b40-9d5db94b9186/resources
Content-type: application/json

{
    "distributeForStudentWork": false,
    "resource": {
        "displayName": "Template - My Story",
        "appId": "6fbeb90c-3d55-4bd5-82c4-bfe824be4300",
        "appIconWebUrl": "https://statics.teams.cdn.office.net/evergreen-assets/ThirdPartyApps/6fbeb90c-3d55-4bd5-82c4-bfe824be4300_largeImage.png?v=2.0.2",
        "teamsEmbeddedContentUrl": "https://app.api.edu.buncee.com/player/C7B0866C9B7E485EAE21AE14DBC3FD08?embed=1&render_slide_panel=1",
        "webUrl": "https://app.edu.buncee.com/buncee/C7B0866C9B7E485EAE21AE14DBC3FD08",
        "@odata.type": "#microsoft.graph.educationTeamsAppResource"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationAssignmentResource
{
	DistributeForStudentWork = false,
	Resource = new EducationTeamsAppResource
	{
		DisplayName = "Template - My Story",
		AppId = "6fbeb90c-3d55-4bd5-82c4-bfe824be4300",
		AppIconWebUrl = "https://statics.teams.cdn.office.net/evergreen-assets/ThirdPartyApps/6fbeb90c-3d55-4bd5-82c4-bfe824be4300_largeImage.png?v=2.0.2",
		TeamsEmbeddedContentUrl = "https://app.api.edu.buncee.com/player/C7B0866C9B7E485EAE21AE14DBC3FD08?embed=1&render_slide_panel=1",
		WebUrl = "https://app.edu.buncee.com/buncee/C7B0866C9B7E485EAE21AE14DBC3FD08",
		OdataType = "#microsoft.graph.educationTeamsAppResource",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Resources.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationAssignmentResource()
distributeForStudentWork := false
requestBody.SetDistributeForStudentWork(&distributeForStudentWork) 
resource := graphmodels.NewEducationTeamsAppResource()
displayName := "Template - My Story"
resource.SetDisplayName(&displayName) 
appId := "6fbeb90c-3d55-4bd5-82c4-bfe824be4300"
resource.SetAppId(&appId) 
appIconWebUrl := "https://statics.teams.cdn.office.net/evergreen-assets/ThirdPartyApps/6fbeb90c-3d55-4bd5-82c4-bfe824be4300_largeImage.png?v=2.0.2"
resource.SetAppIconWebUrl(&appIconWebUrl) 
teamsEmbeddedContentUrl := "https://app.api.edu.buncee.com/player/C7B0866C9B7E485EAE21AE14DBC3FD08?embed=1&render_slide_panel=1"
resource.SetTeamsEmbeddedContentUrl(&teamsEmbeddedContentUrl) 
webUrl := "https://app.edu.buncee.com/buncee/C7B0866C9B7E485EAE21AE14DBC3FD08"
resource.SetWebUrl(&webUrl) 
requestBody.SetResource(resource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Resources().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentResource educationAssignmentResource = new EducationAssignmentResource();
educationAssignmentResource.setDistributeForStudentWork(false);
EducationTeamsAppResource resource = new EducationTeamsAppResource();
resource.setDisplayName("Template - My Story");
resource.setAppId("6fbeb90c-3d55-4bd5-82c4-bfe824be4300");
resource.setAppIconWebUrl("https://statics.teams.cdn.office.net/evergreen-assets/ThirdPartyApps/6fbeb90c-3d55-4bd5-82c4-bfe824be4300_largeImage.png?v=2.0.2");
resource.setTeamsEmbeddedContentUrl("https://app.api.edu.buncee.com/player/C7B0866C9B7E485EAE21AE14DBC3FD08?embed=1&render_slide_panel=1");
resource.setWebUrl("https://app.edu.buncee.com/buncee/C7B0866C9B7E485EAE21AE14DBC3FD08");
resource.setOdataType("#microsoft.graph.educationTeamsAppResource");
educationAssignmentResource.setResource(resource);
EducationAssignmentResource result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").resources().post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignmentResource = {
    distributeForStudentWork: false,
    resource: {
        displayName: 'Template - My Story',
        appId: '6fbeb90c-3d55-4bd5-82c4-bfe824be4300',
        appIconWebUrl: 'https://statics.teams.cdn.office.net/evergreen-assets/ThirdPartyApps/6fbeb90c-3d55-4bd5-82c4-bfe824be4300_largeImage.png?v=2.0.2',
        teamsEmbeddedContentUrl: 'https://app.api.edu.buncee.com/player/C7B0866C9B7E485EAE21AE14DBC3FD08?embed=1&render_slide_panel=1',
        webUrl: 'https://app.edu.buncee.com/buncee/C7B0866C9B7E485EAE21AE14DBC3FD08',
        '@odata.type': '#microsoft.graph.educationTeamsAppResource'
    }
};

await client.api('/education/classes/2003c52e-807a-4186-9b49-60c573095461/assignments/820371a1-4589-4a4a-8b40-9d5db94b9186/resources')
	.post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignmentResource;
use Microsoft\Graph\Generated\Models\EducationTeamsAppResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignmentResource();
$requestBody->setDistributeForStudentWork(false);
$resource = new EducationTeamsAppResource();
$resource->setDisplayName('Template - My Story');
$resource->setAppId('6fbeb90c-3d55-4bd5-82c4-bfe824be4300');
$resource->setAppIconWebUrl('https://statics.teams.cdn.office.net/evergreen-assets/ThirdPartyApps/6fbeb90c-3d55-4bd5-82c4-bfe824be4300_largeImage.png?v=2.0.2');
$resource->setTeamsEmbeddedContentUrl('https://app.api.edu.buncee.com/player/C7B0866C9B7E485EAE21AE14DBC3FD08?embed=1&render_slide_panel=1');
$resource->setWebUrl('https://app.edu.buncee.com/buncee/C7B0866C9B7E485EAE21AE14DBC3FD08');
$resource->setOdataType('#microsoft.graph.educationTeamsAppResource');
$requestBody->setResource($resource);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->resources()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	distributeForStudentWork = $false
	resource = @{
		displayName = "Template - My Story"
		appId = "6fbeb90c-3d55-4bd5-82c4-bfe824be4300"
		appIconWebUrl = "https://statics.teams.cdn.office.net/evergreen-assets/ThirdPartyApps/6fbeb90c-3d55-4bd5-82c4-bfe824be4300_largeImage.png?v=2.0.2"
		teamsEmbeddedContentUrl = "https://app.api.edu.buncee.com/player/C7B0866C9B7E485EAE21AE14DBC3FD08?embed=1&render_slide_panel=1"
		webUrl = "https://app.edu.buncee.com/buncee/C7B0866C9B7E485EAE21AE14DBC3FD08"
		"@odata.type" = "#microsoft.graph.educationTeamsAppResource"
	}
}

New-MgEducationClassAssignmentResource -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment_resource import EducationAssignmentResource
from msgraph.generated.models.education_teams_app_resource import EducationTeamsAppResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignmentResource(
	distribute_for_student_work = False,
	resource = EducationTeamsAppResource(
		display_name = "Template - My Story",
		app_id = "6fbeb90c-3d55-4bd5-82c4-bfe824be4300",
		app_icon_web_url = "https://statics.teams.cdn.office.net/evergreen-assets/ThirdPartyApps/6fbeb90c-3d55-4bd5-82c4-bfe824be4300_largeImage.png?v=2.0.2",
		teams_embedded_content_url = "https://app.api.edu.buncee.com/player/C7B0866C9B7E485EAE21AE14DBC3FD08?embed=1&render_slide_panel=1",
		web_url = "https://app.edu.buncee.com/buncee/C7B0866C9B7E485EAE21AE14DBC3FD08",
		odata_type = "#microsoft.graph.educationTeamsAppResource",
	),
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').resources.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('2003c52e-807a-4186-9b49-60c573095461')/assignments('820371a1-4589-4a4a-8b40-9d5db94b9186')/resources/$entity",
    "distributeForStudentWork": false,
    "id": "6821bff5-91e4-4b63-8f98-8157305ff004",
    "resource": {
        "@odata.type": "#microsoft.graph.educationTeamsAppResource",
        "displayName": "Template - My Story",
        "createdDateTime": "2022-12-01T16:35:58.0718192Z",
        "lastModifiedDateTime": "2022-12-01T16:35:58.0718396Z",
        "appId": "6fbeb90c-3d55-4bd5-82c4-bfe824be4300",
        "appIconWebUrl": "https://statics.teams.cdn.office.net/evergreen-assets/ThirdPartyApps/6fbeb90c-3d55-4bd5-82c4-bfe824be4300_largeImage.png?v=2.0.2",
        "teamsEmbeddedContentUrl": "https://app.api.edu.buncee.com/player/C7B0866C9B7E485EAE21AE14DBC3FD08?embed=1&render_slide_panel=1",
        "webUrl": "https://app.edu.buncee.com/buncee/C7B0866C9B7E485EAE21AE14DBC3FD08",
        "createdBy": {
            "application": null,
            "device": null,
            "user": {
                "id": "fffafb29-e8bc-4de3-8106-be76ed2ad499",
                "displayName": null
            }
        },
        "lastModifiedBy": {
            "application": null,
            "device": null,
            "user": {
                "id": "fffafb29-e8bc-4de3-8106-be76ed2ad499",
                "displayName": null
            }
        }
    }
}
```

### Example 8: Create an educationSpeakerProgressResource

The following example shows how to create an [educationSpeakerProgressResource](https://learn.microsoft.com/en-us/graph/api/resources/educationspeakerprogressresource?view=graph-rest-1.0) assignment resource.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
POST https://graph.microsoft.com/v1.0/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/assignments/fe9c8d6f-baad-4b5e-b9d5-e2bb33e4ed19/resources
Content-Type: application/json

{
  "distributeForStudentWork": true,
  "resource": {
    "@odata.type": "microsoft.graph.educationSpeakerProgressResource",
    "displayName": "speakerProgressTestResource",
    "recordingTimeLimitInMinutes": 5,
    "showRehearsalReportToStudentBeforeMediaUpload": true,
    "maxRecordingAttempts": 1,
    "isVideoRequired": true,
    "isAiFeedbackEnabled": true,
    "presentationTitle": "speakerProgressTestResource",
    "spokenLanguageLocale": "en-US",
    "speakerCoachSettings": {
      "deliverySettings": {
        "isPronunciationEnabled": true
      }
    },
    "aiFeedbackCriteria": {
      "speechType": "informative",
      "aiFeedbackSettings": {
        "deliverySettings": {
          "isStyleEnabled": true
        }
      }
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationAssignmentResource
{
	DistributeForStudentWork = true,
	Resource = new EducationSpeakerProgressResource
	{
		OdataType = "microsoft.graph.educationSpeakerProgressResource",
		DisplayName = "speakerProgressTestResource",
		RecordingTimeLimitInMinutes = 5,
		ShowRehearsalReportToStudentBeforeMediaUpload = true,
		MaxRecordingAttempts = 1,
		IsVideoRequired = true,
		IsAiFeedbackEnabled = true,
		PresentationTitle = "speakerProgressTestResource",
		SpokenLanguageLocale = "en-US",
		SpeakerCoachSettings = new EducationSpeakerCoachSettings
		{
			DeliverySettings = new EducationSpeakerCoachDeliverySettings
			{
				IsPronunciationEnabled = true,
			},
		},
		AiFeedbackCriteria = new EducationAiFeedbackCriteria
		{
			SpeechType = EducationSpeechType.Informative,
			AiFeedbackSettings = new EducationAiFeedbackSettings
			{
				DeliverySettings = new EducationAiFeedbackDeliverySettings
				{
					IsStyleEnabled = true,
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Resources.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationAssignmentResource()
distributeForStudentWork := true
requestBody.SetDistributeForStudentWork(&distributeForStudentWork) 
resource := graphmodels.NewEducationSpeakerProgressResource()
displayName := "speakerProgressTestResource"
resource.SetDisplayName(&displayName) 
recordingTimeLimitInMinutes := int32(5)
resource.SetRecordingTimeLimitInMinutes(&recordingTimeLimitInMinutes) 
showRehearsalReportToStudentBeforeMediaUpload := true
resource.SetShowRehearsalReportToStudentBeforeMediaUpload(&showRehearsalReportToStudentBeforeMediaUpload) 
maxRecordingAttempts := int32(1)
resource.SetMaxRecordingAttempts(&maxRecordingAttempts) 
isVideoRequired := true
resource.SetIsVideoRequired(&isVideoRequired) 
isAiFeedbackEnabled := true
resource.SetIsAiFeedbackEnabled(&isAiFeedbackEnabled) 
presentationTitle := "speakerProgressTestResource"
resource.SetPresentationTitle(&presentationTitle) 
spokenLanguageLocale := "en-US"
resource.SetSpokenLanguageLocale(&spokenLanguageLocale) 
speakerCoachSettings := graphmodels.NewEducationSpeakerCoachSettings()
deliverySettings := graphmodels.NewEducationSpeakerCoachDeliverySettings()
isPronunciationEnabled := true
deliverySettings.SetIsPronunciationEnabled(&isPronunciationEnabled) 
speakerCoachSettings.SetDeliverySettings(deliverySettings)
resource.SetSpeakerCoachSettings(speakerCoachSettings)
aiFeedbackCriteria := graphmodels.NewEducationAiFeedbackCriteria()
speechType := graphmodels.INFORMATIVE_EDUCATIONSPEECHTYPE 
aiFeedbackCriteria.SetSpeechType(&speechType) 
aiFeedbackSettings := graphmodels.NewEducationAiFeedbackSettings()
deliverySettings := graphmodels.NewEducationAiFeedbackDeliverySettings()
isStyleEnabled := true
deliverySettings.SetIsStyleEnabled(&isStyleEnabled) 
aiFeedbackSettings.SetDeliverySettings(deliverySettings)
aiFeedbackCriteria.SetAiFeedbackSettings(aiFeedbackSettings)
resource.SetAiFeedbackCriteria(aiFeedbackCriteria)
requestBody.SetResource(resource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Resources().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentResource educationAssignmentResource = new EducationAssignmentResource();
educationAssignmentResource.setDistributeForStudentWork(true);
EducationSpeakerProgressResource resource = new EducationSpeakerProgressResource();
resource.setOdataType("microsoft.graph.educationSpeakerProgressResource");
resource.setDisplayName("speakerProgressTestResource");
resource.setRecordingTimeLimitInMinutes(5);
resource.setShowRehearsalReportToStudentBeforeMediaUpload(true);
resource.setMaxRecordingAttempts(1);
resource.setIsVideoRequired(true);
resource.setIsAiFeedbackEnabled(true);
resource.setPresentationTitle("speakerProgressTestResource");
resource.setSpokenLanguageLocale("en-US");
EducationSpeakerCoachSettings speakerCoachSettings = new EducationSpeakerCoachSettings();
EducationSpeakerCoachDeliverySettings deliverySettings = new EducationSpeakerCoachDeliverySettings();
deliverySettings.setIsPronunciationEnabled(true);
speakerCoachSettings.setDeliverySettings(deliverySettings);
resource.setSpeakerCoachSettings(speakerCoachSettings);
EducationAiFeedbackCriteria aiFeedbackCriteria = new EducationAiFeedbackCriteria();
aiFeedbackCriteria.setSpeechType(EducationSpeechType.Informative);
EducationAiFeedbackSettings aiFeedbackSettings = new EducationAiFeedbackSettings();
EducationAiFeedbackDeliverySettings deliverySettings1 = new EducationAiFeedbackDeliverySettings();
deliverySettings1.setIsStyleEnabled(true);
aiFeedbackSettings.setDeliverySettings(deliverySettings1);
aiFeedbackCriteria.setAiFeedbackSettings(aiFeedbackSettings);
resource.setAiFeedbackCriteria(aiFeedbackCriteria);
educationAssignmentResource.setResource(resource);
EducationAssignmentResource result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").resources().post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationAssignmentResource = {
  distributeForStudentWork: true,
  resource: {
    '@odata.type': 'microsoft.graph.educationSpeakerProgressResource',
    displayName: 'speakerProgressTestResource',
    recordingTimeLimitInMinutes: 5,
    showRehearsalReportToStudentBeforeMediaUpload: true,
    maxRecordingAttempts: 1,
    isVideoRequired: true,
    isAiFeedbackEnabled: true,
    presentationTitle: 'speakerProgressTestResource',
    spokenLanguageLocale: 'en-US',
    speakerCoachSettings: {
      deliverySettings: {
        isPronunciationEnabled: true
      }
    },
    aiFeedbackCriteria: {
      speechType: 'informative',
      aiFeedbackSettings: {
        deliverySettings: {
          isStyleEnabled: true
        }
      }
    }
  }
};

await client.api('/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/assignments/fe9c8d6f-baad-4b5e-b9d5-e2bb33e4ed19/resources')
	.post(educationAssignmentResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationAssignmentResource;
use Microsoft\Graph\Generated\Models\EducationSpeakerProgressResource;
use Microsoft\Graph\Generated\Models\EducationSpeakerCoachSettings;
use Microsoft\Graph\Generated\Models\EducationSpeakerCoachDeliverySettings;
use Microsoft\Graph\Generated\Models\EducationAiFeedbackCriteria;
use Microsoft\Graph\Generated\Models\EducationSpeechType;
use Microsoft\Graph\Generated\Models\EducationAiFeedbackSettings;
use Microsoft\Graph\Generated\Models\EducationAiFeedbackDeliverySettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationAssignmentResource();
$requestBody->setDistributeForStudentWork(true);
$resource = new EducationSpeakerProgressResource();
$resource->setOdataType('microsoft.graph.educationSpeakerProgressResource');
$resource->setDisplayName('speakerProgressTestResource');
$resource->setRecordingTimeLimitInMinutes(5);
$resource->setShowRehearsalReportToStudentBeforeMediaUpload(true);
$resource->setMaxRecordingAttempts(1);
$resource->setIsVideoRequired(true);
$resource->setIsAiFeedbackEnabled(true);
$resource->setPresentationTitle('speakerProgressTestResource');
$resource->setSpokenLanguageLocale('en-US');
$resourceSpeakerCoachSettings = new EducationSpeakerCoachSettings();
$resourceSpeakerCoachSettingsDeliverySettings = new EducationSpeakerCoachDeliverySettings();
$resourceSpeakerCoachSettingsDeliverySettings->setIsPronunciationEnabled(true);
$resourceSpeakerCoachSettings->setDeliverySettings($resourceSpeakerCoachSettingsDeliverySettings);
$resource->setSpeakerCoachSettings($resourceSpeakerCoachSettings);
$resourceAiFeedbackCriteria = new EducationAiFeedbackCriteria();
$resourceAiFeedbackCriteria->setSpeechType(new EducationSpeechType('informative'));
$resourceAiFeedbackCriteriaAiFeedbackSettings = new EducationAiFeedbackSettings();
$resourceAiFeedbackCriteriaAiFeedbackSettingsDeliverySettings = new EducationAiFeedbackDeliverySettings();
$resourceAiFeedbackCriteriaAiFeedbackSettingsDeliverySettings->setIsStyleEnabled(true);
$resourceAiFeedbackCriteriaAiFeedbackSettings->setDeliverySettings($resourceAiFeedbackCriteriaAiFeedbackSettingsDeliverySettings);
$resourceAiFeedbackCriteria->setAiFeedbackSettings($resourceAiFeedbackCriteriaAiFeedbackSettings);
$resource->setAiFeedbackCriteria($resourceAiFeedbackCriteria);
$requestBody->setResource($resource);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->resources()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	distributeForStudentWork = $true
	resource = @{
		"@odata.type" = "microsoft.graph.educationSpeakerProgressResource"
		displayName = "speakerProgressTestResource"
		recordingTimeLimitInMinutes = 
		showRehearsalReportToStudentBeforeMediaUpload = $true
		maxRecordingAttempts = 
		isVideoRequired = $true
		isAiFeedbackEnabled = $true
		presentationTitle = "speakerProgressTestResource"
		spokenLanguageLocale = "en-US"
		speakerCoachSettings = @{
			deliverySettings = @{
				isPronunciationEnabled = $true
			}
		}
		aiFeedbackCriteria = @{
			speechType = "informative"
			aiFeedbackSettings = @{
				deliverySettings = @{
					isStyleEnabled = $true
				}
			}
		}
	}
}

New-MgEducationClassAssignmentResource -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_assignment_resource import EducationAssignmentResource
from msgraph.generated.models.education_speaker_progress_resource import EducationSpeakerProgressResource
from msgraph.generated.models.education_speaker_coach_settings import EducationSpeakerCoachSettings
from msgraph.generated.models.education_speaker_coach_delivery_settings import EducationSpeakerCoachDeliverySettings
from msgraph.generated.models.education_ai_feedback_criteria import EducationAiFeedbackCriteria
from msgraph.generated.models.education_speech_type import EducationSpeechType
from msgraph.generated.models.education_ai_feedback_settings import EducationAiFeedbackSettings
from msgraph.generated.models.education_ai_feedback_delivery_settings import EducationAiFeedbackDeliverySettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationAssignmentResource(
	distribute_for_student_work = True,
	resource = EducationSpeakerProgressResource(
		odata_type = "microsoft.graph.educationSpeakerProgressResource",
		display_name = "speakerProgressTestResource",
		recording_time_limit_in_minutes = 5,
		show_rehearsal_report_to_student_before_media_upload = True,
		max_recording_attempts = 1,
		is_video_required = True,
		is_ai_feedback_enabled = True,
		presentation_title = "speakerProgressTestResource",
		spoken_language_locale = "en-US",
		speaker_coach_settings = EducationSpeakerCoachSettings(
			delivery_settings = EducationSpeakerCoachDeliverySettings(
				is_pronunciation_enabled = True,
			),
		),
		ai_feedback_criteria = EducationAiFeedbackCriteria(
			speech_type = EducationSpeechType.Informative,
			ai_feedback_settings = EducationAiFeedbackSettings(
				delivery_settings = EducationAiFeedbackDeliverySettings(
					is_style_enabled = True,
				),
			),
		),
	),
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').resources.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('37d99af7-cfc5-4e3b-8566-f7d40e4a2070')/assignments('fe9c8d6f-baad-4b5e-b9d5-e2bb33e4ed19')/resources/$entity",
  "distributeForStudentWork": true,
  "id": "af98a1e1-3393-4ee0-8bcc-8b5bb4598d1c",
  "resource": {
    "@odata.type": "#microsoft.graph.educationSpeakerProgressResource",
    "displayName": "speakerProgressTestResource",
    "createdDateTime": "2025-03-17T16:26:03.5530234Z",
    "lastModifiedDateTime": "2025-03-17T16:26:03.5530384Z",
    "recordingTimeLimitInMinutes": 5,
    "showRehearsalReportToStudentBeforeMediaUpload": true,
    "maxRecordingAttempts": 1,
    "isVideoRequired": true,
    "isAiFeedbackEnabled": true,
    "presentationTitle": "speakerProgressTestResource",
    "spokenLanguageLocale": "en-US",
    "createdBy": {
      "application": null,
      "device": null,
      "user": {
        "id": "fffafb29-e8bc-4de3-8106-be76ed2ad499",
        "displayName": null
      }
    },
    "lastModifiedBy": {
      "application": null,
      "device": null,
      "user": {
        "id": "fffafb29-e8bc-4de3-8106-be76ed2ad499",
        "displayName": null
      }
    },
    "speakerCoachSettings": {
      "deliverySettings": {
        "isPaceEnabled": false,
        "areFillerWordsEnabled": false,
        "isPitchEnabled": false,
        "isPronunciationEnabled": true
      },
      "contentSettings": {
        "isInclusivenessEnabled": false,
        "isRepetitiveLanguageEnabled": false
      },
      "audienceEngagementSettings": {
        "isBodyLanguageEnabled": false
      }
    },
    "aiFeedbackCriteria": {
      "speechType": "informative",
      "aiFeedbackSettings": {
        "deliverySettings": {
          "isLanguageUseEnabled": false,
          "areRhetoricalTechniquesEnabled": false,
          "isStyleEnabled": true
        },
        "contentSettings": {
          "isSpeechOrganizationEnabled": false,
          "isMessageClarityEnabled": false,
          "isQualityOfInformationEnabled": false
        },
        "audienceEngagementSettings": {
          "areEngagementStrategiesEnabled": false,
          "isEmotionalAndIntellectualAppealEnabled": false,
          "isCallToActionEnabled": false
        }
      }
    }
  }
}
```

## Related content

- [Status, transitions, and limitations for assignments and submissions](https://learn.microsoft.com/en-us/graph/assignments-submissions-status-transition)
- [Upload files for education assignments and submissions](https://learn.microsoft.com/en-us/graph/education-upload-resource-overview)
