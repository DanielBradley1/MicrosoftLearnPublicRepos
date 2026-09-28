<!-- Source: https://learn.microsoft.com/en-us/graph/tutorial-assign-azureadroles -->
<!-- Sitemap-Last-Modified: 2025-03-24 -->

# Assign privileged roles using PIM for Microsoft Entra roles APIs

Privileged Identity Management \(PIM\) helps organizations reduce risks associated with privileged access by limiting when access is active, managing access scope, and providing an auditable log of privileged access. Privileged access is typically granted for administrative purposes through role-assignable groups or admin roles.

Contoso wants to delegate some admin functions by assigning Microsoft Entra roles to users through security groups. The company assigns eligibility instead of persistently active privileged roles. This method is effective because:

- Removing or adding group members also removes or adds administrators.
- Group members inherit role assignments. You can assign more roles to a group instead of assigning roles directly to individual users.
- Assigning eligibility instead of persistently active privileges enforces **just-in-time access**, granting temporary permissions to carry out privileged tasks. When a group member needs privileges, they activate their assignment temporarily. All role activations are auditable.

You can model role eligibility through groups in two ways:

- Grant a group a permanent role assignment and make principals eligible for the group. In this scenario, group members activate their group membership to get active role assignments.
- Grant a group an eligible role assignment and make the principals permanent members of the group. In this scenario, group members activate their role assignments to get privileges.

In this tutorial, you learn how to:

- Create a role-assignable security group.
- Make a role-assignable security group eligible for a privileged role.
- Grant just-in-time access to a user by activating their eligible assignment.

## Prerequisites

To complete this tutorial, you need:

