<!-- Source: https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleeligibilityschedulerequests?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create roleEligibilityScheduleRequest

Namespace: microsoft.graph

In PIM, request for a role eligibility for a principal through the [unifiedRoleEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedulerequest?view=graph-rest-1.0) object. This operation allows both admins and eligible users to add, revoke, or extend eligible assignments.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleEligibilitySchedule.ReadWrite.Directory | RoleManagement.ReadWrite.Directory |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleEligibilitySchedule.ReadWrite.Directory | RoleManagement.ReadWrite.Directory |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- For read operations: *Global Reader*, *Security Operator*, *Security Reader*, *Security Administrator*, or *Privileged Role Administrator*
- For write operations: *Privileged Role Administrator*

## HTTP request

```http
POST /roleManagement/directory/roleEligibilityScheduleRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [unifiedRoleEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedulerequest?view=graph-rest-1.0) object.

You can specify the following properties when creating an **unifiedRoleEligibilityScheduleRequest**.

| Property | Type | Description |
| :--- | :--- | :--- |
| action | unifiedRoleScheduleRequestActions | Represents the type of operation on the role eligibility request.The possible values are: `adminAssign`, `adminUpdate`, `adminRemove`, `selfActivate`, `selfDeactivate`, `adminExtend`, `adminRenew`, `selfExtend`, `selfRenew`, `unknownFutureValue`.  <br><br><br>- `adminAssign`: For administrators to assign eligible roles to principals.<br>- `adminRemove`: For administrators to remove eligible roles from principals.<br>- `adminUpdate`: For administrators to change existing role eligibilities.<br>- `adminExtend`: For administrators to extend expiring role eligibilities.<br>- `adminRenew`: For administrators to renew expired eligibilities.<br>- `selfActivate`: For users to activate their assignments.<br>- `selfDeactivate`: For users to deactivate their active assignments.<br>- `selfExtend`: For users to request to extend their expiring assignments.<br>- `SelfRenew`: For users to request to renew their expired assignments. |
| appScopeId | String | Identifier of the app-specific scope when the role eligibility is scoped to an app. The scope of a role eligibility determines the set of resources for which the principal is eligible to access. App scopes are scopes that are defined and understood by this application only. Use `/` for tenant-wide app scopes. Use **directoryScopeId** to limit the scope to particular directory objects, for example, administrative units. Either **directoryScopeId** or **appScopeId** is required. |
| directoryScopeId | String | Identifier of the directory object representing the scope of the role eligibility. The scope of an role eligibility determines the set of resources for which the principal has been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. Use `/` for tenant-wide scope. Use **appScopeId** to limit the scope to an application only. Either **directoryScopeId** or **appScopeId** is required. |
| isValidationOnly | Boolean | Determines whether the call is a validation or an actual call. Only set this property if you want to check whether an activation is subject to additional rules like MFA before actually submitting the request. Optional. |
| justification | String | A message provided by users and administrators when create they create the **unifiedRoleEligibilityScheduleRequest** object.  <br>  <br>Optional for `selfDeactivate` and `adminRemove` actions; might be optional or required for other action types depending on the rules in the policy that's linked to the Microsoft Entra role. For more information, see [Rules in PIM](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview). |
| principalId | String | Identifier of the principal that has been granted the role eligibility. Required. |
| roleDefinitionId | String | Identifier of the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object that is being assigned to the principal. Required. |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | The period of the role eligibility. Optional when **action** is `adminRemove`. The period of eligibility is dependent on the [settings of the Microsoft Entra role](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-list-rules?view=graph-rest-1.0). |
| ticketInfo | [ticketInfo](https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-1.0) | Ticket details linked to the role eligibility request including details of the ticket number and ticket system.  <br>  <br>Optional for `selfDeactivate` and `adminRemove` actions; might be optional or required for other action types depending on the rules in the policy that's linked to the Microsoft Entra role. For more information, see [Rules in PIM](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview). |

## Response

If successful, this method returns a `201 Created` response code and an [unifiedRoleEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleeligibilityschedulerequest?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Admin to assign a role eligibility schedule request

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/roleManagement/directory/roleEligibilityScheduleRequests
Content-Type: application/json

{
    "action": "adminAssign",
    "justification": "Assign Attribute Assignment Admin eligibility to restricted user",
    "roleDefinitionId": "8424c6f0-a189-499e-bbd0-26c1753c96d4",
    "directoryScopeId": "/",
    "principalId": "071cc716-8147-4397-a5ba-b2105951cc0b",
    "scheduleInfo": {
        "startDateTime": "2022-04-10T00:00:00Z",
        "expiration": {
            "type": "afterDateTime",
            "endDateTime": "2024-04-10T00:00:00Z"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleEligibilityScheduleRequest
{
	Action = UnifiedRoleScheduleRequestActions.AdminAssign,
	Justification = "Assign Attribute Assignment Admin eligibility to restricted user",
	RoleDefinitionId = "8424c6f0-a189-499e-bbd0-26c1753c96d4",
	DirectoryScopeId = "/",
	PrincipalId = "071cc716-8147-4397-a5ba-b2105951cc0b",
	ScheduleInfo = new RequestSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2022-04-10T00:00:00Z"),
		Expiration = new ExpirationPattern
		{
			Type = ExpirationPatternType.AfterDateTime,
			EndDateTime = DateTimeOffset.Parse("2024-04-10T00:00:00Z"),
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.RoleEligibilityScheduleRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewUnifiedRoleEligibilityScheduleRequest()
action := graphmodels.ADMINASSIGN_UNIFIEDROLESCHEDULEREQUESTACTIONS 
requestBody.SetAction(&action) 
justification := "Assign Attribute Assignment Admin eligibility to restricted user"
requestBody.SetJustification(&justification) 
roleDefinitionId := "8424c6f0-a189-499e-bbd0-26c1753c96d4"
requestBody.SetRoleDefinitionId(&roleDefinitionId) 
directoryScopeId := "/"
requestBody.SetDirectoryScopeId(&directoryScopeId) 
principalId := "071cc716-8147-4397-a5ba-b2105951cc0b"
requestBody.SetPrincipalId(&principalId) 
scheduleInfo := graphmodels.NewRequestSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2022-04-10T00:00:00Z")
scheduleInfo.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
type := graphmodels.AFTERDATETIME_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
endDateTime , err := time.Parse(time.RFC3339, "2024-04-10T00:00:00Z")
expiration.SetEndDateTime(&endDateTime) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleEligibilityScheduleRequests, err := graphClient.RoleManagement().Directory().RoleEligibilityScheduleRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleEligibilityScheduleRequest unifiedRoleEligibilityScheduleRequest = new UnifiedRoleEligibilityScheduleRequest();
unifiedRoleEligibilityScheduleRequest.setAction(UnifiedRoleScheduleRequestActions.AdminAssign);
unifiedRoleEligibilityScheduleRequest.setJustification("Assign Attribute Assignment Admin eligibility to restricted user");
unifiedRoleEligibilityScheduleRequest.setRoleDefinitionId("8424c6f0-a189-499e-bbd0-26c1753c96d4");
unifiedRoleEligibilityScheduleRequest.setDirectoryScopeId("/");
unifiedRoleEligibilityScheduleRequest.setPrincipalId("071cc716-8147-4397-a5ba-b2105951cc0b");
RequestSchedule scheduleInfo = new RequestSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2022-04-10T00:00:00Z");
scheduleInfo.setStartDateTime(startDateTime);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.AfterDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2024-04-10T00:00:00Z");
expiration.setEndDateTime(endDateTime);
scheduleInfo.setExpiration(expiration);
unifiedRoleEligibilityScheduleRequest.setScheduleInfo(scheduleInfo);
UnifiedRoleEligibilityScheduleRequest result = graphClient.roleManagement().directory().roleEligibilityScheduleRequests().post(unifiedRoleEligibilityScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleEligibilityScheduleRequest = {
    action: 'adminAssign',
    justification: 'Assign Attribute Assignment Admin eligibility to restricted user',
    roleDefinitionId: '8424c6f0-a189-499e-bbd0-26c1753c96d4',
    directoryScopeId: '/',
    principalId: '071cc716-8147-4397-a5ba-b2105951cc0b',
    scheduleInfo: {
        startDateTime: '2022-04-10T00:00:00Z',
        expiration: {
            type: 'afterDateTime',
            endDateTime: '2024-04-10T00:00:00Z'
        }
    }
};

await client.api('/roleManagement/directory/roleEligibilityScheduleRequests')
	.post(unifiedRoleEligibilityScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleEligibilityScheduleRequest;
use Microsoft\Graph\Generated\Models\UnifiedRoleScheduleRequestActions;
use Microsoft\Graph\Generated\Models\RequestSchedule;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleEligibilityScheduleRequest();
$requestBody->setAction(new UnifiedRoleScheduleRequestActions('adminAssign'));
$requestBody->setJustification('Assign Attribute Assignment Admin eligibility to restricted user');
$requestBody->setRoleDefinitionId('8424c6f0-a189-499e-bbd0-26c1753c96d4');
$requestBody->setDirectoryScopeId('/');
$requestBody->setPrincipalId('071cc716-8147-4397-a5ba-b2105951cc0b');
$scheduleInfo = new RequestSchedule();
$scheduleInfo->setStartDateTime(new \DateTime('2022-04-10T00:00:00Z'));
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setType(new ExpirationPatternType('afterDateTime'));
$scheduleInfoExpiration->setEndDateTime(new \DateTime('2024-04-10T00:00:00Z'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);

$result = $graphServiceClient->roleManagement()->directory()->roleEligibilityScheduleRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	action = "adminAssign"
	justification = "Assign Attribute Assignment Admin eligibility to restricted user"
	roleDefinitionId = "8424c6f0-a189-499e-bbd0-26c1753c96d4"
	directoryScopeId = "/"
	principalId = "071cc716-8147-4397-a5ba-b2105951cc0b"
	scheduleInfo = @{
		startDateTime = [System.DateTime]::Parse("2022-04-10T00:00:00Z")
		expiration = @{
			type = "afterDateTime"
			endDateTime = [System.DateTime]::Parse("2024-04-10T00:00:00Z")
		}
	}
}

New-MgRoleManagementDirectoryRoleEligibilityScheduleRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_eligibility_schedule_request import UnifiedRoleEligibilityScheduleRequest
from msgraph.generated.models.unified_role_schedule_request_actions import UnifiedRoleScheduleRequestActions
from msgraph.generated.models.request_schedule import RequestSchedule
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleEligibilityScheduleRequest(
	action = UnifiedRoleScheduleRequestActions.AdminAssign,
	justification = "Assign Attribute Assignment Admin eligibility to restricted user",
	role_definition_id = "8424c6f0-a189-499e-bbd0-26c1753c96d4",
	directory_scope_id = "/",
	principal_id = "071cc716-8147-4397-a5ba-b2105951cc0b",
	schedule_info = RequestSchedule(
		start_date_time = "2022-04-10T00:00:00Z",
		expiration = ExpirationPattern(
			type = ExpirationPatternType.AfterDateTime,
			end_date_time = "2024-04-10T00:00:00Z",
		),
	),
)

result = await graph_client.role_management.directory.role_eligibility_schedule_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#roleManagement/directory/roleEligibilityScheduleRequests/$entity",
    "id": "50877283-9d40-433c-bab8-7986dc10458a",
    "status": "Provisioned",
    "createdDateTime": "2022-04-12T09:05:39.7594064Z",
    "completedDateTime": "2022-04-12T09:05:41.8532931Z",
    "approvalId": null,
    "customData": null,
    "action": "adminAssign",
    "principalId": "071cc716-8147-4397-a5ba-b2105951cc0b",
    "roleDefinitionId": "8424c6f0-a189-499e-bbd0-26c1753c96d4",
    "directoryScopeId": "/",
    "appScopeId": null,
    "isValidationOnly": false,
    "targetScheduleId": "50877283-9d40-433c-bab8-7986dc10458a",
    "justification": "Assign Attribute Assignment Admin eligibility to restricted user",
    "createdBy": {
        "application": null,
        "device": null,
        "user": {
            "displayName": null,
            "id": "3fbd929d-8c56-4462-851e-0eb9a7b3a2a5"
        }
    },
    "scheduleInfo": {
        "startDateTime": "2022-04-12T09:05:41.8532931Z",
        "recurrence": null,
        "expiration": {
            "type": "afterDateTime",
            "endDateTime": "2024-04-10T00:00:00Z",
            "duration": null
        }
    },
    "ticketInfo": {
        "ticketNumber": null,
        "ticketSystem": null
    }
}
```

