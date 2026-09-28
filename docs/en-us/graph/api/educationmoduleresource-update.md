<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationmoduleresource-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update educationModuleResource

Namespace: microsoft.graph

Update a [resource](https://learn.microsoft.com/en-us/graph/api/resources/educationmoduleresource?view=graph-rest-1.0) in a [module](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0). Only teachers can perform this operation.

The only one property that can be updated is **displayName**, for all resource types.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EduCurricula.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EduCurricula.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /education/classes/{class-id}/modules/{module-id}/resources/{resource-id}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply the new value for the **displayName** field.

## Response

If successful, this method returns a `200 OK` response code and an [educationModuleResource](https://learn.microsoft.com/en-us/graph/api/resources/educationmoduleresource?view=graph-rest-1.0) object in the response body.

## Examples

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
PATCH https://graph.microsoft.com/v1.0/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/modules/24eda3bf-32e5-4c70-a14d-831e606a2e4f/resources/896c2111-4d04-4b07-8a32-4565f3ba8597
Content-type: application/json

{
    "resource": {
        "displayName": "New pptx file patched.pptx"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationModuleResource
{
	Resource = new EducationResource
	{
		DisplayName = "New pptx file patched.pptx",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Modules["{educationModule-id}"].Resources["{educationModuleResource-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewEducationModuleResource()
resource := graphmodels.NewEducationResource()
displayName := "New pptx file patched.pptx"
resource.SetDisplayName(&displayName) 
requestBody.SetResource(resource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Modules().ByEducationModuleId("educationModule-id").Resources().ByEducationModuleResourceId("educationModuleResource-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationModuleResource educationModuleResource = new EducationModuleResource();
EducationResource resource = new EducationResource();
resource.setDisplayName("New pptx file patched.pptx");
educationModuleResource.setResource(resource);
EducationModuleResource result = graphClient.education().classes().byEducationClassId("{educationClass-id}").modules().byEducationModuleId("{educationModule-id}").resources().byEducationModuleResourceId("{educationModuleResource-id}").patch(educationModuleResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationModuleResource = {
    resource: {
        displayName: 'New pptx file patched.pptx'
    }
};

await client.api('/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/modules/24eda3bf-32e5-4c70-a14d-831e606a2e4f/resources/896c2111-4d04-4b07-8a32-4565f3ba8597')
	.update(educationModuleResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationModuleResource;
use Microsoft\Graph\Generated\Models\EducationResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationModuleResource();
$resource = new EducationResource();
$resource->setDisplayName('New pptx file patched.pptx');
$requestBody->setResource($resource);

$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->modules()->byEducationModuleId('educationModule-id')->resources()->byEducationModuleResourceId('educationModuleResource-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	resource = @{
		displayName = "New pptx file patched.pptx"
	}
}

Update-MgEducationClassModuleResource -EducationClassId $educationClassId -EducationModuleId $educationModuleId -EducationModuleResourceId $educationModuleResourceId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_module_resource import EducationModuleResource
from msgraph.generated.models.education_resource import EducationResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationModuleResource(
	resource = EducationResource(
		display_name = "New pptx file patched.pptx",
	),
)

result = await graph_client.education.classes.by_education_class_id('educationClass-id').modules.by_education_module_id('educationModule-id').resources.by_education_module_resource_id('educationModuleResource-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 Ok
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('37d99af7-cfc5-4e3b-8566-f7d40e4a2070')/modules('24eda3bf-32e5-4c70-a14d-831e606a2e4f')/resources/$entity",
    "id": "896c2111-4d04-4b07-8a32-4565f3ba8597",
    "resource": {
        "@odata.type": "#microsoft.graph.educationPowerPointResource",
        "displayName": "New pptx file patched.pptx",
        "createdDateTime": "2023-04-27T21:17:59.1379936Z",
        "lastModifiedDateTime": "2023-04-27T21:17:59.1380036Z",
        "fileUrl": "https://graph.microsoft.com/v1.0/drives/b!-Ik2sRPLDEWy_bR8l75jfeDcpXQcRKVOmcml10NQLQ1F2UVvTgEnTKi0GO59dbCL/items/01VANVJQYALMDWZF4OQ5D3DGULW2YGP2P2",
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
