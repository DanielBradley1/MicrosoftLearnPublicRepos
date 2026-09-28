<!-- Source: https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignmentschedulerequests?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create roleAssignmentScheduleRequests

Namespace: microsoft.graph

In PIM, carry out the following operations through the [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) object:

- Request active and persistent role assignments for a principal, with or without expiry dates.
- Activate, deactivate, extend, or renew an eligible role assignment for a principal.

To call this API to update, renew, and extend assignments for yourself, you must have multifactor authentication \(MFA\) enforced, and running the query in a session in which they were challenged for MFA. See [Enable per-user Microsoft Entra multifactor authentication to secure sign-in events](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-userstates).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleAssignmentSchedule.ReadWrite.Directory | RoleAssignmentSchedule.Remove.Directory, RoleEligibilitySchedule.Remove.Directory, RoleManagement.ReadWrite.Directory |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleAssignmentSchedule.ReadWrite.Directory | RoleManagement.ReadWrite.Directory, RoleAssignmentSchedule.Remove.Directory, RoleEligibilitySchedule.Remove.Directory |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- For read operations: *Global Reader*, *Security Operator*, *Security Reader*, *Security Administrator*, or *Privileged Role Administrator*
- For write operations: *Privileged Role Administrator*

## HTTP request

```http
POST /roleManagement/directory/roleAssignmentScheduleRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) object.

You can specify the following properties when creating an **unifiedRoleAssignmentScheduleRequest**.

| Property | Type | Description |
| :--- | :--- | :--- |
| action | unifiedRoleScheduleRequestActions | Represents the type of the operation on the role assignment request. The possible values are: `adminAssign`, `adminUpdate`, `adminRemove`, `selfActivate`, `selfDeactivate`, `adminExtend`, `adminRenew`, `selfExtend`, `selfRenew`, `unknownFutureValue`.  <br><br><br>- `adminAssign`: For administrators to assign roles to users or groups.<br>- `adminRemove`: For administrators to remove users or groups from roles.<br>- `adminUpdate`: For administrators to change existing role assignments.<br>- `adminExtend`: For administrators to extend expiring assignments.<br>- `adminRenew`: For administrators to renew expired assignments.<br>- `selfActivate`: For users to activate their assignments.<br>- `selfDeactivate`: For users to deactivate their active assignments.<br>- `selfExtend`: For users to request to extend their expiring assignments.<br>- `selfRenew`: For users to request to renew their expired assignments. |
| customData | String | Free text field to define any custom data for the request. Optional. |
| principalId | String | Identifier of the principal that has been granted the assignment. Required. |
| roleDefinitionId | String | Identifier of the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object that is being assigned. Required. |
| directoryScopeId | String | Identifier of the directory object representing the scope of the assignment. The scope of an assignment determines the set of resources for which the principal has been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. Use `/` for tenant-wide scope. Use **appScopeId** to limit the scope to an application only. Either **directoryScopeId** or **appScopeId** is required. |
| appScopeId | String | Identifier of the app-specific scope when the assignment is scoped to an app. The scope of an assignment determines the set of resources for which the principal has been granted access. App scopes are scopes that are defined and understood by this application only. Use `/` for tenant-wide app scopes. Use **directoryScopeId** to limit the scope to particular directory objects, for example, administrative units. Either **directoryScopeId** or **appScopeId** is required. |
| justification | String | A message provided by users and administrators when create they create the **unifiedRoleAssignmentScheduleRequest** object.  <br>  <br>Optional for `selfDeactivate` and `adminRemove` actions; might be optional or required for other action types depending on the rules in the policy that's linked to the Microsoft Entra role. For more information, see [Rules in PIM](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview). |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | The period of the role assignment request. Recurring schedules are currently unsupported. Required. |
| ticketInfo | [ticketInfo](https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-1.0) | Ticket details linked to the role assignment request including details of the ticket number and ticket system.  <br>  <br>Optional for `selfDeactivate` and `adminRemove` actions; might be optional or required for other action types depending on the rules in the policy that's linked to the Microsoft Entra role. For more information, see [Rules in PIM](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview). |

## Response

If successful, this method returns a `201 Created` response code and an [unifiedRoleAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentschedulerequest?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Admin assigning a directory role to a principal

In the following request, the admin creates a request to assign a role identified by `fdd7a751-b60b-444a-984c-02652fe8fa1c` to a principal identified by ID `071cc716-8147-4397-a5ba-b2105951cc0b`. The scope of their role is all directory objects in the tenant and the assignment is permanent.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
POST https://graph.microsoft.com/v1.0/roleManagement/directory/roleAssignmentScheduleRequests
Content-Type: application/json

{
    "action": "adminAssign",
    "justification": "Assign Groups Admin to IT Helpdesk group",
    "roleDefinitionId": "fdd7a751-b60b-444a-984c-02652fe8fa1c",
    "directoryScopeId": "/",
    "principalId": "071cc716-8147-4397-a5ba-b2105951cc0b",
    "scheduleInfo": {
        "startDateTime": "2022-04-10T00:00:00Z",
        "expiration": {
            "type": "NoExpiration"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleAssignmentScheduleRequest
{
	Action = UnifiedRoleScheduleRequestActions.AdminAssign,
	Justification = "Assign Groups Admin to IT Helpdesk group",
	RoleDefinitionId = "fdd7a751-b60b-444a-984c-02652fe8fa1c",
	DirectoryScopeId = "/",
	PrincipalId = "071cc716-8147-4397-a5ba-b2105951cc0b",
	ScheduleInfo = new RequestSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2022-04-10T00:00:00Z"),
		Expiration = new ExpirationPattern
		{
			Type = ExpirationPatternType.NoExpiration,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.RoleAssignmentScheduleRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewUnifiedRoleAssignmentScheduleRequest()
action := graphmodels.ADMINASSIGN_UNIFIEDROLESCHEDULEREQUESTACTIONS 
requestBody.SetAction(&action) 
justification := "Assign Groups Admin to IT Helpdesk group"
requestBody.SetJustification(&justification) 
roleDefinitionId := "fdd7a751-b60b-444a-984c-02652fe8fa1c"
requestBody.SetRoleDefinitionId(&roleDefinitionId) 
directoryScopeId := "/"
requestBody.SetDirectoryScopeId(&directoryScopeId) 
principalId := "071cc716-8147-4397-a5ba-b2105951cc0b"
requestBody.SetPrincipalId(&principalId) 
scheduleInfo := graphmodels.NewRequestSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2022-04-10T00:00:00Z")
scheduleInfo.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
type := graphmodels.NOEXPIRATION_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleAssignmentScheduleRequests, err := graphClient.RoleManagement().Directory().RoleAssignmentScheduleRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleAssignmentScheduleRequest unifiedRoleAssignmentScheduleRequest = new UnifiedRoleAssignmentScheduleRequest();
unifiedRoleAssignmentScheduleRequest.setAction(UnifiedRoleScheduleRequestActions.AdminAssign);
unifiedRoleAssignmentScheduleRequest.setJustification("Assign Groups Admin to IT Helpdesk group");
unifiedRoleAssignmentScheduleRequest.setRoleDefinitionId("fdd7a751-b60b-444a-984c-02652fe8fa1c");
unifiedRoleAssignmentScheduleRequest.setDirectoryScopeId("/");
unifiedRoleAssignmentScheduleRequest.setPrincipalId("071cc716-8147-4397-a5ba-b2105951cc0b");
RequestSchedule scheduleInfo = new RequestSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2022-04-10T00:00:00Z");
scheduleInfo.setStartDateTime(startDateTime);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.NoExpiration);
scheduleInfo.setExpiration(expiration);
unifiedRoleAssignmentScheduleRequest.setScheduleInfo(scheduleInfo);
UnifiedRoleAssignmentScheduleRequest result = graphClient.roleManagement().directory().roleAssignmentScheduleRequests().post(unifiedRoleAssignmentScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleAssignmentScheduleRequest = {
    action: 'adminAssign',
    justification: 'Assign Groups Admin to IT Helpdesk group',
    roleDefinitionId: 'fdd7a751-b60b-444a-984c-02652fe8fa1c',
    directoryScopeId: '/',
    principalId: '071cc716-8147-4397-a5ba-b2105951cc0b',
    scheduleInfo: {
        startDateTime: '2022-04-10T00:00:00Z',
        expiration: {
            type: 'NoExpiration'
        }
    }
};

await client.api('/roleManagement/directory/roleAssignmentScheduleRequests')
	.post(unifiedRoleAssignmentScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleAssignmentScheduleRequest;
use Microsoft\Graph\Generated\Models\UnifiedRoleScheduleRequestActions;
use Microsoft\Graph\Generated\Models\RequestSchedule;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleAssignmentScheduleRequest();
$requestBody->setAction(new UnifiedRoleScheduleRequestActions('adminAssign'));
$requestBody->setJustification('Assign Groups Admin to IT Helpdesk group');
$requestBody->setRoleDefinitionId('fdd7a751-b60b-444a-984c-02652fe8fa1c');
$requestBody->setDirectoryScopeId('/');
$requestBody->setPrincipalId('071cc716-8147-4397-a5ba-b2105951cc0b');
$scheduleInfo = new RequestSchedule();
$scheduleInfo->setStartDateTime(new \DateTime('2022-04-10T00:00:00Z'));
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setType(new ExpirationPatternType('noExpiration'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);

$result = $graphServiceClient->roleManagement()->directory()->roleAssignmentScheduleRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	action = "adminAssign"
	justification = "Assign Groups Admin to IT Helpdesk group"
	roleDefinitionId = "fdd7a751-b60b-444a-984c-02652fe8fa1c"
	directoryScopeId = "/"
	principalId = "071cc716-8147-4397-a5ba-b2105951cc0b"
	scheduleInfo = @{
		startDateTime = [System.DateTime]::Parse("2022-04-10T00:00:00Z")
		expiration = @{
			type = "NoExpiration"
		}
	}
}

New-MgRoleManagementDirectoryRoleAssignmentScheduleRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_assignment_schedule_request import UnifiedRoleAssignmentScheduleRequest
from msgraph.generated.models.unified_role_schedule_request_actions import UnifiedRoleScheduleRequestActions
from msgraph.generated.models.request_schedule import RequestSchedule
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleAssignmentScheduleRequest(
	action = UnifiedRoleScheduleRequestActions.AdminAssign,
	justification = "Assign Groups Admin to IT Helpdesk group",
	role_definition_id = "fdd7a751-b60b-444a-984c-02652fe8fa1c",
	directory_scope_id = "/",
	principal_id = "071cc716-8147-4397-a5ba-b2105951cc0b",
	schedule_info = RequestSchedule(
		start_date_time = "2022-04-10T00:00:00Z",
		expiration = ExpirationPattern(
			type = ExpirationPatternType.NoExpiration,
		),
	),
)

result = await graph_client.role_management.directory.role_assignment_schedule_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#roleManagement/directory/roleAssignmentScheduleRequests/$entity",
    "id": "95c690fb-3eb3-4942-a03f-4524aed6f31e",
    "status": "Provisioned",
    "createdDateTime": "2022-04-11T11:50:03.9014347Z",
    "completedDateTime": "2022-04-11T11:50:05.9999343Z",
    "approvalId": null,
    "customData": null,
    "action": "adminAssign",
    "principalId": "071cc716-8147-4397-a5ba-b2105951cc0b",
    "roleDefinitionId": "fdd7a751-b60b-444a-984c-02652fe8fa1c",
    "directoryScopeId": "/",
    "appScopeId": null,
    "isValidationOnly": false,
    "targetScheduleId": "95c690fb-3eb3-4942-a03f-4524aed6f31e",
    "justification": "Assign Groups Admin to IT Helpdesk group",
    "createdBy": {
        "application": null,
        "device": null,
        "user": {
            "displayName": null,
            "id": "3fbd929d-8c56-4462-851e-0eb9a7b3a2a5"
        }
    },
    "scheduleInfo": {
        "startDateTime": "2022-04-11T11:50:05.9999343Z",
        "recurrence": null,
        "expiration": {
            "type": "noExpiration",
            "endDateTime": null,
            "duration": null
        }
    },
    "ticketInfo": {
        "ticketNumber": null,
        "ticketSystem": null
    }
}
```

