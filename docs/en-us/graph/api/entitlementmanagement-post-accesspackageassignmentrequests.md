<!-- Source: https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-accesspackageassignmentrequests?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-22 -->

# Create accessPackageAssignmentRequest

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

In [Microsoft Entra Entitlement Management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-beta), create a new [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-beta) object. This operation is used to assign a user to an access package, or to remove an access package assignment.

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

Note

This API will be retired soon. Use the [Post assignmentRequests](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-assignmentrequests?view=graph-rest-beta) API instead.

```http
POST /identityGovernance/entitlementManagement/accessPackageAssignmentRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-beta) object.

For an administrator to request to create an assignment for a user, the value of the **requestType** property is `AdminAdd`, and the **accessPackageAssignment** property contains the `targetId` of the user being assigned, the **assignmentPolicyId** property identifying the [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-beta), and the **accessPackageId** property identifying the [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-beta).

For an administrator to request to remove an assignment, the value of the **requestType** property is `AdminRemove`, and the **accessPackageAssignment** property contains the **id** property identifying the [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-beta) being removed.

For a non-administrator user to request to create their own assignment for either a first assignment or renew assignment, the value of the **requestType** property is `UserAdd`. The **accessPackageAssignment** property contains the `targetId` with the `id` of the users. The **assignmentPolicyId** property identifies the [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-beta). The **accessPackageId** property identifies the [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-beta). The user making the request must already exist in the directory.

For a non-administrator user to request to extend their own assignments, the value of the **requestType** property is `UserExtend`. The **accessPackageAssignment** property contains the `targetId` with the `id` of the users. The **assignmentPolicyId** property identifies the [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-beta). The **accessPackageId** property identifies the [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-beta). The user making the request must already exist in the directory.

## Response

If successful, this method returns a 200-series response code and a new [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-beta) object in the response body.

If this is an `AdminAdd` request, then subsequently an [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-beta) and, if needed, an [accessPackageSubject](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesubject?view=graph-rest-beta) are also created. You can locate those using the query parameters when [listing accessPackageAssignments](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-accesspackageassignments?view=graph-rest-beta).

## Examples

### Example 1: Admin requests a direct assignment for a user already in the directory

#### Request

The following example shows a request for a direct assignment, in which the administrator requests the creation of an assignment for a user. Because the [accessPackageSubject](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesubject?view=graph-rest-beta) might not yet exist, the value of the **targetID** is the object ID of the user being assigned, the value of the **accessPackageId** is the desired access package for that user, and the value of **assignmentPolicyId** is a direct assignment policy in that access package.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentRequests
Content-type: application/json

{
  "requestType": "AdminAdd",
  "accessPackageAssignment":{
     "targetId":"46184453-e63b-4f20-86c2-c557ed5d5df9",
     "assignmentPolicyId":"2264bf65-76ba-417b-a27d-54d291f0cbc8",
     "accessPackageId":"a914b616-e04e-476b-aa37-91038f0b165b"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = "AdminAdd",
	AccessPackageAssignment = new AccessPackageAssignment
	{
		TargetId = "46184453-e63b-4f20-86c2-c557ed5d5df9",
		AssignmentPolicyId = "2264bf65-76ba-417b-a27d-54d291f0cbc8",
		AccessPackageId = "a914b616-e04e-476b-aa37-91038f0b165b",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := "AdminAdd"
requestBody.SetRequestType(&requestType) 
accessPackageAssignment := graphmodels.NewAccessPackageAssignment()
targetId := "46184453-e63b-4f20-86c2-c557ed5d5df9"
accessPackageAssignment.SetTargetId(&targetId) 
assignmentPolicyId := "2264bf65-76ba-417b-a27d-54d291f0cbc8"
accessPackageAssignment.SetAssignmentPolicyId(&assignmentPolicyId) 
accessPackageId := "a914b616-e04e-476b-aa37-91038f0b165b"
accessPackageAssignment.SetAccessPackageId(&accessPackageId) 
requestBody.SetAccessPackageAssignment(accessPackageAssignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType("AdminAdd");
AccessPackageAssignment accessPackageAssignment = new AccessPackageAssignment();
accessPackageAssignment.setTargetId("46184453-e63b-4f20-86c2-c557ed5d5df9");
accessPackageAssignment.setAssignmentPolicyId("2264bf65-76ba-417b-a27d-54d291f0cbc8");
accessPackageAssignment.setAccessPackageId("a914b616-e04e-476b-aa37-91038f0b165b");
accessPackageAssignmentRequest.setAccessPackageAssignment(accessPackageAssignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentRequests().post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
  requestType: 'AdminAdd',
  accessPackageAssignment: {
     targetId: '46184453-e63b-4f20-86c2-c557ed5d5df9',
     assignmentPolicyId: '2264bf65-76ba-417b-a27d-54d291f0cbc8',
     accessPackageId: 'a914b616-e04e-476b-aa37-91038f0b165b'
  }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentRequests')
	.version('beta')
	.post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType('AdminAdd');
$accessPackageAssignment = new AccessPackageAssignment();
$accessPackageAssignment->setTargetId('46184453-e63b-4f20-86c2-c557ed5d5df9');
$accessPackageAssignment->setAssignmentPolicyId('2264bf65-76ba-417b-a27d-54d291f0cbc8');
$accessPackageAssignment->setAccessPackageId('a914b616-e04e-476b-aa37-91038f0b165b');
$requestBody->setAccessPackageAssignment($accessPackageAssignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestType = "AdminAdd"
	accessPackageAssignment = @{
		targetId = "46184453-e63b-4f20-86c2-c557ed5d5df9"
		assignmentPolicyId = "2264bf65-76ba-417b-a27d-54d291f0cbc8"
		accessPackageId = "a914b616-e04e-476b-aa37-91038f0b165b"
	}
}

New-MgBetaEntitlementManagementAccessPackageAssignmentRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph_beta.generated.models.access_package_assignment import AccessPackageAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = "AdminAdd",
	access_package_assignment = AccessPackageAssignment(
		target_id = "46184453-e63b-4f20-86c2-c557ed5d5df9",
		assignment_policy_id = "2264bf65-76ba-417b-a27d-54d291f0cbc8",
		access_package_id = "a914b616-e04e-476b-aa37-91038f0b165b",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_requests.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "7e382d02-4454-436b-b700-59c7dd77f466",
  "requestType": "AdminAdd",
  "requestState": "Submitted",
  "requestStatus": "Accepted",
  "isValidationOnly": false
}
```

