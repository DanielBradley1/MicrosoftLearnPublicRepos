<!-- Source: https://learn.microsoft.com/en-us/graph/api/goals-post-exportjobs?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# Create goalsExportJob

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [goalsExportJob](https://learn.microsoft.com/en-us/graph/api/resources/goalsexportjob?view=graph-rest-beta) object in a Viva Goals organization.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Goals-Export.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /employeeExperience/goals/exportJobs
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [goalsExportJob](https://learn.microsoft.com/en-us/graph/api/resources/goalsexportjob?view=graph-rest-beta) object.

You can specify the following properties when you create a **goalsExportJob** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| goalsOrganizationId | String | The unique identifier of the [Viva Goals organization](https://learn.microsoft.com/en-us/viva/goals/understand-orgs-and-teams#organizations-in-viva-goals). |
| explorerViewId | String | The unique identifier of the explorer view to be exported. |

You can get the **goalsOrganizationId** and **explorerViewId** values from the URL of a [Explorer view](https://learn.microsoft.com/en-us/viva/goals/explorer#default-views-in-explorer).

```http
https://goals.microsoft.com/org_uuid/94a356ab-53d5-40e7-8a85-053d6d3b9eb3/objective-explorer?viewId=e5e7a3c1-8cdf-409d-9ce9-ff730d65d95e
```

- The `org_uuid` in the URL, in this example `94a356ab-53d5-40e7-8a85-053d6d3b9eb3`, represents the **goalsOrganizationId**.
- The `viewId` in the URL, in this example `e5e7a3c1-8cdf-409d-9ce9-ff730d65d95e`, represents the **explorerViewId**.

## Response

If successful, this method returns a `201 Created` response code and a [goalsExportJob](https://learn.microsoft.com/en-us/graph/api/resources/goalsexportjob?view=graph-rest-beta) object in the response body.

This method also returns `409 Conflict` when you attempt to create a [goalsExportJob](https://learn.microsoft.com/en-us/graph/api/resources/goalsexportjob?view=graph-rest-beta) object with the same values \(**goalsOrganizationId** and **explorerViewId**\) as an existing [goalsExportJob](https://learn.microsoft.com/en-us/graph/api/resources/goalsexportjob?view=graph-rest-beta) object that is pending completion.

When the pending job completes, you can create the new [goalsExportJob](https://learn.microsoft.com/en-us/graph/api/resources/goalsexportjob?view=graph-rest-beta) object.

### Response headers

| Name | Description |
| :--- | :--- |
| Location | URL to call to check the status of the operation. Required. |

## Examples

### Example 1: Status is `notStarted`

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
POST https://graph.microsoft.com/beta/employeeExperience/goals/exportJobs
Content-Type: application/json

{
  "goalsOrganizationId": "String",
  "explorerViewId": "String"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new GoalsExportJob
{
	GoalsOrganizationId = "String",
	ExplorerViewId = "String",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.Goals.ExportJobs.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewGoalsExportJob()
goalsOrganizationId := "String"
requestBody.SetGoalsOrganizationId(&goalsOrganizationId) 
explorerViewId := "String"
requestBody.SetExplorerViewId(&explorerViewId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
exportJobs, err := graphClient.EmployeeExperience().Goals().ExportJobs().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GoalsExportJob goalsExportJob = new GoalsExportJob();
goalsExportJob.setGoalsOrganizationId("String");
goalsExportJob.setExplorerViewId("String");
GoalsExportJob result = graphClient.employeeExperience().goals().exportJobs().post(goalsExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const goalsExportJob = {
  goalsOrganizationId: 'String',
  explorerViewId: 'String'
};

await client.api('/employeeExperience/goals/exportJobs')
	.version('beta')
	.post(goalsExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\GoalsExportJob;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GoalsExportJob();
$requestBody->setGoalsOrganizationId('String');
$requestBody->setExplorerViewId('String');

$result = $graphServiceClient->employeeExperience()->goals()->exportJobs()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.goals_export_job import GoalsExportJob
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GoalsExportJob(
	goals_organization_id = "String",
	explorer_view_id = "String",
)

result = await graph_client.employee_experience.goals.export_jobs.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Location: "https://graph.microsoft.com/beta/employeeexperience/goals/exportJobs/j!uJJZyGd87hGFgvZV8bl-GlCBmj39kL1Cl3clung9SgU"

{
  "@odata.type": "#microsoft.graph.goalsExportJob",
  "id": "9eb0bfa0-eaa1-b225-1f83-54ae3e711753",
  "createdDateTime": "String (timestamp)",
  "status": "String"
}
```

### Example 2: Status is `conflicting`

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/employeeExperience/goals/exportJobs
Content-Type: application/json

{
  "goalsOrganizationId": "String",
  "explorerViewId": "String"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new GoalsExportJob
{
	GoalsOrganizationId = "String",
	ExplorerViewId = "String",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.Goals.ExportJobs.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewGoalsExportJob()
goalsOrganizationId := "String"
requestBody.SetGoalsOrganizationId(&goalsOrganizationId) 
explorerViewId := "String"
requestBody.SetExplorerViewId(&explorerViewId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
exportJobs, err := graphClient.EmployeeExperience().Goals().ExportJobs().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GoalsExportJob goalsExportJob = new GoalsExportJob();
goalsExportJob.setGoalsOrganizationId("String");
goalsExportJob.setExplorerViewId("String");
GoalsExportJob result = graphClient.employeeExperience().goals().exportJobs().post(goalsExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const goalsExportJob = {
  goalsOrganizationId: 'String',
  explorerViewId: 'String'
};

await client.api('/employeeExperience/goals/exportJobs')
	.version('beta')
	.post(goalsExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\GoalsExportJob;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GoalsExportJob();
$requestBody->setGoalsOrganizationId('String');
$requestBody->setExplorerViewId('String');

$result = $graphServiceClient->employeeExperience()->goals()->exportJobs()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.goals_export_job import GoalsExportJob
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GoalsExportJob(
	goals_organization_id = "String",
	explorer_view_id = "String",
)

result = await graph_client.employee_experience.goals.export_jobs.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 409 Conflict
Content-type: application/json
Location: "https://graph.microsoft.com/beta/employeeexperience/goals/exportJobs/j!uJJZyGd87hGFgvZV8bl-GlCBmj39kL1Cl3clung9SgU"

{
    "error": 
    {
        "code": "notAllowed",
        "message": "Another export job is still active or waiting to be executed",
        "target": "j!uJJZyGd87hGFgvZV8bl-GlCBmj39kL1Cl3clung9SgU",
        "innererror":
        {
            "code": "exportJobAlreadyExists",
            "date": "String (timestamp)",
            "request-id": "String",
            "client-request-id": "String"
        }
    }
}
```

### Example 3: Specified goalsOrganizationId doesn't exist

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/employeeExperience/goals/exportJobs
Content-Type: application/json

{
  "goalsOrganizationId": "String",
  "explorerViewId": "String"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new GoalsExportJob
{
	GoalsOrganizationId = "String",
	ExplorerViewId = "String",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.Goals.ExportJobs.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewGoalsExportJob()
goalsOrganizationId := "String"
requestBody.SetGoalsOrganizationId(&goalsOrganizationId) 
explorerViewId := "String"
requestBody.SetExplorerViewId(&explorerViewId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
exportJobs, err := graphClient.EmployeeExperience().Goals().ExportJobs().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GoalsExportJob goalsExportJob = new GoalsExportJob();
goalsExportJob.setGoalsOrganizationId("String");
goalsExportJob.setExplorerViewId("String");
GoalsExportJob result = graphClient.employeeExperience().goals().exportJobs().post(goalsExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const goalsExportJob = {
  goalsOrganizationId: 'String',
  explorerViewId: 'String'
};

await client.api('/employeeExperience/goals/exportJobs')
	.version('beta')
	.post(goalsExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\GoalsExportJob;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GoalsExportJob();
$requestBody->setGoalsOrganizationId('String');
$requestBody->setExplorerViewId('String');

$result = $graphServiceClient->employeeExperience()->goals()->exportJobs()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.goals_export_job import GoalsExportJob
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GoalsExportJob(
	goals_organization_id = "String",
	explorer_view_id = "String",
)

result = await graph_client.employee_experience.goals.export_jobs.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 404 Not Found 
Content-type: application/json

{
    "error": {
        "code": "notFound",
        "message": "Goals organization not found",
        "innerError": {
            "code": "goalsOrganizationIdNotFound",
            "date": "String (timestamp)",
            "request-id": "String",
            "client-request-id": "String"
        }
    }
}
```

### Example 4: Invalid goalsOrganizationId is passed

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/beta/employeeExperience/goals/exportJobs
Content-Type: application/json

{
  "goalsOrganizationId": "String",
  "explorerViewId": "String"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new GoalsExportJob
{
	GoalsOrganizationId = "String",
	ExplorerViewId = "String",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.Goals.ExportJobs.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewGoalsExportJob()
goalsOrganizationId := "String"
requestBody.SetGoalsOrganizationId(&goalsOrganizationId) 
explorerViewId := "String"
requestBody.SetExplorerViewId(&explorerViewId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
exportJobs, err := graphClient.EmployeeExperience().Goals().ExportJobs().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GoalsExportJob goalsExportJob = new GoalsExportJob();
goalsExportJob.setGoalsOrganizationId("String");
goalsExportJob.setExplorerViewId("String");
GoalsExportJob result = graphClient.employeeExperience().goals().exportJobs().post(goalsExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const goalsExportJob = {
  goalsOrganizationId: 'String',
  explorerViewId: 'String'
};

await client.api('/employeeExperience/goals/exportJobs')
	.version('beta')
	.post(goalsExportJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\GoalsExportJob;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GoalsExportJob();
$requestBody->setGoalsOrganizationId('String');
$requestBody->setExplorerViewId('String');

$result = $graphServiceClient->employeeExperience()->goals()->exportJobs()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.goals_export_job import GoalsExportJob
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GoalsExportJob(
	goals_organization_id = "String",
	explorer_view_id = "String",
)

result = await graph_client.employee_experience.goals.export_jobs.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 400 Bad Request 
Content-type: application/json

{
    "error": {
        "code": "badRequest",
        "message": "'GoalsOrganizationId' must be specified in 'Export Job', and it should be a valid GUID.",
        "innerError": {
            "code": "invalidGoalsOrganizationId",
            "date": "String (timestamp)",
            "request-id": "String",
            "client-request-id": "String"
        }
    }
}
```
