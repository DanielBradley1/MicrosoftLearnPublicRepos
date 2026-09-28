<!-- Source: https://learn.microsoft.com/en-us/graph/api/permissionsmanagement-post-scheduledpermissionsrequests?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-18 -->

# Create scheduledPermissionsRequest

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Create a new [scheduledPermissionsRequest](https://learn.microsoft.com/en-us/graph/api/resources/scheduledpermissionsrequest?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ScheduledPermissions.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /identityGovernance/permissionsManagement/scheduledPermissionsRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [scheduledPermissionsRequest](https://learn.microsoft.com/en-us/graph/api/resources/scheduledpermissionsrequest?view=graph-rest-beta) object.

You can specify the following properties when creating a **scheduledPermissionsRequest**.

| Property | Type | Description |
| :--- | :--- | :--- |
| requestedPermissions | [permissionsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinition?view=graph-rest-beta) | Defines the permission request itself. Required.  <br>You must specify the **@odata.type** property with the value of the **permissionDefinition** object type in the request body. For example `"@odata.type": "#microsoft.graph.awsPermissionsDefinition"`. |
| notes | String | Additional notes to add to the request. Optional. |
| justification | String | Request justification. Optional. |
| createdDateTime | DateTimeOffset | Time when the scheduledPermissionsRequest was created. Required. |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-beta) | Schedule to assign the requestedPermissions. Optional. |
| ticketInfo | [ticketInfo](https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-beta) | Represents ticketing related metadata that can be used to correlate to the request. Optional. |
| statusDetail | statusDetail | The current status of the request. The possible values are: `submitted`, `approved`, `completed`, `canceled`, `rejected`, `unknownFutureValue`. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [scheduledPermissionsRequest](https://learn.microsoft.com/en-us/graph/api/resources/scheduledpermissionsrequest?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: AWS policy request

#### Request

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
POST https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/scheduledPermissionsRequests
Content-Type: application/json

{
  "requestedPermissions": {
    "@odata.type": "#microsoft.graph.awsPermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "956987887735",
      "authorizationSystemType": "AWS"
    },
    "actionInfo": {
      "@odata.type": "microsoft.graph.awsPolicyPermissionsDefinitionAction",
      "policies": [
        {
          "id": "arn:aws:iam::956987887735:policy/AddUserToGroup"
        }
      ],
      "assignToRoleId": "arn:aws:aim::956987887735:role/saml-user"
    },
    "identityInfo": {
      "externalId": "alex@contoso.com",
      "source": {
        "@odata.type": "microsoft.graph.samlIdentitySource"
      },
      "identityType": "user"
    }
  },
  "justification": "I need to do this because I want to add a user to a group",
  "notes": "Pretty Please",
  "scheduleInfo": {
    "expiration": {
      "duration": "PT1H"
    }
  },
  "ticketInfo": {
    "ticketNumber": "INC1234567",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ScheduledPermissionsRequest
{
	RequestedPermissions = new AwsPermissionsDefinition
	{
		OdataType = "#microsoft.graph.awsPermissionsDefinition",
		AuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem
		{
			AuthorizationSystemId = "956987887735",
			AuthorizationSystemType = "AWS",
		},
		ActionInfo = new AwsPolicyPermissionsDefinitionAction
		{
			OdataType = "microsoft.graph.awsPolicyPermissionsDefinitionAction",
			Policies = new List<PermissionsDefinitionAwsPolicy>
			{
				new PermissionsDefinitionAwsPolicy
				{
					Id = "arn:aws:iam::956987887735:policy/AddUserToGroup",
				},
			},
			AssignToRoleId = "arn:aws:aim::956987887735:role/saml-user",
		},
		IdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity
		{
			ExternalId = "alex@contoso.com",
			Source = new SamlIdentitySource
			{
				OdataType = "microsoft.graph.samlIdentitySource",
			},
			IdentityType = PermissionsDefinitionIdentityType.User,
		},
	},
	Justification = "I need to do this because I want to add a user to a group",
	Notes = "Pretty Please",
	ScheduleInfo = new RequestSchedule
	{
		Expiration = new ExpirationPattern
		{
			Duration = TimeSpan.Parse("PT1H"),
		},
	},
	TicketInfo = new TicketInfo
	{
		TicketNumber = "INC1234567",
		TicketSystem = "ServiceNow",
		TicketSubmitterIdentityId = "alex@contoso.com",
		TicketApproverIdentityId = "alexmanager@contoso.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PermissionsManagement.ScheduledPermissionsRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewScheduledPermissionsRequest()
requestedPermissions := graphmodels.NewAwsPermissionsDefinition()
authorizationSystemInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystem()
authorizationSystemId := "956987887735"
authorizationSystemInfo.SetAuthorizationSystemId(&authorizationSystemId) 
authorizationSystemType := "AWS"
authorizationSystemInfo.SetAuthorizationSystemType(&authorizationSystemType) 
requestedPermissions.SetAuthorizationSystemInfo(authorizationSystemInfo)
actionInfo := graphmodels.NewAwsPolicyPermissionsDefinitionAction()


permissionsDefinitionAwsPolicy := graphmodels.NewPermissionsDefinitionAwsPolicy()
id := "arn:aws:iam::956987887735:policy/AddUserToGroup"
permissionsDefinitionAwsPolicy.SetId(&id) 

policies := []graphmodels.PermissionsDefinitionAwsPolicyable {
	permissionsDefinitionAwsPolicy,
}
actionInfo.SetPolicies(policies)
assignToRoleId := "arn:aws:aim::956987887735:role/saml-user"
actionInfo.SetAssignToRoleId(&assignToRoleId) 
requestedPermissions.SetActionInfo(actionInfo)
identityInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystemIdentity()
externalId := "alex@contoso.com"
identityInfo.SetExternalId(&externalId) 
source := graphmodels.NewSamlIdentitySource()
identityInfo.SetSource(source)
identityType := graphmodels.USER_PERMISSIONSDEFINITIONIDENTITYTYPE 
identityInfo.SetIdentityType(&identityType) 
requestedPermissions.SetIdentityInfo(identityInfo)
requestBody.SetRequestedPermissions(requestedPermissions)
justification := "I need to do this because I want to add a user to a group"
requestBody.SetJustification(&justification) 
notes := "Pretty Please"
requestBody.SetNotes(&notes) 
scheduleInfo := graphmodels.NewRequestSchedule()
expiration := graphmodels.NewExpirationPattern()
duration , err := abstractions.ParseISODuration("PT1H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)
ticketInfo := graphmodels.NewTicketInfo()
ticketNumber := "INC1234567"
ticketInfo.SetTicketNumber(&ticketNumber) 
ticketSystem := "ServiceNow"
ticketInfo.SetTicketSystem(&ticketSystem) 
ticketSubmitterIdentityId := "alex@contoso.com"
ticketInfo.SetTicketSubmitterIdentityId(&ticketSubmitterIdentityId) 
ticketApproverIdentityId := "alexmanager@contoso.com"
ticketInfo.SetTicketApproverIdentityId(&ticketApproverIdentityId) 
requestBody.SetTicketInfo(ticketInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
scheduledPermissionsRequests, err := graphClient.IdentityGovernance().PermissionsManagement().ScheduledPermissionsRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ScheduledPermissionsRequest scheduledPermissionsRequest = new ScheduledPermissionsRequest();
AwsPermissionsDefinition requestedPermissions = new AwsPermissionsDefinition();
requestedPermissions.setOdataType("#microsoft.graph.awsPermissionsDefinition");
PermissionsDefinitionAuthorizationSystem authorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
authorizationSystemInfo.setAuthorizationSystemId("956987887735");
authorizationSystemInfo.setAuthorizationSystemType("AWS");
requestedPermissions.setAuthorizationSystemInfo(authorizationSystemInfo);
AwsPolicyPermissionsDefinitionAction actionInfo = new AwsPolicyPermissionsDefinitionAction();
actionInfo.setOdataType("microsoft.graph.awsPolicyPermissionsDefinitionAction");
LinkedList<PermissionsDefinitionAwsPolicy> policies = new LinkedList<PermissionsDefinitionAwsPolicy>();
PermissionsDefinitionAwsPolicy permissionsDefinitionAwsPolicy = new PermissionsDefinitionAwsPolicy();
permissionsDefinitionAwsPolicy.setId("arn:aws:iam::956987887735:policy/AddUserToGroup");
policies.add(permissionsDefinitionAwsPolicy);
actionInfo.setPolicies(policies);
actionInfo.setAssignToRoleId("arn:aws:aim::956987887735:role/saml-user");
requestedPermissions.setActionInfo(actionInfo);
PermissionsDefinitionAuthorizationSystemIdentity identityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
identityInfo.setExternalId("alex@contoso.com");
SamlIdentitySource source = new SamlIdentitySource();
source.setOdataType("microsoft.graph.samlIdentitySource");
identityInfo.setSource(source);
identityInfo.setIdentityType(PermissionsDefinitionIdentityType.User);
requestedPermissions.setIdentityInfo(identityInfo);
scheduledPermissionsRequest.setRequestedPermissions(requestedPermissions);
scheduledPermissionsRequest.setJustification("I need to do this because I want to add a user to a group");
scheduledPermissionsRequest.setNotes("Pretty Please");
RequestSchedule scheduleInfo = new RequestSchedule();
ExpirationPattern expiration = new ExpirationPattern();
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
scheduledPermissionsRequest.setScheduleInfo(scheduleInfo);
TicketInfo ticketInfo = new TicketInfo();
ticketInfo.setTicketNumber("INC1234567");
ticketInfo.setTicketSystem("ServiceNow");
ticketInfo.setTicketSubmitterIdentityId("alex@contoso.com");
ticketInfo.setTicketApproverIdentityId("alexmanager@contoso.com");
scheduledPermissionsRequest.setTicketInfo(ticketInfo);
ScheduledPermissionsRequest result = graphClient.identityGovernance().permissionsManagement().scheduledPermissionsRequests().post(scheduledPermissionsRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const scheduledPermissionsRequest = {
  requestedPermissions: {
    '@odata.type': '#microsoft.graph.awsPermissionsDefinition',
    authorizationSystemInfo: {
      authorizationSystemId: '956987887735',
      authorizationSystemType: 'AWS'
    },
    actionInfo: {
      '@odata.type': 'microsoft.graph.awsPolicyPermissionsDefinitionAction',
      policies: [
        {
          id: 'arn:aws:iam::956987887735:policy/AddUserToGroup'
        }
      ],
      assignToRoleId: 'arn:aws:aim::956987887735:role/saml-user'
    },
    identityInfo: {
      externalId: 'alex@contoso.com',
      source: {
        '@odata.type': 'microsoft.graph.samlIdentitySource'
      },
      identityType: 'user'
    }
  },
  justification: 'I need to do this because I want to add a user to a group',
  notes: 'Pretty Please',
  scheduleInfo: {
    expiration: {
      duration: 'PT1H'
    }
  },
  ticketInfo: {
    ticketNumber: 'INC1234567',
    ticketSystem: 'ServiceNow',
    ticketSubmitterIdentityId: 'alex@contoso.com',
    ticketApproverIdentityId: 'alexmanager@contoso.com'
  }
};

await client.api('/identityGovernance/permissionsManagement/scheduledPermissionsRequests')
	.version('beta')
	.post(scheduledPermissionsRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ScheduledPermissionsRequest;
use Microsoft\Graph\Beta\Generated\Models\AwsPermissionsDefinition;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystem;
use Microsoft\Graph\Beta\Generated\Models\AwsPolicyPermissionsDefinitionAction;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAwsPolicy;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystemIdentity;
use Microsoft\Graph\Beta\Generated\Models\SamlIdentitySource;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionIdentityType;
use Microsoft\Graph\Beta\Generated\Models\RequestSchedule;
use Microsoft\Graph\Beta\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Beta\Generated\Models\TicketInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ScheduledPermissionsRequest();
$requestedPermissions = new AwsPermissionsDefinition();
$requestedPermissions->setOdataType('#microsoft.graph.awsPermissionsDefinition');
$requestedPermissionsAuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemId('956987887735');
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemType('AWS');
$requestedPermissions->setAuthorizationSystemInfo($requestedPermissionsAuthorizationSystemInfo);
$requestedPermissionsActionInfo = new AwsPolicyPermissionsDefinitionAction();
$requestedPermissionsActionInfo->setOdataType('microsoft.graph.awsPolicyPermissionsDefinitionAction');
$policiesPermissionsDefinitionAwsPolicy1 = new PermissionsDefinitionAwsPolicy();
$policiesPermissionsDefinitionAwsPolicy1->setId('arn:aws:iam::956987887735:policy/AddUserToGroup');
$policiesArray []= $policiesPermissionsDefinitionAwsPolicy1;
$requestedPermissionsActionInfo->setPolicies($policiesArray);

$requestedPermissionsActionInfo->setAssignToRoleId('arn:aws:aim::956987887735:role/saml-user');
$requestedPermissions->setActionInfo($requestedPermissionsActionInfo);
$requestedPermissionsIdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
$requestedPermissionsIdentityInfo->setExternalId('alex@contoso.com');
$requestedPermissionsIdentityInfoSource = new SamlIdentitySource();
$requestedPermissionsIdentityInfoSource->setOdataType('microsoft.graph.samlIdentitySource');
$requestedPermissionsIdentityInfo->setSource($requestedPermissionsIdentityInfoSource);
$requestedPermissionsIdentityInfo->setIdentityType(new PermissionsDefinitionIdentityType('user'));
$requestedPermissions->setIdentityInfo($requestedPermissionsIdentityInfo);
$requestBody->setRequestedPermissions($requestedPermissions);
$requestBody->setJustification('I need to do this because I want to add a user to a group');
$requestBody->setNotes('Pretty Please');
$scheduleInfo = new RequestSchedule();
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setDuration(new \DateInterval('PT1H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);
$ticketInfo = new TicketInfo();
$ticketInfo->setTicketNumber('INC1234567');
$ticketInfo->setTicketSystem('ServiceNow');
$ticketInfo->setTicketSubmitterIdentityId('alex@contoso.com');
$ticketInfo->setTicketApproverIdentityId('alexmanager@contoso.com');
$requestBody->setTicketInfo($ticketInfo);

$result = $graphServiceClient->identityGovernance()->permissionsManagement()->scheduledPermissionsRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestedPermissions = @{
		"@odata.type" = "#microsoft.graph.awsPermissionsDefinition"
		authorizationSystemInfo = @{
			authorizationSystemId = "956987887735"
			authorizationSystemType = "AWS"
		}
		actionInfo = @{
			"@odata.type" = "microsoft.graph.awsPolicyPermissionsDefinitionAction"
			policies = @(
				@{
					id = "arn:aws:iam::956987887735:policy/AddUserToGroup"
				}
			)
			assignToRoleId = "arn:aws:aim::956987887735:role/saml-user"
		}
		identityInfo = @{
			externalId = "alex@contoso.com"
			source = @{
				"@odata.type" = "microsoft.graph.samlIdentitySource"
			}
			identityType = "user"
		}
	}
	justification = "I need to do this because I want to add a user to a group"
	notes = "Pretty Please"
	scheduleInfo = @{
		expiration = @{
			duration = "PT1H"
		}
	}
	ticketInfo = @{
		ticketNumber = "INC1234567"
		ticketSystem = "ServiceNow"
		ticketSubmitterIdentityId = "alex@contoso.com"
		ticketApproverIdentityId = "alexmanager@contoso.com"
	}
}

New-MgBetaIdentityGovernancePermissionManagementScheduledPermissionRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.scheduled_permissions_request import ScheduledPermissionsRequest
from msgraph_beta.generated.models.aws_permissions_definition import AwsPermissionsDefinition
from msgraph_beta.generated.models.permissions_definition_authorization_system import PermissionsDefinitionAuthorizationSystem
from msgraph_beta.generated.models.aws_policy_permissions_definition_action import AwsPolicyPermissionsDefinitionAction
from msgraph_beta.generated.models.permissions_definition_aws_policy import PermissionsDefinitionAwsPolicy
from msgraph_beta.generated.models.permissions_definition_authorization_system_identity import PermissionsDefinitionAuthorizationSystemIdentity
from msgraph_beta.generated.models.saml_identity_source import SamlIdentitySource
from msgraph_beta.generated.models.permissions_definition_identity_type import PermissionsDefinitionIdentityType
from msgraph_beta.generated.models.request_schedule import RequestSchedule
from msgraph_beta.generated.models.expiration_pattern import ExpirationPattern
from msgraph_beta.generated.models.ticket_info import TicketInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ScheduledPermissionsRequest(
	requested_permissions = AwsPermissionsDefinition(
		odata_type = "#microsoft.graph.awsPermissionsDefinition",
		authorization_system_info = PermissionsDefinitionAuthorizationSystem(
			authorization_system_id = "956987887735",
			authorization_system_type = "AWS",
		),
		action_info = AwsPolicyPermissionsDefinitionAction(
			odata_type = "microsoft.graph.awsPolicyPermissionsDefinitionAction",
			policies = [
				PermissionsDefinitionAwsPolicy(
					id = "arn:aws:iam::956987887735:policy/AddUserToGroup",
				),
			],
			assign_to_role_id = "arn:aws:aim::956987887735:role/saml-user",
		),
		identity_info = PermissionsDefinitionAuthorizationSystemIdentity(
			external_id = "alex@contoso.com",
			source = SamlIdentitySource(
				odata_type = "microsoft.graph.samlIdentitySource",
			),
			identity_type = PermissionsDefinitionIdentityType.User,
		),
	),
	justification = "I need to do this because I want to add a user to a group",
	notes = "Pretty Please",
	schedule_info = RequestSchedule(
		expiration = ExpirationPattern(
			duration = "PT1H",
		),
	),
	ticket_info = TicketInfo(
		ticket_number = "INC1234567",
		ticket_system = "ServiceNow",
		ticket_submitter_identity_id = "alex@contoso.com",
		ticket_approver_identity_id = "alexmanager@contoso.com",
	),
)

result = await graph_client.identity_governance.permissions_management.scheduled_permissions_requests.post(request_body)
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

{
  "@odata.type": "microsoft.graph.scheduledPermissionsRequest",
  "id": "00000000-0000-0000-0000-000000000002",
  "requestedPermissions": {
    "@odata.type": "microsoft.graph.awsPermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "956987887735",
      "authorizationSystemType": "AWS",
    },
    "actionInfo": {
      "@odata.type": "microsoft.graph.awsPolicyPermissionsDefinitionAction",
      "policies": [
        {
          "id": "arn:aws:iam::956987887735:policy/AddUserToGroup"
        }
      ],
      "assignToRoleId": "arn:aws:aim::956987887735:role/saml-user"
    },
    "identityInfo": {
      "externalId": "alex@contoso.com",
      "source": {
        "@odata.type": "microsoft.graph.samlIdentitySource"
      },
      "identityType": "user"
    }
 },
 "justification": "I need to do this because I want to add a user to a group",
 "notes": "Pretty Please",
 "createdDateTime": "2023-02-06T12:15:00Z",
 "scheduleInfo": {
    "expiration": {
      "duration": "PT1H"
    },
 },
 "ticketInfo": {
    "ticketNumber": "INC1234567",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
 },
 "statusDetail": "submitted"
}
```

### Example 2: Azure roles request

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/scheduledPermissionsRequests
Content-Type: application/json

{
  "requestedPermissions": {
    "@odata.type": "microsoft.graph.singleResourceAzurePermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "87eefd90-95a3-480a-ba42-56ff299a05ee",
      "authorizationSystemType": "AZURE"
    },
    "actionInfo": {
      "@odata.type": "microsoft.graph.azureRolePermissionsDefinitionAction",
      "roles": [
        {
          "id": "cdda3590-29a3-44f6-95f2-9f980659eb04"
        },
        {
          "id": "312a565d-c81f-4fd8-895a-4e21e48d571c"
        }
      ]
    },
    "identityInfo": {
      "externalId": "alex@contoso.com",
      "source": {
        "@odata.type": "microsoft.graph.edIdentitySource"
      },
      "identityType": "user"
    },
    "resourceId": "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee"
  },
  "justification": "I need to do this because I want to some new azure roles",
  "notes": "Pretty Pleaseeeee",
  "scheduleInfo": {
    "expiration": {
      "duration": "PT1H"
    },
    "recurrence": null
  },
  "ticketInfo": {
    "ticketNumber": "INC1234567",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ScheduledPermissionsRequest
{
	RequestedPermissions = new SingleResourceAzurePermissionsDefinition
	{
		OdataType = "microsoft.graph.singleResourceAzurePermissionsDefinition",
		AuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem
		{
			AuthorizationSystemId = "87eefd90-95a3-480a-ba42-56ff299a05ee",
			AuthorizationSystemType = "AZURE",
		},
		ActionInfo = new AzureRolePermissionsDefinitionAction
		{
			OdataType = "microsoft.graph.azureRolePermissionsDefinitionAction",
			Roles = new List<PermissionsDefinitionAzureRole>
			{
				new PermissionsDefinitionAzureRole
				{
					Id = "cdda3590-29a3-44f6-95f2-9f980659eb04",
				},
				new PermissionsDefinitionAzureRole
				{
					Id = "312a565d-c81f-4fd8-895a-4e21e48d571c",
				},
			},
		},
		IdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity
		{
			ExternalId = "alex@contoso.com",
			Source = new EdIdentitySource
			{
				OdataType = "microsoft.graph.edIdentitySource",
			},
			IdentityType = PermissionsDefinitionIdentityType.User,
		},
		ResourceId = "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee",
	},
	Justification = "I need to do this because I want to some new azure roles",
	Notes = "Pretty Pleaseeeee",
	ScheduleInfo = new RequestSchedule
	{
		Expiration = new ExpirationPattern
		{
			Duration = TimeSpan.Parse("PT1H"),
		},
		Recurrence = null,
	},
	TicketInfo = new TicketInfo
	{
		TicketNumber = "INC1234567",
		TicketSystem = "ServiceNow",
		TicketSubmitterIdentityId = "alex@contoso.com",
		TicketApproverIdentityId = "alexmanager@contoso.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PermissionsManagement.ScheduledPermissionsRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewScheduledPermissionsRequest()
requestedPermissions := graphmodels.NewSingleResourceAzurePermissionsDefinition()
authorizationSystemInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystem()
authorizationSystemId := "87eefd90-95a3-480a-ba42-56ff299a05ee"
authorizationSystemInfo.SetAuthorizationSystemId(&authorizationSystemId) 
authorizationSystemType := "AZURE"
authorizationSystemInfo.SetAuthorizationSystemType(&authorizationSystemType) 
requestedPermissions.SetAuthorizationSystemInfo(authorizationSystemInfo)
actionInfo := graphmodels.NewAzureRolePermissionsDefinitionAction()


permissionsDefinitionAzureRole := graphmodels.NewPermissionsDefinitionAzureRole()
id := "cdda3590-29a3-44f6-95f2-9f980659eb04"
permissionsDefinitionAzureRole.SetId(&id) 
permissionsDefinitionAzureRole1 := graphmodels.NewPermissionsDefinitionAzureRole()
id := "312a565d-c81f-4fd8-895a-4e21e48d571c"
permissionsDefinitionAzureRole1.SetId(&id) 

roles := []graphmodels.PermissionsDefinitionAzureRoleable {
	permissionsDefinitionAzureRole,
	permissionsDefinitionAzureRole1,
}
actionInfo.SetRoles(roles)
requestedPermissions.SetActionInfo(actionInfo)
identityInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystemIdentity()
externalId := "alex@contoso.com"
identityInfo.SetExternalId(&externalId) 
source := graphmodels.NewEdIdentitySource()
identityInfo.SetSource(source)
identityType := graphmodels.USER_PERMISSIONSDEFINITIONIDENTITYTYPE 
identityInfo.SetIdentityType(&identityType) 
requestedPermissions.SetIdentityInfo(identityInfo)
resourceId := "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee"
requestedPermissions.SetResourceId(&resourceId) 
requestBody.SetRequestedPermissions(requestedPermissions)
justification := "I need to do this because I want to some new azure roles"
requestBody.SetJustification(&justification) 
notes := "Pretty Pleaseeeee"
requestBody.SetNotes(&notes) 
scheduleInfo := graphmodels.NewRequestSchedule()
expiration := graphmodels.NewExpirationPattern()
duration , err := abstractions.ParseISODuration("PT1H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
recurrence := null
scheduleInfo.SetRecurrence(&recurrence) 
requestBody.SetScheduleInfo(scheduleInfo)
ticketInfo := graphmodels.NewTicketInfo()
ticketNumber := "INC1234567"
ticketInfo.SetTicketNumber(&ticketNumber) 
ticketSystem := "ServiceNow"
ticketInfo.SetTicketSystem(&ticketSystem) 
ticketSubmitterIdentityId := "alex@contoso.com"
ticketInfo.SetTicketSubmitterIdentityId(&ticketSubmitterIdentityId) 
ticketApproverIdentityId := "alexmanager@contoso.com"
ticketInfo.SetTicketApproverIdentityId(&ticketApproverIdentityId) 
requestBody.SetTicketInfo(ticketInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
scheduledPermissionsRequests, err := graphClient.IdentityGovernance().PermissionsManagement().ScheduledPermissionsRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ScheduledPermissionsRequest scheduledPermissionsRequest = new ScheduledPermissionsRequest();
SingleResourceAzurePermissionsDefinition requestedPermissions = new SingleResourceAzurePermissionsDefinition();
requestedPermissions.setOdataType("microsoft.graph.singleResourceAzurePermissionsDefinition");
PermissionsDefinitionAuthorizationSystem authorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
authorizationSystemInfo.setAuthorizationSystemId("87eefd90-95a3-480a-ba42-56ff299a05ee");
authorizationSystemInfo.setAuthorizationSystemType("AZURE");
requestedPermissions.setAuthorizationSystemInfo(authorizationSystemInfo);
AzureRolePermissionsDefinitionAction actionInfo = new AzureRolePermissionsDefinitionAction();
actionInfo.setOdataType("microsoft.graph.azureRolePermissionsDefinitionAction");
LinkedList<PermissionsDefinitionAzureRole> roles = new LinkedList<PermissionsDefinitionAzureRole>();
PermissionsDefinitionAzureRole permissionsDefinitionAzureRole = new PermissionsDefinitionAzureRole();
permissionsDefinitionAzureRole.setId("cdda3590-29a3-44f6-95f2-9f980659eb04");
roles.add(permissionsDefinitionAzureRole);
PermissionsDefinitionAzureRole permissionsDefinitionAzureRole1 = new PermissionsDefinitionAzureRole();
permissionsDefinitionAzureRole1.setId("312a565d-c81f-4fd8-895a-4e21e48d571c");
roles.add(permissionsDefinitionAzureRole1);
actionInfo.setRoles(roles);
requestedPermissions.setActionInfo(actionInfo);
PermissionsDefinitionAuthorizationSystemIdentity identityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
identityInfo.setExternalId("alex@contoso.com");
EdIdentitySource source = new EdIdentitySource();
source.setOdataType("microsoft.graph.edIdentitySource");
identityInfo.setSource(source);
identityInfo.setIdentityType(PermissionsDefinitionIdentityType.User);
requestedPermissions.setIdentityInfo(identityInfo);
requestedPermissions.setResourceId("/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee");
scheduledPermissionsRequest.setRequestedPermissions(requestedPermissions);
scheduledPermissionsRequest.setJustification("I need to do this because I want to some new azure roles");
scheduledPermissionsRequest.setNotes("Pretty Pleaseeeee");
RequestSchedule scheduleInfo = new RequestSchedule();
ExpirationPattern expiration = new ExpirationPattern();
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
scheduleInfo.setRecurrence(null);
scheduledPermissionsRequest.setScheduleInfo(scheduleInfo);
TicketInfo ticketInfo = new TicketInfo();
ticketInfo.setTicketNumber("INC1234567");
ticketInfo.setTicketSystem("ServiceNow");
ticketInfo.setTicketSubmitterIdentityId("alex@contoso.com");
ticketInfo.setTicketApproverIdentityId("alexmanager@contoso.com");
scheduledPermissionsRequest.setTicketInfo(ticketInfo);
ScheduledPermissionsRequest result = graphClient.identityGovernance().permissionsManagement().scheduledPermissionsRequests().post(scheduledPermissionsRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const scheduledPermissionsRequest = {
  requestedPermissions: {
    '@odata.type': 'microsoft.graph.singleResourceAzurePermissionsDefinition',
    authorizationSystemInfo: {
      authorizationSystemId: '87eefd90-95a3-480a-ba42-56ff299a05ee',
      authorizationSystemType: 'AZURE'
    },
    actionInfo: {
      '@odata.type': 'microsoft.graph.azureRolePermissionsDefinitionAction',
      roles: [
        {
          id: 'cdda3590-29a3-44f6-95f2-9f980659eb04'
        },
        {
          id: '312a565d-c81f-4fd8-895a-4e21e48d571c'
        }
      ]
    },
    identityInfo: {
      externalId: 'alex@contoso.com',
      source: {
        '@odata.type': 'microsoft.graph.edIdentitySource'
      },
      identityType: 'user'
    },
    resourceId: '/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee'
  },
  justification: 'I need to do this because I want to some new azure roles',
  notes: 'Pretty Pleaseeeee',
  scheduleInfo: {
    expiration: {
      duration: 'PT1H'
    },
    recurrence: null
  },
  ticketInfo: {
    ticketNumber: 'INC1234567',
    ticketSystem: 'ServiceNow',
    ticketSubmitterIdentityId: 'alex@contoso.com',
    ticketApproverIdentityId: 'alexmanager@contoso.com'
  }
};

await client.api('/identityGovernance/permissionsManagement/scheduledPermissionsRequests')
	.version('beta')
	.post(scheduledPermissionsRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ScheduledPermissionsRequest;
use Microsoft\Graph\Beta\Generated\Models\SingleResourceAzurePermissionsDefinition;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystem;
use Microsoft\Graph\Beta\Generated\Models\AzureRolePermissionsDefinitionAction;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAzureRole;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystemIdentity;
use Microsoft\Graph\Beta\Generated\Models\EdIdentitySource;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionIdentityType;
use Microsoft\Graph\Beta\Generated\Models\RequestSchedule;
use Microsoft\Graph\Beta\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Beta\Generated\Models\TicketInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ScheduledPermissionsRequest();
$requestedPermissions = new SingleResourceAzurePermissionsDefinition();
$requestedPermissions->setOdataType('microsoft.graph.singleResourceAzurePermissionsDefinition');
$requestedPermissionsAuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemId('87eefd90-95a3-480a-ba42-56ff299a05ee');
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemType('AZURE');
$requestedPermissions->setAuthorizationSystemInfo($requestedPermissionsAuthorizationSystemInfo);
$requestedPermissionsActionInfo = new AzureRolePermissionsDefinitionAction();
$requestedPermissionsActionInfo->setOdataType('microsoft.graph.azureRolePermissionsDefinitionAction');
$rolesPermissionsDefinitionAzureRole1 = new PermissionsDefinitionAzureRole();
$rolesPermissionsDefinitionAzureRole1->setId('cdda3590-29a3-44f6-95f2-9f980659eb04');
$rolesArray []= $rolesPermissionsDefinitionAzureRole1;
$rolesPermissionsDefinitionAzureRole2 = new PermissionsDefinitionAzureRole();
$rolesPermissionsDefinitionAzureRole2->setId('312a565d-c81f-4fd8-895a-4e21e48d571c');
$rolesArray []= $rolesPermissionsDefinitionAzureRole2;
$requestedPermissionsActionInfo->setRoles($rolesArray);

$requestedPermissions->setActionInfo($requestedPermissionsActionInfo);
$requestedPermissionsIdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
$requestedPermissionsIdentityInfo->setExternalId('alex@contoso.com');
$requestedPermissionsIdentityInfoSource = new EdIdentitySource();
$requestedPermissionsIdentityInfoSource->setOdataType('microsoft.graph.edIdentitySource');
$requestedPermissionsIdentityInfo->setSource($requestedPermissionsIdentityInfoSource);
$requestedPermissionsIdentityInfo->setIdentityType(new PermissionsDefinitionIdentityType('user'));
$requestedPermissions->setIdentityInfo($requestedPermissionsIdentityInfo);
$requestedPermissions->setResourceId('/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee');
$requestBody->setRequestedPermissions($requestedPermissions);
$requestBody->setJustification('I need to do this because I want to some new azure roles');
$requestBody->setNotes('Pretty Pleaseeeee');
$scheduleInfo = new RequestSchedule();
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setDuration(new \DateInterval('PT1H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$scheduleInfo->setRecurrence(null);
$requestBody->setScheduleInfo($scheduleInfo);
$ticketInfo = new TicketInfo();
$ticketInfo->setTicketNumber('INC1234567');
$ticketInfo->setTicketSystem('ServiceNow');
$ticketInfo->setTicketSubmitterIdentityId('alex@contoso.com');
$ticketInfo->setTicketApproverIdentityId('alexmanager@contoso.com');
$requestBody->setTicketInfo($ticketInfo);

$result = $graphServiceClient->identityGovernance()->permissionsManagement()->scheduledPermissionsRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestedPermissions = @{
		"@odata.type" = "microsoft.graph.singleResourceAzurePermissionsDefinition"
		authorizationSystemInfo = @{
			authorizationSystemId = "87eefd90-95a3-480a-ba42-56ff299a05ee"
			authorizationSystemType = "AZURE"
		}
		actionInfo = @{
			"@odata.type" = "microsoft.graph.azureRolePermissionsDefinitionAction"
			roles = @(
				@{
					id = "cdda3590-29a3-44f6-95f2-9f980659eb04"
				}
				@{
					id = "312a565d-c81f-4fd8-895a-4e21e48d571c"
				}
			)
		}
		identityInfo = @{
			externalId = "alex@contoso.com"
			source = @{
				"@odata.type" = "microsoft.graph.edIdentitySource"
			}
			identityType = "user"
		}
		resourceId = "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee"
	}
	justification = "I need to do this because I want to some new azure roles"
	notes = "Pretty Pleaseeeee"
	scheduleInfo = @{
		expiration = @{
			duration = "PT1H"
		}
		recurrence = $null
	}
	ticketInfo = @{
		ticketNumber = "INC1234567"
		ticketSystem = "ServiceNow"
		ticketSubmitterIdentityId = "alex@contoso.com"
		ticketApproverIdentityId = "alexmanager@contoso.com"
	}
}

New-MgBetaIdentityGovernancePermissionManagementScheduledPermissionRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.scheduled_permissions_request import ScheduledPermissionsRequest
from msgraph_beta.generated.models.single_resource_azure_permissions_definition import SingleResourceAzurePermissionsDefinition
from msgraph_beta.generated.models.permissions_definition_authorization_system import PermissionsDefinitionAuthorizationSystem
from msgraph_beta.generated.models.azure_role_permissions_definition_action import AzureRolePermissionsDefinitionAction
from msgraph_beta.generated.models.permissions_definition_azure_role import PermissionsDefinitionAzureRole
from msgraph_beta.generated.models.permissions_definition_authorization_system_identity import PermissionsDefinitionAuthorizationSystemIdentity
from msgraph_beta.generated.models.ed_identity_source import EdIdentitySource
from msgraph_beta.generated.models.permissions_definition_identity_type import PermissionsDefinitionIdentityType
from msgraph_beta.generated.models.request_schedule import RequestSchedule
from msgraph_beta.generated.models.expiration_pattern import ExpirationPattern
from msgraph_beta.generated.models.ticket_info import TicketInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ScheduledPermissionsRequest(
	requested_permissions = SingleResourceAzurePermissionsDefinition(
		odata_type = "microsoft.graph.singleResourceAzurePermissionsDefinition",
		authorization_system_info = PermissionsDefinitionAuthorizationSystem(
			authorization_system_id = "87eefd90-95a3-480a-ba42-56ff299a05ee",
			authorization_system_type = "AZURE",
		),
		action_info = AzureRolePermissionsDefinitionAction(
			odata_type = "microsoft.graph.azureRolePermissionsDefinitionAction",
			roles = [
				PermissionsDefinitionAzureRole(
					id = "cdda3590-29a3-44f6-95f2-9f980659eb04",
				),
				PermissionsDefinitionAzureRole(
					id = "312a565d-c81f-4fd8-895a-4e21e48d571c",
				),
			],
		),
		identity_info = PermissionsDefinitionAuthorizationSystemIdentity(
			external_id = "alex@contoso.com",
			source = EdIdentitySource(
				odata_type = "microsoft.graph.edIdentitySource",
			),
			identity_type = PermissionsDefinitionIdentityType.User,
		),
		resource_id = "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee",
	),
	justification = "I need to do this because I want to some new azure roles",
	notes = "Pretty Pleaseeeee",
	schedule_info = RequestSchedule(
		expiration = ExpirationPattern(
			duration = "PT1H",
		),
		recurrence = None,
	),
	ticket_info = TicketInfo(
		ticket_number = "INC1234567",
		ticket_system = "ServiceNow",
		ticket_submitter_identity_id = "alex@contoso.com",
		ticket_approver_identity_id = "alexmanager@contoso.com",
	),
)

result = await graph_client.identity_governance.permissions_management.scheduled_permissions_requests.post(request_body)
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

{
  "@odata.type": "microsoft.graph.scheduledPermissionsRequest",
  "id": "00000000-0000-0000-0000-000000000004",
   "requestedPermissions": {
    "@odata.type": "microsoft.graph.singleResourceAzurePermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "87eefd90-95a3-480a-ba42-56ff299a05ee",
      "authorizationSystemType": "AZURE",
    },
    "actionInfo" : {
      "@odata.type": "microsoft.graph.azureRolePermissionsDefinitionAction",
      "roles": [
        {
          "id": "cdda3590-29a3-44f6-95f2-9f980659eb04"
        },
        {
          "id": "312a565d-c81f-4fd8-895a-4e21e48d571c"
        }
      ]
    },
    "identityInfo": {
      "externalId": "alex@contoso.com",
      "source": {
        "@odata.type": "microsoft.graph.edIdentitySource"
      },
      "identityType": "user"
    },
    "resourceId": "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee"
  },
  "justification": "I need to do this because I want to some new azure roles",
  "notes": "Pretty Pleaseeeee",
  "createdDateTime": "2023-02-06T12:15:00Z",
  "scheduleInfo": {
    "expiration": {
      "duration": "PT1H"
    },
  },
  "ticketInfo": {
    "ticketNumber": "INC1234567",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
  },
  "statusDetail": "submitted"
}
```

### Example 3: GCP actions request

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
POST https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/scheduledPermissionsRequests
Content-Type: application/json

{
  "requestedPermissions": {
    "@odata.type": "microsoft.graph.singleResourceGcpPermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "carbide-bonsai-205017",
      "authorizationSystemType": "GCP"
    },
    "actionInfo": {
      "@odata.type": "microsoft.graph.gcpActionPermissionsDefinitionAction",
      "actions": [
        "aiplatform:dataitems"
      ]
    },
    "identityInfo": {
      "externalId": "alex@contoso.com",
      "source": {
        "@odata.type": "microsoft.graph.edIdentitySource"
      },
      "identityType": "user"
    },
    "resourceId": "carbide-bonsai-205017"
  },
  "justification": "I need to do this because I want to code my own chat GPT-3 bot on GCP",
  "notes": "Pretty Pleaseeeee",
  "scheduleInfo": {
    "expiration": {
      "duration": "PT1H"
    }
  },
  "ticketInfo": {
    "ticketNumber": "INC1234567",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ScheduledPermissionsRequest
{
	RequestedPermissions = new SingleResourceGcpPermissionsDefinition
	{
		OdataType = "microsoft.graph.singleResourceGcpPermissionsDefinition",
		AuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem
		{
			AuthorizationSystemId = "carbide-bonsai-205017",
			AuthorizationSystemType = "GCP",
		},
		ActionInfo = new GcpActionPermissionsDefinitionAction
		{
			OdataType = "microsoft.graph.gcpActionPermissionsDefinitionAction",
			Actions = new List<string>
			{
				"aiplatform:dataitems",
			},
		},
		IdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity
		{
			ExternalId = "alex@contoso.com",
			Source = new EdIdentitySource
			{
				OdataType = "microsoft.graph.edIdentitySource",
			},
			IdentityType = PermissionsDefinitionIdentityType.User,
		},
		ResourceId = "carbide-bonsai-205017",
	},
	Justification = "I need to do this because I want to code my own chat GPT-3 bot on GCP",
	Notes = "Pretty Pleaseeeee",
	ScheduleInfo = new RequestSchedule
	{
		Expiration = new ExpirationPattern
		{
			Duration = TimeSpan.Parse("PT1H"),
		},
	},
	TicketInfo = new TicketInfo
	{
		TicketNumber = "INC1234567",
		TicketSystem = "ServiceNow",
		TicketSubmitterIdentityId = "alex@contoso.com",
		TicketApproverIdentityId = "alexmanager@contoso.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PermissionsManagement.ScheduledPermissionsRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewScheduledPermissionsRequest()
requestedPermissions := graphmodels.NewSingleResourceGcpPermissionsDefinition()
authorizationSystemInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystem()
authorizationSystemId := "carbide-bonsai-205017"
authorizationSystemInfo.SetAuthorizationSystemId(&authorizationSystemId) 
authorizationSystemType := "GCP"
authorizationSystemInfo.SetAuthorizationSystemType(&authorizationSystemType) 
requestedPermissions.SetAuthorizationSystemInfo(authorizationSystemInfo)
actionInfo := graphmodels.NewGcpActionPermissionsDefinitionAction()
actions := []string {
	"aiplatform:dataitems",
}
actionInfo.SetActions(actions)
requestedPermissions.SetActionInfo(actionInfo)
identityInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystemIdentity()
externalId := "alex@contoso.com"
identityInfo.SetExternalId(&externalId) 
source := graphmodels.NewEdIdentitySource()
identityInfo.SetSource(source)
identityType := graphmodels.USER_PERMISSIONSDEFINITIONIDENTITYTYPE 
identityInfo.SetIdentityType(&identityType) 
requestedPermissions.SetIdentityInfo(identityInfo)
resourceId := "carbide-bonsai-205017"
requestedPermissions.SetResourceId(&resourceId) 
requestBody.SetRequestedPermissions(requestedPermissions)
justification := "I need to do this because I want to code my own chat GPT-3 bot on GCP"
requestBody.SetJustification(&justification) 
notes := "Pretty Pleaseeeee"
requestBody.SetNotes(&notes) 
scheduleInfo := graphmodels.NewRequestSchedule()
expiration := graphmodels.NewExpirationPattern()
duration , err := abstractions.ParseISODuration("PT1H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)
ticketInfo := graphmodels.NewTicketInfo()
ticketNumber := "INC1234567"
ticketInfo.SetTicketNumber(&ticketNumber) 
ticketSystem := "ServiceNow"
ticketInfo.SetTicketSystem(&ticketSystem) 
ticketSubmitterIdentityId := "alex@contoso.com"
ticketInfo.SetTicketSubmitterIdentityId(&ticketSubmitterIdentityId) 
ticketApproverIdentityId := "alexmanager@contoso.com"
ticketInfo.SetTicketApproverIdentityId(&ticketApproverIdentityId) 
requestBody.SetTicketInfo(ticketInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
scheduledPermissionsRequests, err := graphClient.IdentityGovernance().PermissionsManagement().ScheduledPermissionsRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ScheduledPermissionsRequest scheduledPermissionsRequest = new ScheduledPermissionsRequest();
SingleResourceGcpPermissionsDefinition requestedPermissions = new SingleResourceGcpPermissionsDefinition();
requestedPermissions.setOdataType("microsoft.graph.singleResourceGcpPermissionsDefinition");
PermissionsDefinitionAuthorizationSystem authorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
authorizationSystemInfo.setAuthorizationSystemId("carbide-bonsai-205017");
authorizationSystemInfo.setAuthorizationSystemType("GCP");
requestedPermissions.setAuthorizationSystemInfo(authorizationSystemInfo);
GcpActionPermissionsDefinitionAction actionInfo = new GcpActionPermissionsDefinitionAction();
actionInfo.setOdataType("microsoft.graph.gcpActionPermissionsDefinitionAction");
LinkedList<String> actions = new LinkedList<String>();
actions.add("aiplatform:dataitems");
actionInfo.setActions(actions);
requestedPermissions.setActionInfo(actionInfo);
PermissionsDefinitionAuthorizationSystemIdentity identityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
identityInfo.setExternalId("alex@contoso.com");
EdIdentitySource source = new EdIdentitySource();
source.setOdataType("microsoft.graph.edIdentitySource");
identityInfo.setSource(source);
identityInfo.setIdentityType(PermissionsDefinitionIdentityType.User);
requestedPermissions.setIdentityInfo(identityInfo);
requestedPermissions.setResourceId("carbide-bonsai-205017");
scheduledPermissionsRequest.setRequestedPermissions(requestedPermissions);
scheduledPermissionsRequest.setJustification("I need to do this because I want to code my own chat GPT-3 bot on GCP");
scheduledPermissionsRequest.setNotes("Pretty Pleaseeeee");
RequestSchedule scheduleInfo = new RequestSchedule();
ExpirationPattern expiration = new ExpirationPattern();
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
scheduledPermissionsRequest.setScheduleInfo(scheduleInfo);
TicketInfo ticketInfo = new TicketInfo();
ticketInfo.setTicketNumber("INC1234567");
ticketInfo.setTicketSystem("ServiceNow");
ticketInfo.setTicketSubmitterIdentityId("alex@contoso.com");
ticketInfo.setTicketApproverIdentityId("alexmanager@contoso.com");
scheduledPermissionsRequest.setTicketInfo(ticketInfo);
ScheduledPermissionsRequest result = graphClient.identityGovernance().permissionsManagement().scheduledPermissionsRequests().post(scheduledPermissionsRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const scheduledPermissionsRequest = {
  requestedPermissions: {
    '@odata.type': 'microsoft.graph.singleResourceGcpPermissionsDefinition',
    authorizationSystemInfo: {
      authorizationSystemId: 'carbide-bonsai-205017',
      authorizationSystemType: 'GCP'
    },
    actionInfo: {
      '@odata.type': 'microsoft.graph.gcpActionPermissionsDefinitionAction',
      actions: [
        'aiplatform:dataitems'
      ]
    },
    identityInfo: {
      externalId: 'alex@contoso.com',
      source: {
        '@odata.type': 'microsoft.graph.edIdentitySource'
      },
      identityType: 'user'
    },
    resourceId: 'carbide-bonsai-205017'
  },
  justification: 'I need to do this because I want to code my own chat GPT-3 bot on GCP',
  notes: 'Pretty Pleaseeeee',
  scheduleInfo: {
    expiration: {
      duration: 'PT1H'
    }
  },
  ticketInfo: {
    ticketNumber: 'INC1234567',
    ticketSystem: 'ServiceNow',
    ticketSubmitterIdentityId: 'alex@contoso.com',
    ticketApproverIdentityId: 'alexmanager@contoso.com'
  }
};

await client.api('/identityGovernance/permissionsManagement/scheduledPermissionsRequests')
	.version('beta')
	.post(scheduledPermissionsRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ScheduledPermissionsRequest;
use Microsoft\Graph\Beta\Generated\Models\SingleResourceGcpPermissionsDefinition;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystem;
use Microsoft\Graph\Beta\Generated\Models\GcpActionPermissionsDefinitionAction;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystemIdentity;
use Microsoft\Graph\Beta\Generated\Models\EdIdentitySource;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionIdentityType;
use Microsoft\Graph\Beta\Generated\Models\RequestSchedule;
use Microsoft\Graph\Beta\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Beta\Generated\Models\TicketInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ScheduledPermissionsRequest();
$requestedPermissions = new SingleResourceGcpPermissionsDefinition();
$requestedPermissions->setOdataType('microsoft.graph.singleResourceGcpPermissionsDefinition');
$requestedPermissionsAuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemId('carbide-bonsai-205017');
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemType('GCP');
$requestedPermissions->setAuthorizationSystemInfo($requestedPermissionsAuthorizationSystemInfo);
$requestedPermissionsActionInfo = new GcpActionPermissionsDefinitionAction();
$requestedPermissionsActionInfo->setOdataType('microsoft.graph.gcpActionPermissionsDefinitionAction');
$requestedPermissionsActionInfo->setActions(['aiplatform:dataitems', 	]);
$requestedPermissions->setActionInfo($requestedPermissionsActionInfo);
$requestedPermissionsIdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
$requestedPermissionsIdentityInfo->setExternalId('alex@contoso.com');
$requestedPermissionsIdentityInfoSource = new EdIdentitySource();
$requestedPermissionsIdentityInfoSource->setOdataType('microsoft.graph.edIdentitySource');
$requestedPermissionsIdentityInfo->setSource($requestedPermissionsIdentityInfoSource);
$requestedPermissionsIdentityInfo->setIdentityType(new PermissionsDefinitionIdentityType('user'));
$requestedPermissions->setIdentityInfo($requestedPermissionsIdentityInfo);
$requestedPermissions->setResourceId('carbide-bonsai-205017');
$requestBody->setRequestedPermissions($requestedPermissions);
$requestBody->setJustification('I need to do this because I want to code my own chat GPT-3 bot on GCP');
$requestBody->setNotes('Pretty Pleaseeeee');
$scheduleInfo = new RequestSchedule();
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setDuration(new \DateInterval('PT1H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);
$ticketInfo = new TicketInfo();
$ticketInfo->setTicketNumber('INC1234567');
$ticketInfo->setTicketSystem('ServiceNow');
$ticketInfo->setTicketSubmitterIdentityId('alex@contoso.com');
$ticketInfo->setTicketApproverIdentityId('alexmanager@contoso.com');
$requestBody->setTicketInfo($ticketInfo);

$result = $graphServiceClient->identityGovernance()->permissionsManagement()->scheduledPermissionsRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestedPermissions = @{
		"@odata.type" = "microsoft.graph.singleResourceGcpPermissionsDefinition"
		authorizationSystemInfo = @{
			authorizationSystemId = "carbide-bonsai-205017"
			authorizationSystemType = "GCP"
		}
		actionInfo = @{
			"@odata.type" = "microsoft.graph.gcpActionPermissionsDefinitionAction"
			actions = @(
			"aiplatform:dataitems"
		)
	}
	identityInfo = @{
		externalId = "alex@contoso.com"
		source = @{
			"@odata.type" = "microsoft.graph.edIdentitySource"
		}
		identityType = "user"
	}
	resourceId = "carbide-bonsai-205017"
}
justification = "I need to do this because I want to code my own chat GPT-3 bot on GCP"
notes = "Pretty Pleaseeeee"
scheduleInfo = @{
	expiration = @{
		duration = "PT1H"
	}
}
ticketInfo = @{
	ticketNumber = "INC1234567"
	ticketSystem = "ServiceNow"
	ticketSubmitterIdentityId = "alex@contoso.com"
	ticketApproverIdentityId = "alexmanager@contoso.com"
}
}

New-MgBetaIdentityGovernancePermissionManagementScheduledPermissionRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.scheduled_permissions_request import ScheduledPermissionsRequest
from msgraph_beta.generated.models.single_resource_gcp_permissions_definition import SingleResourceGcpPermissionsDefinition
from msgraph_beta.generated.models.permissions_definition_authorization_system import PermissionsDefinitionAuthorizationSystem
from msgraph_beta.generated.models.gcp_action_permissions_definition_action import GcpActionPermissionsDefinitionAction
from msgraph_beta.generated.models.permissions_definition_authorization_system_identity import PermissionsDefinitionAuthorizationSystemIdentity
from msgraph_beta.generated.models.ed_identity_source import EdIdentitySource
from msgraph_beta.generated.models.permissions_definition_identity_type import PermissionsDefinitionIdentityType
from msgraph_beta.generated.models.request_schedule import RequestSchedule
from msgraph_beta.generated.models.expiration_pattern import ExpirationPattern
from msgraph_beta.generated.models.ticket_info import TicketInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ScheduledPermissionsRequest(
	requested_permissions = SingleResourceGcpPermissionsDefinition(
		odata_type = "microsoft.graph.singleResourceGcpPermissionsDefinition",
		authorization_system_info = PermissionsDefinitionAuthorizationSystem(
			authorization_system_id = "carbide-bonsai-205017",
			authorization_system_type = "GCP",
		),
		action_info = GcpActionPermissionsDefinitionAction(
			odata_type = "microsoft.graph.gcpActionPermissionsDefinitionAction",
			actions = [
				"aiplatform:dataitems",
			],
		),
		identity_info = PermissionsDefinitionAuthorizationSystemIdentity(
			external_id = "alex@contoso.com",
			source = EdIdentitySource(
				odata_type = "microsoft.graph.edIdentitySource",
			),
			identity_type = PermissionsDefinitionIdentityType.User,
		),
		resource_id = "carbide-bonsai-205017",
	),
	justification = "I need to do this because I want to code my own chat GPT-3 bot on GCP",
	notes = "Pretty Pleaseeeee",
	schedule_info = RequestSchedule(
		expiration = ExpirationPattern(
			duration = "PT1H",
		),
	),
	ticket_info = TicketInfo(
		ticket_number = "INC1234567",
		ticket_system = "ServiceNow",
		ticket_submitter_identity_id = "alex@contoso.com",
		ticket_approver_identity_id = "alexmanager@contoso.com",
	),
)

result = await graph_client.identity_governance.permissions_management.scheduled_permissions_requests.post(request_body)
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

{
  "@odata.type": "microsoft.graph.scheduledPermissionsRequest",
  "id": "00000000-0000-0000-0000-000000000005",
   "requestedPermissions": {
    "@odata.type": "microsoft.graph.singleResourceGcpPermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "carbide-bonsai-205017",
      "authorizationSystemType": "GCP",
    },
    "actionInfo" : {
      "@odata.type": "microsoft.graph.gcpActionPermissionsDefinitionAction",
      "actions": [
        "aiplatform:dataitems"
      ]
    },
    "identityInfo": {
      "externalId": "alex@contoso.com",
      "source": {
        "@odata.type": "microsoft.graph.edIdentitySource"
      },
      "identityType": "user"
    },
    "resourceId": "carbide-bonsai-205017"
  },
  "justification": "I need to do this because I want to code my own chat GPT-3 bot on GCP",
  "notes": "Pretty Pleaseeeee",
  "createdDateTime": "2023-02-06T12:15:00Z",
  "scheduleInfo": {
    "expiration": {
      "duration": "PT1H"
    }
  },
  "ticketInfo": {
    "ticketNumber": "INC1234567",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
  },
  "statusDetail": "submitted"
}
```
