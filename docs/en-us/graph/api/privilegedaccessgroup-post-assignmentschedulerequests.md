<!-- Source: https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-post-assignmentschedulerequests?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create assignmentScheduleRequest

Namespace: microsoft.graph

Create a new [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrivilegedAssignmentSchedule.ReadWrite.AzureADGroup | PrivilegedAssignmentSchedule.Remove.AzureADGroup |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PrivilegedAssignmentSchedule.ReadWrite.AzureADGroup | PrivilegedAssignmentSchedule.Remove.AzureADGroup |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- For role-assignable groups: *Privileged Role Administrator*
- For non-role-assignable groups: *Directory Writer*, *Groups Administrator*, *Identity Governance Administrator*, or *User Administrator*

The role assignments for the calling user should be scoped at the directory level.

Other roles with permissions to manage groups \(such as Exchange Administrators for non-role-assignable Microsoft 365 groups\) and administrators with assignments scoped at administrative unit level can manage groups through groups API and override changes made in Microsoft Entra PIM through PIM for Groups APIs.

## HTTP request

```http
POST /identityGovernance/privilegedAccess/group/assignmentScheduleRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) object.

You can specify the following properties when creating a **privilegedAccessGroupAssignmentScheduleRequest**.

| Property | Type | Description |
| :--- | :--- | :--- |
| accessId | privilegedAccessGroupRelationships | The identifier of the membership or ownership assignment relationship to the group. The possible values are: `owner`, `member`. Required. |
| action | String | Represents the type of the operation on the group membership or ownership assignment request. The possible values are: `adminAssign`, `adminUpdate`, `adminRemove`, `selfActivate`, `selfDeactivate`, `adminExtend`, `adminRenew`.  <br><br><br>- `adminAssign`: For administrators to assign group membership or ownership to principals.<br>- `adminRemove`: For administrators to remove principals from group membership or ownership.<br>- `adminUpdate`: For administrators to change existing group membership or ownership assignments.<br>- `adminExtend`: For administrators to extend expiring assignments.<br>- `adminRenew`: For administrators to renew expired assignments.<br>- `selfActivate`: For principals to activate their assignments.<br>- `selfDeactivate`: For principals to deactivate their active assignments.<br><br>Required. |
| customData | String | Free text field to define any custom data for the request. Optional. |
| groupId | String | The identifier of the group representing the scope of the membership or ownership assignment through PIM for Groups. Required. |
| justification | String | A message provided by users and administrators when they create the **privilegedAccessGroupAssignmentScheduleRequest** object. Optional. |
| principalId | String | The identifier of the principal whose membership or ownership assignment is granted through PIM for Groups. Required. |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | The period of the group membership or ownership assignment for PIM for Groups. Recurring schedules are currently unsupported. Required. |
| ticketInfo | [ticketInfo](https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-1.0) | Ticket details linked to the group membership or ownership assignment request including details of the ticket number and ticket system. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [privilegedAccessGroupAssignmentScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupassignmentschedulerequest?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create an assignment schedule request

The following request creates an assignment schedule request to assign a principal active membership to the specified group. The active membership expires after two hours.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/privilegedAccess/group/assignmentScheduleRequests
Content-Type: application/json

{
  "accessId": "member", 
  "principalId": "3cce9d87-3986-4f19-8335-7ed075408ca2", 
  "groupId": "68e55cce-cf7e-4a2d-9046-3e4e75c4bfa7", 
  "action": "adminAssign", 
  "scheduleInfo": { 
    "startDateTime": "2022-12-08T07:43:00.000Z", 
    "expiration": { 
      "type": "afterDuration", 
      "duration": "PT2H" 
    } 
  }, 
  "justification": "Assign active member access."
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PrivilegedAccessGroupAssignmentScheduleRequest
{
	AccessId = PrivilegedAccessGroupRelationships.Member,
	PrincipalId = "3cce9d87-3986-4f19-8335-7ed075408ca2",
	GroupId = "68e55cce-cf7e-4a2d-9046-3e4e75c4bfa7",
	Action = ScheduleRequestActions.AdminAssign,
	ScheduleInfo = new RequestSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2022-12-08T07:43:00.000Z"),
		Expiration = new ExpirationPattern
		{
			Type = ExpirationPatternType.AfterDuration,
			Duration = TimeSpan.Parse("PT2H"),
		},
	},
	Justification = "Assign active member access.",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PrivilegedAccess.Group.AssignmentScheduleRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewPrivilegedAccessGroupAssignmentScheduleRequest()
accessId := graphmodels.MEMBER_PRIVILEGEDACCESSGROUPRELATIONSHIPS 
requestBody.SetAccessId(&accessId) 
principalId := "3cce9d87-3986-4f19-8335-7ed075408ca2"
requestBody.SetPrincipalId(&principalId) 
groupId := "68e55cce-cf7e-4a2d-9046-3e4e75c4bfa7"
requestBody.SetGroupId(&groupId) 
action := graphmodels.ADMINASSIGN_SCHEDULEREQUESTACTIONS 
requestBody.SetAction(&action) 
scheduleInfo := graphmodels.NewRequestSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2022-12-08T07:43:00.000Z")
scheduleInfo.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
type := graphmodels.AFTERDURATION_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
duration , err := abstractions.ParseISODuration("PT2H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)
justification := "Assign active member access."
requestBody.SetJustification(&justification) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentScheduleRequests, err := graphClient.IdentityGovernance().PrivilegedAccess().Group().AssignmentScheduleRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PrivilegedAccessGroupAssignmentScheduleRequest privilegedAccessGroupAssignmentScheduleRequest = new PrivilegedAccessGroupAssignmentScheduleRequest();
privilegedAccessGroupAssignmentScheduleRequest.setAccessId(PrivilegedAccessGroupRelationships.Member);
privilegedAccessGroupAssignmentScheduleRequest.setPrincipalId("3cce9d87-3986-4f19-8335-7ed075408ca2");
privilegedAccessGroupAssignmentScheduleRequest.setGroupId("68e55cce-cf7e-4a2d-9046-3e4e75c4bfa7");
privilegedAccessGroupAssignmentScheduleRequest.setAction(ScheduleRequestActions.AdminAssign);
RequestSchedule scheduleInfo = new RequestSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2022-12-08T07:43:00.000Z");
scheduleInfo.setStartDateTime(startDateTime);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.AfterDuration);
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT2H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
privilegedAccessGroupAssignmentScheduleRequest.setScheduleInfo(scheduleInfo);
privilegedAccessGroupAssignmentScheduleRequest.setJustification("Assign active member access.");
PrivilegedAccessGroupAssignmentScheduleRequest result = graphClient.identityGovernance().privilegedAccess().group().assignmentScheduleRequests().post(privilegedAccessGroupAssignmentScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const privilegedAccessGroupAssignmentScheduleRequest = {
  accessId: 'member', 
  principalId: '3cce9d87-3986-4f19-8335-7ed075408ca2', 
  groupId: '68e55cce-cf7e-4a2d-9046-3e4e75c4bfa7', 
  action: 'adminAssign', 
  scheduleInfo: { 
    startDateTime: '2022-12-08T07:43:00.000Z', 
    expiration: { 
      type: 'afterDuration', 
      duration: 'PT2H' 
    } 
  }, 
  justification: 'Assign active member access.'
};

await client.api('/identityGovernance/privilegedAccess/group/assignmentScheduleRequests')
	.post(privilegedAccessGroupAssignmentScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\PrivilegedAccessGroupAssignmentScheduleRequest;
use Microsoft\Graph\Generated\Models\PrivilegedAccessGroupRelationships;
use Microsoft\Graph\Generated\Models\ScheduleRequestActions;
use Microsoft\Graph\Generated\Models\RequestSchedule;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PrivilegedAccessGroupAssignmentScheduleRequest();
$requestBody->setAccessId(new PrivilegedAccessGroupRelationships('member'));
$requestBody->setPrincipalId('3cce9d87-3986-4f19-8335-7ed075408ca2');
$requestBody->setGroupId('68e55cce-cf7e-4a2d-9046-3e4e75c4bfa7');
$requestBody->setAction(new ScheduleRequestActions('adminAssign'));
$scheduleInfo = new RequestSchedule();
$scheduleInfo->setStartDateTime(new \DateTime('2022-12-08T07:43:00.000Z'));
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setType(new ExpirationPatternType('afterDuration'));
$scheduleInfoExpiration->setDuration(new \DateInterval('PT2H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);
$requestBody->setJustification('Assign active member access.');

$result = $graphServiceClient->identityGovernance()->privilegedAccess()->group()->assignmentScheduleRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	accessId = "member"
	principalId = "3cce9d87-3986-4f19-8335-7ed075408ca2"
	groupId = "68e55cce-cf7e-4a2d-9046-3e4e75c4bfa7"
	action = "adminAssign"
	scheduleInfo = @{
		startDateTime = [System.DateTime]::Parse("2022-12-08T07:43:00.000Z")
		expiration = @{
			type = "afterDuration"
			duration = "PT2H"
		}
	}
	justification = "Assign active member access."
}

New-MgIdentityGovernancePrivilegedAccessGroupAssignmentScheduleRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.privileged_access_group_assignment_schedule_request import PrivilegedAccessGroupAssignmentScheduleRequest
from msgraph.generated.models.privileged_access_group_relationships import PrivilegedAccessGroupRelationships
from msgraph.generated.models.schedule_request_actions import ScheduleRequestActions
from msgraph.generated.models.request_schedule import RequestSchedule
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PrivilegedAccessGroupAssignmentScheduleRequest(
	access_id = PrivilegedAccessGroupRelationships.Member,
	principal_id = "3cce9d87-3986-4f19-8335-7ed075408ca2",
	group_id = "68e55cce-cf7e-4a2d-9046-3e4e75c4bfa7",
	action = ScheduleRequestActions.AdminAssign,
	schedule_info = RequestSchedule(
		start_date_time = "2022-12-08T07:43:00.000Z",
		expiration = ExpirationPattern(
			type = ExpirationPatternType.AfterDuration,
			duration = "PT2H",
		),
	),
	justification = "Assign active member access.",
)

result = await graph_client.identity_governance.privileged_access.group.assignment_schedule_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/privilegedAccess/group/assignmentScheduleRequests/$entity",
  "id": "34e963f6-150f-cf79-678c-6fcaf978bb49",
  "status": "Provisioned",
  "completedDateTime": "2023-02-07T07:05:55.3404527Z",
  "createdDateTime": "2023-02-07T07:05:53.7895614Z",
  "approvalId": null,
  "customData": null,
  "createdBy": {
      "user": {
          "id": "3cce9d87-3986-4f19-8335-7ed075408ca2"
      }
  },
  "action": "adminAssign",
  "isValidationOnly": false,
  "justification": "Assign active member access.",
  "scheduleInfo": {
      "startDateTime": "2023-02-07T07:05:55.3404527Z",
      "expiration": {
        "type": "afterDuration",
         "duration": "PT2H"
      }
  },
  "ticketInfo": {
      "ticketNumber": null,
      "ticketSystem": null
  },
  "accessId": "member", 
  "principalId": "3cce9d87-3986-4f19-8335-7ed075408ca2", 
  "groupId": "68e55cce-cf7e-4a2d-9046-3e4e75c4bfa7",
  "targetScheduleId": "2b5ed229-4072-478d-9504-a047ebd4b07d_member_6aacaee8-4089-4048-9510-3119367fc943"
}
```

### Example 2: User activates their eligible assignment for PIM for Groups

In the following request, a user identified by **principalId** `3cce9d87-3986-4f19-8335-7ed075408ca2` activates their *eligible membership* to a group managed by PIM identified by **groupId** `2b5ed229-4072-478d-9504-a047ebd4b07d`.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/privilegedAccess/group/assignmentScheduleRequests
Content-Type: application/json

{
  "accessId": "member", 
  "principalId": "3cce9d87-3986-4f19-8335-7ed075408ca2", 
  "groupId": "2b5ed229-4072-478d-9504-a047ebd4b07d", 
  "action": "selfActivate", 
  "scheduleInfo": { 
    "startDateTime": "2023-02-08T07:43:00.000Z", 
    "expiration": { 
      "type": "afterDuration", 
      "duration": "PT2H" 
    } 
  }, 
  "justification": "Activate assignment."
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PrivilegedAccessGroupAssignmentScheduleRequest
{
	AccessId = PrivilegedAccessGroupRelationships.Member,
	PrincipalId = "3cce9d87-3986-4f19-8335-7ed075408ca2",
	GroupId = "2b5ed229-4072-478d-9504-a047ebd4b07d",
	Action = ScheduleRequestActions.SelfActivate,
	ScheduleInfo = new RequestSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2023-02-08T07:43:00.000Z"),
		Expiration = new ExpirationPattern
		{
			Type = ExpirationPatternType.AfterDuration,
			Duration = TimeSpan.Parse("PT2H"),
		},
	},
	Justification = "Activate assignment.",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PrivilegedAccess.Group.AssignmentScheduleRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewPrivilegedAccessGroupAssignmentScheduleRequest()
accessId := graphmodels.MEMBER_PRIVILEGEDACCESSGROUPRELATIONSHIPS 
requestBody.SetAccessId(&accessId) 
principalId := "3cce9d87-3986-4f19-8335-7ed075408ca2"
requestBody.SetPrincipalId(&principalId) 
groupId := "2b5ed229-4072-478d-9504-a047ebd4b07d"
requestBody.SetGroupId(&groupId) 
action := graphmodels.SELFACTIVATE_SCHEDULEREQUESTACTIONS 
requestBody.SetAction(&action) 
scheduleInfo := graphmodels.NewRequestSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2023-02-08T07:43:00.000Z")
scheduleInfo.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
type := graphmodels.AFTERDURATION_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
duration , err := abstractions.ParseISODuration("PT2H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)
justification := "Activate assignment."
requestBody.SetJustification(&justification) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentScheduleRequests, err := graphClient.IdentityGovernance().PrivilegedAccess().Group().AssignmentScheduleRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PrivilegedAccessGroupAssignmentScheduleRequest privilegedAccessGroupAssignmentScheduleRequest = new PrivilegedAccessGroupAssignmentScheduleRequest();
privilegedAccessGroupAssignmentScheduleRequest.setAccessId(PrivilegedAccessGroupRelationships.Member);
privilegedAccessGroupAssignmentScheduleRequest.setPrincipalId("3cce9d87-3986-4f19-8335-7ed075408ca2");
privilegedAccessGroupAssignmentScheduleRequest.setGroupId("2b5ed229-4072-478d-9504-a047ebd4b07d");
privilegedAccessGroupAssignmentScheduleRequest.setAction(ScheduleRequestActions.SelfActivate);
RequestSchedule scheduleInfo = new RequestSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2023-02-08T07:43:00.000Z");
scheduleInfo.setStartDateTime(startDateTime);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.AfterDuration);
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT2H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
privilegedAccessGroupAssignmentScheduleRequest.setScheduleInfo(scheduleInfo);
privilegedAccessGroupAssignmentScheduleRequest.setJustification("Activate assignment.");
PrivilegedAccessGroupAssignmentScheduleRequest result = graphClient.identityGovernance().privilegedAccess().group().assignmentScheduleRequests().post(privilegedAccessGroupAssignmentScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const privilegedAccessGroupAssignmentScheduleRequest = {
  accessId: 'member', 
  principalId: '3cce9d87-3986-4f19-8335-7ed075408ca2', 
  groupId: '2b5ed229-4072-478d-9504-a047ebd4b07d', 
  action: 'selfActivate', 
  scheduleInfo: { 
    startDateTime: '2023-02-08T07:43:00.000Z', 
    expiration: { 
      type: 'afterDuration', 
      duration: 'PT2H' 
    } 
  }, 
  justification: 'Activate assignment.'
};

await client.api('/identityGovernance/privilegedAccess/group/assignmentScheduleRequests')
	.post(privilegedAccessGroupAssignmentScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\PrivilegedAccessGroupAssignmentScheduleRequest;
use Microsoft\Graph\Generated\Models\PrivilegedAccessGroupRelationships;
use Microsoft\Graph\Generated\Models\ScheduleRequestActions;
use Microsoft\Graph\Generated\Models\RequestSchedule;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PrivilegedAccessGroupAssignmentScheduleRequest();
$requestBody->setAccessId(new PrivilegedAccessGroupRelationships('member'));
$requestBody->setPrincipalId('3cce9d87-3986-4f19-8335-7ed075408ca2');
$requestBody->setGroupId('2b5ed229-4072-478d-9504-a047ebd4b07d');
$requestBody->setAction(new ScheduleRequestActions('selfActivate'));
$scheduleInfo = new RequestSchedule();
$scheduleInfo->setStartDateTime(new \DateTime('2023-02-08T07:43:00.000Z'));
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setType(new ExpirationPatternType('afterDuration'));
$scheduleInfoExpiration->setDuration(new \DateInterval('PT2H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);
$requestBody->setJustification('Activate assignment.');

$result = $graphServiceClient->identityGovernance()->privilegedAccess()->group()->assignmentScheduleRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	accessId = "member"
	principalId = "3cce9d87-3986-4f19-8335-7ed075408ca2"
	groupId = "2b5ed229-4072-478d-9504-a047ebd4b07d"
	action = "selfActivate"
	scheduleInfo = @{
		startDateTime = [System.DateTime]::Parse("2023-02-08T07:43:00.000Z")
		expiration = @{
			type = "afterDuration"
			duration = "PT2H"
		}
	}
	justification = "Activate assignment."
}

New-MgIdentityGovernancePrivilegedAccessGroupAssignmentScheduleRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.privileged_access_group_assignment_schedule_request import PrivilegedAccessGroupAssignmentScheduleRequest
from msgraph.generated.models.privileged_access_group_relationships import PrivilegedAccessGroupRelationships
from msgraph.generated.models.schedule_request_actions import ScheduleRequestActions
from msgraph.generated.models.request_schedule import RequestSchedule
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PrivilegedAccessGroupAssignmentScheduleRequest(
	access_id = PrivilegedAccessGroupRelationships.Member,
	principal_id = "3cce9d87-3986-4f19-8335-7ed075408ca2",
	group_id = "2b5ed229-4072-478d-9504-a047ebd4b07d",
	action = ScheduleRequestActions.SelfActivate,
	schedule_info = RequestSchedule(
		start_date_time = "2023-02-08T07:43:00.000Z",
		expiration = ExpirationPattern(
			type = ExpirationPatternType.AfterDuration,
			duration = "PT2H",
		),
	),
	justification = "Activate assignment.",
)

result = await graph_client.identity_governance.privileged_access.group.assignment_schedule_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/privilegedAccess/group/assignmentScheduleRequests/$entity",
  "id": "6aacaee8-4089-4048-9510-3119367fc943",
  "status": "Provisioned",
  "completedDateTime": "2023-02-07T07:05:55.3404527Z",
  "createdDateTime": "2023-02-07T07:05:53.7895614Z",
  "approvalId": null,
  "customData": null,
  "createdBy": {
      "user": {
          "id": "3cce9d87-3986-4f19-8335-7ed075408ca2"
      }
  },
  "action": "selfActivate",
  "isValidationOnly": false,
  "justification": "Activate assignment.",
  "scheduleInfo": {
      "startDateTime": "2023-02-07T07:05:55.3404527Z",
      "expiration": {
        "type": "afterDuration",
         "duration": "PT2H"
      }
  },
  "ticketInfo": {
      "ticketNumber": null,
      "ticketSystem": null
  },
  "accessId": "member", 
  "principalId": "3cce9d87-3986-4f19-8335-7ed075408ca2", 
  "groupId": "2b5ed229-4072-478d-9504-a047ebd4b07d",
  "targetScheduleId": "2b5ed229-4072-478d-9504-a047ebd4b07d_member_6aacaee8-4089-4048-9510-3119367fc943"
}
```