### Example 2: Admin to remove an existing role eligibility schedule request

In the following request, the admin creates a request to revoke the eligibility of a principal with ID `071cc716-8147-4397-a5ba-b2105951cc0b` to a role with ID `8424c6f0-a189-499e-bbd0-26c1753c96d4`.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/roleManagement/directory/roleEligibilityScheduleRequests
Content-Type: application/json

{
    "action": "adminRemove",
    "roleDefinitionId": "8424c6f0-a189-499e-bbd0-26c1753c96d4",
    "directoryScopeId": "/",
    "principalId": "071cc716-8147-4397-a5ba-b2105951cc0b"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleEligibilityScheduleRequest
{
	Action = UnifiedRoleScheduleRequestActions.AdminRemove,
	RoleDefinitionId = "8424c6f0-a189-499e-bbd0-26c1753c96d4",
	DirectoryScopeId = "/",
	PrincipalId = "071cc716-8147-4397-a5ba-b2105951cc0b",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.RoleEligibilityScheduleRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewUnifiedRoleEligibilityScheduleRequest()
action := graphmodels.ADMINREMOVE_UNIFIEDROLESCHEDULEREQUESTACTIONS 
requestBody.SetAction(&action) 
roleDefinitionId := "8424c6f0-a189-499e-bbd0-26c1753c96d4"
requestBody.SetRoleDefinitionId(&roleDefinitionId) 
directoryScopeId := "/"
requestBody.SetDirectoryScopeId(&directoryScopeId) 
principalId := "071cc716-8147-4397-a5ba-b2105951cc0b"
requestBody.SetPrincipalId(&principalId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleEligibilityScheduleRequests, err := graphClient.RoleManagement().Directory().RoleEligibilityScheduleRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleEligibilityScheduleRequest unifiedRoleEligibilityScheduleRequest = new UnifiedRoleEligibilityScheduleRequest();
unifiedRoleEligibilityScheduleRequest.setAction(UnifiedRoleScheduleRequestActions.AdminRemove);
unifiedRoleEligibilityScheduleRequest.setRoleDefinitionId("8424c6f0-a189-499e-bbd0-26c1753c96d4");
unifiedRoleEligibilityScheduleRequest.setDirectoryScopeId("/");
unifiedRoleEligibilityScheduleRequest.setPrincipalId("071cc716-8147-4397-a5ba-b2105951cc0b");
UnifiedRoleEligibilityScheduleRequest result = graphClient.roleManagement().directory().roleEligibilityScheduleRequests().post(unifiedRoleEligibilityScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleEligibilityScheduleRequest = {
    action: 'adminRemove',
    roleDefinitionId: '8424c6f0-a189-499e-bbd0-26c1753c96d4',
    directoryScopeId: '/',
    principalId: '071cc716-8147-4397-a5ba-b2105951cc0b'
};

await client.api('/roleManagement/directory/roleEligibilityScheduleRequests')
	.post(unifiedRoleEligibilityScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleEligibilityScheduleRequest;
use Microsoft\Graph\Generated\Models\UnifiedRoleScheduleRequestActions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleEligibilityScheduleRequest();
$requestBody->setAction(new UnifiedRoleScheduleRequestActions('adminRemove'));
$requestBody->setRoleDefinitionId('8424c6f0-a189-499e-bbd0-26c1753c96d4');
$requestBody->setDirectoryScopeId('/');
$requestBody->setPrincipalId('071cc716-8147-4397-a5ba-b2105951cc0b');

$result = $graphServiceClient->roleManagement()->directory()->roleEligibilityScheduleRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	action = "adminRemove"
	roleDefinitionId = "8424c6f0-a189-499e-bbd0-26c1753c96d4"
	directoryScopeId = "/"
	principalId = "071cc716-8147-4397-a5ba-b2105951cc0b"
}

New-MgRoleManagementDirectoryRoleEligibilityScheduleRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_eligibility_schedule_request import UnifiedRoleEligibilityScheduleRequest
from msgraph.generated.models.unified_role_schedule_request_actions import UnifiedRoleScheduleRequestActions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleEligibilityScheduleRequest(
	action = UnifiedRoleScheduleRequestActions.AdminRemove,
	role_definition_id = "8424c6f0-a189-499e-bbd0-26c1753c96d4",
	directory_scope_id = "/",
	principal_id = "071cc716-8147-4397-a5ba-b2105951cc0b",
)

result = await graph_client.role_management.directory.role_eligibility_schedule_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The response object shows a previous role eligibility for a principal is `Revoked`. The principal will no longer see their previously eligible role.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#roleManagement/directory/roleEligibilityScheduleRequests/$entity",
    "id": "f341269e-c926-41fa-a905-cef3b01b2a67",
    "status": "Revoked",
    "createdDateTime": "2022-04-12T09:12:15.6859992Z",
    "completedDateTime": null,
    "approvalId": null,
    "customData": null,
    "action": "adminRemove",
    "principalId": "071cc716-8147-4397-a5ba-b2105951cc0b",
    "roleDefinitionId": "8424c6f0-a189-499e-bbd0-26c1753c96d4",
    "directoryScopeId": "/",
    "appScopeId": null,
    "isValidationOnly": false,
    "targetScheduleId": null,
    "justification": null,
    "scheduleInfo": null,
    "createdBy": {
        "application": null,
        "device": null,
        "user": {
            "displayName": null,
            "id": "3fbd929d-8c56-4462-851e-0eb9a7b3a2a5"
        }
    },
    "ticketInfo": {
        "ticketNumber": null,
        "ticketSystem": null
    }
}
```
