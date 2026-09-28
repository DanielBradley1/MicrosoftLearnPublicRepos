<!-- Source: https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentrequest-resume?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# accessPackageAssignmentRequest: resume

Namespace: microsoft.graph

Resume a user's access package request after waiting for a callback from a custom extension.

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), when an access package policy has been enabled to call out a custom extension and the request processing is waiting for the callback from the customer, the customer can initiate a resume action. It's performed on an [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) object whose **requestStatus** is in a `WaitingForCallback` state.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.ReadWrite.All | Not available. |

Tip

For delegated access using work or school accounts, the signed-in user must be assigned an administrator role with supported role permissions through one of the following options:

- A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) where the least privileged roles are:

  - *Access package assignment manager*. **This is the least privileged option**
  - *Access package manager*
  - Catalog owner

- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Access package assignment manager* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
POST /identityGovernance/entitlementManagement/assignmentRequests/{accessPackageAssignmentRequestId}/resume
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| source | String | Source from where customer is trying to resume the request, which can be stored in service and will be helpful for auditing. |
| type | String | Indicate at which stage the custom callout extension was executed. The possible values are: `microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated`, `microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestApproved`, `microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestGranted`, `microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestRemoved` |
| data | [accessPackageAssignmentRequestCallbackData](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcallbackdata?view=graph-rest-1.0) | Contains information about the instance of the callout that was made to the customer endpoint. |

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Example 1: Resume an access package assignment request

#### Request

The following example shows a request of a call to resume an access package assignment request that's waiting for a callback.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentRequests/0e60f18c-b2a0-4887-9da8-da2e30a39d99/resume
Content-Type: application/json

