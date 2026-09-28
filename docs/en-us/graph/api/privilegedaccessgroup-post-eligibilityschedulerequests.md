<!-- Source: https://learn.microsoft.com/en-us/graph/api/privilegedaccessgroup-post-eligibilityschedulerequests?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create eligibilityScheduleRequest

Namespace: microsoft.graph

Create a new [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrivilegedEligibilitySchedule.ReadWrite.AzureADGroup | PrivilegedEligibilitySchedule.Remove.AzureADGroup |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PrivilegedEligibilitySchedule.ReadWrite.AzureADGroup | PrivilegedEligibilitySchedule.Remove.AzureADGroup |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- For role-assignable groups: *Privileged Role Administrator*
- For non-role-assignable groups: *Directory Writer*, *Groups Administrator*, *Identity Governance Administrator*, or *User Administrator*

The role assignments for the calling user should be scoped at the directory level.

Other roles with permissions to manage groups \(such as Exchange Administrators for non-role-assignable Microsoft 365 groups\) and administrators with assignments scoped at administrative unit level can manage groups through groups API and override changes made in Microsoft Entra PIM through PIM for Groups APIs.

## HTTP request

```http
POST /identityGovernance/privilegedAccess/group/eligibilityScheduleRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) object.

You can specify the following properties when creating a **privilegedAccessGroupEligibilityScheduleRequest**.

| Property | Type | Description |
| :--- | :--- | :--- |
| accessId | privilegedAccessGroupRelationships | The identifier of the membership or ownership eligibility relationship to the group. The possible values are: `owner`, `member`. Required. |
| action | String | Represents the type of operation on the group membership or ownership eligibility assignment request. The possible values are: `adminAssign`, `adminUpdate`, `adminRemove`, `selfActivate`, `selfDeactivate`, `adminExtend`, `adminRenew`.  <br><br><br>- `adminAssign`: For administrators to assign group membership or ownership eligibility to principals.<br>- `adminRemove`: For administrators to remove principals from group membership or ownership eligibilities.<br>- `adminUpdate`: For administrators to change existing eligible assignments.<br>- `adminExtend`: For administrators to extend expiring eligible assignments.<br>- `adminRenew`: For administrators to renew expired eligible assignments.<br>- `selfActivate`: For principals to activate their eligible assignments.<br>- `selfDeactivate`: For principals to deactivate their eligible assignments. |
| groupId | String | The identifier of the group representing the scope of the membership or ownership eligibility through PIM for Groups. Required. |
| justification | String | A message provided by users and administrators when they create the **privilegedAccessGroupAssignmentScheduleRequest** object. |
| principalId | String | The identifier of the principal whose membership or ownership eligibility to the group is managed through PIM for Groups. Required. |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-1.0) | The period of the group membership or ownership assignment for PIM for Groups. Recurring schedules are currently unsupported. Required. |
| ticketInfo | [ticketInfo](https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-1.0) | Ticket details linked to the group membership or ownership assignment request including details of the ticket number and ticket system. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [privilegedAccessGroupEligibilityScheduleRequest](https://learn.microsoft.com/en-us/graph/api/resources/privilegedaccessgroupeligibilityschedulerequest?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: An admin creates an eligible group ownership request for a principal

The following request creates an eligibility schedule request to make a principal eligible to be a group owner. The eligible ownership expires after two hours.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/privilegedAccess/group/eligibilityScheduleRequests
Content-Type: application/json

{
    "accessId": "member",
    "principalId": "3cce9d87-3986-4f19-8335-7ed075408ca2",
    "groupId": "2b5ed229-4072-478d-9504-a047ebd4b07d",
    "action": "AdminAssign",
    "scheduleInfo": {
        "startDateTime": "2023-02-06T19:25:00.000Z",
        "expiration": {
            "type": "AfterDateTime",
            "endDateTime": "2023-02-07T19:56:00.000Z"
        }
    },
    "justification": "Assign eligible request."
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PrivilegedAccessGroupEligibilityScheduleRequest
{
	AccessId = PrivilegedAccessGroupRelationships.Member,
	PrincipalId = "3cce9d87-3986-4f19-8335-7ed075408ca2",
	GroupId = "2b5ed229-4072-478d-9504-a047ebd4b07d",
	Action = ScheduleRequestActions.AdminAssign,
	ScheduleInfo = new RequestSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2023-02-06T19:25:00.000Z"),
		Expiration = new ExpirationPattern
		{
			Type = ExpirationPatternType.AfterDateTime,
			EndDateTime = DateTimeOffset.Parse("2023-02-07T19:56:00.000Z"),
		},
	},
	Justification = "Assign eligible request.",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PrivilegedAccess.Group.EligibilityScheduleRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewPrivilegedAccessGroupEligibilityScheduleRequest()
accessId := graphmodels.MEMBER_PRIVILEGEDACCESSGROUPRELATIONSHIPS 
requestBody.SetAccessId(&accessId) 
principalId := "3cce9d87-3986-4f19-8335-7ed075408ca2"
requestBody.SetPrincipalId(&principalId) 
groupId := "2b5ed229-4072-478d-9504-a047ebd4b07d"
requestBody.SetGroupId(&groupId) 
action := graphmodels.ADMINASSIGN_SCHEDULEREQUESTACTIONS 
requestBody.SetAction(&action) 
scheduleInfo := graphmodels.NewRequestSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2023-02-06T19:25:00.000Z")
scheduleInfo.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
type := graphmodels.AFTERDATETIME_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
endDateTime , err := time.Parse(time.RFC3339, "2023-02-07T19:56:00.000Z")
expiration.SetEndDateTime(&endDateTime) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)
justification := "Assign eligible request."
requestBody.SetJustification(&justification) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
eligibilityScheduleRequests, err := graphClient.IdentityGovernance().PrivilegedAccess().Group().EligibilityScheduleRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PrivilegedAccessGroupEligibilityScheduleRequest privilegedAccessGroupEligibilityScheduleRequest = new PrivilegedAccessGroupEligibilityScheduleRequest();
privilegedAccessGroupEligibilityScheduleRequest.setAccessId(PrivilegedAccessGroupRelationships.Member);
privilegedAccessGroupEligibilityScheduleRequest.setPrincipalId("3cce9d87-3986-4f19-8335-7ed075408ca2");
privilegedAccessGroupEligibilityScheduleRequest.setGroupId("2b5ed229-4072-478d-9504-a047ebd4b07d");
privilegedAccessGroupEligibilityScheduleRequest.setAction(ScheduleRequestActions.AdminAssign);
RequestSchedule scheduleInfo = new RequestSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2023-02-06T19:25:00.000Z");
scheduleInfo.setStartDateTime(startDateTime);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.AfterDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2023-02-07T19:56:00.000Z");
expiration.setEndDateTime(endDateTime);
scheduleInfo.setExpiration(expiration);
privilegedAccessGroupEligibilityScheduleRequest.setScheduleInfo(scheduleInfo);
privilegedAccessGroupEligibilityScheduleRequest.setJustification("Assign eligible request.");
PrivilegedAccessGroupEligibilityScheduleRequest result = graphClient.identityGovernance().privilegedAccess().group().eligibilityScheduleRequests().post(privilegedAccessGroupEligibilityScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const privilegedAccessGroupEligibilityScheduleRequest = {
    accessId: 'member',
    principalId: '3cce9d87-3986-4f19-8335-7ed075408ca2',
    groupId: '2b5ed229-4072-478d-9504-a047ebd4b07d',
    action: 'AdminAssign',
    scheduleInfo: {
        startDateTime: '2023-02-06T19:25:00.000Z',
        expiration: {
            type: 'AfterDateTime',
            endDateTime: '2023-02-07T19:56:00.000Z'
        }
    },
    justification: 'Assign eligible request.'
};

await client.api('/identityGovernance/privilegedAccess/group/eligibilityScheduleRequests')
	.post(privilegedAccessGroupEligibilityScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\PrivilegedAccessGroupEligibilityScheduleRequest;
use Microsoft\Graph\Generated\Models\PrivilegedAccessGroupRelationships;
use Microsoft\Graph\Generated\Models\ScheduleRequestActions;
use Microsoft\Graph\Generated\Models\RequestSchedule;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PrivilegedAccessGroupEligibilityScheduleRequest();
$requestBody->setAccessId(new PrivilegedAccessGroupRelationships('member'));
$requestBody->setPrincipalId('3cce9d87-3986-4f19-8335-7ed075408ca2');
$requestBody->setGroupId('2b5ed229-4072-478d-9504-a047ebd4b07d');
$requestBody->setAction(new ScheduleRequestActions('adminAssign'));
$scheduleInfo = new RequestSchedule();
$scheduleInfo->setStartDateTime(new \DateTime('2023-02-06T19:25:00.000Z'));
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setType(new ExpirationPatternType('afterDateTime'));
$scheduleInfoExpiration->setEndDateTime(new \DateTime('2023-02-07T19:56:00.000Z'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);
$requestBody->setJustification('Assign eligible request.');

$result = $graphServiceClient->identityGovernance()->privilegedAccess()->group()->eligibilityScheduleRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	accessId = "member"
	principalId = "3cce9d87-3986-4f19-8335-7ed075408ca2"
	groupId = "2b5ed229-4072-478d-9504-a047ebd4b07d"
	action = "AdminAssign"
	scheduleInfo = @{
		startDateTime = [System.DateTime]::Parse("2023-02-06T19:25:00.000Z")
		expiration = @{
			type = "AfterDateTime"
			endDateTime = [System.DateTime]::Parse("2023-02-07T19:56:00.000Z")
		}
	}
	justification = "Assign eligible request."
}

New-MgIdentityGovernancePrivilegedAccessGroupEligibilityScheduleRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.privileged_access_group_eligibility_schedule_request import PrivilegedAccessGroupEligibilityScheduleRequest
from msgraph.generated.models.privileged_access_group_relationships import PrivilegedAccessGroupRelationships
from msgraph.generated.models.schedule_request_actions import ScheduleRequestActions
from msgraph.generated.models.request_schedule import RequestSchedule
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PrivilegedAccessGroupEligibilityScheduleRequest(
	access_id = PrivilegedAccessGroupRelationships.Member,
	principal_id = "3cce9d87-3986-4f19-8335-7ed075408ca2",
	group_id = "2b5ed229-4072-478d-9504-a047ebd4b07d",
	action = ScheduleRequestActions.AdminAssign,
	schedule_info = RequestSchedule(
		start_date_time = "2023-02-06T19:25:00.000Z",
		expiration = ExpirationPattern(
			type = ExpirationPatternType.AfterDateTime,
			end_date_time = "2023-02-07T19:56:00.000Z",
		),
	),
	justification = "Assign eligible request.",
)

result = await graph_client.identity_governance.privileged_access.group.eligibility_schedule_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/privilegedAccess/group/eligibilityScheduleRequests/$entity",
    "id": "f8bd9e2d-bc15-49b1-8a9b-c571b3cf9555",
    "status": "Provisioned",
    "createdDateTime": "2023-02-07T06:57:54.1633903Z",
    "completedDateTime": "2023-02-07T06:57:55.6183972Z",
    "action": "adminAssign",
    "isValidationOnly": false,
    "justification": "Assign eligible request.",
    "principalId": "3cce9d87-3986-4f19-8335-7ed075408ca2",
    "accessId": "member",
    "groupId": "2b5ed229-4072-478d-9504-a047ebd4b07d",
    "targetScheduleId": "2b5ed229-4072-478d-9504-a047ebd4b07d_member_f8bd9e2d-bc15-49b1-8a9b-c571b3cf9555",
    "createdBy": {
        "user": {
            "id": "3cce9d87-3986-4f19-8335-7ed075408ca2"
        }
    },
    "scheduleInfo": {
        "startDateTime": "2023-02-07T06:57:55.6183972Z",
        "recurrence": null,
        "expiration": {
            "type": "afterDateTime",
            "endDateTime": "2023-02-07T19:56:00Z",
            "duration": null
        }
    }
}
```

### Example 2: An admin extends an eligible group membership for a principal

The following request extends an existing eligibility schedule request before it expires.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/privilegedAccess/group/eligibilityScheduleRequests
Content-Type: application/json

{
    "accessId": "member",
    "principalId": "3cce9d87-3986-4f19-8335-7ed075408ca2",
    "groupId": "2b5ed229-4072-478d-9504-a047ebd4b07d",
    "action": "AdminExtend",
    "scheduleInfo": {
        "startDateTime": "2023-02-06T19:25:00.000Z",
        "expiration": {
            "type": "AfterDateTime",
            "endDateTime": "2023-02-07T20:56:00.000Z"
        }
    },
    "justification": "Extend eligible request."
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PrivilegedAccessGroupEligibilityScheduleRequest
{
	AccessId = PrivilegedAccessGroupRelationships.Member,
	PrincipalId = "3cce9d87-3986-4f19-8335-7ed075408ca2",
	GroupId = "2b5ed229-4072-478d-9504-a047ebd4b07d",
	Action = ScheduleRequestActions.AdminExtend,
	ScheduleInfo = new RequestSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2023-02-06T19:25:00.000Z"),
		Expiration = new ExpirationPattern
		{
			Type = ExpirationPatternType.AfterDateTime,
			EndDateTime = DateTimeOffset.Parse("2023-02-07T20:56:00.000Z"),
		},
	},
	Justification = "Extend eligible request.",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PrivilegedAccess.Group.EligibilityScheduleRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewPrivilegedAccessGroupEligibilityScheduleRequest()
accessId := graphmodels.MEMBER_PRIVILEGEDACCESSGROUPRELATIONSHIPS 
requestBody.SetAccessId(&accessId) 
principalId := "3cce9d87-3986-4f19-8335-7ed075408ca2"
requestBody.SetPrincipalId(&principalId) 
groupId := "2b5ed229-4072-478d-9504-a047ebd4b07d"
requestBody.SetGroupId(&groupId) 
action := graphmodels.ADMINEXTEND_SCHEDULEREQUESTACTIONS 
requestBody.SetAction(&action) 
scheduleInfo := graphmodels.NewRequestSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2023-02-06T19:25:00.000Z")
scheduleInfo.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
type := graphmodels.AFTERDATETIME_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
endDateTime , err := time.Parse(time.RFC3339, "2023-02-07T20:56:00.000Z")
expiration.SetEndDateTime(&endDateTime) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)
justification := "Extend eligible request."
requestBody.SetJustification(&justification) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
eligibilityScheduleRequests, err := graphClient.IdentityGovernance().PrivilegedAccess().Group().EligibilityScheduleRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PrivilegedAccessGroupEligibilityScheduleRequest privilegedAccessGroupEligibilityScheduleRequest = new PrivilegedAccessGroupEligibilityScheduleRequest();
privilegedAccessGroupEligibilityScheduleRequest.setAccessId(PrivilegedAccessGroupRelationships.Member);
privilegedAccessGroupEligibilityScheduleRequest.setPrincipalId("3cce9d87-3986-4f19-8335-7ed075408ca2");
privilegedAccessGroupEligibilityScheduleRequest.setGroupId("2b5ed229-4072-478d-9504-a047ebd4b07d");
privilegedAccessGroupEligibilityScheduleRequest.setAction(ScheduleRequestActions.AdminExtend);
RequestSchedule scheduleInfo = new RequestSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2023-02-06T19:25:00.000Z");
scheduleInfo.setStartDateTime(startDateTime);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.AfterDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2023-02-07T20:56:00.000Z");
expiration.setEndDateTime(endDateTime);
scheduleInfo.setExpiration(expiration);
privilegedAccessGroupEligibilityScheduleRequest.setScheduleInfo(scheduleInfo);
privilegedAccessGroupEligibilityScheduleRequest.setJustification("Extend eligible request.");
PrivilegedAccessGroupEligibilityScheduleRequest result = graphClient.identityGovernance().privilegedAccess().group().eligibilityScheduleRequests().post(privilegedAccessGroupEligibilityScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const privilegedAccessGroupEligibilityScheduleRequest = {
    accessId: 'member',
    principalId: '3cce9d87-3986-4f19-8335-7ed075408ca2',
    groupId: '2b5ed229-4072-478d-9504-a047ebd4b07d',
    action: 'AdminExtend',
    scheduleInfo: {
        startDateTime: '2023-02-06T19:25:00.000Z',
        expiration: {
            type: 'AfterDateTime',
            endDateTime: '2023-02-07T20:56:00.000Z'
        }
    },
    justification: 'Extend eligible request.'
};

await client.api('/identityGovernance/privilegedAccess/group/eligibilityScheduleRequests')
	.post(privilegedAccessGroupEligibilityScheduleRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\PrivilegedAccessGroupEligibilityScheduleRequest;
use Microsoft\Graph\Generated\Models\PrivilegedAccessGroupRelationships;
use Microsoft\Graph\Generated\Models\ScheduleRequestActions;
use Microsoft\Graph\Generated\Models\RequestSchedule;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PrivilegedAccessGroupEligibilityScheduleRequest();
$requestBody->setAccessId(new PrivilegedAccessGroupRelationships('member'));
$requestBody->setPrincipalId('3cce9d87-3986-4f19-8335-7ed075408ca2');
$requestBody->setGroupId('2b5ed229-4072-478d-9504-a047ebd4b07d');
$requestBody->setAction(new ScheduleRequestActions('adminExtend'));
$scheduleInfo = new RequestSchedule();
$scheduleInfo->setStartDateTime(new \DateTime('2023-02-06T19:25:00.000Z'));
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setType(new ExpirationPatternType('afterDateTime'));
$scheduleInfoExpiration->setEndDateTime(new \DateTime('2023-02-07T20:56:00.000Z'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);
$requestBody->setJustification('Extend eligible request.');

$result = $graphServiceClient->identityGovernance()->privilegedAccess()->group()->eligibilityScheduleRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	accessId = "member"
	principalId = "3cce9d87-3986-4f19-8335-7ed075408ca2"
	groupId = "2b5ed229-4072-478d-9504-a047ebd4b07d"
	action = "AdminExtend"
	scheduleInfo = @{
		startDateTime = [System.DateTime]::Parse("2023-02-06T19:25:00.000Z")
		expiration = @{
			type = "AfterDateTime"
			endDateTime = [System.DateTime]::Parse("2023-02-07T20:56:00.000Z")
		}
	}
	justification = "Extend eligible request."
}

New-MgIdentityGovernancePrivilegedAccessGroupEligibilityScheduleRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.privileged_access_group_eligibility_schedule_request import PrivilegedAccessGroupEligibilityScheduleRequest
from msgraph.generated.models.privileged_access_group_relationships import PrivilegedAccessGroupRelationships
from msgraph.generated.models.schedule_request_actions import ScheduleRequestActions
from msgraph.generated.models.request_schedule import RequestSchedule
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PrivilegedAccessGroupEligibilityScheduleRequest(
	access_id = PrivilegedAccessGroupRelationships.Member,
	principal_id = "3cce9d87-3986-4f19-8335-7ed075408ca2",
	group_id = "2b5ed229-4072-478d-9504-a047ebd4b07d",
	action = ScheduleRequestActions.AdminExtend,
	schedule_info = RequestSchedule(
		start_date_time = "2023-02-06T19:25:00.000Z",
		expiration = ExpirationPattern(
			type = ExpirationPatternType.AfterDateTime,
			end_date_time = "2023-02-07T20:56:00.000Z",
		),
	),
	justification = "Extend eligible request.",
)

result = await graph_client.identity_governance.privileged_access.group.eligibility_schedule_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/privilegedAccess/group/eligibilityScheduleRequests/$entity",
    "id": "e3405b79-c0d8-4597-87b5-a84451e29224",
    "status": "Provisioned",
    "createdDateTime": "2023-02-07T07:01:25.9239454Z",
    "completedDateTime": "2023-02-07T07:01:27.3379548Z",
    "action": "adminExtend",
    "isValidationOnly": false,
    "justification": "Extend eligible request.",
    "principalId": "3cce9d87-3986-4f19-8335-7ed075408ca2",
    "accessId": "member",
    "groupId": "2b5ed229-4072-478d-9504-a047ebd4b07d",
    "targetScheduleId": "2b5ed229-4072-478d-9504-a047ebd4b07d_member_e3405b79-c0d8-4597-87b5-a84451e29224",
    "createdBy": {
        "user": {
            "id": "3cce9d87-3986-4f19-8335-7ed075408ca2"
        }
    },
    "scheduleInfo": {
        "startDateTime": "2023-02-07T07:01:27.3379548Z",
        "expiration": {
            "type": "afterDateTime",
            "endDateTime": "2023-02-07T20:56:00Z",
            "duration": null
        }
    }
}
```