- A Microsoft Entra tenant with a Microsoft Entra ID P2 or Microsoft Entra ID Governance license
- An API client such as [Graph Explorer](https://aka.ms/ge) signed in with an account that has at least the Privileged Role Administrator role
- A test user enabled for MFA with access to their Microsoft Authenticator app
- Delegated permissions:

  - `Group.ReadWrite.All` to create the group
  - `RoleManagement.ReadWrite.Directory` to make the group role-assignable and to configure and manage eligible and active role assignments. This permission should be granted to all users in the tenant.

## Step 1: Create a role-assignable security group

Assign yourself as the group owner, and add yourself and the test user as members.

### Request: Create a role-assignable group

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/groups
Content-type: application/json

{
    "description": "IT Helpdesk to support Contoso employees",
    "displayName": "IT Helpdesk (User)",
    "mailEnabled": false,
    "mailNickname": "userHelpdesk",
    "securityEnabled": true,
    "isAssignableToRole": true,
    "owners@odata.bind": [
        "https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6"
    ],
    "members@odata.bind": [
        "https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6",
        "https://graph.microsoft.com/v1.0/users/d9771b4c-06c5-491a-92cb-3aa4e225a725"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Group
{
	Description = "IT Helpdesk to support Contoso employees",
	DisplayName = "IT Helpdesk (User)",
	MailEnabled = false,
	MailNickname = "userHelpdesk",
	SecurityEnabled = true,
	IsAssignableToRole = true,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"owners@odata.bind" , new List<string>
			{
				"https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6",
			}
		},
		{
			"members@odata.bind" , new List<string>
			{
				"https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6",
				"https://graph.microsoft.com/v1.0/users/d9771b4c-06c5-491a-92cb-3aa4e225a725",
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewGroup()
description := "IT Helpdesk to support Contoso employees"
requestBody.SetDescription(&description) 
displayName := "IT Helpdesk (User)"
requestBody.SetDisplayName(&displayName) 
mailEnabled := false
requestBody.SetMailEnabled(&mailEnabled) 
mailNickname := "userHelpdesk"
requestBody.SetMailNickname(&mailNickname) 
securityEnabled := true
requestBody.SetSecurityEnabled(&securityEnabled) 
isAssignableToRole := true
requestBody.SetIsAssignableToRole(&isAssignableToRole) 
additionalData := map[string]interface{}{
	odataBind := []string {
		"https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6",
	}
	odataBind := []string {
		"https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6",
		"https://graph.microsoft.com/v1.0/users/d9771b4c-06c5-491a-92cb-3aa4e225a725",
	}
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groups, err := graphClient.Groups().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Group group = new Group();
group.setDescription("IT Helpdesk to support Contoso employees");
group.setDisplayName("IT Helpdesk (User)");
group.setMailEnabled(false);
group.setMailNickname("userHelpdesk");
group.setSecurityEnabled(true);
group.setIsAssignableToRole(true);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<String> ownersOdataBind = new LinkedList<String>();
ownersOdataBind.add("https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6");
additionalData.put("owners@odata.bind", ownersOdataBind);
LinkedList<String> membersOdataBind = new LinkedList<String>();
membersOdataBind.add("https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6");
membersOdataBind.add("https://graph.microsoft.com/v1.0/users/d9771b4c-06c5-491a-92cb-3aa4e225a725");
additionalData.put("members@odata.bind", membersOdataBind);
group.setAdditionalData(additionalData);
Group result = graphClient.groups().post(group);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const group = {
    description: 'IT Helpdesk to support Contoso employees',
    displayName: 'IT Helpdesk (User)',
    mailEnabled: false,
    mailNickname: 'userHelpdesk',
    securityEnabled: true,
    isAssignableToRole: true,
    'owners@odata.bind': [
        'https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6'
    ],
    'members@odata.bind': [
        'https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6',
        'https://graph.microsoft.com/v1.0/users/d9771b4c-06c5-491a-92cb-3aa4e225a725'
    ]
};

await client.api('/groups')
	.post(group);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Group;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Group();
$requestBody->setDescription('IT Helpdesk to support Contoso employees');
$requestBody->setDisplayName('IT Helpdesk (User)');
$requestBody->setMailEnabled(false);
$requestBody->setMailNickname('userHelpdesk');
$requestBody->setSecurityEnabled(true);
$requestBody->setIsAssignableToRole(true);
$additionalData = [
	'owners@odata.bind' => [
'https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6', ],
	'members@odata.bind' => [
'https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6', 'https://graph.microsoft.com/v1.0/users/d9771b4c-06c5-491a-92cb-3aa4e225a725', ],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->groups()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	description = "IT Helpdesk to support Contoso employees"
	displayName = "IT Helpdesk (User)"
	mailEnabled = $false
	mailNickname = "userHelpdesk"
	securityEnabled = $true
	isAssignableToRole = $true
	"owners@odata.bind" = @(
	"https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6"
)
"members@odata.bind" = @(
"https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6"
"https://graph.microsoft.com/v1.0/users/d9771b4c-06c5-491a-92cb-3aa4e225a725"
)
}

New-MgGroup -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group import Group
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Group(
	description = "IT Helpdesk to support Contoso employees",
	display_name = "IT Helpdesk (User)",
	mail_enabled = False,
	mail_nickname = "userHelpdesk",
	security_enabled = True,
	is_assignable_to_role = True,
	additional_data = {
			"owners@odata_bind" : [
				"https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6",
			],
			"members@odata_bind" : [
				"https://graph.microsoft.com/v1.0/users/e2330663-f949-41b5-a3dc-faeb793e14c6",
				"https://graph.microsoft.com/v1.0/users/d9771b4c-06c5-491a-92cb-3aa4e225a725",
			],
	}
)

result = await graph_client.groups.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups/$entity",
    "id": "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3",
    "description": "IT Helpdesk to support Contoso employees",
    "displayName": "IT Helpdesk (User)",
    "groupTypes": [],
    "isAssignableToRole": true,
    "mailEnabled": false,
    "mailNickname": "userHelpdesk",
    "securityEnabled": true
}
```

## Step 2: Create a unifiedRoleEligibilityScheduleRequest

Assign the security group as eligible for the *User Administrator* role for one year. Scope the eligible assignment to your entire tenant. Tenant-level scoping allows the user admin to manage all users in your tenant, except higher privileged users like Global Administrators.

### Request

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
Content-type: application/json

{
    "action": "AdminAssign",
    "justification": "Assign User Admin eligibility to IT Helpdesk (User) group",
    "roleDefinitionId": "fe930be7-5e62-47db-91af-98c3a49a38b1",
    "directoryScopeId": "/",
    "principalId": "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3",
    "scheduleInfo": {
        "startDateTime": "2025-03-21T11:06:00Z",
        "expiration": {
            "endDateTime": "2026-03-21T00:00:00Z",
            "type": "AfterDateTime"
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
	Justification = "Assign User Admin eligibility to IT Helpdesk (User) group",
	RoleDefinitionId = "fe930be7-5e62-47db-91af-98c3a49a38b1",
	DirectoryScopeId = "/",
	PrincipalId = "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3",
	ScheduleInfo = new RequestSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2025-03-21T11:06:00Z"),
		Expiration = new ExpirationPattern
		{
			EndDateTime = DateTimeOffset.Parse("2026-03-21T00:00:00Z"),
			Type = ExpirationPatternType.AfterDateTime,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.RoleEligibilityScheduleRequests.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
justification := "Assign User Admin eligibility to IT Helpdesk (User) group"
requestBody.SetJustification(&justification) 
roleDefinitionId := "fe930be7-5e62-47db-91af-98c3a49a38b1"
requestBody.SetRoleDefinitionId(&roleDefinitionId) 
directoryScopeId := "/"
requestBody.SetDirectoryScopeId(&directoryScopeId) 
principalId := "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3"
requestBody.SetPrincipalId(&principalId) 
scheduleInfo := graphmodels.NewRequestSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2025-03-21T11:06:00Z")
scheduleInfo.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
endDateTime , err := time.Parse(time.RFC3339, "2026-03-21T00:00:00Z")
expiration.SetEndDateTime(&endDateTime) 
type := graphmodels.AFTERDATETIME_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleEligibilityScheduleRequests, err := graphClient.RoleManagement().Directory().RoleEligibilityScheduleRequests().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleEligibilityScheduleRequest unifiedRoleEligibilityScheduleRequest = new UnifiedRoleEligibilityScheduleRequest();
unifiedRoleEligibilityScheduleRequest.setAction(UnifiedRoleScheduleRequestActions.AdminAssign);
unifiedRoleEligibilityScheduleRequest.setJustification("Assign User Admin eligibility to IT Helpdesk (User) group");
unifiedRoleEligibilityScheduleRequest.setRoleDefinitionId("fe930be7-5e62-47db-91af-98c3a49a38b1");
unifiedRoleEligibilityScheduleRequest.setDirectoryScopeId("/");
unifiedRoleEligibilityScheduleRequest.setPrincipalId("1189bbdd-1268-4a72-8c6d-6fe77d28f2e3");
RequestSchedule scheduleInfo = new RequestSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2025-03-21T11:06:00Z");
scheduleInfo.setStartDateTime(startDateTime);
ExpirationPattern expiration = new ExpirationPattern();
OffsetDateTime endDateTime = OffsetDateTime.parse("2026-03-21T00:00:00Z");
expiration.setEndDateTime(endDateTime);
expiration.setType(ExpirationPatternType.AfterDateTime);
scheduleInfo.setExpiration(expiration);
unifiedRoleEligibilityScheduleRequest.setScheduleInfo(scheduleInfo);
UnifiedRoleEligibilityScheduleRequest result = graphClient.roleManagement().directory().roleEligibilityScheduleRequests().post(unifiedRoleEligibilityScheduleRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleEligibilityScheduleRequest = {
    action: 'AdminAssign',
    justification: 'Assign User Admin eligibility to IT Helpdesk (User) group',
    roleDefinitionId: 'fe930be7-5e62-47db-91af-98c3a49a38b1',
    directoryScopeId: '/',
    principalId: '1189bbdd-1268-4a72-8c6d-6fe77d28f2e3',
    scheduleInfo: {
        startDateTime: '2025-03-21T11:06:00Z',
        expiration: {
            endDateTime: '2026-03-21T00:00:00Z',
            type: 'AfterDateTime'
        }
    }
};

await client.api('/roleManagement/directory/roleEligibilityScheduleRequests')
	.post(unifiedRoleEligibilityScheduleRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
$requestBody->setJustification('Assign User Admin eligibility to IT Helpdesk (User) group');
$requestBody->setRoleDefinitionId('fe930be7-5e62-47db-91af-98c3a49a38b1');
$requestBody->setDirectoryScopeId('/');
$requestBody->setPrincipalId('1189bbdd-1268-4a72-8c6d-6fe77d28f2e3');
$scheduleInfo = new RequestSchedule();
$scheduleInfo->setStartDateTime(new \DateTime('2025-03-21T11:06:00Z'));
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setEndDateTime(new \DateTime('2026-03-21T00:00:00Z'));
$scheduleInfoExpiration->setType(new ExpirationPatternType('afterDateTime'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);

$result = $graphServiceClient->roleManagement()->directory()->roleEligibilityScheduleRequests()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	action = "AdminAssign"
	justification = "Assign User Admin eligibility to IT Helpdesk (User) group"
	roleDefinitionId = "fe930be7-5e62-47db-91af-98c3a49a38b1"
	directoryScopeId = "/"
	principalId = "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3"
	scheduleInfo = @{
		startDateTime = [System.DateTime]::Parse("2025-03-21T11:06:00Z")
		expiration = @{
			endDateTime = [System.DateTime]::Parse("2026-03-21T00:00:00Z")
			type = "AfterDateTime"
		}
	}
}

New-MgRoleManagementDirectoryRoleEligibilityScheduleRequest -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
	justification = "Assign User Admin eligibility to IT Helpdesk (User) group",
	role_definition_id = "fe930be7-5e62-47db-91af-98c3a49a38b1",
	directory_scope_id = "/",
	principal_id = "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3",
	schedule_info = RequestSchedule(
		start_date_time = "2025-03-21T11:06:00Z",
		expiration = ExpirationPattern(
			end_date_time = "2026-03-21T00:00:00Z",
			type = ExpirationPatternType.AfterDateTime,
		),
	),
)

result = await graph_client.role_management.directory.role_eligibility_schedule_requests.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#roleManagement/directory/roleEligibilityScheduleRequests/$entity",
    "id": "12956159-24b8-4619-b9ea-8ce21f81a38f",
    "status": "Provisioned",
    "createdDateTime": "2025-03-21T11:07:23.4563591Z",
    "completedDateTime": "2025-03-21T11:07:24.8573295Z",
    "action": "adminAssign",
    "principalId": "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3",
    "roleDefinitionId": "fe930be7-5e62-47db-91af-98c3a49a38b1",
    "directoryScopeId": "/",
    "targetScheduleId": "12956159-24b8-4619-b9ea-8ce21f81a38f",
    "justification": "Assign User Admin eligibility to IT Helpdesk (User) group",
    "createdBy": {
        "application": null,
        "device": null,
        "user": {
            "id": "e2330663-f949-41b5-a3dc-faeb793e14c6"
        }
    },
    "scheduleInfo": {
        "startDateTime": "2025-03-21T11:07:24.8573295Z",
        "expiration": {
            "type": "afterDateTime",
            "endDateTime": "2026-03-21T00:00:00Z",
            "duration": null
        }
    },
    "ticketInfo": {}
}
```

## Step 3: Confirm the user's current role assignments

Group members are now eligible for the User Administrator role but can't use the role until they activate it. The following request confirms the user's existing active role assignments. The request returns an empty collection.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/roleManagement/directory/roleAssignments?$filter=principalId eq 'd9771b4c-06c5-491a-92cb-3aa4e225a725'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.RoleAssignments.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "principalId eq 'd9771b4c-06c5-491a-92cb-3aa4e225a725'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphrolemanagement "github.com/microsoftgraph/msgraph-sdk-go/rolemanagement"
	  //other-imports
)


requestFilter := "principalId eq 'd9771b4c-06c5-491a-92cb-3aa4e225a725'"

requestParameters := &graphrolemanagement.DirectoryRoleAssignmentsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphrolemanagement.DirectoryRoleAssignmentsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleAssignments, err := graphClient.RoleManagement().Directory().RoleAssignments().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleAssignmentCollectionResponse result = graphClient.roleManagement().directory().roleAssignments().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "principalId eq 'd9771b4c-06c5-491a-92cb-3aa4e225a725'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let roleAssignments = await client.api('/roleManagement/directory/roleAssignments')
	.filter('principalId eq \'d9771b4c-06c5-491a-92cb-3aa4e225a725\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\RoleManagement\Directory\RoleAssignments\RoleAssignmentsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new RoleAssignmentsRequestBuilderGetRequestConfiguration();
$queryParameters = RoleAssignmentsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "principalId eq 'd9771b4c-06c5-491a-92cb-3aa4e225a725'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->roleManagement()->directory()->roleAssignments()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgRoleManagementDirectoryRoleAssignment -Filter "principalId eq 'd9771b4c-06c5-491a-92cb-3aa4e225a725'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.role_management.directory.role_assignments.role_assignments_request_builder import RoleAssignmentsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = RoleAssignmentsRequestBuilder.RoleAssignmentsRequestBuilderGetQueryParameters(
		filter = "principalId eq 'd9771b4c-06c5-491a-92cb-3aa4e225a725'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.role_management.directory.role_assignments.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Step 4: User self-activates their eligible assignment

An incident ticket `CONTOSO: Security-012345` requires invalidating all employee refresh tokens. As an IT Helpdesk member, Aline wants to resolve this task.

Start the Authenticator app on your phone and open Aline Dupuy's account.

Sign in to Graph Explorer as Aline. The following request shows how to activate your User Administrator role for five hours.

### Request

To activate a role, call the `roleAssignmentScheduleRequests` endpoint. In this request, the `UserActivate` action allows you to activate your eligible assignment.

- For **principalId**, supply the value of your \(Aline's\) **id**.
- The **roleDefinitionId** is the **id** of the role you're eligible for, in this case, the User Administrator role.
- Enter the details of the ticket system that provides an auditable justification for activating the request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/roleManagement/directory/roleAssignmentScheduleRequests
Content-type: application/json

{
    "action": "SelfActivate",
    "principalId": "d9771b4c-06c5-491a-92cb-3aa4e225a725",
    "roleDefinitionId": "fe930be7-5e62-47db-91af-98c3a49a38b1",
    "directoryScopeId": "/",
    "justification": "Need to invalidate all app refresh tokens for Contoso users.",
    "scheduleInfo": {
        "startDateTime": "2025-03-21T11:46:00.000Z",
        "expiration": {
            "type": "AfterDuration",
            "duration": "PT5H"
        }
    },
    "ticketInfo": {
        "ticketNumber": "CONTOSO:Security-012345",
        "ticketSystem": "Contoso ICM"
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
	PrincipalId = "d9771b4c-06c5-491a-92cb-3aa4e225a725",
	RoleDefinitionId = "fe930be7-5e62-47db-91af-98c3a49a38b1",
	DirectoryScopeId = "/",
	Justification = "Need to invalidate all app refresh tokens for Contoso users.",
	ScheduleInfo = new RequestSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2025-03-21T11:46:00.000Z"),
		Expiration = new ExpirationPattern
		{
			Type = ExpirationPatternType.AfterDuration,
			Duration = TimeSpan.Parse("PT5H"),
		},
	},
	TicketInfo = new TicketInfo
	{
		TicketNumber = "CONTOSO:Security-012345",
		TicketSystem = "Contoso ICM",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.RoleAssignmentScheduleRequests.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
principalId := "d9771b4c-06c5-491a-92cb-3aa4e225a725"
requestBody.SetPrincipalId(&principalId) 
roleDefinitionId := "fe930be7-5e62-47db-91af-98c3a49a38b1"
requestBody.SetRoleDefinitionId(&roleDefinitionId) 
directoryScopeId := "/"
requestBody.SetDirectoryScopeId(&directoryScopeId) 
justification := "Need to invalidate all app refresh tokens for Contoso users."
requestBody.SetJustification(&justification) 
scheduleInfo := graphmodels.NewRequestSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2025-03-21T11:46:00.000Z")
scheduleInfo.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
type := graphmodels.AFTERDURATION_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
duration , err := abstractions.ParseISODuration("PT5H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)
ticketInfo := graphmodels.NewTicketInfo()
ticketNumber := "CONTOSO:Security-012345"
ticketInfo.SetTicketNumber(&ticketNumber) 
ticketSystem := "Contoso ICM"
ticketInfo.SetTicketSystem(&ticketSystem) 
requestBody.SetTicketInfo(ticketInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleAssignmentScheduleRequests, err := graphClient.RoleManagement().Directory().RoleAssignmentScheduleRequests().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleAssignmentScheduleRequest unifiedRoleAssignmentScheduleRequest = new UnifiedRoleAssignmentScheduleRequest();
unifiedRoleAssignmentScheduleRequest.setAction(UnifiedRoleScheduleRequestActions.SelfActivate);
unifiedRoleAssignmentScheduleRequest.setPrincipalId("d9771b4c-06c5-491a-92cb-3aa4e225a725");
unifiedRoleAssignmentScheduleRequest.setRoleDefinitionId("fe930be7-5e62-47db-91af-98c3a49a38b1");
unifiedRoleAssignmentScheduleRequest.setDirectoryScopeId("/");
unifiedRoleAssignmentScheduleRequest.setJustification("Need to invalidate all app refresh tokens for Contoso users.");
RequestSchedule scheduleInfo = new RequestSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2025-03-21T11:46:00.000Z");
scheduleInfo.setStartDateTime(startDateTime);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.AfterDuration);
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT5H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
unifiedRoleAssignmentScheduleRequest.setScheduleInfo(scheduleInfo);
TicketInfo ticketInfo = new TicketInfo();
ticketInfo.setTicketNumber("CONTOSO:Security-012345");
ticketInfo.setTicketSystem("Contoso ICM");
unifiedRoleAssignmentScheduleRequest.setTicketInfo(ticketInfo);
UnifiedRoleAssignmentScheduleRequest result = graphClient.roleManagement().directory().roleAssignmentScheduleRequests().post(unifiedRoleAssignmentScheduleRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleAssignmentScheduleRequest = {
    action: 'SelfActivate',
    principalId: 'd9771b4c-06c5-491a-92cb-3aa4e225a725',
    roleDefinitionId: 'fe930be7-5e62-47db-91af-98c3a49a38b1',
    directoryScopeId: '/',
    justification: 'Need to invalidate all app refresh tokens for Contoso users.',
    scheduleInfo: {
        startDateTime: '2025-03-21T11:46:00.000Z',
        expiration: {
            type: 'AfterDuration',
            duration: 'PT5H'
        }
    },
    ticketInfo: {
        ticketNumber: 'CONTOSO:Security-012345',
        ticketSystem: 'Contoso ICM'
    }
};

await client.api('/roleManagement/directory/roleAssignmentScheduleRequests')
	.post(unifiedRoleAssignmentScheduleRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
$requestBody->setPrincipalId('d9771b4c-06c5-491a-92cb-3aa4e225a725');
$requestBody->setRoleDefinitionId('fe930be7-5e62-47db-91af-98c3a49a38b1');
$requestBody->setDirectoryScopeId('/');
$requestBody->setJustification('Need to invalidate all app refresh tokens for Contoso users.');
$scheduleInfo = new RequestSchedule();
$scheduleInfo->setStartDateTime(new \DateTime('2025-03-21T11:46:00.000Z'));
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setType(new ExpirationPatternType('afterDuration'));
$scheduleInfoExpiration->setDuration(new \DateInterval('PT5H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);
$ticketInfo = new TicketInfo();
$ticketInfo->setTicketNumber('CONTOSO:Security-012345');
$ticketInfo->setTicketSystem('Contoso ICM');
$requestBody->setTicketInfo($ticketInfo);

$result = $graphServiceClient->roleManagement()->directory()->roleAssignmentScheduleRequests()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	action = "SelfActivate"
	principalId = "d9771b4c-06c5-491a-92cb-3aa4e225a725"
	roleDefinitionId = "fe930be7-5e62-47db-91af-98c3a49a38b1"
	directoryScopeId = "/"
	justification = "Need to invalidate all app refresh tokens for Contoso users."
	scheduleInfo = @{
		startDateTime = [System.DateTime]::Parse("2025-03-21T11:46:00.000Z")
		expiration = @{
			type = "AfterDuration"
			duration = "PT5H"
		}
	}
	ticketInfo = @{
		ticketNumber = "CONTOSO:Security-012345"
		ticketSystem = "Contoso ICM"
	}
}

New-MgRoleManagementDirectoryRoleAssignmentScheduleRequest -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
	principal_id = "d9771b4c-06c5-491a-92cb-3aa4e225a725",
	role_definition_id = "fe930be7-5e62-47db-91af-98c3a49a38b1",
	directory_scope_id = "/",
	justification = "Need to invalidate all app refresh tokens for Contoso users.",
	schedule_info = RequestSchedule(
		start_date_time = "2025-03-21T11:46:00.000Z",
		expiration = ExpirationPattern(
			type = ExpirationPatternType.AfterDuration,
			duration = "PT5H",
		),
	),
	ticket_info = TicketInfo(
		ticket_number = "CONTOSO:Security-012345",
		ticket_system = "Contoso ICM",
	),
)

result = await graph_client.role_management.directory.role_assignment_schedule_requests.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#roleManagement/directory/roleAssignmentScheduleRequests/$entity",
    "id": "fdde3804-2cd0-4349-b1f6-674927c94f0b",
    "status": "Provisioned",
    "createdDateTime": "2025-03-21T11:46:41.9645736Z",
    "completedDateTime": "2025-03-21T11:46:42.4165908Z",
    "action": "selfActivate",
    "principalId": "d9771b4c-06c5-491a-92cb-3aa4e225a725",
    "roleDefinitionId": "fe930be7-5e62-47db-91af-98c3a49a38b1",
    "directoryScopeId": "/",
    "isValidationOnly": false,
    "targetScheduleId": "fdde3804-2cd0-4349-b1f6-674927c94f0b",
    "justification": "Need to invalidate all app refresh tokens for Contoso users.",
    "createdBy": {
        "user": {
            "id": "d9771b4c-06c5-491a-92cb-3aa4e225a725"
        }
    },
    "scheduleInfo": {
        "startDateTime": "2025-03-21T11:46:42.4165908Z",
        "expiration": {
            "type": "afterDuration",
            "endDateTime": null,
            "duration": "PT5H"
        }
    },
    "ticketInfo": {
        "ticketNumber": "CONTOSO:Security-012345",
        "ticketSystem": "Contoso ICM"
    }
}
```

## Step 5: Confirm the role assignment

You can confirm your assignment by running the following request. The response object returns your newly activated role assignment with its status set to either `Provisioned` or `Granted`. With your new privilege, carry out any allowed actions within five hours your assignment is active for. After five hours, the active assignment expires but through your membership in the **IT Support \(Users\)** group, you're eligible for the User Administrator role.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
GET https://graph.microsoft.com/v1.0/roleManagement/directory/roleAssignmentScheduleRequests/filterByCurrentUser(on='principal')?$expand=roleDefinition
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.RoleAssignmentScheduleRequests.FilterByCurrentUserWithOn("principal").GetAsFilterByCurrentUserWithOnGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "roleDefinition" };
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphrolemanagement "github.com/microsoftgraph/msgraph-sdk-go/rolemanagement"
	  //other-imports
)

requestParameters := &graphrolemanagement.DirectoryRoleAssignmentScheduleRequestsFilterByCurrentUserWithOnRequestBuilderGetQueryParameters{
	Expand: [] string {"roleDefinition"},
}
configuration := &graphrolemanagement.DirectoryRoleAssignmentScheduleRequestsFilterByCurrentUserWithOnRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
on := "principal"
filterByCurrentUser, err := graphClient.RoleManagement().Directory().RoleAssignmentScheduleRequests().FilterByCurrentUserWithOn(&on).GetAsFilterByCurrentUserWithOnGetResponse(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.roleManagement().directory().roleAssignmentScheduleRequests().filterByCurrentUserWithOn("principal").get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"roleDefinition"};
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let filterByCurrentUser = await client.api('/roleManagement/directory/roleAssignmentScheduleRequests/filterByCurrentUser(on='principal')')
	.expand('roleDefinition')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\RoleManagement\Directory\RoleAssignmentScheduleRequests\FilterByCurrentUser(on='{on}')\FilterByCurrentUserWithOnRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new FilterByCurrentUserWithOnRequestBuilderGetRequestConfiguration();
$queryParameters = FilterByCurrentUserWithOnRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["roleDefinition"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->roleManagement()->directory()->roleAssignmentScheduleRequests()->filterByCurrentUserWithOn('principal', )->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Invoke-MgFilterRoleManagementDirectoryRoleAssignmentScheduleRequestByCurrentUser -ExpandProperty "roleDefinition"  -On $onId 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.role_management.directory.role_assignment_schedule_requests.filter_by_current_user(on='{on}').filter_by_current_user_with_on_request_builder import FilterByCurrentUserWithOnRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = FilterByCurrentUserWithOnRequestBuilder.FilterByCurrentUserWithOnRequestBuilderGetQueryParameters(
		expand = ["roleDefinition"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.role_management.directory.role_assignment_schedule_requests.filter_by_current_user_with_on("principal").get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Step 6: Clean up resources

Sign in as the Privileged Role Administrator and delete the resources created for this tutorial.

### Revoke the role eligibility for the group

#### Request

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/v1.0/roleManagement/directory/roleEligibilityScheduleRequests
Content-type: application/json

{
    "action": "AdminRemove",
    "principalId": "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3",
    "roleDefinitionId": "fe930be7-5e62-47db-91af-98c3a49a38b1",
    "directoryScopeId": "/"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleEligibilityScheduleRequest
{
	Action = UnifiedRoleScheduleRequestActions.AdminRemove,
	PrincipalId = "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3",
	RoleDefinitionId = "fe930be7-5e62-47db-91af-98c3a49a38b1",
	DirectoryScopeId = "/",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.RoleEligibilityScheduleRequests.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
principalId := "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3"
requestBody.SetPrincipalId(&principalId) 
roleDefinitionId := "fe930be7-5e62-47db-91af-98c3a49a38b1"
requestBody.SetRoleDefinitionId(&roleDefinitionId) 
directoryScopeId := "/"
requestBody.SetDirectoryScopeId(&directoryScopeId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleEligibilityScheduleRequests, err := graphClient.RoleManagement().Directory().RoleEligibilityScheduleRequests().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleEligibilityScheduleRequest unifiedRoleEligibilityScheduleRequest = new UnifiedRoleEligibilityScheduleRequest();
unifiedRoleEligibilityScheduleRequest.setAction(UnifiedRoleScheduleRequestActions.AdminRemove);
unifiedRoleEligibilityScheduleRequest.setPrincipalId("1189bbdd-1268-4a72-8c6d-6fe77d28f2e3");
unifiedRoleEligibilityScheduleRequest.setRoleDefinitionId("fe930be7-5e62-47db-91af-98c3a49a38b1");
unifiedRoleEligibilityScheduleRequest.setDirectoryScopeId("/");
UnifiedRoleEligibilityScheduleRequest result = graphClient.roleManagement().directory().roleEligibilityScheduleRequests().post(unifiedRoleEligibilityScheduleRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleEligibilityScheduleRequest = {
    action: 'AdminRemove',
    principalId: '1189bbdd-1268-4a72-8c6d-6fe77d28f2e3',
    roleDefinitionId: 'fe930be7-5e62-47db-91af-98c3a49a38b1',
    directoryScopeId: '/'
};

await client.api('/roleManagement/directory/roleEligibilityScheduleRequests')
	.post(unifiedRoleEligibilityScheduleRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleEligibilityScheduleRequest;
use Microsoft\Graph\Generated\Models\UnifiedRoleScheduleRequestActions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleEligibilityScheduleRequest();
$requestBody->setAction(new UnifiedRoleScheduleRequestActions('adminRemove'));
$requestBody->setPrincipalId('1189bbdd-1268-4a72-8c6d-6fe77d28f2e3');
$requestBody->setRoleDefinitionId('fe930be7-5e62-47db-91af-98c3a49a38b1');
$requestBody->setDirectoryScopeId('/');

$result = $graphServiceClient->roleManagement()->directory()->roleEligibilityScheduleRequests()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	action = "AdminRemove"
	principalId = "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3"
	roleDefinitionId = "fe930be7-5e62-47db-91af-98c3a49a38b1"
	directoryScopeId = "/"
}

New-MgRoleManagementDirectoryRoleEligibilityScheduleRequest -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_eligibility_schedule_request import UnifiedRoleEligibilityScheduleRequest
from msgraph.generated.models.unified_role_schedule_request_actions import UnifiedRoleScheduleRequestActions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleEligibilityScheduleRequest(
	action = UnifiedRoleScheduleRequestActions.AdminRemove,
	principal_id = "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3",
	role_definition_id = "fe930be7-5e62-47db-91af-98c3a49a38b1",
	directory_scope_id = "/",
)

result = await graph_client.role_management.directory.role_eligibility_schedule_requests.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#roleManagement/directory/roleEligibilityScheduleRequests/$entity",
    "id": "749ebf39-ffa9-4f43-aaaf-58e0d41f9efc",
    "status": "Revoked",
    "createdDateTime": "2025-03-21T12:03:14.551954Z",
    "action": "adminRemove",
    "principalId": "1189bbdd-1268-4a72-8c6d-6fe77d28f2e3",
    "roleDefinitionId": "fe930be7-5e62-47db-91af-98c3a49a38b1",
    "directoryScopeId": "/",
    "createdBy": {
        "user": {
            "displayName": null,
            "id": "e2330663-f949-41b5-a3dc-faeb793e14c6"
        }
    }
}
```

### Delete the IT Support \(Users\) group

The request returns a `204 No Content` response code.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
DELETE https://graph.microsoft.com/v1.0/groups/d9771b4c-06c5-491a-92cb-3aa4e225a725
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Groups["{group-id}"].DeleteAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Groups().ByGroupId("group-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.groups().byGroupId("{group-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/groups/d9771b4c-06c5-491a-92cb-3aa4e225a725')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->groups()->byGroupId('group-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

Remove-MgGroup -GroupId $groupId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.groups.by_group_id('group-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Conclusion

In this tutorial, you learned how to manage privileged role assignments in Microsoft Entra ID using PIM APIs.

- Instead of making the group eligible for the privileged role, you can assign an active role to the group and make members eligible for the group using PIM for Groups APIs.
- MFA was required for role activation. You can change this requirement in Microsoft Entra role settings.
- You can also configure:

  - Maximum allowed duration for role activation.
  - Whether justification and ticket information are required for activating the role.

## Related content

- [Assign Microsoft Entra roles in Privileged Identity Management using Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/tutorial-pim)
- [Overview of role management through PIM](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview)
- [Govern membership and ownership of groups using PIM for groups](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagement-for-groups-api-overview)
- [Rules in PIM - mapping guide](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview)