### Example 2: User activating their eligible role

#### Request

In the following request, a user identified by **principalId** `071cc716-8147-4397-a5ba-b2105951cc0b` activates their own *eligible role* to a Microsoft Entra role identified by ID `8424c6f0-a189-499e-bbd0-26c1753c96d4`. The scope of their role is all directory objects in the tenant and the assignment is for five hours. To run this request, the calling user must have multifactor authentication \(MFA\) enforced, and running the query in a session in which they were challenged for MFA.

To retrieve the details of their eligibility requests and identify the eligibility to activate, the user will call the [unifiedRoleEligibilitySchedule: filterByCurrentUser](https://learn.microsoft.com/en-us/graph/api/unifiedroleeligibilityschedule-filterbycurrentuser?view=graph-rest-1.0) API.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
POST https://graph.microsoft.com/v1.0/roleManagement/directory/roleAssignmentScheduleRequests/
Content-Type: application/json

{
    "action": "selfActivate",
    "principalId": "071cc716-8147-4397-a5ba-b2105951cc0b",
    "roleDefinitionId": "8424c6f0-a189-499e-bbd0-26c1753c96d4",
    "directoryScopeId": "/",
    "justification": "I need access to the Attribute Administrator role to manage attributes to be assigned to restricted AUs",
    "scheduleInfo": {
        "startDateTime": "2022-04-14T00:00:00.000Z",
        "expiration": {
            "type": "AfterDuration",
            "duration": "PT5H"
        }
    },
    "ticketInfo": {
        "ticketNumber": "CONTOSO:Normal-67890",
        "ticketSystem": "MS Project"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleAssignmentScheduleRequest
{
	Action = UnifiedRoleScheduleRequestActions.SelfActivate,
	PrincipalId = "071cc716-8147-4397-a5ba-b2105951cc0b",
	RoleDefinitionId = "8424c6f0-a189-499e-bbd0-26c1753c96d4",
	DirectoryScopeId = "/",
	Justification = "I need access to the Attribute Administrator role to manage attributes to be assigned to restricted AUs",
	ScheduleInfo = new RequestSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2022-04-14T00:00:00.000Z"),
		Expiration = new ExpirationPattern
		{
			Type = ExpirationPatternType.AfterDuration,
			Duration = TimeSpan.Parse("PT5H"),
		},
	},
	TicketInfo = new TicketInfo
	{
		TicketNumber = "CONTOSO:Normal-67890",
		TicketSystem = "MS Project",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.RoleAssignmentScheduleRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewUnifiedRoleAssignmentScheduleRequest()
action := graphmodels.SELFACTIVATE_UNIFIEDROLESCHEDULEREQUESTACTIONS 
requestBody.SetAction(&action) 
principalId := "071cc716-8147-4397-a5ba-b2105951cc0b"
requestBody.SetPrincipalId(&principalId) 
roleDefinitionId := "8424c6f0-a189-499e-bbd0-26c1753c96d4"
requestBody.SetRoleDefinitionId(&roleDefinitionId) 
directoryScopeId := "/"
requestBody.SetDirectoryScopeId(&directoryScopeId) 
justification := "I need access to the Attribute Administrator role to manage attributes to be assigned to restricted AUs"
requestBody.SetJustification(&justification) 
scheduleInfo := graphmodels.NewRequestSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2022-04-14T00:00:00.000Z")
scheduleInfo.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
type := graphmodels.AFTERDURATION_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
duration , err := abstractions.ParseISODuration("PT5H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)
ticketInfo := graphmodels.NewTicketInfo()
ticketNumber := "CONTOSO:Normal-67890"
ticketInfo.SetTicketNumber(&ticketNumber) 
ticketSystem := "MS Project"
ticketInfo.SetTicketSystem(&ticketSystem) 
requestBody.SetTicketInfo(ticketInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleAssignmentScheduleRequests, err := graphClient.RoleManagement().Directory().RoleAssignmentScheduleRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleAssignmentScheduleRequest unifiedRoleAssignmentScheduleRequest = new UnifiedRoleAssignmentScheduleRequest();
unifiedRoleAssignmentScheduleRequest.setAction(UnifiedRoleScheduleRequestActions.SelfActivate);
unifiedRoleAssignmentScheduleRequest.setPrincipalId("071cc716-8147-4397-a5ba-b2105951cc0b");
unifiedRoleAssignmentScheduleRequest.setRoleDefinitionId("8424c6f0-a189-499e-bbd0-26c1753c96d4");
unifiedRoleAssignmentScheduleRequest.setDirectoryScopeId("/");
unifiedRoleAssignmentScheduleRequest.setJustification("I need access to the Attribute Administrator role to manage attributes to be assigned to restricted AUs");
RequestSchedule scheduleInfo = new RequestSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2022-04-14T00:00:00.000Z");
scheduleInfo.setStartDateTime(startDateTime);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.AfterDuration);
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT5H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
unifiedRoleAssignmentScheduleRequest.setScheduleInfo(scheduleInfo);
TicketInfo ticketInfo = new TicketInfo();
ticketInfo.setTicketNumber("CONTOSO:Normal-67890");
ticketInfo.setTicketSystem("MS Project");
unifiedRoleAssignmentScheduleRequest.setTicketInfo(ticketInfo);
UnifiedRoleAssignmentScheduleRequest result = graphClient.roleManagement().directory().roleAssignmentScheduleRequests().post(unifiedRoleAssignmentScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleAssignmentScheduleRequest = {
    action: 'selfActivate',
    principalId: '071cc716-8147-4397-a5ba-b2105951cc0b',
    roleDefinitionId: '8424c6f0-a189-499e-bbd0-26c1753c96d4',
    directoryScopeId: '/',
    justification: 'I need access to the Attribute Administrator role to manage attributes to be assigned to restricted AUs',
    scheduleInfo: {
        startDateTime: '2022-04-14T00:00:00.000Z',
        expiration: {
            type: 'AfterDuration',
            duration: 'PT5H'
        }
    },
    ticketInfo: {
        ticketNumber: 'CONTOSO:Normal-67890',
        ticketSystem: 'MS Project'
    }
};

await client.api('/roleManagement/directory/roleAssignmentScheduleRequests/')
	.post(unifiedRoleAssignmentScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleAssignmentScheduleRequest;
use Microsoft\Graph\Generated\Models\UnifiedRoleScheduleRequestActions;
use Microsoft\Graph\Generated\Models\RequestSchedule;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;
use Microsoft\Graph\Generated\Models\TicketInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleAssignmentScheduleRequest();
$requestBody->setAction(new UnifiedRoleScheduleRequestActions('selfActivate'));
$requestBody->setPrincipalId('071cc716-8147-4397-a5ba-b2105951cc0b');
$requestBody->setRoleDefinitionId('8424c6f0-a189-499e-bbd0-26c1753c96d4');
$requestBody->setDirectoryScopeId('/');
$requestBody->setJustification('I need access to the Attribute Administrator role to manage attributes to be assigned to restricted AUs');
$scheduleInfo = new RequestSchedule();
$scheduleInfo->setStartDateTime(new \DateTime('2022-04-14T00:00:00.000Z'));
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setType(new ExpirationPatternType('afterDuration'));
$scheduleInfoExpiration->setDuration(new \DateInterval('PT5H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);
$ticketInfo = new TicketInfo();
$ticketInfo->setTicketNumber('CONTOSO:Normal-67890');
$ticketInfo->setTicketSystem('MS Project');
$requestBody->setTicketInfo($ticketInfo);

$result = $graphServiceClient->roleManagement()->directory()->roleAssignmentScheduleRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	action = "selfActivate"
	principalId = "071cc716-8147-4397-a5ba-b2105951cc0b"
	roleDefinitionId = "8424c6f0-a189-499e-bbd0-26c1753c96d4"
	directoryScopeId = "/"
	justification = "I need access to the Attribute Administrator role to manage attributes to be assigned to restricted AUs"
	scheduleInfo = @{
		startDateTime = [System.DateTime]::Parse("2022-04-14T00:00:00.000Z")
		expiration = @{
			type = "AfterDuration"
			duration = "PT5H"
		}
	}
	ticketInfo = @{
		ticketNumber = "CONTOSO:Normal-67890"
		ticketSystem = "MS Project"
	}
}

New-MgRoleManagementDirectoryRoleAssignmentScheduleRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_assignment_schedule_request import UnifiedRoleAssignmentScheduleRequest
from msgraph.generated.models.unified_role_schedule_request_actions import UnifiedRoleScheduleRequestActions
from msgraph.generated.models.request_schedule import RequestSchedule
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
from msgraph.generated.models.ticket_info import TicketInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleAssignmentScheduleRequest(
	action = UnifiedRoleScheduleRequestActions.SelfActivate,
	principal_id = "071cc716-8147-4397-a5ba-b2105951cc0b",
	role_definition_id = "8424c6f0-a189-499e-bbd0-26c1753c96d4",
	directory_scope_id = "/",
	justification = "I need access to the Attribute Administrator role to manage attributes to be assigned to restricted AUs",
	schedule_info = RequestSchedule(
		start_date_time = "2022-04-14T00:00:00.000Z",
		expiration = ExpirationPattern(
			type = ExpirationPatternType.AfterDuration,
			duration = "PT5H",
		),
	),
	ticket_info = TicketInfo(
		ticket_number = "CONTOSO:Normal-67890",
		ticket_system = "MS Project",
	),
)

result = await graph_client.role_management.directory.role_assignment_schedule_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#roleManagement/directory/roleAssignmentScheduleRequests/$entity",
    "id": "911bab8a-6912-4de2-9dc0-2648ede7dd6d",
    "status": "Granted",
    "createdDateTime": "2022-04-13T08:52:32.6485851Z",
    "completedDateTime": "2022-04-14T00:00:00Z",
    "approvalId": null,
    "customData": null,
    "action": "selfActivate",
    "principalId": "071cc716-8147-4397-a5ba-b2105951cc0b",
    "roleDefinitionId": "8424c6f0-a189-499e-bbd0-26c1753c96d4",
    "directoryScopeId": "/",
    "appScopeId": null,
    "isValidationOnly": false,
    "targetScheduleId": "911bab8a-6912-4de2-9dc0-2648ede7dd6d",
    "justification": "I need access to the Attribute Administrator role to manage attributes to be assigned to restricted AUs",
    "createdBy": {
        "application": null,
        "device": null,
        "user": {
            "displayName": null,
            "id": "071cc716-8147-4397-a5ba-b2105951cc0b"
        }
    },
    "scheduleInfo": {
        "startDateTime": "2022-04-14T00:00:00Z",
        "recurrence": null,
        "expiration": {
            "type": "afterDuration",
            "endDateTime": null,
            "duration": "PT5H"
        }
    },
    "ticketInfo": {
        "ticketNumber": "CONTOSO:Normal-67890",
        "ticketSystem": "MS Project"
    }
}
```
