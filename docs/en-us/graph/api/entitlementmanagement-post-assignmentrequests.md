<!-- Source: https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-assignmentrequests?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Create accessPackageAssignmentRequest

Namespace: microsoft.graph

In [Microsoft Entra Entitlement Management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), create a new [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) object. This operation is used to assign a user to an access package, update the assignment, or to remove an access package assignment.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementMgmt-SubjectAccess.ReadWrite | EntitlementManagement.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.ReadWrite.All | Not available. |

Tip

The role and permission required for delegated access using work or school accounts depend on the `requestType` of the request being submitted.

**End-user requests** — `userAdd`, `userUpdate`, `userRemove`, and `approverRemove`:

- The signed-in user **doesn't need** an administrator role.
- The least privileged permission is `EntitlementMgmt-SubjectAccess.ReadWrite`.
- Holding the permission isn't sufficient on its own — whether an end-user can submit a request is also governed by the corresponding accessPackageAssignmentPolicy, which controls who can be assigned to an access package and who can request it \(`allowedTargetScope`, `specificAllowedTargets`, and `requestorSettings`\).

**Administrator requests** — `adminAdd`, `adminUpdate`, and `adminRemove`:

- The least privileged permission is `EntitlementManagement.ReadWrite.All`.
- The signed-in user **must** be assigned a supported administrator role. Supported roles, from least to most privileged:

  - A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate):

    - *Access package assignment manager*. **This is the least privileged option**
    - *Access package manager*
    - *Catalog owner*

  - A more privileged [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json):

    - *Identity Governance Administrator*

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Access package assignment manager* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
POST /identityGovernance/entitlementManagement/assignmentRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) object.

For an administrator to request to create an assignment for a user, the value of the **requestType** property is `adminAdd`, and the **assignment** property contains the **targetId** with the ID of the user being assigned, the **assignmentPolicyId** property identifying the [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0), and the **accessPackageId** property identifying the [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0).

For an administrator to request to update an assignment \(for example to extend the assignment or update answers to questions\), the value of the **requestType** property is `adminUpdate`, and the **assignment** property contains the **id** property identifying the [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) being updated.

For an administrator to request to remove an assignment, the value of the **requestType** property is `adminRemove`, and the **assignment** property contains the **id** property identifying the [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) being removed.

For a non-administrator user to request to create their own assignment for either a first assignment or to renew an assignment, the value of the **requestType** property is `userAdd`. The **assignment** property contains an object with the `targetId` with the `id` of the user. The **assignmentPolicyId** property identifies the [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0). The **accessPackageId** property identifies the [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0). The user making the request must already exist in the directory.

For a non-administrator user to request to update their own assignment, the value of the **requestType** property is `userUpdate`. The **assignment** property contains the **ID** property identifying the [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) being updated. The **schedule** property contains the updated schedule.

## Response

If successful, this method returns a 200-series response code and a new [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) object in the response body.

If this is an `adminAdd` or `userAdd` request, then after any approval checks an [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) and, if needed, an [accessPackageSubject](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesubject?view=graph-rest-1.0) are also created. You can locate those using the query parameters when [listing accessPackageAssignments](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-assignments?view=graph-rest-1.0).

## Examples

### Example 1: Admin requests a direct assignment for a user already in the directory

#### Request

The following example shows a request for a direct assignment, in which the administrator requests the creation of an assignment for a user. Because the [accessPackageSubject](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesubject?view=graph-rest-1.0) might not yet exist, the value of the **targetID** is the object ID of the user being assigned, the value of the **accessPackageId** is the desired access package for that user, and the value of **assignmentPolicyId** is a direct assignment policy in that access package.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentRequests
Content-type: application/json