{
  "source": "Contoso.SodCheckProcess",
  "type": "microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated",
  "data": {
    "@odata.type": "microsoft.graph.accessPackageAssignmentRequestCallbackData",
    "stage": "assignmentRequestCreated",
    "customExtensionStageInstanceId": "957d0c50-466b-4840-bb5b-c92cea7141ff",
    "customExtensionStageInstanceDetail": "This user is all verified"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.EntitlementManagement.AssignmentRequests.Item.Resume;
using Microsoft.Graph.Models;

var requestBody = new ResumePostRequestBody
{
	Source = "Contoso.SodCheckProcess",
	Type = "microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated",
	Data = new AccessPackageAssignmentRequestCallbackData
	{
		OdataType = "microsoft.graph.accessPackageAssignmentRequestCallbackData",
		Stage = AccessPackageCustomExtensionStage.AssignmentRequestCreated,
		CustomExtensionStageInstanceId = "957d0c50-466b-4840-bb5b-c92cea7141ff",
		CustomExtensionStageInstanceDetail = "This user is all verified",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.EntitlementManagement.AssignmentRequests["{accessPackageAssignmentRequest-id}"].Resume.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphidentitygovernance.NewResumePostRequestBody()
source := "Contoso.SodCheckProcess"
requestBody.SetSource(&source) 
type := "microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated"
requestBody.SetType(&type) 
data := graphmodels.NewAccessPackageAssignmentRequestCallbackData()
stage := graphmodels.ASSIGNMENTREQUESTCREATED_ACCESSPACKAGECUSTOMEXTENSIONSTAGE 
data.SetStage(&stage) 
customExtensionStageInstanceId := "957d0c50-466b-4840-bb5b-c92cea7141ff"
data.SetCustomExtensionStageInstanceId(&customExtensionStageInstanceId) 
customExtensionStageInstanceDetail := "This user is all verified"
data.SetCustomExtensionStageInstanceDetail(&customExtensionStageInstanceDetail) 
requestBody.SetData(data)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityGovernance().EntitlementManagement().AssignmentRequests().ByAccessPackageAssignmentRequestId("accessPackageAssignmentRequest-id").Resume().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.entitlementmanagement.assignmentrequests.item.resume.ResumePostRequestBody resumePostRequestBody = new com.microsoft.graph.identitygovernance.entitlementmanagement.assignmentrequests.item.resume.ResumePostRequestBody();
resumePostRequestBody.setSource("Contoso.SodCheckProcess");
resumePostRequestBody.setType("microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated");
AccessPackageAssignmentRequestCallbackData data = new AccessPackageAssignmentRequestCallbackData();
data.setOdataType("microsoft.graph.accessPackageAssignmentRequestCallbackData");
data.setStage(AccessPackageCustomExtensionStage.AssignmentRequestCreated);
data.setCustomExtensionStageInstanceId("957d0c50-466b-4840-bb5b-c92cea7141ff");
data.setCustomExtensionStageInstanceDetail("This user is all verified");
resumePostRequestBody.setData(data);
graphClient.identityGovernance().entitlementManagement().assignmentRequests().byAccessPackageAssignmentRequestId("{accessPackageAssignmentRequest-id}").resume().post(resumePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const resume = {
  source: 'Contoso.SodCheckProcess',
  type: 'microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated',
  data: {
    '@odata.type': 'microsoft.graph.accessPackageAssignmentRequestCallbackData',
    stage: 'assignmentRequestCreated',
    customExtensionStageInstanceId: '957d0c50-466b-4840-bb5b-c92cea7141ff',
    customExtensionStageInstanceDetail: 'This user is all verified'
  }
};

await client.api('/identityGovernance/entitlementManagement/assignmentRequests/0e60f18c-b2a0-4887-9da8-da2e30a39d99/resume')
	.post(resume);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\EntitlementManagement\AssignmentRequests\Item\Resume\ResumePostRequestBody;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequestCallbackData;
use Microsoft\Graph\Generated\Models\AccessPackageCustomExtensionStage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ResumePostRequestBody();
$requestBody->setSource('Contoso.SodCheckProcess');
$requestBody->setType('microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated');
$data = new AccessPackageAssignmentRequestCallbackData();
$data->setOdataType('microsoft.graph.accessPackageAssignmentRequestCallbackData');
$data->setStage(new AccessPackageCustomExtensionStage('assignmentRequestCreated'));
$data->setCustomExtensionStageInstanceId('957d0c50-466b-4840-bb5b-c92cea7141ff');
$data->setCustomExtensionStageInstanceDetail('This user is all verified');
$requestBody->setData($data);

$graphServiceClient->identityGovernance()->entitlementManagement()->assignmentRequests()->byAccessPackageAssignmentRequestId('accessPackageAssignmentRequest-id')->resume()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	source = "Contoso.SodCheckProcess"
	type = "microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated"
	data = @{
		"@odata.type" = "microsoft.graph.accessPackageAssignmentRequestCallbackData"
		stage = "assignmentRequestCreated"
		customExtensionStageInstanceId = "957d0c50-466b-4840-bb5b-c92cea7141ff"
		customExtensionStageInstanceDetail = "This user is all verified"
	}
}

Resume-MgEntitlementManagementAssignmentRequest -AccessPackageAssignmentRequestId $accessPackageAssignmentRequestId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.entitlementmanagement.assignmentrequests.item.resume.resume_post_request_body import ResumePostRequestBody
from msgraph.generated.models.access_package_assignment_request_callback_data import AccessPackageAssignmentRequestCallbackData
from msgraph.generated.models.access_package_custom_extension_stage import AccessPackageCustomExtensionStage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ResumePostRequestBody(
	source = "Contoso.SodCheckProcess",
	type = "microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated",
	data = AccessPackageAssignmentRequestCallbackData(
		odata_type = "microsoft.graph.accessPackageAssignmentRequestCallbackData",
		stage = AccessPackageCustomExtensionStage.AssignmentRequestCreated,
		custom_extension_stage_instance_id = "957d0c50-466b-4840-bb5b-c92cea7141ff",
		custom_extension_stage_instance_detail = "This user is all verified",
	),
)

await graph_client.identity_governance.entitlement_management.assignment_requests.by_access_package_assignment_request_id('accessPackageAssignmentRequest-id').resume.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Resume and deny an access package assignment request

#### Request

The following example shows a request to resume the processing of an access package assignment request by denying the request that's waiting for a callback. A request cannot be denied at the `assignmentRequestCreated` stage of the callout.

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentRequests/9e60f18c-b2a0-4887-9da8-da2e30a39d99/resume
Content-Type: application/json

{
  "source": "Contoso.SodCheckProcess",
  "type": "microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated",
  "data": {
    "@odata.type": "microsoft.graph.accessPackageAssignmentRequestCallbackData",
    "stage": "AssignmentRequestCreated",
    "customExtensionStageInstanceId": "857d0c50-466b-4840-bb5b-c92cea7141ff",
    "state": "denied",
    "customExtensionStageInstanceDetail": "Potential risk user based on the SOD check"
  }
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 3: Resume an access package assignment request from a custom extension

#### Request

The following example shows a request of a call to resume an access package assignment request that's waiting for a callback from a custom extension to determine the approver of the access package assignment.

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackageAssignmentRequests/0e60f18c-b2a0-4887-9da8-da2e30a39d99/resume
Content-Type: application/json

{
  "source": "Contoso.CustoEXT",
  "type": "microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated",
  "data": {
    "@odata.type": "microsoft.graph.microsoft.graph.assignmentRequestApprovalStageCallbackData",
    "approvalStage": {
      "durationBeforeAutomaticDenial": "P2D",
      "escalationApprovers": [],
      "fallbackEscalationApprovers": [],
      "fallbackPrimaryApprovers": [],
      "isApproverJustificationRequired": false,
      "isEscalationEnabled": false,
      "primaryApprovers": [
        {
          "@@odata.type": "#microsoft.graph.singleUser",
          "description": "Primary approver of access package assignment.",
          "id": "",
          "isBackup": false
        }
      ]
    },
    "customExtensionStageInstanceDetail": "A approval stage from Logic Apps",
    "customExtensionStageInstanceId": "@{triggerBody()?['CustomExtensionStageInstanceId']}",
    "stage": "assignmentRequestDeterminingApprovalRequirements"
  },
  "source": "LogicApps",
  "type": "microsoft.graph.accessPackageCustomExtensionStage.assignmentRequestCreated"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
