<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-post-tasks?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-03 -->

# Create case task

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a [task](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta) for a [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CaseManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CaseManagement.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This API supports the following built-in roles:

- Global Reader
- Security Reader
- Security Operator
- Security Administrator

## HTTP request

```http
POST /security/caseManagement/cases/{caseId}/tasks
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.security.caseManagement.task](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta) object.

You can specify the following properties when creating a **task**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the resource. Required. |
| status | [microsoft.graph.security.caseManagement.taskStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta#taskstatus-values) | The lifecycle status of the resource. Required. |
| description | String | The description of the resource. Optional. |
| assignedTo | String | The user assigned to the resource. Optional. |
| closingNotes | String | Notes recorded when the resource is completed or closed. Optional. |
| dueDateTime | DateTimeOffset | The target completion date and time. Optional. |
| priority | [microsoft.graph.security.caseManagement.caseTaskPriority](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta#casetaskpriority-values) | The priority assigned to the resource. Required. |
| category | [microsoft.graph.security.caseManagement.caseTaskCategory](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta#casetaskcategory-values) | The functional category of the task. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.caseManagement.task](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/security/caseManagement/cases/{caseId}/tasks
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.caseManagement.task",
  "displayName": "Validate affected devices",
  "status": "new",
  "description": "Review affected devices and collect evidence",
  "assignedTo": "user@contoso.com",
  "closingNotes": "Investigation completed and documented",
  "dueDateTime": "2026-06-29T17:54:43Z",
  "priority": "high",
  "category": "investigate"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Security.CaseManagement;

var requestBody = new TaskObject
{
	OdataType = "#microsoft.graph.security.caseManagement.task",
	DisplayName = "Validate affected devices",
	Status = TaskStatus.New,
	Description = "Review affected devices and collect evidence",
	AssignedTo = "user@contoso.com",
	ClosingNotes = "Investigation completed and documented",
	DueDateTime = DateTimeOffset.Parse("2026-06-29T17:54:43Z"),
	Priority = CaseTaskPriority.High,
	Category = CaseTaskCategory.Investigate,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.CaseManagement.Cases["{case-id}"].Tasks.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodelssecuritycasemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/models/security/casemanagement"
	  //other-imports
)

requestBody := graphmodelssecuritycasemanagement.NewTask()
displayName := "Validate affected devices"
requestBody.SetDisplayName(&displayName) 
status := graphmodels.NEW_TASKSTATUS 
requestBody.SetStatus(&status) 
description := "Review affected devices and collect evidence"
requestBody.SetDescription(&description) 
assignedTo := "user@contoso.com"
requestBody.SetAssignedTo(&assignedTo) 
closingNotes := "Investigation completed and documented"
requestBody.SetClosingNotes(&closingNotes) 
dueDateTime , err := time.Parse(time.RFC3339, "2026-06-29T17:54:43Z")
requestBody.SetDueDateTime(&dueDateTime) 
priority := graphmodels.HIGH_CASETASKPRIORITY 
requestBody.SetPriority(&priority) 
category := graphmodels.INVESTIGATE_CASETASKCATEGORY 
requestBody.SetCategory(&category) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tasks, err := graphClient.Security().CaseManagement().Cases().ByCaseId("case-id").Tasks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.security.casemanagement.Task task = new com.microsoft.graph.beta.models.security.casemanagement.Task();
task.setOdataType("#microsoft.graph.security.caseManagement.task");
task.setDisplayName("Validate affected devices");
task.setStatus(com.microsoft.graph.beta.models.security.casemanagement.TaskStatus.New);
task.setDescription("Review affected devices and collect evidence");
task.setAssignedTo("user@contoso.com");
task.setClosingNotes("Investigation completed and documented");
OffsetDateTime dueDateTime = OffsetDateTime.parse("2026-06-29T17:54:43Z");
task.setDueDateTime(dueDateTime);
task.setPriority(com.microsoft.graph.beta.models.security.casemanagement.CaseTaskPriority.High);
task.setCategory(com.microsoft.graph.beta.models.security.casemanagement.CaseTaskCategory.Investigate);
com.microsoft.graph.models.security.casemanagement.Task result = graphClient.security().caseManagement().cases().byCaseId("{case-id}").tasks().post(task);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const task = {
  '@odata.type': '#microsoft.graph.security.caseManagement.task',
  displayName: 'Validate affected devices',
  status: 'new',
  description: 'Review affected devices and collect evidence',
  assignedTo: 'user@contoso.com',
  closingNotes: 'Investigation completed and documented',
  dueDateTime: '2026-06-29T17:54:43Z',
  priority: 'high',
  category: 'investigate'
};

await client.api('/security/caseManagement/cases/{caseId}/tasks')
	.version('beta')
	.post(task);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\Task;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\TaskStatus;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\CaseTaskPriority;
use Microsoft\Graph\Beta\Generated\Models\Security\CaseManagement\CaseTaskCategory;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Task();
$requestBody->setOdataType('#microsoft.graph.security.caseManagement.task');
$requestBody->setDisplayName('Validate affected devices');
$requestBody->setStatus(new TaskStatus('new'));
$requestBody->setDescription('Review affected devices and collect evidence');
$requestBody->setAssignedTo('user@contoso.com');
$requestBody->setClosingNotes('Investigation completed and documented');
$requestBody->setDueDateTime(new \DateTime('2026-06-29T17:54:43Z'));
$requestBody->setPriority(new CaseTaskPriority('high'));
$requestBody->setCategory(new CaseTaskCategory('investigate'));

$result = $graphServiceClient->security()->caseManagement()->cases()->byCaseId('case-id')->tasks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.caseManagement.task"
	displayName = "Validate affected devices"
	status = "new"
	description = "Review affected devices and collect evidence"
	assignedTo = "user@contoso.com"
	closingNotes = "Investigation completed and documented"
	dueDateTime = [System.DateTime]::Parse("2026-06-29T17:54:43Z")
	priority = "high"
	category = "investigate"
}

New-MgBetaSecurityCaseManagementCaseTask -CaseId $caseId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.security.case_management.task import Task
from msgraph_beta.generated.models.task_status import TaskStatus
from msgraph_beta.generated.models.case_task_priority import CaseTaskPriority
from msgraph_beta.generated.models.case_task_category import CaseTaskCategory
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Task(
	odata_type = "#microsoft.graph.security.caseManagement.task",
	display_name = "Validate affected devices",
	status = TaskStatus.New,
	description = "Review affected devices and collect evidence",
	assigned_to = "user@contoso.com",
	closing_notes = "Investigation completed and documented",
	due_date_time = "2026-06-29T17:54:43Z",
	priority = CaseTaskPriority.High,
	category = CaseTaskCategory.Investigate,
)

result = await graph_client.security.case_management.cases.by_case_id('case-id').tasks.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.caseManagement.task",
  "id": "1601f158-fa4e-ceaa-7789-685b5e916d72",
  "createdDateTime": "2026-05-20T11:12:28Z",
  "createdBy": "user@contoso.com",
  "lastModifiedDateTime": "2026-05-20T11:18:45Z",
  "lastModifiedBy": "user@contoso.com",
  "displayName": "Validate affected devices",
  "status": "new",
  "description": "Review affected devices and collect evidence",
  "assignedTo": "user@contoso.com",
  "closingNotes": "Investigation completed and documented",
  "dueDateTime": "2026-06-29T17:54:43Z",
  "priority": "high",
  "category": "investigate"
}
```