### Example 2: Remove an assignment

To remove assignments, create a new accessPackageAssignmentRequest object with the following settings:

- The value of the **requestType** property set to `AdminRemove`.
- In the **accessPackageAssignment** property, include an object with the identifier of the **accessPackageAssignment** objects to delete.

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
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentRequests
Content-type: application/json

{
    "requestType": "AdminRemove",
    "accessPackageAssignment":{
     "id": "a6bb6942-3ae1-4259-9908-0133aaee9377"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = "AdminRemove",
	AccessPackageAssignment = new AccessPackageAssignment
	{
		Id = "a6bb6942-3ae1-4259-9908-0133aaee9377",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := "AdminRemove"
requestBody.SetRequestType(&requestType) 
accessPackageAssignment := graphmodels.NewAccessPackageAssignment()
id := "a6bb6942-3ae1-4259-9908-0133aaee9377"
accessPackageAssignment.SetId(&id) 
requestBody.SetAccessPackageAssignment(accessPackageAssignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType("AdminRemove");
AccessPackageAssignment accessPackageAssignment = new AccessPackageAssignment();
accessPackageAssignment.setId("a6bb6942-3ae1-4259-9908-0133aaee9377");
accessPackageAssignmentRequest.setAccessPackageAssignment(accessPackageAssignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentRequests().post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
    requestType: 'AdminRemove',
    accessPackageAssignment: {
     id: 'a6bb6942-3ae1-4259-9908-0133aaee9377'
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentRequests')
	.version('beta')
	.post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType('AdminRemove');
$accessPackageAssignment = new AccessPackageAssignment();
$accessPackageAssignment->setId('a6bb6942-3ae1-4259-9908-0133aaee9377');
$requestBody->setAccessPackageAssignment($accessPackageAssignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestType = "AdminRemove"
	accessPackageAssignment = @{
		id = "a6bb6942-3ae1-4259-9908-0133aaee9377"
	}
}

New-MgBetaEntitlementManagementAccessPackageAssignmentRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph_beta.generated.models.access_package_assignment import AccessPackageAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = "AdminRemove",
	access_package_assignment = AccessPackageAssignment(
		id = "a6bb6942-3ae1-4259-9908-0133aaee9377",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_requests.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties are returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#accessPackageAssignmentRequests/$entity",

    "id": "78eaee8c-e6cf-48c9-8f99-aae44c35e379",
    "requestType": "AdminRemove",
    "requestState": "Submitted",
    "requestStatus": "Accepted"
}
```

### Example 3: Request an assignment by providing answers to questions

The following example shows a request where the requestor provided answers to the approver to help them make their decision.

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
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentRequests
Content-type: application/json

{
    "requestType": "UserAdd",
    "accessPackageAssignment": {
        "targetId": "46184453-e63b-4f20-86c2-c557ed5d5df9",
        "assignmentPolicyId": "2264bf65-76ba-417b-a27d-54d291f0cbc8",
        "accessPackageId": "a914b616-e04e-476b-aa37-91038f0b165b"
    },
    "answers": [
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "Arizona",
            "answeredQuestion": {
                "@odata.type": "#microsoft.graph.accessPackageMultipleChoiceQuestion",
                "id": "A714EC6F-4EE0-4614-BD81-37E0C5ECBBFF"
            }
        },
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "Need access to marketing campaign material",
            "answeredQuestion": {
                "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
                "id": "AA615EE9-D9D8-4C03-BE91-BEE37106DEDA"
            }
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = "UserAdd",
	AccessPackageAssignment = new AccessPackageAssignment
	{
		TargetId = "46184453-e63b-4f20-86c2-c557ed5d5df9",
		AssignmentPolicyId = "2264bf65-76ba-417b-a27d-54d291f0cbc8",
		AccessPackageId = "a914b616-e04e-476b-aa37-91038f0b165b",
	},
	Answers = new List<AccessPackageAnswer>
	{
		new AccessPackageAnswerString
		{
			OdataType = "#microsoft.graph.accessPackageAnswerString",
			Value = "Arizona",
			AnsweredQuestion = new AccessPackageMultipleChoiceQuestion
			{
				OdataType = "#microsoft.graph.accessPackageMultipleChoiceQuestion",
				Id = "A714EC6F-4EE0-4614-BD81-37E0C5ECBBFF",
			},
		},
		new AccessPackageAnswerString
		{
			OdataType = "#microsoft.graph.accessPackageAnswerString",
			Value = "Need access to marketing campaign material",
			AnsweredQuestion = new AccessPackageTextInputQuestion
			{
				OdataType = "#microsoft.graph.accessPackageTextInputQuestion",
				Id = "AA615EE9-D9D8-4C03-BE91-BEE37106DEDA",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := "UserAdd"
requestBody.SetRequestType(&requestType) 
accessPackageAssignment := graphmodels.NewAccessPackageAssignment()
targetId := "46184453-e63b-4f20-86c2-c557ed5d5df9"
accessPackageAssignment.SetTargetId(&targetId) 
assignmentPolicyId := "2264bf65-76ba-417b-a27d-54d291f0cbc8"
accessPackageAssignment.SetAssignmentPolicyId(&assignmentPolicyId) 
accessPackageId := "a914b616-e04e-476b-aa37-91038f0b165b"
accessPackageAssignment.SetAccessPackageId(&accessPackageId) 
requestBody.SetAccessPackageAssignment(accessPackageAssignment)


accessPackageAnswer := graphmodels.NewAccessPackageAnswerString()
value := "Arizona"
accessPackageAnswer.SetValue(&value) 
answeredQuestion := graphmodels.NewAccessPackageMultipleChoiceQuestion()
id := "A714EC6F-4EE0-4614-BD81-37E0C5ECBBFF"
answeredQuestion.SetId(&id) 
accessPackageAnswer.SetAnsweredQuestion(answeredQuestion)
accessPackageAnswer1 := graphmodels.NewAccessPackageAnswerString()
value := "Need access to marketing campaign material"
accessPackageAnswer1.SetValue(&value) 
answeredQuestion := graphmodels.NewAccessPackageTextInputQuestion()
id := "AA615EE9-D9D8-4C03-BE91-BEE37106DEDA"
answeredQuestion.SetId(&id) 
accessPackageAnswer1.SetAnsweredQuestion(answeredQuestion)

answers := []graphmodels.AccessPackageAnswerable {
	accessPackageAnswer,
	accessPackageAnswer1,
}
requestBody.SetAnswers(answers)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType("UserAdd");
AccessPackageAssignment accessPackageAssignment = new AccessPackageAssignment();
accessPackageAssignment.setTargetId("46184453-e63b-4f20-86c2-c557ed5d5df9");
accessPackageAssignment.setAssignmentPolicyId("2264bf65-76ba-417b-a27d-54d291f0cbc8");
accessPackageAssignment.setAccessPackageId("a914b616-e04e-476b-aa37-91038f0b165b");
accessPackageAssignmentRequest.setAccessPackageAssignment(accessPackageAssignment);
LinkedList<AccessPackageAnswer> answers = new LinkedList<AccessPackageAnswer>();
AccessPackageAnswerString accessPackageAnswer = new AccessPackageAnswerString();
accessPackageAnswer.setOdataType("#microsoft.graph.accessPackageAnswerString");
accessPackageAnswer.setValue("Arizona");
AccessPackageMultipleChoiceQuestion answeredQuestion = new AccessPackageMultipleChoiceQuestion();
answeredQuestion.setOdataType("#microsoft.graph.accessPackageMultipleChoiceQuestion");
answeredQuestion.setId("A714EC6F-4EE0-4614-BD81-37E0C5ECBBFF");
accessPackageAnswer.setAnsweredQuestion(answeredQuestion);
answers.add(accessPackageAnswer);
AccessPackageAnswerString accessPackageAnswer1 = new AccessPackageAnswerString();
accessPackageAnswer1.setOdataType("#microsoft.graph.accessPackageAnswerString");
accessPackageAnswer1.setValue("Need access to marketing campaign material");
AccessPackageTextInputQuestion answeredQuestion1 = new AccessPackageTextInputQuestion();
answeredQuestion1.setOdataType("#microsoft.graph.accessPackageTextInputQuestion");
answeredQuestion1.setId("AA615EE9-D9D8-4C03-BE91-BEE37106DEDA");
accessPackageAnswer1.setAnsweredQuestion(answeredQuestion1);
answers.add(accessPackageAnswer1);
accessPackageAssignmentRequest.setAnswers(answers);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentRequests().post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
    requestType: 'UserAdd',
    accessPackageAssignment: {
        targetId: '46184453-e63b-4f20-86c2-c557ed5d5df9',
        assignmentPolicyId: '2264bf65-76ba-417b-a27d-54d291f0cbc8',
        accessPackageId: 'a914b616-e04e-476b-aa37-91038f0b165b'
    },
    answers: [
        {
            '@odata.type': '#microsoft.graph.accessPackageAnswerString',
            value: 'Arizona',
            answeredQuestion: {
                '@odata.type': '#microsoft.graph.accessPackageMultipleChoiceQuestion',
                id: 'A714EC6F-4EE0-4614-BD81-37E0C5ECBBFF'
            }
        },
        {
            '@odata.type': '#microsoft.graph.accessPackageAnswerString',
            value: 'Need access to marketing campaign material',
            answeredQuestion: {
                '@odata.type': '#microsoft.graph.accessPackageTextInputQuestion',
                id: 'AA615EE9-D9D8-4C03-BE91-BEE37106DEDA'
            }
        }
    ]
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentRequests')
	.version('beta')
	.post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignment;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAnswer;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAnswerString;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageMultipleChoiceQuestion;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageTextInputQuestion;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType('UserAdd');
$accessPackageAssignment = new AccessPackageAssignment();
$accessPackageAssignment->setTargetId('46184453-e63b-4f20-86c2-c557ed5d5df9');
$accessPackageAssignment->setAssignmentPolicyId('2264bf65-76ba-417b-a27d-54d291f0cbc8');
$accessPackageAssignment->setAccessPackageId('a914b616-e04e-476b-aa37-91038f0b165b');
$requestBody->setAccessPackageAssignment($accessPackageAssignment);
$answersAccessPackageAnswer1 = new AccessPackageAnswerString();
$answersAccessPackageAnswer1->setOdataType('#microsoft.graph.accessPackageAnswerString');
$answersAccessPackageAnswer1->setValue('Arizona');
$answersAccessPackageAnswer1AnsweredQuestion = new AccessPackageMultipleChoiceQuestion();
$answersAccessPackageAnswer1AnsweredQuestion->setOdataType('#microsoft.graph.accessPackageMultipleChoiceQuestion');
$answersAccessPackageAnswer1AnsweredQuestion->setId('A714EC6F-4EE0-4614-BD81-37E0C5ECBBFF');
$answersAccessPackageAnswer1->setAnsweredQuestion($answersAccessPackageAnswer1AnsweredQuestion);
$answersArray []= $answersAccessPackageAnswer1;
$answersAccessPackageAnswer2 = new AccessPackageAnswerString();
$answersAccessPackageAnswer2->setOdataType('#microsoft.graph.accessPackageAnswerString');
$answersAccessPackageAnswer2->setValue('Need access to marketing campaign material');
$answersAccessPackageAnswer2AnsweredQuestion = new AccessPackageTextInputQuestion();
$answersAccessPackageAnswer2AnsweredQuestion->setOdataType('#microsoft.graph.accessPackageTextInputQuestion');
$answersAccessPackageAnswer2AnsweredQuestion->setId('AA615EE9-D9D8-4C03-BE91-BEE37106DEDA');
$answersAccessPackageAnswer2->setAnsweredQuestion($answersAccessPackageAnswer2AnsweredQuestion);
$answersArray []= $answersAccessPackageAnswer2;
$requestBody->setAnswers($answersArray);


$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestType = "UserAdd"
	accessPackageAssignment = @{
		targetId = "46184453-e63b-4f20-86c2-c557ed5d5df9"
		assignmentPolicyId = "2264bf65-76ba-417b-a27d-54d291f0cbc8"
		accessPackageId = "a914b616-e04e-476b-aa37-91038f0b165b"
	}
	answers = @(
		@{
			"@odata.type" = "#microsoft.graph.accessPackageAnswerString"
			value = "Arizona"
			answeredQuestion = @{
				"@odata.type" = "#microsoft.graph.accessPackageMultipleChoiceQuestion"
				id = "A714EC6F-4EE0-4614-BD81-37E0C5ECBBFF"
			}
		}
		@{
			"@odata.type" = "#microsoft.graph.accessPackageAnswerString"
			value = "Need access to marketing campaign material"
			answeredQuestion = @{
				"@odata.type" = "#microsoft.graph.accessPackageTextInputQuestion"
				id = "AA615EE9-D9D8-4C03-BE91-BEE37106DEDA"
			}
		}
	)
}

New-MgBetaEntitlementManagementAccessPackageAssignmentRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph_beta.generated.models.access_package_assignment import AccessPackageAssignment
from msgraph_beta.generated.models.access_package_answer import AccessPackageAnswer
from msgraph_beta.generated.models.access_package_answer_string import AccessPackageAnswerString
from msgraph_beta.generated.models.access_package_multiple_choice_question import AccessPackageMultipleChoiceQuestion
from msgraph_beta.generated.models.access_package_text_input_question import AccessPackageTextInputQuestion
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = "UserAdd",
	access_package_assignment = AccessPackageAssignment(
		target_id = "46184453-e63b-4f20-86c2-c557ed5d5df9",
		assignment_policy_id = "2264bf65-76ba-417b-a27d-54d291f0cbc8",
		access_package_id = "a914b616-e04e-476b-aa37-91038f0b165b",
	),
	answers = [
		AccessPackageAnswerString(
			odata_type = "#microsoft.graph.accessPackageAnswerString",
			value = "Arizona",
			answered_question = AccessPackageMultipleChoiceQuestion(
				odata_type = "#microsoft.graph.accessPackageMultipleChoiceQuestion",
				id = "A714EC6F-4EE0-4614-BD81-37E0C5ECBBFF",
			),
		),
		AccessPackageAnswerString(
			odata_type = "#microsoft.graph.accessPackageAnswerString",
			value = "Need access to marketing campaign material",
			answered_question = AccessPackageTextInputQuestion(
				odata_type = "#microsoft.graph.accessPackageTextInputQuestion",
				id = "AA615EE9-D9D8-4C03-BE91-BEE37106DEDA",
			),
		),
	],
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_requests.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "7e382d02-4454-436b-b700-59c7dd77f466",
    "requestType": "UserAdd",
    "requestState": "Submitted",
    "requestStatus": "Accepted",
    "isValidationOnly": false,
    "answers": [
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "Arizona",
            "answeredQuestion": {
                "id": "A714EC6F-4EE0-4614-BD81-37E0C5ECBBFF",
                "isRequired": false,
                "text": {
                    "defaultText": "what state are you from?",
                    "localizedTexts": [
                        {
                            "text": "¿De qué estado eres?",
                            "languageCode": "es"
                        }
                    ]
                },
                "@odata.type": "#microsoft.graph.accessPackageMultipleChoiceQuestion",
                "choices": [
                    {
                        "actualValue": "AZ",
                        "displayValue": {
                            "localizedTexts": [
                                {
                                    "text": "Arizona",
                                    "languageCode": "es"
                                }
                            ]
                        }
                    },
                    {
                        "actualValue": "CA",
                        "displayValue": {
                            "localizedTexts": [
                                {
                                    "text": "California",
                                    "languageCode": "es"
                                }
                            ]
                        }
                    },
                    {
                        "actualValue": "OH",
                        "displayValue": {
                            "localizedTexts": [
                                {
                                    "text": "Ohio",
                                    "languageCode": "es"
                                }
                            ]
                        }
                    }
                ],
                "allowsMultipleSelection": false
            }
        },
        {
            "@odata.type": "#microsoft.graph.accessPackageAnswerString",
            "value": "Need access to marketing campaign material",
            "answeredQuestion": {
                "id": "AA615EE9-D9D8-4C03-BE91-BEE37106DEDA",
                "isRequired": false,
                "text": {
                    "defaultText": "Who is your manager?",
                    "localizedTexts": [
                        {
                            "text": "por qué necesita acceso a este paquete",
                            "languageCode": "es"
                        }
                    ]
                },
                "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
                "isSingleLineQuestion": false
            }
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
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentRequests
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
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = "UserAdd",
	AccessPackageAssignment = new AccessPackageAssignment
	{
		AccessPackageId = "a914b616-e04e-476b-aa37-91038f0b165b",
	},
	Justification = "Need access to New Hire access package",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := "UserAdd"
requestBody.SetRequestType(&requestType) 
accessPackageAssignment := graphmodels.NewAccessPackageAssignment()
accessPackageId := "a914b616-e04e-476b-aa37-91038f0b165b"
accessPackageAssignment.SetAccessPackageId(&accessPackageId) 
requestBody.SetAccessPackageAssignment(accessPackageAssignment)
justification := "Need access to New Hire access package"
requestBody.SetJustification(&justification) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType("UserAdd");
AccessPackageAssignment accessPackageAssignment = new AccessPackageAssignment();
accessPackageAssignment.setAccessPackageId("a914b616-e04e-476b-aa37-91038f0b165b");
accessPackageAssignmentRequest.setAccessPackageAssignment(accessPackageAssignment);
accessPackageAssignmentRequest.setJustification("Need access to New Hire access package");
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentRequests().post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentRequests')
	.version('beta')
	.post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType('UserAdd');
$accessPackageAssignment = new AccessPackageAssignment();
$accessPackageAssignment->setAccessPackageId('a914b616-e04e-476b-aa37-91038f0b165b');
$requestBody->setAccessPackageAssignment($accessPackageAssignment);
$requestBody->setJustification('Need access to New Hire access package');

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestType = "UserAdd"
	accessPackageAssignment = @{
		accessPackageId = "a914b616-e04e-476b-aa37-91038f0b165b"
	}
	justification = "Need access to New Hire access package"
}

New-MgBetaEntitlementManagementAccessPackageAssignmentRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph_beta.generated.models.access_package_assignment import AccessPackageAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = "UserAdd",
	access_package_assignment = AccessPackageAssignment(
		access_package_id = "a914b616-e04e-476b-aa37-91038f0b165b",
	),
	justification = "Need access to New Hire access package",
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_requests.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties are returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "813bbc6b-31f5-4cdf-8fed-1ba4284a1e3f",
    "requestType": "UserAdd",
    "requestState": "Submitted",
    "requestStatus": "Accepted",
    "isValidationOnly": false,
    "expirationDateTime": null,
    "justification": "Requested for the new task.",
    "answers": [],
    "schedule": {
        "startDateTime": null,
        "recurrence": null,
        "expiration": {
            "endDateTime": null,
            "duration": null,
            "type": null
        }
    }
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
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentRequests
Content-type: application/json

{
  "requestType": "AdminAdd",
  "accessPackageAssignment":{
     "target": {
        "email": "user@contoso.com"
     },
     "assignmentPolicyId":"2264bf65-76ba-417b-a27d-54d291f0cbc8",
     "accessPackageId":"a914b616-e04e-476b-aa37-91038f0b165b"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = "AdminAdd",
	AccessPackageAssignment = new AccessPackageAssignment
	{
		Target = new AccessPackageSubject
		{
			Email = "user@contoso.com",
		},
		AssignmentPolicyId = "2264bf65-76ba-417b-a27d-54d291f0cbc8",
		AccessPackageId = "a914b616-e04e-476b-aa37-91038f0b165b",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := "AdminAdd"
requestBody.SetRequestType(&requestType) 
accessPackageAssignment := graphmodels.NewAccessPackageAssignment()
target := graphmodels.NewAccessPackageSubject()
email := "user@contoso.com"
target.SetEmail(&email) 
accessPackageAssignment.SetTarget(target)
assignmentPolicyId := "2264bf65-76ba-417b-a27d-54d291f0cbc8"
accessPackageAssignment.SetAssignmentPolicyId(&assignmentPolicyId) 
accessPackageId := "a914b616-e04e-476b-aa37-91038f0b165b"
accessPackageAssignment.SetAccessPackageId(&accessPackageId) 
requestBody.SetAccessPackageAssignment(accessPackageAssignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType("AdminAdd");
AccessPackageAssignment accessPackageAssignment = new AccessPackageAssignment();
AccessPackageSubject target = new AccessPackageSubject();
target.setEmail("user@contoso.com");
accessPackageAssignment.setTarget(target);
accessPackageAssignment.setAssignmentPolicyId("2264bf65-76ba-417b-a27d-54d291f0cbc8");
accessPackageAssignment.setAccessPackageId("a914b616-e04e-476b-aa37-91038f0b165b");
accessPackageAssignmentRequest.setAccessPackageAssignment(accessPackageAssignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentRequests().post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
  requestType: 'AdminAdd',
  accessPackageAssignment: {
     target: {
        email: 'user@contoso.com'
     },
     assignmentPolicyId: '2264bf65-76ba-417b-a27d-54d291f0cbc8',
     accessPackageId: 'a914b616-e04e-476b-aa37-91038f0b165b'
  }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentRequests')
	.version('beta')
	.post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignment;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageSubject;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType('AdminAdd');
$accessPackageAssignment = new AccessPackageAssignment();
$accessPackageAssignmentTarget = new AccessPackageSubject();
$accessPackageAssignmentTarget->setEmail('user@contoso.com');
$accessPackageAssignment->setTarget($accessPackageAssignmentTarget);
$accessPackageAssignment->setAssignmentPolicyId('2264bf65-76ba-417b-a27d-54d291f0cbc8');
$accessPackageAssignment->setAccessPackageId('a914b616-e04e-476b-aa37-91038f0b165b');
$requestBody->setAccessPackageAssignment($accessPackageAssignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestType = "AdminAdd"
	accessPackageAssignment = @{
		target = @{
			email = "user@contoso.com"
		}
		assignmentPolicyId = "2264bf65-76ba-417b-a27d-54d291f0cbc8"
		accessPackageId = "a914b616-e04e-476b-aa37-91038f0b165b"
	}
}

New-MgBetaEntitlementManagementAccessPackageAssignmentRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph_beta.generated.models.access_package_assignment import AccessPackageAssignment
from msgraph_beta.generated.models.access_package_subject import AccessPackageSubject
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = "AdminAdd",
	access_package_assignment = AccessPackageAssignment(
		target = AccessPackageSubject(
			email = "user@contoso.com",
		),
		assignment_policy_id = "2264bf65-76ba-417b-a27d-54d291f0cbc8",
		access_package_id = "a914b616-e04e-476b-aa37-91038f0b165b",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_requests.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "7e382d02-4454-436b-b700-59c7dd77f466",
  "requestType": "AdminAdd",
  "requestState": "Submitted",
  "requestStatus": "Accepted",
  "isValidationOnly": false
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
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentRequests
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.accessPackageAssignmentRequest",
    "id": "7a6ab703-0780-4b37-8445-81f679b2d75c",
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
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new AccessPackageAssignmentRequest
{
	OdataType = "#microsoft.graph.accessPackageAssignmentRequest",
	Id = "7a6ab703-0780-4b37-8445-81f679b2d75c",
	RequestType = "adminUpdate",
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
	AdditionalData = new Dictionary<string, object>
	{
		{
			"assignment" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"id", new UntypedString("44c741c1-2cf4-40db-83b6-e0112f8e5a83")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
id := "7a6ab703-0780-4b37-8445-81f679b2d75c"
requestBody.SetId(&id) 
requestType := "adminUpdate"
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
additionalData := map[string]interface{}{
assignment := graph.New()
id := "44c741c1-2cf4-40db-83b6-e0112f8e5a83"
assignment.SetId(&id) 
	requestBody.SetAssignment(assignment)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setOdataType("#microsoft.graph.accessPackageAssignmentRequest");
accessPackageAssignmentRequest.setId("7a6ab703-0780-4b37-8445-81f679b2d75c");
accessPackageAssignmentRequest.setRequestType("adminUpdate");
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
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 assignment = new ();
assignment.setId("44c741c1-2cf4-40db-83b6-e0112f8e5a83");
additionalData.put("assignment", assignment);
accessPackageAssignmentRequest.setAdditionalData(additionalData);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentRequests().post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
    '@odata.type': '#microsoft.graph.accessPackageAssignmentRequest',
    id: '7a6ab703-0780-4b37-8445-81f679b2d75c',
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

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentRequests')
	.version('beta')
	.post(accessPackageAssignmentRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAnswer;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAnswerString;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageMultipleChoiceQuestion;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageTextInputQuestion;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setOdataType('#microsoft.graph.accessPackageAssignmentRequest');
$requestBody->setId('7a6ab703-0780-4b37-8445-81f679b2d75c');
$requestBody->setRequestType('adminUpdate');
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

$additionalData = [
'assignment' => [
	'id' => '44c741c1-2cf4-40db-83b6-e0112f8e5a83',
],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	"@odata.type" = "#microsoft.graph.accessPackageAssignmentRequest"
	id = "7a6ab703-0780-4b37-8445-81f679b2d75c"
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

New-MgBetaEntitlementManagementAccessPackageAssignmentRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph_beta.generated.models.access_package_answer import AccessPackageAnswer
from msgraph_beta.generated.models.access_package_answer_string import AccessPackageAnswerString
from msgraph_beta.generated.models.access_package_multiple_choice_question import AccessPackageMultipleChoiceQuestion
from msgraph_beta.generated.models.access_package_text_input_question import AccessPackageTextInputQuestion
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	odata_type = "#microsoft.graph.accessPackageAssignmentRequest",
	id = "7a6ab703-0780-4b37-8445-81f679b2d75c",
	request_type = "adminUpdate",
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
	additional_data = {
			"assignment" : {
					"id" : "44c741c1-2cf4-40db-83b6-e0112f8e5a83",
			},
	}
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_requests.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties are returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#accessPackageAssignmentRequests/$entity",
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