{
  "requestType": "adminAdd",
  "assignment":{
     "targetId":"46184453-e63b-4f20-86c2-c557ed5d5df9",
     "assignmentPolicyId":"2264bf65-76ba-417b-a27d-54d291f0cbc8",
     "accessPackageId":"a914b616-e04e-476b-aa37-91038f0b165b"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = AccessPackageRequestType.AdminAdd,
	Assignment = new AccessPackageAssignment
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"targetId" , "46184453-e63b-4f20-86c2-c557ed5d5df9"
			},
			{
				"assignmentPolicyId" , "2264bf65-76ba-417b-a27d-54d291f0cbc8"
			},
			{
				"accessPackageId" , "a914b616-e04e-476b-aa37-91038f0b165b"
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := graphmodels.ADMINADD_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
assignment := graphmodels.NewAccessPackageAssignment()
additionalData := map[string]interface{}{
	"targetId" : "46184453-e63b-4f20-86c2-c557ed5d5df9", 
	"assignmentPolicyId" : "2264bf65-76ba-417b-a27d-54d291f0cbc8", 
	"accessPackageId" : "a914b616-e04e-476b-aa37-91038f0b165b", 
}
assignment.SetAdditionalData(additionalData)
requestBody.SetAssignment(assignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType(AccessPackageRequestType.AdminAdd);
AccessPackageAssignment assignment = new AccessPackageAssignment();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("targetId", "46184453-e63b-4f20-86c2-c557ed5d5df9");
additionalData.put("assignmentPolicyId", "2264bf65-76ba-417b-a27d-54d291f0cbc8");
additionalData.put("accessPackageId", "a914b616-e04e-476b-aa37-91038f0b165b");
assignment.setAdditionalData(additionalData);
accessPackageAssignmentRequest.setAssignment(assignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().assignmentRequests().post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
  requestType: 'adminAdd',
  assignment: {
     targetId: '46184453-e63b-4f20-86c2-c557ed5d5df9',
     assignmentPolicyId: '2264bf65-76ba-417b-a27d-54d291f0cbc8',
     accessPackageId: 'a914b616-e04e-476b-aa37-91038f0b165b'
  }
};

await client.api('/identityGovernance/entitlementManagement/assignmentRequests')
	.post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType(new AccessPackageRequestType('adminAdd'));
$assignment = new AccessPackageAssignment();
$additionalData = [
	'targetId' => '46184453-e63b-4f20-86c2-c557ed5d5df9',
	'assignmentPolicyId' => '2264bf65-76ba-417b-a27d-54d291f0cbc8',
	'accessPackageId' => 'a914b616-e04e-476b-aa37-91038f0b165b',
];
$assignment->setAdditionalData($additionalData);
$requestBody->setAssignment($assignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "adminAdd"
	assignment = @{
		targetId = "46184453-e63b-4f20-86c2-c557ed5d5df9"
		assignmentPolicyId = "2264bf65-76ba-417b-a27d-54d291f0cbc8"
		accessPackageId = "a914b616-e04e-476b-aa37-91038f0b165b"
	}
}

New-MgEntitlementManagementAssignmentRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_assignment import AccessPackageAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = AccessPackageRequestType.AdminAdd,
	assignment = AccessPackageAssignment(
		additional_data = {
				"target_id" : "46184453-e63b-4f20-86c2-c557ed5d5df9",
				"assignment_policy_id" : "2264bf65-76ba-417b-a27d-54d291f0cbc8",
				"access_package_id" : "a914b616-e04e-476b-aa37-91038f0b165b",
		}
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "46184453-e63b-4f20-86c2-c557ed5d5df9",
  "requestType": "adminAdd",
  "requestState": "Submitted",
  "requestStatus": "Accepted"
}
```

### Example 2: Remove an assignment

To remove assignments, create a new **accessPackageAssignmentRequest** object with the following settings:

- The value of the **requestType** property set to `adminRemove`.
- In the **assignment** property, include an object with the identifier of the **accessPackageAssignment** object to delete.

#### Request

The following example shows how to remove an assignment.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentRequests
Content-type: application/json

{
    "requestType": "adminRemove",
    "assignment":{
     "id": "a6bb6942-3ae1-4259-9908-0133aaee9377"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = AccessPackageRequestType.AdminRemove,
	Assignment = new AccessPackageAssignment
	{
		Id = "a6bb6942-3ae1-4259-9908-0133aaee9377",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := graphmodels.ADMINREMOVE_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
assignment := graphmodels.NewAccessPackageAssignment()
id := "a6bb6942-3ae1-4259-9908-0133aaee9377"
assignment.SetId(&id) 
requestBody.SetAssignment(assignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType(AccessPackageRequestType.AdminRemove);
AccessPackageAssignment assignment = new AccessPackageAssignment();
assignment.setId("a6bb6942-3ae1-4259-9908-0133aaee9377");
accessPackageAssignmentRequest.setAssignment(assignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().assignmentRequests().post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
    requestType: 'adminRemove',
    assignment: {
     id: 'a6bb6942-3ae1-4259-9908-0133aaee9377'
    }
};

await client.api('/identityGovernance/entitlementManagement/assignmentRequests')
	.post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType(new AccessPackageRequestType('adminRemove'));
$assignment = new AccessPackageAssignment();
$assignment->setId('a6bb6942-3ae1-4259-9908-0133aaee9377');
$requestBody->setAssignment($assignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "adminRemove"
	assignment = @{
		id = "a6bb6942-3ae1-4259-9908-0133aaee9377"
	}
}

New-MgEntitlementManagementAssignmentRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_assignment import AccessPackageAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = AccessPackageRequestType.AdminRemove,
	assignment = AccessPackageAssignment(
		id = "a6bb6942-3ae1-4259-9908-0133aaee9377",
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties are returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#accessPackageAssignmentRequests/$entity",
    "id": "78eaee8c-e6cf-48c9-8f99-aae44c35e379",
    "requestType": "adminRemove",
    "requestState": "Submitted",
    "requestStatus": "Accepted"
}
```

### Example 3: Request an assignment by providing answers to questions

The following example shows how a user can request an access package assignment for themselves by answering questions required by the policy during the request process.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentRequests
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.accessPackageAssignmentRequest",
    "requestType": "userAdd",
    "answers": [
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "displayValue": "This is the answer to a multiple choice question",
            "value": "MultipleChoiceAnswerValue",
            "answeredQuestion": {
                "@odata.type": "#microsoft.graph.accessPackageMultipleChoiceQuestion",
                "id": "8fe745e7-80b2-490d-bd22-4e708c77288c"
            }
        },
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "This is my answer to a text input question.",
            "displayValue": "This is my answer.",
            "answeredQuestion": {
                "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
                "id": "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6"
            }
        }
    ],
    "assignment": {
        "accessPackageId": "977c7ff4-ef8f-4910-9d31-49048ddf3120"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	OdataType = "#microsoft.graph.accessPackageAssignmentRequest",
	RequestType = AccessPackageRequestType.UserAdd,
	Answers = new List<AccessPackageAnswer>
	{
		new AccessPackageAnswerString
		{
			OdataType = "#microsoft.graph.accessPackageAnswerString",
			DisplayValue = "This is the answer to a multiple choice question",
			Value = "MultipleChoiceAnswerValue",
			AnsweredQuestion = new AccessPackageMultipleChoiceQuestion
			{
				OdataType = "#microsoft.graph.accessPackageMultipleChoiceQuestion",
				Id = "8fe745e7-80b2-490d-bd22-4e708c77288c",
			},
		},
		new AccessPackageAnswerString
		{
			OdataType = "#microsoft.graph.accessPackageAnswerString",
			Value = "This is my answer to a text input question.",
			DisplayValue = "This is my answer.",
			AnsweredQuestion = new AccessPackageTextInputQuestion
			{
				OdataType = "#microsoft.graph.accessPackageTextInputQuestion",
				Id = "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6",
			},
		},
	},
	Assignment = new AccessPackageAssignment
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"accessPackageId" , "977c7ff4-ef8f-4910-9d31-49048ddf3120"
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := graphmodels.USERADD_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 


accessPackageAnswer := graphmodels.NewAccessPackageAnswerString()
displayValue := "This is the answer to a multiple choice question"
accessPackageAnswer.SetDisplayValue(&displayValue) 
value := "MultipleChoiceAnswerValue"
accessPackageAnswer.SetValue(&value) 
answeredQuestion := graphmodels.NewAccessPackageMultipleChoiceQuestion()
id := "8fe745e7-80b2-490d-bd22-4e708c77288c"
answeredQuestion.SetId(&id) 
accessPackageAnswer.SetAnsweredQuestion(answeredQuestion)
accessPackageAnswer1 := graphmodels.NewAccessPackageAnswerString()
value := "This is my answer to a text input question."
accessPackageAnswer1.SetValue(&value) 
displayValue := "This is my answer."
accessPackageAnswer1.SetDisplayValue(&displayValue) 
answeredQuestion := graphmodels.NewAccessPackageTextInputQuestion()
id := "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6"
answeredQuestion.SetId(&id) 
accessPackageAnswer1.SetAnsweredQuestion(answeredQuestion)

answers := []graphmodels.AccessPackageAnswerable {
	accessPackageAnswer,
	accessPackageAnswer1,
}
requestBody.SetAnswers(answers)
assignment := graphmodels.NewAccessPackageAssignment()
additionalData := map[string]interface{}{
	"accessPackageId" : "977c7ff4-ef8f-4910-9d31-49048ddf3120", 
}
assignment.SetAdditionalData(additionalData)
requestBody.SetAssignment(assignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setOdataType("#microsoft.graph.accessPackageAssignmentRequest");
accessPackageAssignmentRequest.setRequestType(AccessPackageRequestType.UserAdd);
LinkedList<AccessPackageAnswer> answers = new LinkedList<AccessPackageAnswer>();
AccessPackageAnswerString accessPackageAnswer = new AccessPackageAnswerString();
accessPackageAnswer.setOdataType("#microsoft.graph.accessPackageAnswerString");
accessPackageAnswer.setDisplayValue("This is the answer to a multiple choice question");
accessPackageAnswer.setValue("MultipleChoiceAnswerValue");
AccessPackageMultipleChoiceQuestion answeredQuestion = new AccessPackageMultipleChoiceQuestion();
answeredQuestion.setOdataType("#microsoft.graph.accessPackageMultipleChoiceQuestion");
answeredQuestion.setId("8fe745e7-80b2-490d-bd22-4e708c77288c");
accessPackageAnswer.setAnsweredQuestion(answeredQuestion);
answers.add(accessPackageAnswer);
AccessPackageAnswerString accessPackageAnswer1 = new AccessPackageAnswerString();
accessPackageAnswer1.setOdataType("#microsoft.graph.accessPackageAnswerString");
accessPackageAnswer1.setValue("This is my answer to a text input question.");
accessPackageAnswer1.setDisplayValue("This is my answer.");
AccessPackageTextInputQuestion answeredQuestion1 = new AccessPackageTextInputQuestion();
answeredQuestion1.setOdataType("#microsoft.graph.accessPackageTextInputQuestion");
answeredQuestion1.setId("7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6");
accessPackageAnswer1.setAnsweredQuestion(answeredQuestion1);
answers.add(accessPackageAnswer1);
accessPackageAssignmentRequest.setAnswers(answers);
AccessPackageAssignment assignment = new AccessPackageAssignment();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("accessPackageId", "977c7ff4-ef8f-4910-9d31-49048ddf3120");
assignment.setAdditionalData(additionalData);
accessPackageAssignmentRequest.setAssignment(assignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().assignmentRequests().post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
    '@odata.type': '#microsoft.graph.accessPackageAssignmentRequest',
    requestType: 'userAdd',
    answers: [
        {
            '@odata.type': '#microsoft.graph.accessPackageAnswerString',
            displayValue: 'This is the answer to a multiple choice question',
            value: 'MultipleChoiceAnswerValue',
            answeredQuestion: {
                '@odata.type': '#microsoft.graph.accessPackageMultipleChoiceQuestion',
                id: '8fe745e7-80b2-490d-bd22-4e708c77288c'
            }
        },
        {
            '@odata.type': '#microsoft.graph.accessPackageAnswerString',
            value: 'This is my answer to a text input question.',
            displayValue: 'This is my answer.',
            answeredQuestion: {
                '@odata.type': '#microsoft.graph.accessPackageTextInputQuestion',
                id: '7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6'
            }
        }
    ],
    assignment: {
        accessPackageId: '977c7ff4-ef8f-4910-9d31-49048ddf3120'
    }
};

await client.api('/identityGovernance/entitlementManagement/assignmentRequests')
	.post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageAnswer;
use Microsoft\Graph\Generated\Models\AccessPackageAnswerString;
use Microsoft\Graph\Generated\Models\AccessPackageMultipleChoiceQuestion;
use Microsoft\Graph\Generated\Models\AccessPackageTextInputQuestion;
use Microsoft\Graph\Generated\Models\AccessPackageAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setOdataType('#microsoft.graph.accessPackageAssignmentRequest');
$requestBody->setRequestType(new AccessPackageRequestType('userAdd'));
$answersAccessPackageAnswer1 = new AccessPackageAnswerString();
$answersAccessPackageAnswer1->setOdataType('#microsoft.graph.accessPackageAnswerString');
$answersAccessPackageAnswer1->setDisplayValue('This is the answer to a multiple choice question');
$answersAccessPackageAnswer1->setValue('MultipleChoiceAnswerValue');
$answersAccessPackageAnswer1AnsweredQuestion = new AccessPackageMultipleChoiceQuestion();
$answersAccessPackageAnswer1AnsweredQuestion->setOdataType('#microsoft.graph.accessPackageMultipleChoiceQuestion');
$answersAccessPackageAnswer1AnsweredQuestion->setId('8fe745e7-80b2-490d-bd22-4e708c77288c');
$answersAccessPackageAnswer1->setAnsweredQuestion($answersAccessPackageAnswer1AnsweredQuestion);
$answersArray []= $answersAccessPackageAnswer1;
$answersAccessPackageAnswer2 = new AccessPackageAnswerString();
$answersAccessPackageAnswer2->setOdataType('#microsoft.graph.accessPackageAnswerString');
$answersAccessPackageAnswer2->setValue('This is my answer to a text input question.');
$answersAccessPackageAnswer2->setDisplayValue('This is my answer.');
$answersAccessPackageAnswer2AnsweredQuestion = new AccessPackageTextInputQuestion();
$answersAccessPackageAnswer2AnsweredQuestion->setOdataType('#microsoft.graph.accessPackageTextInputQuestion');
$answersAccessPackageAnswer2AnsweredQuestion->setId('7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6');
$answersAccessPackageAnswer2->setAnsweredQuestion($answersAccessPackageAnswer2AnsweredQuestion);
$answersArray []= $answersAccessPackageAnswer2;
$requestBody->setAnswers($answersArray);

$assignment = new AccessPackageAssignment();
$additionalData = [
'accessPackageId' => '977c7ff4-ef8f-4910-9d31-49048ddf3120',
];
$assignment->setAdditionalData($additionalData);
$requestBody->setAssignment($assignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	"@odata.type" = "#microsoft.graph.accessPackageAssignmentRequest"
	requestType = "userAdd"
	answers = @(
		@{
			"@odata.type" = "#microsoft.graph.accessPackageAnswerString"
			displayValue = "This is the answer to a multiple choice question"
			value = "MultipleChoiceAnswerValue"
			answeredQuestion = @{
				"@odata.type" = "#microsoft.graph.accessPackageMultipleChoiceQuestion"
				id = "8fe745e7-80b2-490d-bd22-4e708c77288c"
			}
		}
		@{
			"@odata.type" = "#microsoft.graph.accessPackageAnswerString"
			value = "This is my answer to a text input question."
			displayValue = "This is my answer."
			answeredQuestion = @{
				"@odata.type" = "#microsoft.graph.accessPackageTextInputQuestion"
				id = "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6"
			}
		}
	)
	assignment = @{
		accessPackageId = "977c7ff4-ef8f-4910-9d31-49048ddf3120"
	}
}

New-MgEntitlementManagementAssignmentRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_answer import AccessPackageAnswer
from msgraph.generated.models.access_package_answer_string import AccessPackageAnswerString
from msgraph.generated.models.access_package_multiple_choice_question import AccessPackageMultipleChoiceQuestion
from msgraph.generated.models.access_package_text_input_question import AccessPackageTextInputQuestion
from msgraph.generated.models.access_package_assignment import AccessPackageAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	odata_type = "#microsoft.graph.accessPackageAssignmentRequest",
	request_type = AccessPackageRequestType.UserAdd,
	answers = [
		AccessPackageAnswerString(
			odata_type = "#microsoft.graph.accessPackageAnswerString",
			display_value = "This is the answer to a multiple choice question",
			value = "MultipleChoiceAnswerValue",
			answered_question = AccessPackageMultipleChoiceQuestion(
				odata_type = "#microsoft.graph.accessPackageMultipleChoiceQuestion",
				id = "8fe745e7-80b2-490d-bd22-4e708c77288c",
			),
		),
		AccessPackageAnswerString(
			odata_type = "#microsoft.graph.accessPackageAnswerString",
			value = "This is my answer to a text input question.",
			display_value = "This is my answer.",
			answered_question = AccessPackageTextInputQuestion(
				odata_type = "#microsoft.graph.accessPackageTextInputQuestion",
				id = "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6",
			),
		),
	],
	assignment = AccessPackageAssignment(
		additional_data = {
				"access_package_id" : "977c7ff4-ef8f-4910-9d31-49048ddf3120",
		}
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties are returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#accessPackageAssignmentRequests/$entity",
    "id": "7a6ab703-0780-4b37-8445-81f679b2d75c",
    "requestType": "userAdd",
    "state": "submitted",
    "status": "Accepted",
    "createdDateTime": null,
    "completedDateTime": null,
    "schedule": {
        "startDateTime": null,
        "recurrence": null,
        "expiration": {
            "endDateTime": null,
            "duration": null,
            "type": "notSpecified"
        }
    },
    "answers": [
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "MultipleChoiceAnswerValue",
            "answeredQuestion": {
                "@odata.type": "#microsoft.graph.accessPackageMultipleChoiceQuestion",
                "id": "8fe745e7-80b2-490d-bd22-4e708c77288c"   
            },
            "displayValue": "This is the answer to a multiple choice question"
        },
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "This is my answer to a text input question.",
            "answeredQuestion": {
                "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
                "id": "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6"
            },
            "displayValue": "This is my answer."
        }
    ]
}
```

### Example 4: Request a package and provide a justification

The following example shows how to request an access package and provide justification to the approver.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentRequests
Content-type: application/json

{
    "requestType": "UserAdd",
    "accessPackageAssignment": {
        "accessPackageId": "a914b616-e04e-476b-aa37-91038f0b165b"
    },
    "justification":"Need access to New Hire access package"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = AccessPackageRequestType.UserAdd,
	Justification = "Need access to New Hire access package",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"accessPackageAssignment" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"accessPackageId", new UntypedString("a914b616-e04e-476b-aa37-91038f0b165b")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := graphmodels.USERADD_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
justification := "Need access to New Hire access package"
requestBody.SetJustification(&justification) 
additionalData := map[string]interface{}{
accessPackageAssignment := graph.New()
accessPackageId := "a914b616-e04e-476b-aa37-91038f0b165b"
accessPackageAssignment.SetAccessPackageId(&accessPackageId) 
	requestBody.SetAccessPackageAssignment(accessPackageAssignment)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType(AccessPackageRequestType.UserAdd);
accessPackageAssignmentRequest.setJustification("Need access to New Hire access package");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 accessPackageAssignment = new ();
accessPackageAssignment.setAccessPackageId("a914b616-e04e-476b-aa37-91038f0b165b");
additionalData.put("accessPackageAssignment", accessPackageAssignment);
accessPackageAssignmentRequest.setAdditionalData(additionalData);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().assignmentRequests().post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
    requestType: 'UserAdd',
    accessPackageAssignment: {
        accessPackageId: 'a914b616-e04e-476b-aa37-91038f0b165b'
    },
    justification: 'Need access to New Hire access package'
};

await client.api('/identityGovernance/entitlementManagement/assignmentRequests')
	.post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType(new AccessPackageRequestType('userAdd'));
$requestBody->setJustification('Need access to New Hire access package');
$additionalData = [
	'accessPackageAssignment' => [
		'accessPackageId' => 'a914b616-e04e-476b-aa37-91038f0b165b',
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "UserAdd"
	accessPackageAssignment = @{
		accessPackageId = "a914b616-e04e-476b-aa37-91038f0b165b"
	}
	justification = "Need access to New Hire access package"
}

New-MgEntitlementManagementAssignmentRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = AccessPackageRequestType.UserAdd,
	justification = "Need access to New Hire access package",
	additional_data = {
			"access_package_assignment" : {
					"access_package_id" : "a914b616-e04e-476b-aa37-91038f0b165b",
			},
	}
)

result = await graph_client.identity_governance.entitlement_management.assignment_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties are returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/assignmentRequests/$entity",
    "id": "9c1e258d-7723-43b1-ae21-e6eeeb324fe5",
    "requestType": "UserAdd",
    "requestState": "Submitted",
    "requestStatus": "Accepted",
    "createdDateTime": null,
    "completedDate": null,
    "justification": "Need access to New Hire access package",
    "isValidationOnly": false,
    "schedule": {
        "startDateTime": null,
        "recurrence": null,
        "expiration": {
            "endDateTime": null,
            "duration": null,
            "type": "notSpecified"
        }
    },
    "answers": [],
    "verifiedCredentialsData": []
}
```

### Example 5: Admin requests a direct assignment for a user not yet in the directory

#### Request

The following example shows a request for a direct assignment, in which the administrator requests the creation of an assignment for a user who doesn't exist in the directory. The value of the **accessPackageId** is the desired access package for that user, and the value of **assignmentPolicyId** is a direct assignment policy in that access package.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentRequests
Content-type: application/json

{
  "requestType": "AdminAdd",
  "assignment":{
     "target": {
        "email": "user@contoso.com"
     },
     "assignmentPolicy":{
        "id": "11114b50-0a08-4f96-83e9-1d714aa2cd79"
     },
     "accessPackage": {
        "id": "11115C72-0612-4C43-A044-FC0A4E71A4C5"
     }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = AccessPackageRequestType.AdminAdd,
	Assignment = new AccessPackageAssignment
	{
		Target = new AccessPackageSubject
		{
			Email = "user@contoso.com",
		},
		AssignmentPolicy = new AccessPackageAssignmentPolicy
		{
			Id = "11114b50-0a08-4f96-83e9-1d714aa2cd79",
		},
		AccessPackage = new AccessPackage
		{
			Id = "11115C72-0612-4C43-A044-FC0A4E71A4C5",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := graphmodels.ADMINADD_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
assignment := graphmodels.NewAccessPackageAssignment()
target := graphmodels.NewAccessPackageSubject()
email := "user@contoso.com"
target.SetEmail(&email) 
assignment.SetTarget(target)
assignmentPolicy := graphmodels.NewAccessPackageAssignmentPolicy()
id := "11114b50-0a08-4f96-83e9-1d714aa2cd79"
assignmentPolicy.SetId(&id) 
assignment.SetAssignmentPolicy(assignmentPolicy)
accessPackage := graphmodels.NewAccessPackage()
id := "11115C72-0612-4C43-A044-FC0A4E71A4C5"
accessPackage.SetId(&id) 
assignment.SetAccessPackage(accessPackage)
requestBody.SetAssignment(assignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType(AccessPackageRequestType.AdminAdd);
AccessPackageAssignment assignment = new AccessPackageAssignment();
AccessPackageSubject target = new AccessPackageSubject();
target.setEmail("user@contoso.com");
assignment.setTarget(target);
AccessPackageAssignmentPolicy assignmentPolicy = new AccessPackageAssignmentPolicy();
assignmentPolicy.setId("11114b50-0a08-4f96-83e9-1d714aa2cd79");
assignment.setAssignmentPolicy(assignmentPolicy);
AccessPackage accessPackage = new AccessPackage();
accessPackage.setId("11115C72-0612-4C43-A044-FC0A4E71A4C5");
assignment.setAccessPackage(accessPackage);
accessPackageAssignmentRequest.setAssignment(assignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().assignmentRequests().post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
  requestType: 'AdminAdd',
  assignment: {
     target: {
        email: 'user@contoso.com'
     },
     assignmentPolicy: {
        id: '11114b50-0a08-4f96-83e9-1d714aa2cd79'
     },
     accessPackage: {
        id: '11115C72-0612-4C43-A044-FC0A4E71A4C5'
     }
  }
};

await client.api('/identityGovernance/entitlementManagement/assignmentRequests')
	.post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageAssignment;
use Microsoft\Graph\Generated\Models\AccessPackageSubject;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Generated\Models\AccessPackage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType(new AccessPackageRequestType('adminAdd'));
$assignment = new AccessPackageAssignment();
$assignmentTarget = new AccessPackageSubject();
$assignmentTarget->setEmail('user@contoso.com');
$assignment->setTarget($assignmentTarget);
$assignmentAssignmentPolicy = new AccessPackageAssignmentPolicy();
$assignmentAssignmentPolicy->setId('11114b50-0a08-4f96-83e9-1d714aa2cd79');
$assignment->setAssignmentPolicy($assignmentAssignmentPolicy);
$assignmentAccessPackage = new AccessPackage();
$assignmentAccessPackage->setId('11115C72-0612-4C43-A044-FC0A4E71A4C5');
$assignment->setAccessPackage($assignmentAccessPackage);
$requestBody->setAssignment($assignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "AdminAdd"
	assignment = @{
		target = @{
			email = "user@contoso.com"
		}
		assignmentPolicy = @{
			id = "11114b50-0a08-4f96-83e9-1d714aa2cd79"
		}
		accessPackage = @{
			id = "11115C72-0612-4C43-A044-FC0A4E71A4C5"
		}
	}
}

New-MgEntitlementManagementAssignmentRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_assignment import AccessPackageAssignment
from msgraph.generated.models.access_package_subject import AccessPackageSubject
from msgraph.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph.generated.models.access_package import AccessPackage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = AccessPackageRequestType.AdminAdd,
	assignment = AccessPackageAssignment(
		target = AccessPackageSubject(
			email = "user@contoso.com",
		),
		assignment_policy = AccessPackageAssignmentPolicy(
			id = "11114b50-0a08-4f96-83e9-1d714aa2cd79",
		),
		access_package = AccessPackage(
			id = "11115C72-0612-4C43-A044-FC0A4E71A4C5",
		),
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/assignmentRequests/$entity",
    "id": "cb32aef9-2976-496d-9804-eb432fd894a7",
    "requestType": "AdminAdd",
    "requestState": "Submitted",
    "requestStatus": "Accepted",
    "createdDateTime": null,
    "completedDate": null,
    "justification": null,
    "isValidationOnly": false,
    "schedule": {
        "startDateTime": null,
        "recurrence": null,
        "expiration": {
            "endDateTime": null,
            "duration": null,
            "type": "notSpecified"
        }
    },
    "answers": [],
    "verifiedCredentialsData": [],
    "customExtensionHandlerInstances": [],
    "customExtensionCalloutInstances": []
}
```

### Example 6: Request an update to answers for an assignment

The following example shows how an admin can request updates to an assignment to edit their responses to questions that were answered during the request for the assignment.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentRequests
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.accessPackageAssignmentRequest",
    "requestType": "adminUpdate",
    "answers": [
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "UpdatedAnswerValue",
            "answeredQuestion": {
                "@odata.type": "#microsoft.graph.accessPackageMultipleChoiceQuestion",
                "id": "8fe745e7-80b2-490d-bd22-4e708c77288c"
            }
        },
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "My updated answer.",
            "displayValue": "This is my updated answer to the question.",
            "answeredQuestion": {
                "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
                "id": "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6"
            }
        }
    ],
    "assignment": {
        "id": "44c741c1-2cf4-40db-83b6-e0112f8e5a83"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	OdataType = "#microsoft.graph.accessPackageAssignmentRequest",
	RequestType = AccessPackageRequestType.AdminUpdate,
	Answers = new List<AccessPackageAnswer>
	{
		new AccessPackageAnswerString
		{
			OdataType = "#microsoft.graph.accessPackageAnswerString",
			Value = "UpdatedAnswerValue",
			AnsweredQuestion = new AccessPackageMultipleChoiceQuestion
			{
				OdataType = "#microsoft.graph.accessPackageMultipleChoiceQuestion",
				Id = "8fe745e7-80b2-490d-bd22-4e708c77288c",
			},
		},
		new AccessPackageAnswerString
		{
			OdataType = "#microsoft.graph.accessPackageAnswerString",
			Value = "My updated answer.",
			DisplayValue = "This is my updated answer to the question.",
			AnsweredQuestion = new AccessPackageTextInputQuestion
			{
				OdataType = "#microsoft.graph.accessPackageTextInputQuestion",
				Id = "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6",
			},
		},
	},
	Assignment = new AccessPackageAssignment
	{
		Id = "44c741c1-2cf4-40db-83b6-e0112f8e5a83",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := graphmodels.ADMINUPDATE_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 


accessPackageAnswer := graphmodels.NewAccessPackageAnswerString()
value := "UpdatedAnswerValue"
accessPackageAnswer.SetValue(&value) 
answeredQuestion := graphmodels.NewAccessPackageMultipleChoiceQuestion()
id := "8fe745e7-80b2-490d-bd22-4e708c77288c"
answeredQuestion.SetId(&id) 
accessPackageAnswer.SetAnsweredQuestion(answeredQuestion)
accessPackageAnswer1 := graphmodels.NewAccessPackageAnswerString()
value := "My updated answer."
accessPackageAnswer1.SetValue(&value) 
displayValue := "This is my updated answer to the question."
accessPackageAnswer1.SetDisplayValue(&displayValue) 
answeredQuestion := graphmodels.NewAccessPackageTextInputQuestion()
id := "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6"
answeredQuestion.SetId(&id) 
accessPackageAnswer1.SetAnsweredQuestion(answeredQuestion)

answers := []graphmodels.AccessPackageAnswerable {
	accessPackageAnswer,
	accessPackageAnswer1,
}
requestBody.SetAnswers(answers)
assignment := graphmodels.NewAccessPackageAssignment()
id := "44c741c1-2cf4-40db-83b6-e0112f8e5a83"
assignment.SetId(&id) 
requestBody.SetAssignment(assignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setOdataType("#microsoft.graph.accessPackageAssignmentRequest");
accessPackageAssignmentRequest.setRequestType(AccessPackageRequestType.AdminUpdate);
LinkedList<AccessPackageAnswer> answers = new LinkedList<AccessPackageAnswer>();
AccessPackageAnswerString accessPackageAnswer = new AccessPackageAnswerString();
accessPackageAnswer.setOdataType("#microsoft.graph.accessPackageAnswerString");
accessPackageAnswer.setValue("UpdatedAnswerValue");
AccessPackageMultipleChoiceQuestion answeredQuestion = new AccessPackageMultipleChoiceQuestion();
answeredQuestion.setOdataType("#microsoft.graph.accessPackageMultipleChoiceQuestion");
answeredQuestion.setId("8fe745e7-80b2-490d-bd22-4e708c77288c");
accessPackageAnswer.setAnsweredQuestion(answeredQuestion);
answers.add(accessPackageAnswer);
AccessPackageAnswerString accessPackageAnswer1 = new AccessPackageAnswerString();
accessPackageAnswer1.setOdataType("#microsoft.graph.accessPackageAnswerString");
accessPackageAnswer1.setValue("My updated answer.");
accessPackageAnswer1.setDisplayValue("This is my updated answer to the question.");
AccessPackageTextInputQuestion answeredQuestion1 = new AccessPackageTextInputQuestion();
answeredQuestion1.setOdataType("#microsoft.graph.accessPackageTextInputQuestion");
answeredQuestion1.setId("7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6");
accessPackageAnswer1.setAnsweredQuestion(answeredQuestion1);
answers.add(accessPackageAnswer1);
accessPackageAssignmentRequest.setAnswers(answers);
AccessPackageAssignment assignment = new AccessPackageAssignment();
assignment.setId("44c741c1-2cf4-40db-83b6-e0112f8e5a83");
accessPackageAssignmentRequest.setAssignment(assignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().assignmentRequests().post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
    '@odata.type': '#microsoft.graph.accessPackageAssignmentRequest',
    requestType: 'adminUpdate',
    answers: [
        {
            '@odata.type': '#microsoft.graph.accessPackageAnswerString',
            value: 'UpdatedAnswerValue',
            answeredQuestion: {
                '@odata.type': '#microsoft.graph.accessPackageMultipleChoiceQuestion',
                id: '8fe745e7-80b2-490d-bd22-4e708c77288c'
            }
        },
        {
            '@odata.type': '#microsoft.graph.accessPackageAnswerString',
            value: 'My updated answer.',
            displayValue: 'This is my updated answer to the question.',
            answeredQuestion: {
                '@odata.type': '#microsoft.graph.accessPackageTextInputQuestion',
                id: '7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6'
            }
        }
    ],
    assignment: {
        id: '44c741c1-2cf4-40db-83b6-e0112f8e5a83'
    }
};

await client.api('/identityGovernance/entitlementManagement/assignmentRequests')
	.post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageAnswer;
use Microsoft\Graph\Generated\Models\AccessPackageAnswerString;
use Microsoft\Graph\Generated\Models\AccessPackageMultipleChoiceQuestion;
use Microsoft\Graph\Generated\Models\AccessPackageTextInputQuestion;
use Microsoft\Graph\Generated\Models\AccessPackageAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setOdataType('#microsoft.graph.accessPackageAssignmentRequest');
$requestBody->setRequestType(new AccessPackageRequestType('adminUpdate'));
$answersAccessPackageAnswer1 = new AccessPackageAnswerString();
$answersAccessPackageAnswer1->setOdataType('#microsoft.graph.accessPackageAnswerString');
$answersAccessPackageAnswer1->setValue('UpdatedAnswerValue');
$answersAccessPackageAnswer1AnsweredQuestion = new AccessPackageMultipleChoiceQuestion();
$answersAccessPackageAnswer1AnsweredQuestion->setOdataType('#microsoft.graph.accessPackageMultipleChoiceQuestion');
$answersAccessPackageAnswer1AnsweredQuestion->setId('8fe745e7-80b2-490d-bd22-4e708c77288c');
$answersAccessPackageAnswer1->setAnsweredQuestion($answersAccessPackageAnswer1AnsweredQuestion);
$answersArray []= $answersAccessPackageAnswer1;
$answersAccessPackageAnswer2 = new AccessPackageAnswerString();
$answersAccessPackageAnswer2->setOdataType('#microsoft.graph.accessPackageAnswerString');
$answersAccessPackageAnswer2->setValue('My updated answer.');
$answersAccessPackageAnswer2->setDisplayValue('This is my updated answer to the question.');
$answersAccessPackageAnswer2AnsweredQuestion = new AccessPackageTextInputQuestion();
$answersAccessPackageAnswer2AnsweredQuestion->setOdataType('#microsoft.graph.accessPackageTextInputQuestion');
$answersAccessPackageAnswer2AnsweredQuestion->setId('7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6');
$answersAccessPackageAnswer2->setAnsweredQuestion($answersAccessPackageAnswer2AnsweredQuestion);
$answersArray []= $answersAccessPackageAnswer2;
$requestBody->setAnswers($answersArray);

$assignment = new AccessPackageAssignment();
$assignment->setId('44c741c1-2cf4-40db-83b6-e0112f8e5a83');
$requestBody->setAssignment($assignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	"@odata.type" = "#microsoft.graph.accessPackageAssignmentRequest"
	requestType = "adminUpdate"
	answers = @(
		@{
			"@odata.type" = "#microsoft.graph.accessPackageAnswerString"
			value = "UpdatedAnswerValue"
			answeredQuestion = @{
				"@odata.type" = "#microsoft.graph.accessPackageMultipleChoiceQuestion"
				id = "8fe745e7-80b2-490d-bd22-4e708c77288c"
			}
		}
		@{
			"@odata.type" = "#microsoft.graph.accessPackageAnswerString"
			value = "My updated answer."
			displayValue = "This is my updated answer to the question."
			answeredQuestion = @{
				"@odata.type" = "#microsoft.graph.accessPackageTextInputQuestion"
				id = "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6"
			}
		}
	)
	assignment = @{
		id = "44c741c1-2cf4-40db-83b6-e0112f8e5a83"
	}
}

New-MgEntitlementManagementAssignmentRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_answer import AccessPackageAnswer
from msgraph.generated.models.access_package_answer_string import AccessPackageAnswerString
from msgraph.generated.models.access_package_multiple_choice_question import AccessPackageMultipleChoiceQuestion
from msgraph.generated.models.access_package_text_input_question import AccessPackageTextInputQuestion
from msgraph.generated.models.access_package_assignment import AccessPackageAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	odata_type = "#microsoft.graph.accessPackageAssignmentRequest",
	request_type = AccessPackageRequestType.AdminUpdate,
	answers = [
		AccessPackageAnswerString(
			odata_type = "#microsoft.graph.accessPackageAnswerString",
			value = "UpdatedAnswerValue",
			answered_question = AccessPackageMultipleChoiceQuestion(
				odata_type = "#microsoft.graph.accessPackageMultipleChoiceQuestion",
				id = "8fe745e7-80b2-490d-bd22-4e708c77288c",
			),
		),
		AccessPackageAnswerString(
			odata_type = "#microsoft.graph.accessPackageAnswerString",
			value = "My updated answer.",
			display_value = "This is my updated answer to the question.",
			answered_question = AccessPackageTextInputQuestion(
				odata_type = "#microsoft.graph.accessPackageTextInputQuestion",
				id = "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6",
			),
		),
	],
	assignment = AccessPackageAssignment(
		id = "44c741c1-2cf4-40db-83b6-e0112f8e5a83",
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties are returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#accessPackageAssignmentRequests/$entity",
    "id": "0c471116-e439-40a6-8441-fe739dd48dab",
    "requestType": "adminUpdate",
    "state": "submitted",
    "status": "Accepted",
    "createdDateTime": null,
    "completedDateTime": null,
    "schedule": {
        "startDateTime": null,
        "recurrence": null,
        "expiration": {
            "endDateTime": null,
            "duration": null,
            "type": "notSpecified"
        }
    },
    "answers": [
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "UpdatedAnswerValue",
            "displayValue": "This is the answer to a multiple choice question",
            "answeredQuestion": {
                "@odata.type": "#microsoft.graph.accessPackageMultipleChoiceQuestion",
                "id": "8fe745e7-80b2-490d-bd22-4e708c77288c"   
            }         
        },
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "My updated answer.",
            "displayValue": "This is my updated answer to the question.",
            "answeredQuestion": {
                "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
                "id": "7aaa18c9-8e4f-440f-bd5a-3a7ce312cbe6"
            }
        }
    ]
}
```

### Example 7: Update the expiration date for an access package assignment

The following example shows how to update the expiration date for an access package assignment.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentRequests
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.accessPackageAssignmentRequest",
    "requestType": "adminUpdate",
    "schedule": {
        "startDateTime": "2023-05-23T20:04:02.39Z",
        "recurrence": null,
        "expiration": {
            "endDateTime": "2024-07-01T00:00:00.00Z",
            "duration": null,
            "type": "afterDateTime"
        }
    },
    "assignment": {
        "id": "329f8dac-8062-4c1b-a9b8-39b7132f9bff"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	OdataType = "#microsoft.graph.accessPackageAssignmentRequest",
	RequestType = AccessPackageRequestType.AdminUpdate,
	Schedule = new EntitlementManagementSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2023-05-23T20:04:02.39Z"),
		Recurrence = null,
		Expiration = new ExpirationPattern
		{
			EndDateTime = DateTimeOffset.Parse("2024-07-01T00:00:00.00Z"),
			Duration = null,
			Type = ExpirationPatternType.AfterDateTime,
		},
	},
	Assignment = new AccessPackageAssignment
	{
		Id = "329f8dac-8062-4c1b-a9b8-39b7132f9bff",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := graphmodels.ADMINUPDATE_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
schedule := graphmodels.NewEntitlementManagementSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2023-05-23T20:04:02.39Z")
schedule.SetStartDateTime(&startDateTime) 
recurrence := null
schedule.SetRecurrence(&recurrence) 
expiration := graphmodels.NewExpirationPattern()
endDateTime , err := time.Parse(time.RFC3339, "2024-07-01T00:00:00.00Z")
expiration.SetEndDateTime(&endDateTime) 
duration := null
expiration.SetDuration(&duration) 
type := graphmodels.AFTERDATETIME_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
schedule.SetExpiration(expiration)
requestBody.SetSchedule(schedule)
assignment := graphmodels.NewAccessPackageAssignment()
id := "329f8dac-8062-4c1b-a9b8-39b7132f9bff"
assignment.SetId(&id) 
requestBody.SetAssignment(assignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setOdataType("#microsoft.graph.accessPackageAssignmentRequest");
accessPackageAssignmentRequest.setRequestType(AccessPackageRequestType.AdminUpdate);
EntitlementManagementSchedule schedule = new EntitlementManagementSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2023-05-23T20:04:02.39Z");
schedule.setStartDateTime(startDateTime);
schedule.setRecurrence(null);
ExpirationPattern expiration = new ExpirationPattern();
OffsetDateTime endDateTime = OffsetDateTime.parse("2024-07-01T00:00:00.00Z");
expiration.setEndDateTime(endDateTime);
expiration.setDuration(null);
expiration.setType(ExpirationPatternType.AfterDateTime);
schedule.setExpiration(expiration);
accessPackageAssignmentRequest.setSchedule(schedule);
AccessPackageAssignment assignment = new AccessPackageAssignment();
assignment.setId("329f8dac-8062-4c1b-a9b8-39b7132f9bff");
accessPackageAssignmentRequest.setAssignment(assignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().assignmentRequests().post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
    '@odata.type': '#microsoft.graph.accessPackageAssignmentRequest',
    requestType: 'adminUpdate',
    schedule: {
        startDateTime: '2023-05-23T20:04:02.39Z',
        recurrence: null,
        expiration: {
            endDateTime: '2024-07-01T00:00:00.00Z',
            duration: null,
            type: 'afterDateTime'
        }
    },
    assignment: {
        id: '329f8dac-8062-4c1b-a9b8-39b7132f9bff'
    }
};

await client.api('/identityGovernance/entitlementManagement/assignmentRequests')
	.post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\EntitlementManagementSchedule;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;
use Microsoft\Graph\Generated\Models\AccessPackageAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setOdataType('#microsoft.graph.accessPackageAssignmentRequest');
$requestBody->setRequestType(new AccessPackageRequestType('adminUpdate'));
$schedule = new EntitlementManagementSchedule();
$schedule->setStartDateTime(new \DateTime('2023-05-23T20:04:02.39Z'));
$schedule->setRecurrence(null);
$scheduleExpiration = new ExpirationPattern();
$scheduleExpiration->setEndDateTime(new \DateTime('2024-07-01T00:00:00.00Z'));
$scheduleExpiration->setDuration(null);
$scheduleExpiration->setType(new ExpirationPatternType('afterDateTime'));
$schedule->setExpiration($scheduleExpiration);
$requestBody->setSchedule($schedule);
$assignment = new AccessPackageAssignment();
$assignment->setId('329f8dac-8062-4c1b-a9b8-39b7132f9bff');
$requestBody->setAssignment($assignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	"@odata.type" = "#microsoft.graph.accessPackageAssignmentRequest"
	requestType = "adminUpdate"
	schedule = @{
		startDateTime = [System.DateTime]::Parse("2023-05-23T20:04:02.39Z")
		recurrence = $null
		expiration = @{
			endDateTime = [System.DateTime]::Parse("2024-07-01T00:00:00.00Z")
			duration = $null
			type = "afterDateTime"
		}
	}
	assignment = @{
		id = "329f8dac-8062-4c1b-a9b8-39b7132f9bff"
	}
}

New-MgEntitlementManagementAssignmentRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.entitlement_management_schedule import EntitlementManagementSchedule
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
from msgraph.generated.models.access_package_assignment import AccessPackageAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	odata_type = "#microsoft.graph.accessPackageAssignmentRequest",
	request_type = AccessPackageRequestType.AdminUpdate,
	schedule = EntitlementManagementSchedule(
		start_date_time = "2023-05-23T20:04:02.39Z",
		recurrence = None,
		expiration = ExpirationPattern(
			end_date_time = "2024-07-01T00:00:00.00Z",
			duration = None,
			type = ExpirationPatternType.AfterDateTime,
		),
	),
	assignment = AccessPackageAssignment(
		id = "329f8dac-8062-4c1b-a9b8-39b7132f9bff",
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties are returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/assignmentRequests/$entity",
    "id": "5b682fbb-d6e5-4118-a471-46dfc553e9cc",
    "requestType": "adminUpdate",
    "state": "submitted",
    "status": "Accepted",
    "createdDateTime": null,
    "completedDateTime": null,
    "schedule": {
        "startDateTime": "2024-06-07T15:53:35.333Z",
        "recurrence": null,
        "expiration": {
            "endDateTime": "2024-07-01T00:00:00Z",
            "duration": null,
            "type": "afterDateTime"
        }
    },
    "answers": [],
    "customExtensionCalloutInstances": []
}
```

### Example 8: Update the answers and expiration date for an access package assignment

The following example shows how a user can update their answers and the expiration date for their access package assignment.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentRequests
Content-type: application/json

{
    "requestType": "userUpdate",
    "answers": [
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "My updated answer.",
            "answeredQuestion": {
                "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
                "id": "0d31cc60-968e-4f92-955b-443fed03d6f6"
            }
        }

    ],
    "schedule": {
        "startDateTime": "2024-09-18T20:49:16.17Z",
        "recurrence": null,
        "expiration": {
            "endDateTime": "2024-10-18T20:49:15.17Z",
            "duration": null,
            "type": "afterDateTime"
        }
    },
    "assignment": {
        "id": "329f8dac-8062-4c1b-a9b8-39b7132f9bff"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = AccessPackageRequestType.UserUpdate,
	Answers = new List<AccessPackageAnswer>
	{
		new AccessPackageAnswerString
		{
			OdataType = "#microsoft.graph.accessPackageAnswerString",
			Value = "My updated answer.",
			AnsweredQuestion = new AccessPackageTextInputQuestion
			{
				OdataType = "#microsoft.graph.accessPackageTextInputQuestion",
				Id = "0d31cc60-968e-4f92-955b-443fed03d6f6",
			},
		},
	},
	Schedule = new EntitlementManagementSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2024-09-18T20:49:16.17Z"),
		Recurrence = null,
		Expiration = new ExpirationPattern
		{
			EndDateTime = DateTimeOffset.Parse("2024-10-18T20:49:15.17Z"),
			Duration = null,
			Type = ExpirationPatternType.AfterDateTime,
		},
	},
	Assignment = new AccessPackageAssignment
	{
		Id = "329f8dac-8062-4c1b-a9b8-39b7132f9bff",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := graphmodels.USERUPDATE_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 


accessPackageAnswer := graphmodels.NewAccessPackageAnswerString()
value := "My updated answer."
accessPackageAnswer.SetValue(&value) 
answeredQuestion := graphmodels.NewAccessPackageTextInputQuestion()
id := "0d31cc60-968e-4f92-955b-443fed03d6f6"
answeredQuestion.SetId(&id) 
accessPackageAnswer.SetAnsweredQuestion(answeredQuestion)

answers := []graphmodels.AccessPackageAnswerable {
	accessPackageAnswer,
}
requestBody.SetAnswers(answers)
schedule := graphmodels.NewEntitlementManagementSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2024-09-18T20:49:16.17Z")
schedule.SetStartDateTime(&startDateTime) 
recurrence := null
schedule.SetRecurrence(&recurrence) 
expiration := graphmodels.NewExpirationPattern()
endDateTime , err := time.Parse(time.RFC3339, "2024-10-18T20:49:15.17Z")
expiration.SetEndDateTime(&endDateTime) 
duration := null
expiration.SetDuration(&duration) 
type := graphmodels.AFTERDATETIME_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
schedule.SetExpiration(expiration)
requestBody.SetSchedule(schedule)
assignment := graphmodels.NewAccessPackageAssignment()
id := "329f8dac-8062-4c1b-a9b8-39b7132f9bff"
assignment.SetId(&id) 
requestBody.SetAssignment(assignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType(AccessPackageRequestType.UserUpdate);
LinkedList<AccessPackageAnswer> answers = new LinkedList<AccessPackageAnswer>();
AccessPackageAnswerString accessPackageAnswer = new AccessPackageAnswerString();
accessPackageAnswer.setOdataType("#microsoft.graph.accessPackageAnswerString");
accessPackageAnswer.setValue("My updated answer.");
AccessPackageTextInputQuestion answeredQuestion = new AccessPackageTextInputQuestion();
answeredQuestion.setOdataType("#microsoft.graph.accessPackageTextInputQuestion");
answeredQuestion.setId("0d31cc60-968e-4f92-955b-443fed03d6f6");
accessPackageAnswer.setAnsweredQuestion(answeredQuestion);
answers.add(accessPackageAnswer);
accessPackageAssignmentRequest.setAnswers(answers);
EntitlementManagementSchedule schedule = new EntitlementManagementSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2024-09-18T20:49:16.17Z");
schedule.setStartDateTime(startDateTime);
schedule.setRecurrence(null);
ExpirationPattern expiration = new ExpirationPattern();
OffsetDateTime endDateTime = OffsetDateTime.parse("2024-10-18T20:49:15.17Z");
expiration.setEndDateTime(endDateTime);
expiration.setDuration(null);
expiration.setType(ExpirationPatternType.AfterDateTime);
schedule.setExpiration(expiration);
accessPackageAssignmentRequest.setSchedule(schedule);
AccessPackageAssignment assignment = new AccessPackageAssignment();
assignment.setId("329f8dac-8062-4c1b-a9b8-39b7132f9bff");
accessPackageAssignmentRequest.setAssignment(assignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().assignmentRequests().post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
    requestType: 'userUpdate',
    answers: [
        {
            '@odata.type': '#microsoft.graph.accessPackageAnswerString',
            value: 'My updated answer.',
            answeredQuestion: {
                '@odata.type': '#microsoft.graph.accessPackageTextInputQuestion',
                id: '0d31cc60-968e-4f92-955b-443fed03d6f6'
            }
        }

    ],
    schedule: {
        startDateTime: '2024-09-18T20:49:16.17Z',
        recurrence: null,
        expiration: {
            endDateTime: '2024-10-18T20:49:15.17Z',
            duration: null,
            type: 'afterDateTime'
        }
    },
    assignment: {
        id: '329f8dac-8062-4c1b-a9b8-39b7132f9bff'
    }
};

await client.api('/identityGovernance/entitlementManagement/assignmentRequests')
	.post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageAnswer;
use Microsoft\Graph\Generated\Models\AccessPackageAnswerString;
use Microsoft\Graph\Generated\Models\AccessPackageTextInputQuestion;
use Microsoft\Graph\Generated\Models\EntitlementManagementSchedule;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;
use Microsoft\Graph\Generated\Models\AccessPackageAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType(new AccessPackageRequestType('userUpdate'));
$answersAccessPackageAnswer1 = new AccessPackageAnswerString();
$answersAccessPackageAnswer1->setOdataType('#microsoft.graph.accessPackageAnswerString');
$answersAccessPackageAnswer1->setValue('My updated answer.');
$answersAccessPackageAnswer1AnsweredQuestion = new AccessPackageTextInputQuestion();
$answersAccessPackageAnswer1AnsweredQuestion->setOdataType('#microsoft.graph.accessPackageTextInputQuestion');
$answersAccessPackageAnswer1AnsweredQuestion->setId('0d31cc60-968e-4f92-955b-443fed03d6f6');
$answersAccessPackageAnswer1->setAnsweredQuestion($answersAccessPackageAnswer1AnsweredQuestion);
$answersArray []= $answersAccessPackageAnswer1;
$requestBody->setAnswers($answersArray);

$schedule = new EntitlementManagementSchedule();
$schedule->setStartDateTime(new \DateTime('2024-09-18T20:49:16.17Z'));
$schedule->setRecurrence(null);
$scheduleExpiration = new ExpirationPattern();
$scheduleExpiration->setEndDateTime(new \DateTime('2024-10-18T20:49:15.17Z'));
$scheduleExpiration->setDuration(null);
$scheduleExpiration->setType(new ExpirationPatternType('afterDateTime'));
$schedule->setExpiration($scheduleExpiration);
$requestBody->setSchedule($schedule);
$assignment = new AccessPackageAssignment();
$assignment->setId('329f8dac-8062-4c1b-a9b8-39b7132f9bff');
$requestBody->setAssignment($assignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "userUpdate"
	answers = @(
		@{
			"@odata.type" = "#microsoft.graph.accessPackageAnswerString"
			value = "My updated answer."
			answeredQuestion = @{
				"@odata.type" = "#microsoft.graph.accessPackageTextInputQuestion"
				id = "0d31cc60-968e-4f92-955b-443fed03d6f6"
			}
		}
	)
	schedule = @{
		startDateTime = [System.DateTime]::Parse("2024-09-18T20:49:16.17Z")
		recurrence = $null
		expiration = @{
			endDateTime = [System.DateTime]::Parse("2024-10-18T20:49:15.17Z")
			duration = $null
			type = "afterDateTime"
		}
	}
	assignment = @{
		id = "329f8dac-8062-4c1b-a9b8-39b7132f9bff"
	}
}

New-MgEntitlementManagementAssignmentRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_answer import AccessPackageAnswer
from msgraph.generated.models.access_package_answer_string import AccessPackageAnswerString
from msgraph.generated.models.access_package_text_input_question import AccessPackageTextInputQuestion
from msgraph.generated.models.entitlement_management_schedule import EntitlementManagementSchedule
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
from msgraph.generated.models.access_package_assignment import AccessPackageAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = AccessPackageRequestType.UserUpdate,
	answers = [
		AccessPackageAnswerString(
			odata_type = "#microsoft.graph.accessPackageAnswerString",
			value = "My updated answer.",
			answered_question = AccessPackageTextInputQuestion(
				odata_type = "#microsoft.graph.accessPackageTextInputQuestion",
				id = "0d31cc60-968e-4f92-955b-443fed03d6f6",
			),
		),
	],
	schedule = EntitlementManagementSchedule(
		start_date_time = "2024-09-18T20:49:16.17Z",
		recurrence = None,
		expiration = ExpirationPattern(
			end_date_time = "2024-10-18T20:49:15.17Z",
			duration = None,
			type = ExpirationPatternType.AfterDateTime,
		),
	),
	assignment = AccessPackageAssignment(
		id = "329f8dac-8062-4c1b-a9b8-39b7132f9bff",
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties are returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/assignmentRequests/$entity",
    "id": "e0f8458c-7681-42ad-a0b5-0c9587c4dad8",
    "requestType": "userUpdate",
    "state": "submitted",
    "status": "Accepted"
}
```

### Example 9: Request a package on behalf of a direct employee

The following example shows how a manager can request an access package assignment on behalf of their direct employee.

Note

The requestor \(manager\) is extracted from the token, and the target object is determined by the `id` of the direct employee who is receiving access.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentRequests
Content-type: application/json

{
   "assignment": {
       "accessPackageId": "5b98f958-0dea-4a5b-836e-109dccbd530c",
       "schedule": {
           "startDateTime": null,
           "stopDateTime": null
       },
       "assignmentPolicyId": "c5f7847f-83a8-4315-a754-d94a6f39b875",
       "target": {
           "displayName": "Idris Ibrahim",
           "email": "IdrisIbrahim@woodgrovebank.com",
           "objectId": "21aceaba-fe13-4e3b-aa8c-4c588d5e7387",
           "subjectType": "user"
       }
   },
   "justification": "Access for direct employee",
   "requestType": "UserAdd",
   "answers": []
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	Assignment = new AccessPackageAssignment
	{
		Schedule = new EntitlementManagementSchedule
		{
			StartDateTime = null,
			AdditionalData = new Dictionary<string, object>
			{
				{
					"stopDateTime" , null
				},
			},
		},
		Target = new AccessPackageSubject
		{
			DisplayName = "Idris Ibrahim",
			Email = "IdrisIbrahim@woodgrovebank.com",
			ObjectId = "21aceaba-fe13-4e3b-aa8c-4c588d5e7387",
			SubjectType = AccessPackageSubjectType.User,
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"accessPackageId" , "5b98f958-0dea-4a5b-836e-109dccbd530c"
			},
			{
				"assignmentPolicyId" , "c5f7847f-83a8-4315-a754-d94a6f39b875"
			},
		},
	},
	Justification = "Access for direct employee",
	RequestType = AccessPackageRequestType.UserAdd,
	Answers = new List<AccessPackageAnswer>
	{
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
assignment := graphmodels.NewAccessPackageAssignment()
schedule := graphmodels.NewEntitlementManagementSchedule()
startDateTime := null
schedule.SetStartDateTime(&startDateTime) 
additionalData := map[string]interface{}{
	stopDateTime := null
schedule.SetStopDateTime(&stopDateTime) 
}
schedule.SetAdditionalData(additionalData)
assignment.SetSchedule(schedule)
target := graphmodels.NewAccessPackageSubject()
displayName := "Idris Ibrahim"
target.SetDisplayName(&displayName) 
email := "IdrisIbrahim@woodgrovebank.com"
target.SetEmail(&email) 
objectId := "21aceaba-fe13-4e3b-aa8c-4c588d5e7387"
target.SetObjectId(&objectId) 
subjectType := graphmodels.USER_ACCESSPACKAGESUBJECTTYPE 
target.SetSubjectType(&subjectType) 
assignment.SetTarget(target)
additionalData := map[string]interface{}{
	"accessPackageId" : "5b98f958-0dea-4a5b-836e-109dccbd530c", 
	"assignmentPolicyId" : "c5f7847f-83a8-4315-a754-d94a6f39b875", 
}
assignment.SetAdditionalData(additionalData)
requestBody.SetAssignment(assignment)
justification := "Access for direct employee"
requestBody.SetJustification(&justification) 
requestType := graphmodels.USERADD_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
answers := []graphmodels.AccessPackageAnswerable {

}
requestBody.SetAnswers(answers)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
AccessPackageAssignment assignment = new AccessPackageAssignment();
EntitlementManagementSchedule schedule = new EntitlementManagementSchedule();
schedule.setStartDateTime(null);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("stopDateTime", null);
schedule.setAdditionalData(additionalData);
assignment.setSchedule(schedule);
AccessPackageSubject target = new AccessPackageSubject();
target.setDisplayName("Idris Ibrahim");
target.setEmail("IdrisIbrahim@woodgrovebank.com");
target.setObjectId("21aceaba-fe13-4e3b-aa8c-4c588d5e7387");
target.setSubjectType(AccessPackageSubjectType.User);
assignment.setTarget(target);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("accessPackageId", "5b98f958-0dea-4a5b-836e-109dccbd530c");
additionalData1.put("assignmentPolicyId", "c5f7847f-83a8-4315-a754-d94a6f39b875");
assignment.setAdditionalData(additionalData1);
accessPackageAssignmentRequest.setAssignment(assignment);
accessPackageAssignmentRequest.setJustification("Access for direct employee");
accessPackageAssignmentRequest.setRequestType(AccessPackageRequestType.UserAdd);
LinkedList<AccessPackageAnswer> answers = new LinkedList<AccessPackageAnswer>();
accessPackageAssignmentRequest.setAnswers(answers);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().assignmentRequests().post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
   assignment: {
       accessPackageId: '5b98f958-0dea-4a5b-836e-109dccbd530c',
       schedule: {
           startDateTime: null,
           stopDateTime: null
       },
       assignmentPolicyId: 'c5f7847f-83a8-4315-a754-d94a6f39b875',
       target: {
           displayName: 'Idris Ibrahim',
           email: 'IdrisIbrahim@woodgrovebank.com',
           objectId: '21aceaba-fe13-4e3b-aa8c-4c588d5e7387',
           subjectType: 'user'
       }
   },
   justification: 'Access for direct employee',
   requestType: 'UserAdd',
   answers: []
};

await client.api('/identityGovernance/entitlementManagement/assignmentRequests')
	.post(accessPackageAssignmentRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Generated\Models\AccessPackageAssignment;
use Microsoft\Graph\Generated\Models\EntitlementManagementSchedule;
use Microsoft\Graph\Generated\Models\AccessPackageSubject;
use Microsoft\Graph\Generated\Models\AccessPackageSubjectType;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageAnswer;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$assignment = new AccessPackageAssignment();
$assignmentSchedule = new EntitlementManagementSchedule();
$assignmentSchedule->setStartDateTime(null);
$additionalData = [
	'stopDateTime' => null,
];
$assignmentSchedule->setAdditionalData($additionalData);
$assignment->setSchedule($assignmentSchedule);
$assignmentTarget = new AccessPackageSubject();
$assignmentTarget->setDisplayName('Idris Ibrahim');
$assignmentTarget->setEmail('IdrisIbrahim@woodgrovebank.com');
$assignmentTarget->setObjectId('21aceaba-fe13-4e3b-aa8c-4c588d5e7387');
$assignmentTarget->setSubjectType(new AccessPackageSubjectType('user'));
$assignment->setTarget($assignmentTarget);
$additionalData = [
	'accessPackageId' => '5b98f958-0dea-4a5b-836e-109dccbd530c',
	'assignmentPolicyId' => 'c5f7847f-83a8-4315-a754-d94a6f39b875',
];
$assignment->setAdditionalData($additionalData);
$requestBody->setAssignment($assignment);
$requestBody->setJustification('Access for direct employee');
$requestBody->setRequestType(new AccessPackageRequestType('userAdd'));
$requestBody->setAnswers([	]);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	assignment = @{
		accessPackageId = "5b98f958-0dea-4a5b-836e-109dccbd530c"
		schedule = @{
			startDateTime = $null
			stopDateTime = $null
		}
		assignmentPolicyId = "c5f7847f-83a8-4315-a754-d94a6f39b875"
		target = @{
			displayName = "Idris Ibrahim"
			email = "IdrisIbrahim@woodgrovebank.com"
			objectId = "21aceaba-fe13-4e3b-aa8c-4c588d5e7387"
			subjectType = "user"
		}
	}
	justification = "Access for direct employee"
	requestType = "UserAdd"
	answers = @(
	)
}

New-MgEntitlementManagementAssignmentRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph.generated.models.access_package_assignment import AccessPackageAssignment
from msgraph.generated.models.entitlement_management_schedule import EntitlementManagementSchedule
from msgraph.generated.models.access_package_subject import AccessPackageSubject
from msgraph.generated.models.access_package_subject_type import AccessPackageSubjectType
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_answer import AccessPackageAnswer
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	assignment = AccessPackageAssignment(
		schedule = EntitlementManagementSchedule(
			start_date_time = None,
			additional_data = {
					"stop_date_time" : None,
			}
		),
		target = AccessPackageSubject(
			display_name = "Idris Ibrahim",
			email = "IdrisIbrahim@woodgrovebank.com",
			object_id = "21aceaba-fe13-4e3b-aa8c-4c588d5e7387",
			subject_type = AccessPackageSubjectType.User,
		),
		additional_data = {
				"access_package_id" : "5b98f958-0dea-4a5b-836e-109dccbd530c",
				"assignment_policy_id" : "c5f7847f-83a8-4315-a754-d94a6f39b875",
		}
	),
	justification = "Access for direct employee",
	request_type = AccessPackageRequestType.UserAdd,
	answers = [
	],
)

result = await graph_client.identity_governance.entitlement_management.assignment_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties are returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/assignmentRequests/$entity",
    "id": "445a3118-6bf2-4a19-94ad-5660295963fd",
    "requestType": "userAdd",
    "state": "submitted",
    "status": "Accepted",
    "createdDateTime": null,
    "completedDateTime": null,
    "schedule": {
        "startDateTime": null,
        "recurrence": null,
        "expiration": {
            "endDateTime": null,
            "duration": null,
            "type": "notSpecified"
        }
    },
    "answers": [],
    "customExtensionCalloutInstances": []
}
```
