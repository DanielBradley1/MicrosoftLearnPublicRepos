<!-- Source: https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-assignmentpolicies?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create assignmentPolicies

Namespace: microsoft.graph

Create a new [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) object in [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0). The request includes a reference to the [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) that contains this policy, which must already exist.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

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

  - *Access package manager*. **This is the least privileged option**
  - Catalog owner

- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Access package manager* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
POST /identityGovernance/entitlementManagement/assignmentPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) object.

You can specify the following properties when creating an **accessPackageAssignmentPolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the policy. |
| displayName | String | The display name of the policy. |
| allowedTargetScope | allowedTargetScope | Who is allowed to be assigned the access package through this policy. The possible values are: `notSpecified`, `specificDirectoryUsers`, `specificConnectedOrganizationUsers`, `specificDirectoryServicePrincipals`, `allMemberUsers`, `allDirectoryUsers`, `allDirectoryServicePrincipals`, `allConfiguredConnectedOrganizationUsers`, `allExternalUsers`, `unknownFutureValue`. Optional. |
| expiration | [expirationPattern](https://learn.microsoft.com/en-us/graph/api/resources/expirationpattern?view=graph-rest-1.0) | The expiration date for assignments created in this policy. |
| notificationSettings | [accessPackageNotificationSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagenotificationsettings?view=graph-rest-1.0) | Represents the settings for email notifications for requests to an access package. |
| requestApprovalSettings | [accessPackageAssignmentApprovalSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentapprovalsettings?view=graph-rest-1.0) | Specifies the settings for approval of requests for an access package assignment through this policy. For example, if approval is required for new requests. |
| requestorSettings | [accessPackageAssignmentRequestorSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestorsettings?view=graph-rest-1.0) | Provides additional settings to select who can create a request for an access package assignment through this policy, and what they can include in their request. |
| reviewSettings | [accessPackageAssignmentReviewSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentreviewsettings?view=graph-rest-1.0) | Settings for access reviews of assignments through this policy. |
| specificAllowedTargets | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | The principals that can be assigned access from an access package through this policy. |
| automaticRequestSettings | [accessPackageAutomaticRequestSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageautomaticrequestsettings?view=graph-rest-1.0) | This property is only present for an auto assignment policy; if absent, this is a request-based policy. |
| accessPackage | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) | A reference to the access package that will contain the policy, which must already exist. |
| questions | [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0) collection | Questions that are posed to the requestor. |

## Response

If successful, this method returns a `201 Created` response code and an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a direct assignment policy

A direct assignment policy is useful when access package assignment requests will only be created by an administrator, not by users themselves.

#### Request

The following example shows a request to create an access package assignment policy. In this policy, no users can request, no approval is required, and there are no access reviews.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentPolicies
Content-Type: application/json

{
  "displayName": "New Policy",
  "description": "policy for assignment",
  "allowedTargetScope": "notSpecified",
  "specificAllowedTargets": [],
  "expiration": {
      "endDateTime": null,
      "duration": null,
      "type": "noExpiration"
  },
  "requestorSettings": {
      "enableTargetsToSelfAddAccess": false,
      "enableTargetsToSelfUpdateAccess": false,
      "enableTargetsToSelfRemoveAccess": false,
      "allowCustomAssignmentSchedule": true,
      "enableOnBehalfRequestorsToAddAccess": false,
      "enableOnBehalfRequestorsToUpdateAccess": false,
      "enableOnBehalfRequestorsToRemoveAccess": false,
      "onBehalfRequestors": []
  },
  "requestApprovalSettings": {
      "isApprovalRequiredForAdd": false,
      "isApprovalRequiredForUpdate": false,
      "stages": []
  },
  "accessPackage": {
      "id": "a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentPolicy
{
	DisplayName = "New Policy",
	Description = "policy for assignment",
	AllowedTargetScope = AllowedTargetScope.NotSpecified,
	SpecificAllowedTargets = new List<SubjectSet>
	{
	},
	Expiration = new ExpirationPattern
	{
		EndDateTime = null,
		Duration = null,
		Type = ExpirationPatternType.NoExpiration,
	},
	RequestorSettings = new AccessPackageAssignmentRequestorSettings
	{
		EnableTargetsToSelfAddAccess = false,
		EnableTargetsToSelfUpdateAccess = false,
		EnableTargetsToSelfRemoveAccess = false,
		AllowCustomAssignmentSchedule = true,
		EnableOnBehalfRequestorsToAddAccess = false,
		EnableOnBehalfRequestorsToUpdateAccess = false,
		EnableOnBehalfRequestorsToRemoveAccess = false,
		OnBehalfRequestors = new List<SubjectSet>
		{
		},
	},
	RequestApprovalSettings = new AccessPackageAssignmentApprovalSettings
	{
		IsApprovalRequiredForAdd = false,
		IsApprovalRequiredForUpdate = false,
		Stages = new List<AccessPackageApprovalStage>
		{
		},
	},
	AccessPackage = new AccessPackage
	{
		Id = "a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
displayName := "New Policy"
requestBody.SetDisplayName(&displayName) 
description := "policy for assignment"
requestBody.SetDescription(&description) 
allowedTargetScope := graphmodels.NOTSPECIFIED_ALLOWEDTARGETSCOPE 
requestBody.SetAllowedTargetScope(&allowedTargetScope) 
specificAllowedTargets := []graphmodels.SubjectSetable {

}
requestBody.SetSpecificAllowedTargets(specificAllowedTargets)
expiration := graphmodels.NewExpirationPattern()
endDateTime := null
expiration.SetEndDateTime(&endDateTime) 
duration := null
expiration.SetDuration(&duration) 
type := graphmodels.NOEXPIRATION_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
requestBody.SetExpiration(expiration)
requestorSettings := graphmodels.NewAccessPackageAssignmentRequestorSettings()
enableTargetsToSelfAddAccess := false
requestorSettings.SetEnableTargetsToSelfAddAccess(&enableTargetsToSelfAddAccess) 
enableTargetsToSelfUpdateAccess := false
requestorSettings.SetEnableTargetsToSelfUpdateAccess(&enableTargetsToSelfUpdateAccess) 
enableTargetsToSelfRemoveAccess := false
requestorSettings.SetEnableTargetsToSelfRemoveAccess(&enableTargetsToSelfRemoveAccess) 
allowCustomAssignmentSchedule := true
requestorSettings.SetAllowCustomAssignmentSchedule(&allowCustomAssignmentSchedule) 
enableOnBehalfRequestorsToAddAccess := false
requestorSettings.SetEnableOnBehalfRequestorsToAddAccess(&enableOnBehalfRequestorsToAddAccess) 
enableOnBehalfRequestorsToUpdateAccess := false
requestorSettings.SetEnableOnBehalfRequestorsToUpdateAccess(&enableOnBehalfRequestorsToUpdateAccess) 
enableOnBehalfRequestorsToRemoveAccess := false
requestorSettings.SetEnableOnBehalfRequestorsToRemoveAccess(&enableOnBehalfRequestorsToRemoveAccess) 
onBehalfRequestors := []graphmodels.SubjectSetable {

}
requestorSettings.SetOnBehalfRequestors(onBehalfRequestors)
requestBody.SetRequestorSettings(requestorSettings)
requestApprovalSettings := graphmodels.NewAccessPackageAssignmentApprovalSettings()
isApprovalRequiredForAdd := false
requestApprovalSettings.SetIsApprovalRequiredForAdd(&isApprovalRequiredForAdd) 
isApprovalRequiredForUpdate := false
requestApprovalSettings.SetIsApprovalRequiredForUpdate(&isApprovalRequiredForUpdate) 
stages := []graphmodels.AccessPackageApprovalStageable {

}
requestApprovalSettings.SetStages(stages)
requestBody.SetRequestApprovalSettings(requestApprovalSettings)
accessPackage := graphmodels.NewAccessPackage()
id := "a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b"
accessPackage.SetId(&id) 
requestBody.SetAccessPackage(accessPackage)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentPolicies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setDisplayName("New Policy");
accessPackageAssignmentPolicy.setDescription("policy for assignment");
accessPackageAssignmentPolicy.setAllowedTargetScope(AllowedTargetScope.NotSpecified);
LinkedList<SubjectSet> specificAllowedTargets = new LinkedList<SubjectSet>();
accessPackageAssignmentPolicy.setSpecificAllowedTargets(specificAllowedTargets);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setEndDateTime(null);
expiration.setDuration(null);
expiration.setType(ExpirationPatternType.NoExpiration);
accessPackageAssignmentPolicy.setExpiration(expiration);
AccessPackageAssignmentRequestorSettings requestorSettings = new AccessPackageAssignmentRequestorSettings();
requestorSettings.setEnableTargetsToSelfAddAccess(false);
requestorSettings.setEnableTargetsToSelfUpdateAccess(false);
requestorSettings.setEnableTargetsToSelfRemoveAccess(false);
requestorSettings.setAllowCustomAssignmentSchedule(true);
requestorSettings.setEnableOnBehalfRequestorsToAddAccess(false);
requestorSettings.setEnableOnBehalfRequestorsToUpdateAccess(false);
requestorSettings.setEnableOnBehalfRequestorsToRemoveAccess(false);
LinkedList<SubjectSet> onBehalfRequestors = new LinkedList<SubjectSet>();
requestorSettings.setOnBehalfRequestors(onBehalfRequestors);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
AccessPackageAssignmentApprovalSettings requestApprovalSettings = new AccessPackageAssignmentApprovalSettings();
requestApprovalSettings.setIsApprovalRequiredForAdd(false);
requestApprovalSettings.setIsApprovalRequiredForUpdate(false);
LinkedList<AccessPackageApprovalStage> stages = new LinkedList<AccessPackageApprovalStage>();
requestApprovalSettings.setStages(stages);
accessPackageAssignmentPolicy.setRequestApprovalSettings(requestApprovalSettings);
AccessPackage accessPackage = new AccessPackage();
accessPackage.setId("a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b");
accessPackageAssignmentPolicy.setAccessPackage(accessPackage);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().assignmentPolicies().post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
  displayName: 'New Policy',
  description: 'policy for assignment',
  allowedTargetScope: 'notSpecified',
  specificAllowedTargets: [],
  expiration: {
      endDateTime: null,
      duration: null,
      type: 'noExpiration'
  },
  requestorSettings: {
      enableTargetsToSelfAddAccess: false,
      enableTargetsToSelfUpdateAccess: false,
      enableTargetsToSelfRemoveAccess: false,
      allowCustomAssignmentSchedule: true,
      enableOnBehalfRequestorsToAddAccess: false,
      enableOnBehalfRequestorsToUpdateAccess: false,
      enableOnBehalfRequestorsToRemoveAccess: false,
      onBehalfRequestors: []
  },
  requestApprovalSettings: {
      isApprovalRequiredForAdd: false,
      isApprovalRequiredForUpdate: false,
      stages: []
  },
  accessPackage: {
      id: 'a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b'
  }
};

await client.api('/identityGovernance/entitlementManagement/assignmentPolicies')
	.post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Generated\Models\AllowedTargetScope;
use Microsoft\Graph\Generated\Models\SubjectSet;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequestorSettings;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentApprovalSettings;
use Microsoft\Graph\Generated\Models\AccessPackageApprovalStage;
use Microsoft\Graph\Generated\Models\AccessPackage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setDisplayName('New Policy');
$requestBody->setDescription('policy for assignment');
$requestBody->setAllowedTargetScope(new AllowedTargetScope('notSpecified'));
$requestBody->setSpecificAllowedTargets([	]);
$expiration = new ExpirationPattern();
$expiration->setEndDateTime(null);
$expiration->setDuration(null);
$expiration->setType(new ExpirationPatternType('noExpiration'));
$requestBody->setExpiration($expiration);
$requestorSettings = new AccessPackageAssignmentRequestorSettings();
$requestorSettings->setEnableTargetsToSelfAddAccess(false);
$requestorSettings->setEnableTargetsToSelfUpdateAccess(false);
$requestorSettings->setEnableTargetsToSelfRemoveAccess(false);
$requestorSettings->setAllowCustomAssignmentSchedule(true);
$requestorSettings->setEnableOnBehalfRequestorsToAddAccess(false);
$requestorSettings->setEnableOnBehalfRequestorsToUpdateAccess(false);
$requestorSettings->setEnableOnBehalfRequestorsToRemoveAccess(false);
$requestorSettings->setOnBehalfRequestors([	]);
$requestBody->setRequestorSettings($requestorSettings);
$requestApprovalSettings = new AccessPackageAssignmentApprovalSettings();
$requestApprovalSettings->setIsApprovalRequiredForAdd(false);
$requestApprovalSettings->setIsApprovalRequiredForUpdate(false);
$requestApprovalSettings->setStages([	]);
$requestBody->setRequestApprovalSettings($requestApprovalSettings);
$accessPackage = new AccessPackage();
$accessPackage->setId('a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b');
$requestBody->setAccessPackage($accessPackage);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentPolicies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "New Policy"
	description = "policy for assignment"
	allowedTargetScope = "notSpecified"
	specificAllowedTargets = @(
	)
	expiration = @{
		endDateTime = $null
		duration = $null
		type = "noExpiration"
	}
	requestorSettings = @{
		enableTargetsToSelfAddAccess = $false
		enableTargetsToSelfUpdateAccess = $false
		enableTargetsToSelfRemoveAccess = $false
		allowCustomAssignmentSchedule = $true
		enableOnBehalfRequestorsToAddAccess = $false
		enableOnBehalfRequestorsToUpdateAccess = $false
		enableOnBehalfRequestorsToRemoveAccess = $false
		onBehalfRequestors = @(
		)
	}
	requestApprovalSettings = @{
		isApprovalRequiredForAdd = $false
		isApprovalRequiredForUpdate = $false
		stages = @(
		)
	}
	accessPackage = @{
		id = "a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b"
	}
}

New-MgEntitlementManagementAssignmentPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph.generated.models.allowed_target_scope import AllowedTargetScope
from msgraph.generated.models.subject_set import SubjectSet
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
from msgraph.generated.models.access_package_assignment_requestor_settings import AccessPackageAssignmentRequestorSettings
from msgraph.generated.models.access_package_assignment_approval_settings import AccessPackageAssignmentApprovalSettings
from msgraph.generated.models.access_package_approval_stage import AccessPackageApprovalStage
from msgraph.generated.models.access_package import AccessPackage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	display_name = "New Policy",
	description = "policy for assignment",
	allowed_target_scope = AllowedTargetScope.NotSpecified,
	specific_allowed_targets = [
	],
	expiration = ExpirationPattern(
		end_date_time = None,
		duration = None,
		type = ExpirationPatternType.NoExpiration,
	),
	requestor_settings = AccessPackageAssignmentRequestorSettings(
		enable_targets_to_self_add_access = False,
		enable_targets_to_self_update_access = False,
		enable_targets_to_self_remove_access = False,
		allow_custom_assignment_schedule = True,
		enable_on_behalf_requestors_to_add_access = False,
		enable_on_behalf_requestors_to_update_access = False,
		enable_on_behalf_requestors_to_remove_access = False,
		on_behalf_requestors = [
		],
	),
	request_approval_settings = AccessPackageAssignmentApprovalSettings(
		is_approval_required_for_add = False,
		is_approval_required_for_update = False,
		stages = [
		],
	),
	access_package = AccessPackage(
		id = "a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b",
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187",
  "displayName": "New policy",
  "description": "policy for assignment"
}
```

### Example 2: Create a policy for users from other organizations to request

The following example shows a more complex policy with two stages of approval and recurring access reviews.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentPolicies
Content-Type: application/json

{
    "displayName": "policy for external access requests",
    "description": "policy for users from connected organizations to request access, with two stages of approval.",
    "allowedTargetScope": "allConfiguredConnectedOrganizationUsers",
    "specificAllowedTargets": [],
    "expiration": {
        "type": "noExpiration"
    },
    "requestorSettings": {
        "enableTargetsToSelfAddAccess": true,
        "enableTargetsToSelfUpdateAccess": true,
        "enableTargetsToSelfRemoveAccess": true,
        "allowCustomAssignmentSchedule": false,
        "enableOnBehalfRequestorsToAddAccess": false,
        "enableOnBehalfRequestorsToUpdateAccess": false,
        "enableOnBehalfRequestorsToRemoveAccess": false,
        "onBehalfRequestors": []
    },
    "requestApprovalSettings": {
        "isApprovalRequiredForAdd": true,
        "isApprovalRequiredForUpdate": false,
        "stages": [
            {
                "durationBeforeAutomaticDenial": "P14D",
                "isApproverJustificationRequired": false,
                "isEscalationEnabled": false,
                "durationBeforeEscalation": "PT0S",
                "primaryApprovers": [
                    {
                        "@odata.type": "#microsoft.graph.internalSponsors"
                    }
                ],
                "fallbackPrimaryApprovers": [
                    {
                        "@odata.type": "#microsoft.graph.singleUser",
                        "userId": "7deff43e-1f17-44ef-9e5f-d516b0ba11d4"
                    },
                    {
                        "@odata.type": "#microsoft.graph.groupMembers",
                        "groupId": "1623f912-5e86-41c2-af47-39dd67582b66"
                    }
                ],
                "escalationApprovers": [],
                "fallbackEscalationApprovers": []
            },
            {
                "durationBeforeAutomaticDenial": "P14D",
                "isApproverJustificationRequired": false,
                "isEscalationEnabled": false,
                "durationBeforeEscalation": "PT0S",
                "primaryApprovers": [],
                "fallbackPrimaryApprovers": [
                    {
                        "@odata.type": "#microsoft.graph.singleUser",
                        "userId": "46184453-e63b-4f20-86c2-c557ed5d5df9"
                    },
                    {
                        "@odata.type": "#microsoft.graph.groupMembers",
                        "groupId": "1623f912-5e86-41c2-af47-39dd67582b66"
                    }
                ],
                "escalationApprovers": [],
                "fallbackEscalationApprovers": []
            }
        ]
    },
    "reviewSettings": {
        "isEnabled": true,
        "expirationBehavior": "keepAccess",
        "isRecommendationEnabled": true,
        "isReviewerJustificationRequired": true,
        "isSelfReview": false,
        "schedule": {
            "startDateTime": "2022-07-02T06:59:59.998Z",
            "expiration": {
                "duration": "P14D",
                "type": "afterDuration"
            },
            "recurrence": {
                "pattern": {
                    "type": "absoluteMonthly",
                    "interval": 3,
                    "month": 0,
                    "dayOfMonth": 0,
                    "daysOfWeek": []
                },
                "range": {
                    "type": "noEnd",
                    "numberOfOccurrences": 0
                }
            }
        },
        "primaryReviewers": [
            {
                "@odata.type": "#microsoft.graph.groupMembers",
                "groupId": "1623f912-5e86-41c2-af47-39dd67582b66"
            }
        ],
        "fallbackReviewers": []
    },
    "accessPackage": {
        "id": "a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentPolicy
{
	DisplayName = "policy for external access requests",
	Description = "policy for users from connected organizations to request access, with two stages of approval.",
	AllowedTargetScope = AllowedTargetScope.AllConfiguredConnectedOrganizationUsers,
	SpecificAllowedTargets = new List<SubjectSet>
	{
	},
	Expiration = new ExpirationPattern
	{
		Type = ExpirationPatternType.NoExpiration,
	},
	RequestorSettings = new AccessPackageAssignmentRequestorSettings
	{
		EnableTargetsToSelfAddAccess = true,
		EnableTargetsToSelfUpdateAccess = true,
		EnableTargetsToSelfRemoveAccess = true,
		AllowCustomAssignmentSchedule = false,
		EnableOnBehalfRequestorsToAddAccess = false,
		EnableOnBehalfRequestorsToUpdateAccess = false,
		EnableOnBehalfRequestorsToRemoveAccess = false,
		OnBehalfRequestors = new List<SubjectSet>
		{
		},
	},
	RequestApprovalSettings = new AccessPackageAssignmentApprovalSettings
	{
		IsApprovalRequiredForAdd = true,
		IsApprovalRequiredForUpdate = false,
		Stages = new List<AccessPackageApprovalStage>
		{
			new AccessPackageApprovalStage
			{
				DurationBeforeAutomaticDenial = TimeSpan.Parse("P14D"),
				IsApproverJustificationRequired = false,
				IsEscalationEnabled = false,
				DurationBeforeEscalation = TimeSpan.Parse("PT0S"),
				PrimaryApprovers = new List<SubjectSet>
				{
					new InternalSponsors
					{
						OdataType = "#microsoft.graph.internalSponsors",
					},
				},
				FallbackPrimaryApprovers = new List<SubjectSet>
				{
					new SingleUser
					{
						OdataType = "#microsoft.graph.singleUser",
						UserId = "7deff43e-1f17-44ef-9e5f-d516b0ba11d4",
					},
					new GroupMembers
					{
						OdataType = "#microsoft.graph.groupMembers",
						GroupId = "1623f912-5e86-41c2-af47-39dd67582b66",
					},
				},
				EscalationApprovers = new List<SubjectSet>
				{
				},
				FallbackEscalationApprovers = new List<SubjectSet>
				{
				},
			},
			new AccessPackageApprovalStage
			{
				DurationBeforeAutomaticDenial = TimeSpan.Parse("P14D"),
				IsApproverJustificationRequired = false,
				IsEscalationEnabled = false,
				DurationBeforeEscalation = TimeSpan.Parse("PT0S"),
				PrimaryApprovers = new List<SubjectSet>
				{
				},
				FallbackPrimaryApprovers = new List<SubjectSet>
				{
					new SingleUser
					{
						OdataType = "#microsoft.graph.singleUser",
						UserId = "46184453-e63b-4f20-86c2-c557ed5d5df9",
					},
					new GroupMembers
					{
						OdataType = "#microsoft.graph.groupMembers",
						GroupId = "1623f912-5e86-41c2-af47-39dd67582b66",
					},
				},
				EscalationApprovers = new List<SubjectSet>
				{
				},
				FallbackEscalationApprovers = new List<SubjectSet>
				{
				},
			},
		},
	},
	ReviewSettings = new AccessPackageAssignmentReviewSettings
	{
		IsEnabled = true,
		ExpirationBehavior = AccessReviewExpirationBehavior.KeepAccess,
		IsRecommendationEnabled = true,
		IsReviewerJustificationRequired = true,
		IsSelfReview = false,
		Schedule = new EntitlementManagementSchedule
		{
			StartDateTime = DateTimeOffset.Parse("2022-07-02T06:59:59.998Z"),
			Expiration = new ExpirationPattern
			{
				Duration = TimeSpan.Parse("P14D"),
				Type = ExpirationPatternType.AfterDuration,
			},
			Recurrence = new PatternedRecurrence
			{
				Pattern = new RecurrencePattern
				{
					Type = RecurrencePatternType.AbsoluteMonthly,
					Interval = 3,
					Month = 0,
					DayOfMonth = 0,
					DaysOfWeek = new List<DayOfWeekObject>
					{
					},
				},
				Range = new RecurrenceRange
				{
					Type = RecurrenceRangeType.NoEnd,
					NumberOfOccurrences = 0,
				},
			},
		},
		PrimaryReviewers = new List<SubjectSet>
		{
			new GroupMembers
			{
				OdataType = "#microsoft.graph.groupMembers",
				GroupId = "1623f912-5e86-41c2-af47-39dd67582b66",
			},
		},
		FallbackReviewers = new List<SubjectSet>
		{
		},
	},
	AccessPackage = new AccessPackage
	{
		Id = "a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
displayName := "policy for external access requests"
requestBody.SetDisplayName(&displayName) 
description := "policy for users from connected organizations to request access, with two stages of approval."
requestBody.SetDescription(&description) 
allowedTargetScope := graphmodels.ALLCONFIGUREDCONNECTEDORGANIZATIONUSERS_ALLOWEDTARGETSCOPE 
requestBody.SetAllowedTargetScope(&allowedTargetScope) 
specificAllowedTargets := []graphmodels.SubjectSetable {

}
requestBody.SetSpecificAllowedTargets(specificAllowedTargets)
expiration := graphmodels.NewExpirationPattern()
type := graphmodels.NOEXPIRATION_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
requestBody.SetExpiration(expiration)
requestorSettings := graphmodels.NewAccessPackageAssignmentRequestorSettings()
enableTargetsToSelfAddAccess := true
requestorSettings.SetEnableTargetsToSelfAddAccess(&enableTargetsToSelfAddAccess) 
enableTargetsToSelfUpdateAccess := true
requestorSettings.SetEnableTargetsToSelfUpdateAccess(&enableTargetsToSelfUpdateAccess) 
enableTargetsToSelfRemoveAccess := true
requestorSettings.SetEnableTargetsToSelfRemoveAccess(&enableTargetsToSelfRemoveAccess) 
allowCustomAssignmentSchedule := false
requestorSettings.SetAllowCustomAssignmentSchedule(&allowCustomAssignmentSchedule) 
enableOnBehalfRequestorsToAddAccess := false
requestorSettings.SetEnableOnBehalfRequestorsToAddAccess(&enableOnBehalfRequestorsToAddAccess) 
enableOnBehalfRequestorsToUpdateAccess := false
requestorSettings.SetEnableOnBehalfRequestorsToUpdateAccess(&enableOnBehalfRequestorsToUpdateAccess) 
enableOnBehalfRequestorsToRemoveAccess := false
requestorSettings.SetEnableOnBehalfRequestorsToRemoveAccess(&enableOnBehalfRequestorsToRemoveAccess) 
onBehalfRequestors := []graphmodels.SubjectSetable {

}
requestorSettings.SetOnBehalfRequestors(onBehalfRequestors)
requestBody.SetRequestorSettings(requestorSettings)
requestApprovalSettings := graphmodels.NewAccessPackageAssignmentApprovalSettings()
isApprovalRequiredForAdd := true
requestApprovalSettings.SetIsApprovalRequiredForAdd(&isApprovalRequiredForAdd) 
isApprovalRequiredForUpdate := false
requestApprovalSettings.SetIsApprovalRequiredForUpdate(&isApprovalRequiredForUpdate) 


accessPackageApprovalStage := graphmodels.NewAccessPackageApprovalStage()
durationBeforeAutomaticDenial , err := abstractions.ParseISODuration("P14D")
accessPackageApprovalStage.SetDurationBeforeAutomaticDenial(&durationBeforeAutomaticDenial) 
isApproverJustificationRequired := false
accessPackageApprovalStage.SetIsApproverJustificationRequired(&isApproverJustificationRequired) 
isEscalationEnabled := false
accessPackageApprovalStage.SetIsEscalationEnabled(&isEscalationEnabled) 
durationBeforeEscalation , err := abstractions.ParseISODuration("PT0S")
accessPackageApprovalStage.SetDurationBeforeEscalation(&durationBeforeEscalation) 


subjectSet := graphmodels.NewInternalSponsors()

primaryApprovers := []graphmodels.SubjectSetable {
	subjectSet,
}
accessPackageApprovalStage.SetPrimaryApprovers(primaryApprovers)


subjectSet := graphmodels.NewSingleUser()
userId := "7deff43e-1f17-44ef-9e5f-d516b0ba11d4"
subjectSet.SetUserId(&userId) 
subjectSet1 := graphmodels.NewGroupMembers()
groupId := "1623f912-5e86-41c2-af47-39dd67582b66"
subjectSet1.SetGroupId(&groupId) 

fallbackPrimaryApprovers := []graphmodels.SubjectSetable {
	subjectSet,
	subjectSet1,
}
accessPackageApprovalStage.SetFallbackPrimaryApprovers(fallbackPrimaryApprovers)
escalationApprovers := []graphmodels.SubjectSetable {

}
accessPackageApprovalStage.SetEscalationApprovers(escalationApprovers)
fallbackEscalationApprovers := []graphmodels.SubjectSetable {

}
accessPackageApprovalStage.SetFallbackEscalationApprovers(fallbackEscalationApprovers)
accessPackageApprovalStage1 := graphmodels.NewAccessPackageApprovalStage()
durationBeforeAutomaticDenial , err := abstractions.ParseISODuration("P14D")
accessPackageApprovalStage1.SetDurationBeforeAutomaticDenial(&durationBeforeAutomaticDenial) 
isApproverJustificationRequired := false
accessPackageApprovalStage1.SetIsApproverJustificationRequired(&isApproverJustificationRequired) 
isEscalationEnabled := false
accessPackageApprovalStage1.SetIsEscalationEnabled(&isEscalationEnabled) 
durationBeforeEscalation , err := abstractions.ParseISODuration("PT0S")
accessPackageApprovalStage1.SetDurationBeforeEscalation(&durationBeforeEscalation) 
primaryApprovers := []graphmodels.SubjectSetable {

}
accessPackageApprovalStage1.SetPrimaryApprovers(primaryApprovers)


subjectSet := graphmodels.NewSingleUser()
userId := "46184453-e63b-4f20-86c2-c557ed5d5df9"
subjectSet.SetUserId(&userId) 
subjectSet1 := graphmodels.NewGroupMembers()
groupId := "1623f912-5e86-41c2-af47-39dd67582b66"
subjectSet1.SetGroupId(&groupId) 

fallbackPrimaryApprovers := []graphmodels.SubjectSetable {
	subjectSet,
	subjectSet1,
}
accessPackageApprovalStage1.SetFallbackPrimaryApprovers(fallbackPrimaryApprovers)
escalationApprovers := []graphmodels.SubjectSetable {

}
accessPackageApprovalStage1.SetEscalationApprovers(escalationApprovers)
fallbackEscalationApprovers := []graphmodels.SubjectSetable {

}
accessPackageApprovalStage1.SetFallbackEscalationApprovers(fallbackEscalationApprovers)

stages := []graphmodels.AccessPackageApprovalStageable {
	accessPackageApprovalStage,
	accessPackageApprovalStage1,
}
requestApprovalSettings.SetStages(stages)
requestBody.SetRequestApprovalSettings(requestApprovalSettings)
reviewSettings := graphmodels.NewAccessPackageAssignmentReviewSettings()
isEnabled := true
reviewSettings.SetIsEnabled(&isEnabled) 
expirationBehavior := graphmodels.KEEPACCESS_ACCESSREVIEWEXPIRATIONBEHAVIOR 
reviewSettings.SetExpirationBehavior(&expirationBehavior) 
isRecommendationEnabled := true
reviewSettings.SetIsRecommendationEnabled(&isRecommendationEnabled) 
isReviewerJustificationRequired := true
reviewSettings.SetIsReviewerJustificationRequired(&isReviewerJustificationRequired) 
isSelfReview := false
reviewSettings.SetIsSelfReview(&isSelfReview) 
schedule := graphmodels.NewEntitlementManagementSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2022-07-02T06:59:59.998Z")
schedule.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
duration , err := abstractions.ParseISODuration("P14D")
expiration.SetDuration(&duration) 
type := graphmodels.AFTERDURATION_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
schedule.SetExpiration(expiration)
recurrence := graphmodels.NewPatternedRecurrence()
pattern := graphmodels.NewRecurrencePattern()
type := graphmodels.ABSOLUTEMONTHLY_RECURRENCEPATTERNTYPE 
pattern.SetType(&type) 
interval := int32(3)
pattern.SetInterval(&interval) 
month := int32(0)
pattern.SetMonth(&month) 
dayOfMonth := int32(0)
pattern.SetDayOfMonth(&dayOfMonth) 
daysOfWeek := []graphmodels.DayOfWeekable {

}
pattern.SetDaysOfWeek(daysOfWeek)
recurrence.SetPattern(pattern)
range := graphmodels.NewRecurrenceRange()
type := graphmodels.NOEND_RECURRENCERANGETYPE 
range.SetType(&type) 
numberOfOccurrences := int32(0)
range.SetNumberOfOccurrences(&numberOfOccurrences) 
recurrence.SetRange(range)
schedule.SetRecurrence(recurrence)
reviewSettings.SetSchedule(schedule)


subjectSet := graphmodels.NewGroupMembers()
groupId := "1623f912-5e86-41c2-af47-39dd67582b66"
subjectSet.SetGroupId(&groupId) 

primaryReviewers := []graphmodels.SubjectSetable {
	subjectSet,
}
reviewSettings.SetPrimaryReviewers(primaryReviewers)
fallbackReviewers := []graphmodels.SubjectSetable {

}
reviewSettings.SetFallbackReviewers(fallbackReviewers)
requestBody.SetReviewSettings(reviewSettings)
accessPackage := graphmodels.NewAccessPackage()
id := "a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b"
accessPackage.SetId(&id) 
requestBody.SetAccessPackage(accessPackage)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentPolicies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setDisplayName("policy for external access requests");
accessPackageAssignmentPolicy.setDescription("policy for users from connected organizations to request access, with two stages of approval.");
accessPackageAssignmentPolicy.setAllowedTargetScope(AllowedTargetScope.AllConfiguredConnectedOrganizationUsers);
LinkedList<SubjectSet> specificAllowedTargets = new LinkedList<SubjectSet>();
accessPackageAssignmentPolicy.setSpecificAllowedTargets(specificAllowedTargets);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.NoExpiration);
accessPackageAssignmentPolicy.setExpiration(expiration);
AccessPackageAssignmentRequestorSettings requestorSettings = new AccessPackageAssignmentRequestorSettings();
requestorSettings.setEnableTargetsToSelfAddAccess(true);
requestorSettings.setEnableTargetsToSelfUpdateAccess(true);
requestorSettings.setEnableTargetsToSelfRemoveAccess(true);
requestorSettings.setAllowCustomAssignmentSchedule(false);
requestorSettings.setEnableOnBehalfRequestorsToAddAccess(false);
requestorSettings.setEnableOnBehalfRequestorsToUpdateAccess(false);
requestorSettings.setEnableOnBehalfRequestorsToRemoveAccess(false);
LinkedList<SubjectSet> onBehalfRequestors = new LinkedList<SubjectSet>();
requestorSettings.setOnBehalfRequestors(onBehalfRequestors);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
AccessPackageAssignmentApprovalSettings requestApprovalSettings = new AccessPackageAssignmentApprovalSettings();
requestApprovalSettings.setIsApprovalRequiredForAdd(true);
requestApprovalSettings.setIsApprovalRequiredForUpdate(false);
LinkedList<AccessPackageApprovalStage> stages = new LinkedList<AccessPackageApprovalStage>();
AccessPackageApprovalStage accessPackageApprovalStage = new AccessPackageApprovalStage();
PeriodAndDuration durationBeforeAutomaticDenial = PeriodAndDuration.ofDuration(Duration.parse("P14D"));
accessPackageApprovalStage.setDurationBeforeAutomaticDenial(durationBeforeAutomaticDenial);
accessPackageApprovalStage.setIsApproverJustificationRequired(false);
accessPackageApprovalStage.setIsEscalationEnabled(false);
PeriodAndDuration durationBeforeEscalation = PeriodAndDuration.ofDuration(Duration.parse("PT0S"));
accessPackageApprovalStage.setDurationBeforeEscalation(durationBeforeEscalation);
LinkedList<SubjectSet> primaryApprovers = new LinkedList<SubjectSet>();
InternalSponsors subjectSet = new InternalSponsors();
subjectSet.setOdataType("#microsoft.graph.internalSponsors");
primaryApprovers.add(subjectSet);
accessPackageApprovalStage.setPrimaryApprovers(primaryApprovers);
LinkedList<SubjectSet> fallbackPrimaryApprovers = new LinkedList<SubjectSet>();
SingleUser subjectSet1 = new SingleUser();
subjectSet1.setOdataType("#microsoft.graph.singleUser");
subjectSet1.setUserId("7deff43e-1f17-44ef-9e5f-d516b0ba11d4");
fallbackPrimaryApprovers.add(subjectSet1);
GroupMembers subjectSet2 = new GroupMembers();
subjectSet2.setOdataType("#microsoft.graph.groupMembers");
subjectSet2.setGroupId("1623f912-5e86-41c2-af47-39dd67582b66");
fallbackPrimaryApprovers.add(subjectSet2);
accessPackageApprovalStage.setFallbackPrimaryApprovers(fallbackPrimaryApprovers);
LinkedList<SubjectSet> escalationApprovers = new LinkedList<SubjectSet>();
accessPackageApprovalStage.setEscalationApprovers(escalationApprovers);
LinkedList<SubjectSet> fallbackEscalationApprovers = new LinkedList<SubjectSet>();
accessPackageApprovalStage.setFallbackEscalationApprovers(fallbackEscalationApprovers);
stages.add(accessPackageApprovalStage);
AccessPackageApprovalStage accessPackageApprovalStage1 = new AccessPackageApprovalStage();
PeriodAndDuration durationBeforeAutomaticDenial1 = PeriodAndDuration.ofDuration(Duration.parse("P14D"));
accessPackageApprovalStage1.setDurationBeforeAutomaticDenial(durationBeforeAutomaticDenial1);
accessPackageApprovalStage1.setIsApproverJustificationRequired(false);
accessPackageApprovalStage1.setIsEscalationEnabled(false);
PeriodAndDuration durationBeforeEscalation1 = PeriodAndDuration.ofDuration(Duration.parse("PT0S"));
accessPackageApprovalStage1.setDurationBeforeEscalation(durationBeforeEscalation1);
LinkedList<SubjectSet> primaryApprovers1 = new LinkedList<SubjectSet>();
accessPackageApprovalStage1.setPrimaryApprovers(primaryApprovers1);
LinkedList<SubjectSet> fallbackPrimaryApprovers1 = new LinkedList<SubjectSet>();
SingleUser subjectSet3 = new SingleUser();
subjectSet3.setOdataType("#microsoft.graph.singleUser");
subjectSet3.setUserId("46184453-e63b-4f20-86c2-c557ed5d5df9");
fallbackPrimaryApprovers1.add(subjectSet3);
GroupMembers subjectSet4 = new GroupMembers();
subjectSet4.setOdataType("#microsoft.graph.groupMembers");
subjectSet4.setGroupId("1623f912-5e86-41c2-af47-39dd67582b66");
fallbackPrimaryApprovers1.add(subjectSet4);
accessPackageApprovalStage1.setFallbackPrimaryApprovers(fallbackPrimaryApprovers1);
LinkedList<SubjectSet> escalationApprovers1 = new LinkedList<SubjectSet>();
accessPackageApprovalStage1.setEscalationApprovers(escalationApprovers1);
LinkedList<SubjectSet> fallbackEscalationApprovers1 = new LinkedList<SubjectSet>();
accessPackageApprovalStage1.setFallbackEscalationApprovers(fallbackEscalationApprovers1);
stages.add(accessPackageApprovalStage1);
requestApprovalSettings.setStages(stages);
accessPackageAssignmentPolicy.setRequestApprovalSettings(requestApprovalSettings);
AccessPackageAssignmentReviewSettings reviewSettings = new AccessPackageAssignmentReviewSettings();
reviewSettings.setIsEnabled(true);
reviewSettings.setExpirationBehavior(AccessReviewExpirationBehavior.KeepAccess);
reviewSettings.setIsRecommendationEnabled(true);
reviewSettings.setIsReviewerJustificationRequired(true);
reviewSettings.setIsSelfReview(false);
EntitlementManagementSchedule schedule = new EntitlementManagementSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2022-07-02T06:59:59.998Z");
schedule.setStartDateTime(startDateTime);
ExpirationPattern expiration1 = new ExpirationPattern();
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("P14D"));
expiration1.setDuration(duration);
expiration1.setType(ExpirationPatternType.AfterDuration);
schedule.setExpiration(expiration1);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.AbsoluteMonthly);
pattern.setInterval(3);
pattern.setMonth(0);
pattern.setDayOfMonth(0);
LinkedList<DayOfWeek> daysOfWeek = new LinkedList<DayOfWeek>();
pattern.setDaysOfWeek(daysOfWeek);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.NoEnd);
range.setNumberOfOccurrences(0);
recurrence.setRange(range);
schedule.setRecurrence(recurrence);
reviewSettings.setSchedule(schedule);
LinkedList<SubjectSet> primaryReviewers = new LinkedList<SubjectSet>();
GroupMembers subjectSet5 = new GroupMembers();
subjectSet5.setOdataType("#microsoft.graph.groupMembers");
subjectSet5.setGroupId("1623f912-5e86-41c2-af47-39dd67582b66");
primaryReviewers.add(subjectSet5);
reviewSettings.setPrimaryReviewers(primaryReviewers);
LinkedList<SubjectSet> fallbackReviewers = new LinkedList<SubjectSet>();
reviewSettings.setFallbackReviewers(fallbackReviewers);
accessPackageAssignmentPolicy.setReviewSettings(reviewSettings);
AccessPackage accessPackage = new AccessPackage();
accessPackage.setId("a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b");
accessPackageAssignmentPolicy.setAccessPackage(accessPackage);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().assignmentPolicies().post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
    displayName: 'policy for external access requests',
    description: 'policy for users from connected organizations to request access, with two stages of approval.',
    allowedTargetScope: 'allConfiguredConnectedOrganizationUsers',
    specificAllowedTargets: [],
    expiration: {
        type: 'noExpiration'
    },
    requestorSettings: {
        enableTargetsToSelfAddAccess: true,
        enableTargetsToSelfUpdateAccess: true,
        enableTargetsToSelfRemoveAccess: true,
        allowCustomAssignmentSchedule: false,
        enableOnBehalfRequestorsToAddAccess: false,
        enableOnBehalfRequestorsToUpdateAccess: false,
        enableOnBehalfRequestorsToRemoveAccess: false,
        onBehalfRequestors: []
    },
    requestApprovalSettings: {
        isApprovalRequiredForAdd: true,
        isApprovalRequiredForUpdate: false,
        stages: [
            {
                durationBeforeAutomaticDenial: 'P14D',
                isApproverJustificationRequired: false,
                isEscalationEnabled: false,
                durationBeforeEscalation: 'PT0S',
                primaryApprovers: [
                    {
                        '@odata.type': '#microsoft.graph.internalSponsors'
                    }
                ],
                fallbackPrimaryApprovers: [
                    {
                        '@odata.type': '#microsoft.graph.singleUser',
                        userId: '7deff43e-1f17-44ef-9e5f-d516b0ba11d4'
                    },
                    {
                        '@odata.type': '#microsoft.graph.groupMembers',
                        groupId: '1623f912-5e86-41c2-af47-39dd67582b66'
                    }
                ],
                escalationApprovers: [],
                fallbackEscalationApprovers: []
            },
            {
                durationBeforeAutomaticDenial: 'P14D',
                isApproverJustificationRequired: false,
                isEscalationEnabled: false,
                durationBeforeEscalation: 'PT0S',
                primaryApprovers: [],
                fallbackPrimaryApprovers: [
                    {
                        '@odata.type': '#microsoft.graph.singleUser',
                        userId: '46184453-e63b-4f20-86c2-c557ed5d5df9'
                    },
                    {
                        '@odata.type': '#microsoft.graph.groupMembers',
                        groupId: '1623f912-5e86-41c2-af47-39dd67582b66'
                    }
                ],
                escalationApprovers: [],
                fallbackEscalationApprovers: []
            }
        ]
    },
    reviewSettings: {
        isEnabled: true,
        expirationBehavior: 'keepAccess',
        isRecommendationEnabled: true,
        isReviewerJustificationRequired: true,
        isSelfReview: false,
        schedule: {
            startDateTime: '2022-07-02T06:59:59.998Z',
            expiration: {
                duration: 'P14D',
                type: 'afterDuration'
            },
            recurrence: {
                pattern: {
                    type: 'absoluteMonthly',
                    interval: 3,
                    month: 0,
                    dayOfMonth: 0,
                    daysOfWeek: []
                },
                range: {
                    type: 'noEnd',
                    numberOfOccurrences: 0
                }
            }
        },
        primaryReviewers: [
            {
                '@odata.type': '#microsoft.graph.groupMembers',
                groupId: '1623f912-5e86-41c2-af47-39dd67582b66'
            }
        ],
        fallbackReviewers: []
    },
    accessPackage: {
        id: 'a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b'
    }
};

await client.api('/identityGovernance/entitlementManagement/assignmentPolicies')
	.post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Generated\Models\AllowedTargetScope;
use Microsoft\Graph\Generated\Models\SubjectSet;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequestorSettings;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentApprovalSettings;
use Microsoft\Graph\Generated\Models\AccessPackageApprovalStage;
use Microsoft\Graph\Generated\Models\InternalSponsors;
use Microsoft\Graph\Generated\Models\SingleUser;
use Microsoft\Graph\Generated\Models\GroupMembers;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentReviewSettings;
use Microsoft\Graph\Generated\Models\AccessReviewExpirationBehavior;
use Microsoft\Graph\Generated\Models\EntitlementManagementSchedule;
use Microsoft\Graph\Generated\Models\PatternedRecurrence;
use Microsoft\Graph\Generated\Models\RecurrencePattern;
use Microsoft\Graph\Generated\Models\RecurrencePatternType;
use Microsoft\Graph\Generated\Models\DayOfWeek;
use Microsoft\Graph\Generated\Models\RecurrenceRange;
use Microsoft\Graph\Generated\Models\RecurrenceRangeType;
use Microsoft\Graph\Generated\Models\AccessPackage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setDisplayName('policy for external access requests');
$requestBody->setDescription('policy for users from connected organizations to request access, with two stages of approval.');
$requestBody->setAllowedTargetScope(new AllowedTargetScope('allConfiguredConnectedOrganizationUsers'));
$requestBody->setSpecificAllowedTargets([	]);
$expiration = new ExpirationPattern();
$expiration->setType(new ExpirationPatternType('noExpiration'));
$requestBody->setExpiration($expiration);
$requestorSettings = new AccessPackageAssignmentRequestorSettings();
$requestorSettings->setEnableTargetsToSelfAddAccess(true);
$requestorSettings->setEnableTargetsToSelfUpdateAccess(true);
$requestorSettings->setEnableTargetsToSelfRemoveAccess(true);
$requestorSettings->setAllowCustomAssignmentSchedule(false);
$requestorSettings->setEnableOnBehalfRequestorsToAddAccess(false);
$requestorSettings->setEnableOnBehalfRequestorsToUpdateAccess(false);
$requestorSettings->setEnableOnBehalfRequestorsToRemoveAccess(false);
$requestorSettings->setOnBehalfRequestors([	]);
$requestBody->setRequestorSettings($requestorSettings);
$requestApprovalSettings = new AccessPackageAssignmentApprovalSettings();
$requestApprovalSettings->setIsApprovalRequiredForAdd(true);
$requestApprovalSettings->setIsApprovalRequiredForUpdate(false);
$stagesAccessPackageApprovalStage1 = new AccessPackageApprovalStage();
$stagesAccessPackageApprovalStage1->setDurationBeforeAutomaticDenial(new \DateInterval('P14D'));
$stagesAccessPackageApprovalStage1->setIsApproverJustificationRequired(false);
$stagesAccessPackageApprovalStage1->setIsEscalationEnabled(false);
$stagesAccessPackageApprovalStage1->setDurationBeforeEscalation(new \DateInterval('PT0S'));
$primaryApproversSubjectSet1 = new InternalSponsors();
$primaryApproversSubjectSet1->setOdataType('#microsoft.graph.internalSponsors');
$primaryApproversArray []= $primaryApproversSubjectSet1;
$stagesAccessPackageApprovalStage1->setPrimaryApprovers($primaryApproversArray);

$fallbackPrimaryApproversSubjectSet1 = new SingleUser();
$fallbackPrimaryApproversSubjectSet1->setOdataType('#microsoft.graph.singleUser');
$fallbackPrimaryApproversSubjectSet1->setUserId('7deff43e-1f17-44ef-9e5f-d516b0ba11d4');
$fallbackPrimaryApproversArray []= $fallbackPrimaryApproversSubjectSet1;
$fallbackPrimaryApproversSubjectSet2 = new GroupMembers();
$fallbackPrimaryApproversSubjectSet2->setOdataType('#microsoft.graph.groupMembers');
$fallbackPrimaryApproversSubjectSet2->setGroupId('1623f912-5e86-41c2-af47-39dd67582b66');
$fallbackPrimaryApproversArray []= $fallbackPrimaryApproversSubjectSet2;
$stagesAccessPackageApprovalStage1->setFallbackPrimaryApprovers($fallbackPrimaryApproversArray);

$stagesAccessPackageApprovalStage1->setEscalationApprovers([]);
$stagesAccessPackageApprovalStage1->setFallbackEscalationApprovers([]);
$stagesArray []= $stagesAccessPackageApprovalStage1;
$stagesAccessPackageApprovalStage2 = new AccessPackageApprovalStage();
$stagesAccessPackageApprovalStage2->setDurationBeforeAutomaticDenial(new \DateInterval('P14D'));
$stagesAccessPackageApprovalStage2->setIsApproverJustificationRequired(false);
$stagesAccessPackageApprovalStage2->setIsEscalationEnabled(false);
$stagesAccessPackageApprovalStage2->setDurationBeforeEscalation(new \DateInterval('PT0S'));
$stagesAccessPackageApprovalStage2->setPrimaryApprovers([]);
$fallbackPrimaryApproversSubjectSet1 = new SingleUser();
$fallbackPrimaryApproversSubjectSet1->setOdataType('#microsoft.graph.singleUser');
$fallbackPrimaryApproversSubjectSet1->setUserId('46184453-e63b-4f20-86c2-c557ed5d5df9');
$fallbackPrimaryApproversArray []= $fallbackPrimaryApproversSubjectSet1;
$fallbackPrimaryApproversSubjectSet2 = new GroupMembers();
$fallbackPrimaryApproversSubjectSet2->setOdataType('#microsoft.graph.groupMembers');
$fallbackPrimaryApproversSubjectSet2->setGroupId('1623f912-5e86-41c2-af47-39dd67582b66');
$fallbackPrimaryApproversArray []= $fallbackPrimaryApproversSubjectSet2;
$stagesAccessPackageApprovalStage2->setFallbackPrimaryApprovers($fallbackPrimaryApproversArray);

$stagesAccessPackageApprovalStage2->setEscalationApprovers([]);
$stagesAccessPackageApprovalStage2->setFallbackEscalationApprovers([]);
$stagesArray []= $stagesAccessPackageApprovalStage2;
$requestApprovalSettings->setStages($stagesArray);

$requestBody->setRequestApprovalSettings($requestApprovalSettings);
$reviewSettings = new AccessPackageAssignmentReviewSettings();
$reviewSettings->setIsEnabled(true);
$reviewSettings->setExpirationBehavior(new AccessReviewExpirationBehavior('keepAccess'));
$reviewSettings->setIsRecommendationEnabled(true);
$reviewSettings->setIsReviewerJustificationRequired(true);
$reviewSettings->setIsSelfReview(false);
$reviewSettingsSchedule = new EntitlementManagementSchedule();
$reviewSettingsSchedule->setStartDateTime(new \DateTime('2022-07-02T06:59:59.998Z'));
$reviewSettingsScheduleExpiration = new ExpirationPattern();
$reviewSettingsScheduleExpiration->setDuration(new \DateInterval('P14D'));
$reviewSettingsScheduleExpiration->setType(new ExpirationPatternType('afterDuration'));
$reviewSettingsSchedule->setExpiration($reviewSettingsScheduleExpiration);
$reviewSettingsScheduleRecurrence = new PatternedRecurrence();
$reviewSettingsScheduleRecurrencePattern = new RecurrencePattern();
$reviewSettingsScheduleRecurrencePattern->setType(new RecurrencePatternType('absoluteMonthly'));
$reviewSettingsScheduleRecurrencePattern->setInterval(3);
$reviewSettingsScheduleRecurrencePattern->setMonth(0);
$reviewSettingsScheduleRecurrencePattern->setDayOfMonth(0);
$reviewSettingsScheduleRecurrencePattern->setDaysOfWeek([]);
$reviewSettingsScheduleRecurrence->setPattern($reviewSettingsScheduleRecurrencePattern);
$reviewSettingsScheduleRecurrenceRange = new RecurrenceRange();
$reviewSettingsScheduleRecurrenceRange->setType(new RecurrenceRangeType('noEnd'));
$reviewSettingsScheduleRecurrenceRange->setNumberOfOccurrences(0);
$reviewSettingsScheduleRecurrence->setRange($reviewSettingsScheduleRecurrenceRange);
$reviewSettingsSchedule->setRecurrence($reviewSettingsScheduleRecurrence);
$reviewSettings->setSchedule($reviewSettingsSchedule);
$primaryReviewersSubjectSet1 = new GroupMembers();
$primaryReviewersSubjectSet1->setOdataType('#microsoft.graph.groupMembers');
$primaryReviewersSubjectSet1->setGroupId('1623f912-5e86-41c2-af47-39dd67582b66');
$primaryReviewersArray []= $primaryReviewersSubjectSet1;
$reviewSettings->setPrimaryReviewers($primaryReviewersArray);

$reviewSettings->setFallbackReviewers([]);
$requestBody->setReviewSettings($reviewSettings);
$accessPackage = new AccessPackage();
$accessPackage->setId('a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b');
$requestBody->setAccessPackage($accessPackage);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentPolicies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "policy for external access requests"
	description = "policy for users from connected organizations to request access, with two stages of approval."
	allowedTargetScope = "allConfiguredConnectedOrganizationUsers"
	specificAllowedTargets = @(
	)
	expiration = @{
		type = "noExpiration"
	}
	requestorSettings = @{
		enableTargetsToSelfAddAccess = $true
		enableTargetsToSelfUpdateAccess = $true
		enableTargetsToSelfRemoveAccess = $true
		allowCustomAssignmentSchedule = $false
		enableOnBehalfRequestorsToAddAccess = $false
		enableOnBehalfRequestorsToUpdateAccess = $false
		enableOnBehalfRequestorsToRemoveAccess = $false
		onBehalfRequestors = @(
		)
	}
	requestApprovalSettings = @{
		isApprovalRequiredForAdd = $true
		isApprovalRequiredForUpdate = $false
		stages = @(
			@{
				durationBeforeAutomaticDenial = "P14D"
				isApproverJustificationRequired = $false
				isEscalationEnabled = $false
				durationBeforeEscalation = "PT0S"
				primaryApprovers = @(
					@{
						"@odata.type" = "#microsoft.graph.internalSponsors"
					}
				)
				fallbackPrimaryApprovers = @(
					@{
						"@odata.type" = "#microsoft.graph.singleUser"
						userId = "7deff43e-1f17-44ef-9e5f-d516b0ba11d4"
					}
					@{
						"@odata.type" = "#microsoft.graph.groupMembers"
						groupId = "1623f912-5e86-41c2-af47-39dd67582b66"
					}
				)
				escalationApprovers = @(
				)
				fallbackEscalationApprovers = @(
				)
			}
			@{
				durationBeforeAutomaticDenial = "P14D"
				isApproverJustificationRequired = $false
				isEscalationEnabled = $false
				durationBeforeEscalation = "PT0S"
				primaryApprovers = @(
				)
				fallbackPrimaryApprovers = @(
					@{
						"@odata.type" = "#microsoft.graph.singleUser"
						userId = "46184453-e63b-4f20-86c2-c557ed5d5df9"
					}
					@{
						"@odata.type" = "#microsoft.graph.groupMembers"
						groupId = "1623f912-5e86-41c2-af47-39dd67582b66"
					}
				)
				escalationApprovers = @(
				)
				fallbackEscalationApprovers = @(
				)
			}
		)
	}
	reviewSettings = @{
		isEnabled = $true
		expirationBehavior = "keepAccess"
		isRecommendationEnabled = $true
		isReviewerJustificationRequired = $true
		isSelfReview = $false
		schedule = @{
			startDateTime = [System.DateTime]::Parse("2022-07-02T06:59:59.998Z")
			expiration = @{
				duration = "P14D"
				type = "afterDuration"
			}
			recurrence = @{
				pattern = @{
					type = "absoluteMonthly"
					interval = 3
					month = 0
					dayOfMonth = 0
					daysOfWeek = @(
					)
				}
				range = @{
					type = "noEnd"
					numberOfOccurrences = 0
				}
			}
		}
		primaryReviewers = @(
			@{
				"@odata.type" = "#microsoft.graph.groupMembers"
				groupId = "1623f912-5e86-41c2-af47-39dd67582b66"
			}
		)
		fallbackReviewers = @(
		)
	}
	accessPackage = @{
		id = "a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b"
	}
}

New-MgEntitlementManagementAssignmentPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph.generated.models.allowed_target_scope import AllowedTargetScope
from msgraph.generated.models.subject_set import SubjectSet
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
from msgraph.generated.models.access_package_assignment_requestor_settings import AccessPackageAssignmentRequestorSettings
from msgraph.generated.models.access_package_assignment_approval_settings import AccessPackageAssignmentApprovalSettings
from msgraph.generated.models.access_package_approval_stage import AccessPackageApprovalStage
from msgraph.generated.models.internal_sponsors import InternalSponsors
from msgraph.generated.models.single_user import SingleUser
from msgraph.generated.models.group_members import GroupMembers
from msgraph.generated.models.access_package_assignment_review_settings import AccessPackageAssignmentReviewSettings
from msgraph.generated.models.access_review_expiration_behavior import AccessReviewExpirationBehavior
from msgraph.generated.models.entitlement_management_schedule import EntitlementManagementSchedule
from msgraph.generated.models.patterned_recurrence import PatternedRecurrence
from msgraph.generated.models.recurrence_pattern import RecurrencePattern
from msgraph.generated.models.recurrence_pattern_type import RecurrencePatternType
from msgraph.generated.models.day_of_week import DayOfWeek
from msgraph.generated.models.recurrence_range import RecurrenceRange
from msgraph.generated.models.recurrence_range_type import RecurrenceRangeType
from msgraph.generated.models.access_package import AccessPackage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	display_name = "policy for external access requests",
	description = "policy for users from connected organizations to request access, with two stages of approval.",
	allowed_target_scope = AllowedTargetScope.AllConfiguredConnectedOrganizationUsers,
	specific_allowed_targets = [
	],
	expiration = ExpirationPattern(
		type = ExpirationPatternType.NoExpiration,
	),
	requestor_settings = AccessPackageAssignmentRequestorSettings(
		enable_targets_to_self_add_access = True,
		enable_targets_to_self_update_access = True,
		enable_targets_to_self_remove_access = True,
		allow_custom_assignment_schedule = False,
		enable_on_behalf_requestors_to_add_access = False,
		enable_on_behalf_requestors_to_update_access = False,
		enable_on_behalf_requestors_to_remove_access = False,
		on_behalf_requestors = [
		],
	),
	request_approval_settings = AccessPackageAssignmentApprovalSettings(
		is_approval_required_for_add = True,
		is_approval_required_for_update = False,
		stages = [
			AccessPackageApprovalStage(
				duration_before_automatic_denial = "P14D",
				is_approver_justification_required = False,
				is_escalation_enabled = False,
				duration_before_escalation = "PT0S",
				primary_approvers = [
					InternalSponsors(
						odata_type = "#microsoft.graph.internalSponsors",
					),
				],
				fallback_primary_approvers = [
					SingleUser(
						odata_type = "#microsoft.graph.singleUser",
						user_id = "7deff43e-1f17-44ef-9e5f-d516b0ba11d4",
					),
					GroupMembers(
						odata_type = "#microsoft.graph.groupMembers",
						group_id = "1623f912-5e86-41c2-af47-39dd67582b66",
					),
				],
				escalation_approvers = [
				],
				fallback_escalation_approvers = [
				],
			),
			AccessPackageApprovalStage(
				duration_before_automatic_denial = "P14D",
				is_approver_justification_required = False,
				is_escalation_enabled = False,
				duration_before_escalation = "PT0S",
				primary_approvers = [
				],
				fallback_primary_approvers = [
					SingleUser(
						odata_type = "#microsoft.graph.singleUser",
						user_id = "46184453-e63b-4f20-86c2-c557ed5d5df9",
					),
					GroupMembers(
						odata_type = "#microsoft.graph.groupMembers",
						group_id = "1623f912-5e86-41c2-af47-39dd67582b66",
					),
				],
				escalation_approvers = [
				],
				fallback_escalation_approvers = [
				],
			),
		],
	),
	review_settings = AccessPackageAssignmentReviewSettings(
		is_enabled = True,
		expiration_behavior = AccessReviewExpirationBehavior.KeepAccess,
		is_recommendation_enabled = True,
		is_reviewer_justification_required = True,
		is_self_review = False,
		schedule = EntitlementManagementSchedule(
			start_date_time = "2022-07-02T06:59:59.998Z",
			expiration = ExpirationPattern(
				duration = "P14D",
				type = ExpirationPatternType.AfterDuration,
			),
			recurrence = PatternedRecurrence(
				pattern = RecurrencePattern(
					type = RecurrencePatternType.AbsoluteMonthly,
					interval = 3,
					month = 0,
					day_of_month = 0,
					days_of_week = [
					],
				),
				range = RecurrenceRange(
					type = RecurrenceRangeType.NoEnd,
					number_of_occurrences = 0,
				),
			),
		),
		primary_reviewers = [
			GroupMembers(
				odata_type = "#microsoft.graph.groupMembers",
				group_id = "1623f912-5e86-41c2-af47-39dd67582b66",
			),
		],
		fallback_reviewers = [
		],
	),
	access_package = AccessPackage(
		id = "a2e1ca1e-4e56-47d2-9daa-e2ba8d12a82b",
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "9d8f2361-39be-482e-b267-34ad6baef4d3",
    "displayName": "policy for external access requests",
    "description": "policy for users from connected organizations to request access, with two stages of approval."
}
```

### Example 3: Create a policy that automatically creates assignments based on a membership rule

The following example shows a policy that automatically creates assignments for users in the sales department.

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentPolicies
Content-Type: application/json

{
    "displayName": "Sales department users",
    "description": "All users from sales department",
    "allowedTargetScope": "specificDirectoryUsers",
    "specificAllowedTargets": [
        {
            "@odata.type": "#microsoft.graph.attributeRuleMembers",
            "description": "Membership rule for all users from sales department",
            "membershipRule": "(user.department -eq \"Sales\")"
        }
    ],
    "automaticRequestSettings": {
        "requestAccessForAllowedTargets": true,
        "removeAccessWhenTargetLeavesAllowedTargets": true,
        "gracePeriodBeforeAccessRemoval": "P7D"
    },
    "accessPackage": {
        "id": "8a36831e-1527-4b2b-aff2-81259a8d8e76"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentPolicy
{
	DisplayName = "Sales department users",
	Description = "All users from sales department",
	AllowedTargetScope = AllowedTargetScope.SpecificDirectoryUsers,
	SpecificAllowedTargets = new List<SubjectSet>
	{
		new AttributeRuleMembers
		{
			OdataType = "#microsoft.graph.attributeRuleMembers",
			Description = "Membership rule for all users from sales department",
			MembershipRule = "(user.department -eq \"Sales\")",
		},
	},
	AutomaticRequestSettings = new AccessPackageAutomaticRequestSettings
	{
		RequestAccessForAllowedTargets = true,
		RemoveAccessWhenTargetLeavesAllowedTargets = true,
		GracePeriodBeforeAccessRemoval = TimeSpan.Parse("P7D"),
	},
	AccessPackage = new AccessPackage
	{
		Id = "8a36831e-1527-4b2b-aff2-81259a8d8e76",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
displayName := "Sales department users"
requestBody.SetDisplayName(&displayName) 
description := "All users from sales department"
requestBody.SetDescription(&description) 
allowedTargetScope := graphmodels.SPECIFICDIRECTORYUSERS_ALLOWEDTARGETSCOPE 
requestBody.SetAllowedTargetScope(&allowedTargetScope) 


subjectSet := graphmodels.NewAttributeRuleMembers()
description := "Membership rule for all users from sales department"
subjectSet.SetDescription(&description) 
membershipRule := "(user.department -eq \"Sales\")"
subjectSet.SetMembershipRule(&membershipRule) 

specificAllowedTargets := []graphmodels.SubjectSetable {
	subjectSet,
}
requestBody.SetSpecificAllowedTargets(specificAllowedTargets)
automaticRequestSettings := graphmodels.NewAccessPackageAutomaticRequestSettings()
requestAccessForAllowedTargets := true
automaticRequestSettings.SetRequestAccessForAllowedTargets(&requestAccessForAllowedTargets) 
removeAccessWhenTargetLeavesAllowedTargets := true
automaticRequestSettings.SetRemoveAccessWhenTargetLeavesAllowedTargets(&removeAccessWhenTargetLeavesAllowedTargets) 
gracePeriodBeforeAccessRemoval , err := abstractions.ParseISODuration("P7D")
automaticRequestSettings.SetGracePeriodBeforeAccessRemoval(&gracePeriodBeforeAccessRemoval) 
requestBody.SetAutomaticRequestSettings(automaticRequestSettings)
accessPackage := graphmodels.NewAccessPackage()
id := "8a36831e-1527-4b2b-aff2-81259a8d8e76"
accessPackage.SetId(&id) 
requestBody.SetAccessPackage(accessPackage)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentPolicies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setDisplayName("Sales department users");
accessPackageAssignmentPolicy.setDescription("All users from sales department");
accessPackageAssignmentPolicy.setAllowedTargetScope(AllowedTargetScope.SpecificDirectoryUsers);
LinkedList<SubjectSet> specificAllowedTargets = new LinkedList<SubjectSet>();
AttributeRuleMembers subjectSet = new AttributeRuleMembers();
subjectSet.setOdataType("#microsoft.graph.attributeRuleMembers");
subjectSet.setDescription("Membership rule for all users from sales department");
subjectSet.setMembershipRule("(user.department -eq \"Sales\")");
specificAllowedTargets.add(subjectSet);
accessPackageAssignmentPolicy.setSpecificAllowedTargets(specificAllowedTargets);
AccessPackageAutomaticRequestSettings automaticRequestSettings = new AccessPackageAutomaticRequestSettings();
automaticRequestSettings.setRequestAccessForAllowedTargets(true);
automaticRequestSettings.setRemoveAccessWhenTargetLeavesAllowedTargets(true);
PeriodAndDuration gracePeriodBeforeAccessRemoval = PeriodAndDuration.ofDuration(Duration.parse("P7D"));
automaticRequestSettings.setGracePeriodBeforeAccessRemoval(gracePeriodBeforeAccessRemoval);
accessPackageAssignmentPolicy.setAutomaticRequestSettings(automaticRequestSettings);
AccessPackage accessPackage = new AccessPackage();
accessPackage.setId("8a36831e-1527-4b2b-aff2-81259a8d8e76");
accessPackageAssignmentPolicy.setAccessPackage(accessPackage);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().assignmentPolicies().post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
    displayName: 'Sales department users',
    description: 'All users from sales department',
    allowedTargetScope: 'specificDirectoryUsers',
    specificAllowedTargets: [
        {
            '@odata.type': '#microsoft.graph.attributeRuleMembers',
            description: 'Membership rule for all users from sales department',
            membershipRule: '(user.department -eq \"Sales\")'
        }
    ],
    automaticRequestSettings: {
        requestAccessForAllowedTargets: true,
        removeAccessWhenTargetLeavesAllowedTargets: true,
        gracePeriodBeforeAccessRemoval: 'P7D'
    },
    accessPackage: {
        id: '8a36831e-1527-4b2b-aff2-81259a8d8e76'
    }
};

await client.api('/identityGovernance/entitlementManagement/assignmentPolicies')
	.post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Generated\Models\AllowedTargetScope;
use Microsoft\Graph\Generated\Models\SubjectSet;
use Microsoft\Graph\Generated\Models\AttributeRuleMembers;
use Microsoft\Graph\Generated\Models\AccessPackageAutomaticRequestSettings;
use Microsoft\Graph\Generated\Models\AccessPackage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setDisplayName('Sales department users');
$requestBody->setDescription('All users from sales department');
$requestBody->setAllowedTargetScope(new AllowedTargetScope('specificDirectoryUsers'));
$specificAllowedTargetsSubjectSet1 = new AttributeRuleMembers();
$specificAllowedTargetsSubjectSet1->setOdataType('#microsoft.graph.attributeRuleMembers');
$specificAllowedTargetsSubjectSet1->setDescription('Membership rule for all users from sales department');
$specificAllowedTargetsSubjectSet1->setMembershipRule('(user.department -eq \"Sales\")');
$specificAllowedTargetsArray []= $specificAllowedTargetsSubjectSet1;
$requestBody->setSpecificAllowedTargets($specificAllowedTargetsArray);

$automaticRequestSettings = new AccessPackageAutomaticRequestSettings();
$automaticRequestSettings->setRequestAccessForAllowedTargets(true);
$automaticRequestSettings->setRemoveAccessWhenTargetLeavesAllowedTargets(true);
$automaticRequestSettings->setGracePeriodBeforeAccessRemoval(new \DateInterval('P7D'));
$requestBody->setAutomaticRequestSettings($automaticRequestSettings);
$accessPackage = new AccessPackage();
$accessPackage->setId('8a36831e-1527-4b2b-aff2-81259a8d8e76');
$requestBody->setAccessPackage($accessPackage);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentPolicies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Sales department users"
	description = "All users from sales department"
	allowedTargetScope = "specificDirectoryUsers"
	specificAllowedTargets = @(
		@{
			"@odata.type" = "#microsoft.graph.attributeRuleMembers"
			description = "Membership rule for all users from sales department"
			membershipRule = "(user.department -eq "Sales")"
		}
	)
	automaticRequestSettings = @{
		requestAccessForAllowedTargets = $true
		removeAccessWhenTargetLeavesAllowedTargets = $true
		gracePeriodBeforeAccessRemoval = "P7D"
	}
	accessPackage = @{
		id = "8a36831e-1527-4b2b-aff2-81259a8d8e76"
	}
}

New-MgEntitlementManagementAssignmentPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph.generated.models.allowed_target_scope import AllowedTargetScope
from msgraph.generated.models.subject_set import SubjectSet
from msgraph.generated.models.attribute_rule_members import AttributeRuleMembers
from msgraph.generated.models.access_package_automatic_request_settings import AccessPackageAutomaticRequestSettings
from msgraph.generated.models.access_package import AccessPackage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	display_name = "Sales department users",
	description = "All users from sales department",
	allowed_target_scope = AllowedTargetScope.SpecificDirectoryUsers,
	specific_allowed_targets = [
		AttributeRuleMembers(
			odata_type = "#microsoft.graph.attributeRuleMembers",
			description = "Membership rule for all users from sales department",
			membership_rule = "(user.department -eq \"Sales\")",
		),
	],
	automatic_request_settings = AccessPackageAutomaticRequestSettings(
		request_access_for_allowed_targets = True,
		remove_access_when_target_leaves_allowed_targets = True,
		grace_period_before_access_removal = "P7D",
	),
	access_package = AccessPackage(
		id = "8a36831e-1527-4b2b-aff2-81259a8d8e76",
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "id": "962493bb-be02-4aeb-a233-a205bbfe1d8d",
    "displayName": "Sales department users",
    "description": "All users from sales department"
}
```

### Example 4: Create a policy where requestors are asked to answer questions while requesting access to provide additional information to approvers

The following example shows a policy that automatically creates assignments for users in the sales department.

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentPolicies
Content-Type: application/json

{
    "displayName": "A Policy With Questions",
    "description": "",
    "allowedTargetScope": "allMemberUsers",
    "expiration": {
        "type": "noExpiration"
    },
    "requestorSettings": {
        "enableTargetsToSelfAddAccess": "true",
        "enableTargetsToSelfUpdateAccess": "true",
        "enableTargetsToSelfRemoveAccess": "true"
    },
    "requestApprovalSettings": {
        "isApprovalRequiredForAdd": "true",
        "isApprovalRequiredForUpdate": "true",
        "stages": [
            {
                "durationBeforeAutomaticDenial": "P7D",
                "isApproverJustificationRequired": "false",
                "isEscalationEnabled": "false",
                "fallbackPrimaryApprovers": [],
                "escalationApprovers": [],
                "fallbackEscalationApprovers": [],
                "primaryApprovers": [
                    {
                        "@odata.type": "#microsoft.graph.singleUser",
                        "userId": "08a551cb-575a-4343-b914-f6e42798bd20"
                    }
                ]
            }
        ]
    },
    "questions": [
        {
            "@odata.type": "#microsoft.graph.accessPackageMultipleChoiceQuestion",
            "sequence": "1",
            "isRequired": "true",
            "isAnswerEditable": "true",
            "text": "What country are you working from?",
            "isMultipleSelectionAllowed": "false",
            "choices": [
                {
                    "@odata.type": "microsoft.graph.accessPackageAnswerChoice",
                    "actualValue": "KE",
                    "text": "Kenya"
                },
                {
                    "@odata.type": "microsoft.graph.accessPackageAnswerChoice",
                    "actualValue": "US",
                    "text": "United States"
                },
                {
                    "@odata.type": "microsoft.graph.accessPackageAnswerChoice",
                    "actualValue": "GY",
                    "text": "Guyana"
                },
                {
                    "@odata.type": "microsoft.graph.accessPackageAnswerChoice",
                    "actualValue": "BD",
                    "text": "Bangladesh"
                },
                {
                    "@odata.type": "microsoft.graph.accessPackageAnswerChoice",
                    "actualValue": "JP",
                    "text": "Japan"
                }
            ]
        },
        {
            "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
            "sequence": "2",
            "isRequired": "true",
            "isAnswerEditable": "true",
            "text": "What do you do for work?",
            "localizations": [
                {
                    "languageCode": "fr-CA",
                    "text": "Que fais-tu comme travail?"
                }
            ],
            "isSingleLineQuestion": "false",
            "regexPattern": "[a-zA-Z]+[a-zA-Z\\s]*"
        }
    ],
    "accessPackage": {
        "id": "977c7ff4-ef8f-4910-9d31-49048ddf3120"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentPolicy
{
	DisplayName = "A Policy With Questions",
	Description = "",
	AllowedTargetScope = AllowedTargetScope.AllMemberUsers,
	Expiration = new ExpirationPattern
	{
		Type = ExpirationPatternType.NoExpiration,
	},
	RequestorSettings = new AccessPackageAssignmentRequestorSettings
	{
		EnableTargetsToSelfAddAccess = true,
		EnableTargetsToSelfUpdateAccess = true,
		EnableTargetsToSelfRemoveAccess = true,
	},
	RequestApprovalSettings = new AccessPackageAssignmentApprovalSettings
	{
		IsApprovalRequiredForAdd = true,
		IsApprovalRequiredForUpdate = true,
		Stages = new List<AccessPackageApprovalStage>
		{
			new AccessPackageApprovalStage
			{
				DurationBeforeAutomaticDenial = TimeSpan.Parse("P7D"),
				IsApproverJustificationRequired = false,
				IsEscalationEnabled = false,
				FallbackPrimaryApprovers = new List<SubjectSet>
				{
				},
				EscalationApprovers = new List<SubjectSet>
				{
				},
				FallbackEscalationApprovers = new List<SubjectSet>
				{
				},
				PrimaryApprovers = new List<SubjectSet>
				{
					new SingleUser
					{
						OdataType = "#microsoft.graph.singleUser",
						UserId = "08a551cb-575a-4343-b914-f6e42798bd20",
					},
				},
			},
		},
	},
	Questions = new List<AccessPackageQuestion>
	{
		new AccessPackageMultipleChoiceQuestion
		{
			OdataType = "#microsoft.graph.accessPackageMultipleChoiceQuestion",
			Sequence = 1,
			IsRequired = true,
			IsAnswerEditable = true,
			Text = "What country are you working from?",
			IsMultipleSelectionAllowed = false,
			Choices = new List<AccessPackageAnswerChoice>
			{
				new AccessPackageAnswerChoice
				{
					OdataType = "microsoft.graph.accessPackageAnswerChoice",
					ActualValue = "KE",
					Text = "Kenya",
				},
				new AccessPackageAnswerChoice
				{
					OdataType = "microsoft.graph.accessPackageAnswerChoice",
					ActualValue = "US",
					Text = "United States",
				},
				new AccessPackageAnswerChoice
				{
					OdataType = "microsoft.graph.accessPackageAnswerChoice",
					ActualValue = "GY",
					Text = "Guyana",
				},
				new AccessPackageAnswerChoice
				{
					OdataType = "microsoft.graph.accessPackageAnswerChoice",
					ActualValue = "BD",
					Text = "Bangladesh",
				},
				new AccessPackageAnswerChoice
				{
					OdataType = "microsoft.graph.accessPackageAnswerChoice",
					ActualValue = "JP",
					Text = "Japan",
				},
			},
		},
		new AccessPackageTextInputQuestion
		{
			OdataType = "#microsoft.graph.accessPackageTextInputQuestion",
			Sequence = 2,
			IsRequired = true,
			IsAnswerEditable = true,
			Text = "What do you do for work?",
			Localizations = new List<AccessPackageLocalizedText>
			{
				new AccessPackageLocalizedText
				{
					LanguageCode = "fr-CA",
					Text = "Que fais-tu comme travail?",
				},
			},
			IsSingleLineQuestion = false,
			RegexPattern = "[a-zA-Z]+[a-zA-Z\s]*",
		},
	},
	AccessPackage = new AccessPackage
	{
		Id = "977c7ff4-ef8f-4910-9d31-49048ddf3120",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
displayName := "A Policy With Questions"
requestBody.SetDisplayName(&displayName) 
description := ""
requestBody.SetDescription(&description) 
allowedTargetScope := graphmodels.ALLMEMBERUSERS_ALLOWEDTARGETSCOPE 
requestBody.SetAllowedTargetScope(&allowedTargetScope) 
expiration := graphmodels.NewExpirationPattern()
type := graphmodels.NOEXPIRATION_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
requestBody.SetExpiration(expiration)
requestorSettings := graphmodels.NewAccessPackageAssignmentRequestorSettings()
enableTargetsToSelfAddAccess := true
requestorSettings.SetEnableTargetsToSelfAddAccess(&enableTargetsToSelfAddAccess) 
enableTargetsToSelfUpdateAccess := true
requestorSettings.SetEnableTargetsToSelfUpdateAccess(&enableTargetsToSelfUpdateAccess) 
enableTargetsToSelfRemoveAccess := true
requestorSettings.SetEnableTargetsToSelfRemoveAccess(&enableTargetsToSelfRemoveAccess) 
requestBody.SetRequestorSettings(requestorSettings)
requestApprovalSettings := graphmodels.NewAccessPackageAssignmentApprovalSettings()
isApprovalRequiredForAdd := true
requestApprovalSettings.SetIsApprovalRequiredForAdd(&isApprovalRequiredForAdd) 
isApprovalRequiredForUpdate := true
requestApprovalSettings.SetIsApprovalRequiredForUpdate(&isApprovalRequiredForUpdate) 


accessPackageApprovalStage := graphmodels.NewAccessPackageApprovalStage()
durationBeforeAutomaticDenial , err := abstractions.ParseISODuration("P7D")
accessPackageApprovalStage.SetDurationBeforeAutomaticDenial(&durationBeforeAutomaticDenial) 
isApproverJustificationRequired := false
accessPackageApprovalStage.SetIsApproverJustificationRequired(&isApproverJustificationRequired) 
isEscalationEnabled := false
accessPackageApprovalStage.SetIsEscalationEnabled(&isEscalationEnabled) 
fallbackPrimaryApprovers := []graphmodels.SubjectSetable {

}
accessPackageApprovalStage.SetFallbackPrimaryApprovers(fallbackPrimaryApprovers)
escalationApprovers := []graphmodels.SubjectSetable {

}
accessPackageApprovalStage.SetEscalationApprovers(escalationApprovers)
fallbackEscalationApprovers := []graphmodels.SubjectSetable {

}
accessPackageApprovalStage.SetFallbackEscalationApprovers(fallbackEscalationApprovers)


subjectSet := graphmodels.NewSingleUser()
userId := "08a551cb-575a-4343-b914-f6e42798bd20"
subjectSet.SetUserId(&userId) 

primaryApprovers := []graphmodels.SubjectSetable {
	subjectSet,
}
accessPackageApprovalStage.SetPrimaryApprovers(primaryApprovers)

stages := []graphmodels.AccessPackageApprovalStageable {
	accessPackageApprovalStage,
}
requestApprovalSettings.SetStages(stages)
requestBody.SetRequestApprovalSettings(requestApprovalSettings)


accessPackageQuestion := graphmodels.NewAccessPackageMultipleChoiceQuestion()
sequence := int32(1)
accessPackageQuestion.SetSequence(&sequence) 
isRequired := true
accessPackageQuestion.SetIsRequired(&isRequired) 
isAnswerEditable := true
accessPackageQuestion.SetIsAnswerEditable(&isAnswerEditable) 
text := "What country are you working from?"
accessPackageQuestion.SetText(&text) 
isMultipleSelectionAllowed := false
accessPackageQuestion.SetIsMultipleSelectionAllowed(&isMultipleSelectionAllowed) 


accessPackageAnswerChoice := graphmodels.NewAccessPackageAnswerChoice()
actualValue := "KE"
accessPackageAnswerChoice.SetActualValue(&actualValue) 
text := "Kenya"
accessPackageAnswerChoice.SetText(&text) 
accessPackageAnswerChoice1 := graphmodels.NewAccessPackageAnswerChoice()
actualValue := "US"
accessPackageAnswerChoice1.SetActualValue(&actualValue) 
text := "United States"
accessPackageAnswerChoice1.SetText(&text) 
accessPackageAnswerChoice2 := graphmodels.NewAccessPackageAnswerChoice()
actualValue := "GY"
accessPackageAnswerChoice2.SetActualValue(&actualValue) 
text := "Guyana"
accessPackageAnswerChoice2.SetText(&text) 
accessPackageAnswerChoice3 := graphmodels.NewAccessPackageAnswerChoice()
actualValue := "BD"
accessPackageAnswerChoice3.SetActualValue(&actualValue) 
text := "Bangladesh"
accessPackageAnswerChoice3.SetText(&text) 
accessPackageAnswerChoice4 := graphmodels.NewAccessPackageAnswerChoice()
actualValue := "JP"
accessPackageAnswerChoice4.SetActualValue(&actualValue) 
text := "Japan"
accessPackageAnswerChoice4.SetText(&text) 

choices := []graphmodels.AccessPackageAnswerChoiceable {
	accessPackageAnswerChoice,
	accessPackageAnswerChoice1,
	accessPackageAnswerChoice2,
	accessPackageAnswerChoice3,
	accessPackageAnswerChoice4,
}
accessPackageQuestion.SetChoices(choices)
accessPackageQuestion1 := graphmodels.NewAccessPackageTextInputQuestion()
sequence := int32(2)
accessPackageQuestion1.SetSequence(&sequence) 
isRequired := true
accessPackageQuestion1.SetIsRequired(&isRequired) 
isAnswerEditable := true
accessPackageQuestion1.SetIsAnswerEditable(&isAnswerEditable) 
text := "What do you do for work?"
accessPackageQuestion1.SetText(&text) 


accessPackageLocalizedText := graphmodels.NewAccessPackageLocalizedText()
languageCode := "fr-CA"
accessPackageLocalizedText.SetLanguageCode(&languageCode) 
text := "Que fais-tu comme travail?"
accessPackageLocalizedText.SetText(&text) 

localizations := []graphmodels.AccessPackageLocalizedTextable {
	accessPackageLocalizedText,
}
accessPackageQuestion1.SetLocalizations(localizations)
isSingleLineQuestion := false
accessPackageQuestion1.SetIsSingleLineQuestion(&isSingleLineQuestion) 
regexPattern := "[a-zA-Z]+[a-zA-Z\s]*"
accessPackageQuestion1.SetRegexPattern(&regexPattern) 

questions := []graphmodels.AccessPackageQuestionable {
	accessPackageQuestion,
	accessPackageQuestion1,
}
requestBody.SetQuestions(questions)
accessPackage := graphmodels.NewAccessPackage()
id := "977c7ff4-ef8f-4910-9d31-49048ddf3120"
accessPackage.SetId(&id) 
requestBody.SetAccessPackage(accessPackage)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentPolicies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setDisplayName("A Policy With Questions");
accessPackageAssignmentPolicy.setDescription("");
accessPackageAssignmentPolicy.setAllowedTargetScope(AllowedTargetScope.AllMemberUsers);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.NoExpiration);
accessPackageAssignmentPolicy.setExpiration(expiration);
AccessPackageAssignmentRequestorSettings requestorSettings = new AccessPackageAssignmentRequestorSettings();
requestorSettings.setEnableTargetsToSelfAddAccess(true);
requestorSettings.setEnableTargetsToSelfUpdateAccess(true);
requestorSettings.setEnableTargetsToSelfRemoveAccess(true);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
AccessPackageAssignmentApprovalSettings requestApprovalSettings = new AccessPackageAssignmentApprovalSettings();
requestApprovalSettings.setIsApprovalRequiredForAdd(true);
requestApprovalSettings.setIsApprovalRequiredForUpdate(true);
LinkedList<AccessPackageApprovalStage> stages = new LinkedList<AccessPackageApprovalStage>();
AccessPackageApprovalStage accessPackageApprovalStage = new AccessPackageApprovalStage();
PeriodAndDuration durationBeforeAutomaticDenial = PeriodAndDuration.ofDuration(Duration.parse("P7D"));
accessPackageApprovalStage.setDurationBeforeAutomaticDenial(durationBeforeAutomaticDenial);
accessPackageApprovalStage.setIsApproverJustificationRequired(false);
accessPackageApprovalStage.setIsEscalationEnabled(false);
LinkedList<SubjectSet> fallbackPrimaryApprovers = new LinkedList<SubjectSet>();
accessPackageApprovalStage.setFallbackPrimaryApprovers(fallbackPrimaryApprovers);
LinkedList<SubjectSet> escalationApprovers = new LinkedList<SubjectSet>();
accessPackageApprovalStage.setEscalationApprovers(escalationApprovers);
LinkedList<SubjectSet> fallbackEscalationApprovers = new LinkedList<SubjectSet>();
accessPackageApprovalStage.setFallbackEscalationApprovers(fallbackEscalationApprovers);
LinkedList<SubjectSet> primaryApprovers = new LinkedList<SubjectSet>();
SingleUser subjectSet = new SingleUser();
subjectSet.setOdataType("#microsoft.graph.singleUser");
subjectSet.setUserId("08a551cb-575a-4343-b914-f6e42798bd20");
primaryApprovers.add(subjectSet);
accessPackageApprovalStage.setPrimaryApprovers(primaryApprovers);
stages.add(accessPackageApprovalStage);
requestApprovalSettings.setStages(stages);
accessPackageAssignmentPolicy.setRequestApprovalSettings(requestApprovalSettings);
LinkedList<AccessPackageQuestion> questions = new LinkedList<AccessPackageQuestion>();
AccessPackageMultipleChoiceQuestion accessPackageQuestion = new AccessPackageMultipleChoiceQuestion();
accessPackageQuestion.setOdataType("#microsoft.graph.accessPackageMultipleChoiceQuestion");
accessPackageQuestion.setSequence(1);
accessPackageQuestion.setIsRequired(true);
accessPackageQuestion.setIsAnswerEditable(true);
accessPackageQuestion.setText("What country are you working from?");
accessPackageQuestion.setIsMultipleSelectionAllowed(false);
LinkedList<AccessPackageAnswerChoice> choices = new LinkedList<AccessPackageAnswerChoice>();
AccessPackageAnswerChoice accessPackageAnswerChoice = new AccessPackageAnswerChoice();
accessPackageAnswerChoice.setOdataType("microsoft.graph.accessPackageAnswerChoice");
accessPackageAnswerChoice.setActualValue("KE");
accessPackageAnswerChoice.setText("Kenya");
choices.add(accessPackageAnswerChoice);
AccessPackageAnswerChoice accessPackageAnswerChoice1 = new AccessPackageAnswerChoice();
accessPackageAnswerChoice1.setOdataType("microsoft.graph.accessPackageAnswerChoice");
accessPackageAnswerChoice1.setActualValue("US");
accessPackageAnswerChoice1.setText("United States");
choices.add(accessPackageAnswerChoice1);
AccessPackageAnswerChoice accessPackageAnswerChoice2 = new AccessPackageAnswerChoice();
accessPackageAnswerChoice2.setOdataType("microsoft.graph.accessPackageAnswerChoice");
accessPackageAnswerChoice2.setActualValue("GY");
accessPackageAnswerChoice2.setText("Guyana");
choices.add(accessPackageAnswerChoice2);
AccessPackageAnswerChoice accessPackageAnswerChoice3 = new AccessPackageAnswerChoice();
accessPackageAnswerChoice3.setOdataType("microsoft.graph.accessPackageAnswerChoice");
accessPackageAnswerChoice3.setActualValue("BD");
accessPackageAnswerChoice3.setText("Bangladesh");
choices.add(accessPackageAnswerChoice3);
AccessPackageAnswerChoice accessPackageAnswerChoice4 = new AccessPackageAnswerChoice();
accessPackageAnswerChoice4.setOdataType("microsoft.graph.accessPackageAnswerChoice");
accessPackageAnswerChoice4.setActualValue("JP");
accessPackageAnswerChoice4.setText("Japan");
choices.add(accessPackageAnswerChoice4);
accessPackageQuestion.setChoices(choices);
questions.add(accessPackageQuestion);
AccessPackageTextInputQuestion accessPackageQuestion1 = new AccessPackageTextInputQuestion();
accessPackageQuestion1.setOdataType("#microsoft.graph.accessPackageTextInputQuestion");
accessPackageQuestion1.setSequence(2);
accessPackageQuestion1.setIsRequired(true);
accessPackageQuestion1.setIsAnswerEditable(true);
accessPackageQuestion1.setText("What do you do for work?");
LinkedList<AccessPackageLocalizedText> localizations = new LinkedList<AccessPackageLocalizedText>();
AccessPackageLocalizedText accessPackageLocalizedText = new AccessPackageLocalizedText();
accessPackageLocalizedText.setLanguageCode("fr-CA");
accessPackageLocalizedText.setText("Que fais-tu comme travail?");
localizations.add(accessPackageLocalizedText);
accessPackageQuestion1.setLocalizations(localizations);
accessPackageQuestion1.setIsSingleLineQuestion(false);
accessPackageQuestion1.setRegexPattern("[a-zA-Z]+[a-zA-Z\s]*");
questions.add(accessPackageQuestion1);
accessPackageAssignmentPolicy.setQuestions(questions);
AccessPackage accessPackage = new AccessPackage();
accessPackage.setId("977c7ff4-ef8f-4910-9d31-49048ddf3120");
accessPackageAssignmentPolicy.setAccessPackage(accessPackage);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().assignmentPolicies().post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
    displayName: 'A Policy With Questions',
    description: '',
    allowedTargetScope: 'allMemberUsers',
    expiration: {
        type: 'noExpiration'
    },
    requestorSettings: {
        enableTargetsToSelfAddAccess: 'true',
        enableTargetsToSelfUpdateAccess: 'true',
        enableTargetsToSelfRemoveAccess: 'true'
    },
    requestApprovalSettings: {
        isApprovalRequiredForAdd: 'true',
        isApprovalRequiredForUpdate: 'true',
        stages: [
            {
                durationBeforeAutomaticDenial: 'P7D',
                isApproverJustificationRequired: 'false',
                isEscalationEnabled: 'false',
                fallbackPrimaryApprovers: [],
                escalationApprovers: [],
                fallbackEscalationApprovers: [],
                primaryApprovers: [
                    {
                        '@odata.type': '#microsoft.graph.singleUser',
                        userId: '08a551cb-575a-4343-b914-f6e42798bd20'
                    }
                ]
            }
        ]
    },
    questions: [
        {
            '@odata.type': '#microsoft.graph.accessPackageMultipleChoiceQuestion',
            sequence: '1',
            isRequired: 'true',
            isAnswerEditable: 'true',
            text: 'What country are you working from?',
            isMultipleSelectionAllowed: 'false',
            choices: [
                {
                    '@odata.type': 'microsoft.graph.accessPackageAnswerChoice',
                    actualValue: 'KE',
                    text: 'Kenya'
                },
                {
                    '@odata.type': 'microsoft.graph.accessPackageAnswerChoice',
                    actualValue: 'US',
                    text: 'United States'
                },
                {
                    '@odata.type': 'microsoft.graph.accessPackageAnswerChoice',
                    actualValue: 'GY',
                    text: 'Guyana'
                },
                {
                    '@odata.type': 'microsoft.graph.accessPackageAnswerChoice',
                    actualValue: 'BD',
                    text: 'Bangladesh'
                },
                {
                    '@odata.type': 'microsoft.graph.accessPackageAnswerChoice',
                    actualValue: 'JP',
                    text: 'Japan'
                }
            ]
        },
        {
            '@odata.type': '#microsoft.graph.accessPackageTextInputQuestion',
            sequence: '2',
            isRequired: 'true',
            isAnswerEditable: 'true',
            text: 'What do you do for work?',
            localizations: [
                {
                    languageCode: 'fr-CA',
                    text: 'Que fais-tu comme travail?'
                }
            ],
            isSingleLineQuestion: 'false',
            regexPattern: '[a-zA-Z]+[a-zA-Z\\s]*'
        }
    ],
    accessPackage: {
        id: '977c7ff4-ef8f-4910-9d31-49048ddf3120'
    }
};

await client.api('/identityGovernance/entitlementManagement/assignmentPolicies')
	.post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Generated\Models\AllowedTargetScope;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequestorSettings;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentApprovalSettings;
use Microsoft\Graph\Generated\Models\AccessPackageApprovalStage;
use Microsoft\Graph\Generated\Models\SubjectSet;
use Microsoft\Graph\Generated\Models\SingleUser;
use Microsoft\Graph\Generated\Models\AccessPackageQuestion;
use Microsoft\Graph\Generated\Models\AccessPackageMultipleChoiceQuestion;
use Microsoft\Graph\Generated\Models\AccessPackageAnswerChoice;
use Microsoft\Graph\Generated\Models\AccessPackageTextInputQuestion;
use Microsoft\Graph\Generated\Models\AccessPackageLocalizedText;
use Microsoft\Graph\Generated\Models\AccessPackage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setDisplayName('A Policy With Questions');
$requestBody->setDescription('');
$requestBody->setAllowedTargetScope(new AllowedTargetScope('allMemberUsers'));
$expiration = new ExpirationPattern();
$expiration->setType(new ExpirationPatternType('noExpiration'));
$requestBody->setExpiration($expiration);
$requestorSettings = new AccessPackageAssignmentRequestorSettings();
$requestorSettings->setEnableTargetsToSelfAddAccess(true);
$requestorSettings->setEnableTargetsToSelfUpdateAccess(true);
$requestorSettings->setEnableTargetsToSelfRemoveAccess(true);
$requestBody->setRequestorSettings($requestorSettings);
$requestApprovalSettings = new AccessPackageAssignmentApprovalSettings();
$requestApprovalSettings->setIsApprovalRequiredForAdd(true);
$requestApprovalSettings->setIsApprovalRequiredForUpdate(true);
$stagesAccessPackageApprovalStage1 = new AccessPackageApprovalStage();
$stagesAccessPackageApprovalStage1->setDurationBeforeAutomaticDenial(new \DateInterval('P7D'));
$stagesAccessPackageApprovalStage1->setIsApproverJustificationRequired(false);
$stagesAccessPackageApprovalStage1->setIsEscalationEnabled(false);
$stagesAccessPackageApprovalStage1->setFallbackPrimaryApprovers([	]);
$stagesAccessPackageApprovalStage1->setEscalationApprovers([	]);
$stagesAccessPackageApprovalStage1->setFallbackEscalationApprovers([	]);
$primaryApproversSubjectSet1 = new SingleUser();
$primaryApproversSubjectSet1->setOdataType('#microsoft.graph.singleUser');
$primaryApproversSubjectSet1->setUserId('08a551cb-575a-4343-b914-f6e42798bd20');
$primaryApproversArray []= $primaryApproversSubjectSet1;
$stagesAccessPackageApprovalStage1->setPrimaryApprovers($primaryApproversArray);

$stagesArray []= $stagesAccessPackageApprovalStage1;
$requestApprovalSettings->setStages($stagesArray);

$requestBody->setRequestApprovalSettings($requestApprovalSettings);
$questionsAccessPackageQuestion1 = new AccessPackageMultipleChoiceQuestion();
$questionsAccessPackageQuestion1->setOdataType('#microsoft.graph.accessPackageMultipleChoiceQuestion');
$questionsAccessPackageQuestion1->setSequence(1);
$questionsAccessPackageQuestion1->setIsRequired(true);
$questionsAccessPackageQuestion1->setIsAnswerEditable(true);
$questionsAccessPackageQuestion1->setText('What country are you working from?');
$questionsAccessPackageQuestion1->setIsMultipleSelectionAllowed(false);
$choicesAccessPackageAnswerChoice1 = new AccessPackageAnswerChoice();
$choicesAccessPackageAnswerChoice1->setOdataType('microsoft.graph.accessPackageAnswerChoice');
$choicesAccessPackageAnswerChoice1->setActualValue('KE');
$choicesAccessPackageAnswerChoice1->setText('Kenya');
$choicesArray []= $choicesAccessPackageAnswerChoice1;
$choicesAccessPackageAnswerChoice2 = new AccessPackageAnswerChoice();
$choicesAccessPackageAnswerChoice2->setOdataType('microsoft.graph.accessPackageAnswerChoice');
$choicesAccessPackageAnswerChoice2->setActualValue('US');
$choicesAccessPackageAnswerChoice2->setText('United States');
$choicesArray []= $choicesAccessPackageAnswerChoice2;
$choicesAccessPackageAnswerChoice3 = new AccessPackageAnswerChoice();
$choicesAccessPackageAnswerChoice3->setOdataType('microsoft.graph.accessPackageAnswerChoice');
$choicesAccessPackageAnswerChoice3->setActualValue('GY');
$choicesAccessPackageAnswerChoice3->setText('Guyana');
$choicesArray []= $choicesAccessPackageAnswerChoice3;
$choicesAccessPackageAnswerChoice4 = new AccessPackageAnswerChoice();
$choicesAccessPackageAnswerChoice4->setOdataType('microsoft.graph.accessPackageAnswerChoice');
$choicesAccessPackageAnswerChoice4->setActualValue('BD');
$choicesAccessPackageAnswerChoice4->setText('Bangladesh');
$choicesArray []= $choicesAccessPackageAnswerChoice4;
$choicesAccessPackageAnswerChoice5 = new AccessPackageAnswerChoice();
$choicesAccessPackageAnswerChoice5->setOdataType('microsoft.graph.accessPackageAnswerChoice');
$choicesAccessPackageAnswerChoice5->setActualValue('JP');
$choicesAccessPackageAnswerChoice5->setText('Japan');
$choicesArray []= $choicesAccessPackageAnswerChoice5;
$questionsAccessPackageQuestion1->setChoices($choicesArray);

$questionsArray []= $questionsAccessPackageQuestion1;
$questionsAccessPackageQuestion2 = new AccessPackageTextInputQuestion();
$questionsAccessPackageQuestion2->setOdataType('#microsoft.graph.accessPackageTextInputQuestion');
$questionsAccessPackageQuestion2->setSequence(2);
$questionsAccessPackageQuestion2->setIsRequired(true);
$questionsAccessPackageQuestion2->setIsAnswerEditable(true);
$questionsAccessPackageQuestion2->setText('What do you do for work?');
$localizationsAccessPackageLocalizedText1 = new AccessPackageLocalizedText();
$localizationsAccessPackageLocalizedText1->setLanguageCode('fr-CA');
$localizationsAccessPackageLocalizedText1->setText('Que fais-tu comme travail?');
$localizationsArray []= $localizationsAccessPackageLocalizedText1;
$questionsAccessPackageQuestion2->setLocalizations($localizationsArray);

$questionsAccessPackageQuestion2->setIsSingleLineQuestion(false);
$questionsAccessPackageQuestion2->setRegexPattern('[a-zA-Z]+[a-zA-Z\s]*');
$questionsArray []= $questionsAccessPackageQuestion2;
$requestBody->setQuestions($questionsArray);

$accessPackage = new AccessPackage();
$accessPackage->setId('977c7ff4-ef8f-4910-9d31-49048ddf3120');
$requestBody->setAccessPackage($accessPackage);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentPolicies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "A Policy With Questions"
	description = ""
	allowedTargetScope = "allMemberUsers"
	expiration = @{
		type = "noExpiration"
	}
	requestorSettings = @{
		enableTargetsToSelfAddAccess = "true"
		enableTargetsToSelfUpdateAccess = "true"
		enableTargetsToSelfRemoveAccess = "true"
	}
	requestApprovalSettings = @{
		isApprovalRequiredForAdd = "true"
		isApprovalRequiredForUpdate = "true"
		stages = @(
			@{
				durationBeforeAutomaticDenial = "P7D"
				isApproverJustificationRequired = "false"
				isEscalationEnabled = "false"
				fallbackPrimaryApprovers = @(
				)
				escalationApprovers = @(
				)
				fallbackEscalationApprovers = @(
				)
				primaryApprovers = @(
					@{
						"@odata.type" = "#microsoft.graph.singleUser"
						userId = "08a551cb-575a-4343-b914-f6e42798bd20"
					}
				)
			}
		)
	}
	questions = @(
		@{
			"@odata.type" = "#microsoft.graph.accessPackageMultipleChoiceQuestion"
			sequence = "1"
			isRequired = "true"
			isAnswerEditable = "true"
			text = "What country are you working from?"
			isMultipleSelectionAllowed = "false"
			choices = @(
				@{
					"@odata.type" = "microsoft.graph.accessPackageAnswerChoice"
					actualValue = "KE"
					text = "Kenya"
				}
				@{
					"@odata.type" = "microsoft.graph.accessPackageAnswerChoice"
					actualValue = "US"
					text = "United States"
				}
				@{
					"@odata.type" = "microsoft.graph.accessPackageAnswerChoice"
					actualValue = "GY"
					text = "Guyana"
				}
				@{
					"@odata.type" = "microsoft.graph.accessPackageAnswerChoice"
					actualValue = "BD"
					text = "Bangladesh"
				}
				@{
					"@odata.type" = "microsoft.graph.accessPackageAnswerChoice"
					actualValue = "JP"
					text = "Japan"
				}
			)
		}
		@{
			"@odata.type" = "#microsoft.graph.accessPackageTextInputQuestion"
			sequence = "2"
			isRequired = "true"
			isAnswerEditable = "true"
			text = "What do you do for work?"
			localizations = @(
				@{
					languageCode = "fr-CA"
					text = "Que fais-tu comme travail?"
				}
			)
			isSingleLineQuestion = "false"
			regexPattern = "[a-zA-Z]+[a-zA-Z\s]*"
		}
	)
	accessPackage = @{
		id = "977c7ff4-ef8f-4910-9d31-49048ddf3120"
	}
}

New-MgEntitlementManagementAssignmentPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph.generated.models.allowed_target_scope import AllowedTargetScope
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
from msgraph.generated.models.access_package_assignment_requestor_settings import AccessPackageAssignmentRequestorSettings
from msgraph.generated.models.access_package_assignment_approval_settings import AccessPackageAssignmentApprovalSettings
from msgraph.generated.models.access_package_approval_stage import AccessPackageApprovalStage
from msgraph.generated.models.subject_set import SubjectSet
from msgraph.generated.models.single_user import SingleUser
from msgraph.generated.models.access_package_question import AccessPackageQuestion
from msgraph.generated.models.access_package_multiple_choice_question import AccessPackageMultipleChoiceQuestion
from msgraph.generated.models.access_package_answer_choice import AccessPackageAnswerChoice
from msgraph.generated.models.access_package_text_input_question import AccessPackageTextInputQuestion
from msgraph.generated.models.access_package_localized_text import AccessPackageLocalizedText
from msgraph.generated.models.access_package import AccessPackage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	display_name = "A Policy With Questions",
	description = "",
	allowed_target_scope = AllowedTargetScope.AllMemberUsers,
	expiration = ExpirationPattern(
		type = ExpirationPatternType.NoExpiration,
	),
	requestor_settings = AccessPackageAssignmentRequestorSettings(
		enable_targets_to_self_add_access = True,
		enable_targets_to_self_update_access = True,
		enable_targets_to_self_remove_access = True,
	),
	request_approval_settings = AccessPackageAssignmentApprovalSettings(
		is_approval_required_for_add = True,
		is_approval_required_for_update = True,
		stages = [
			AccessPackageApprovalStage(
				duration_before_automatic_denial = "P7D",
				is_approver_justification_required = False,
				is_escalation_enabled = False,
				fallback_primary_approvers = [
				],
				escalation_approvers = [
				],
				fallback_escalation_approvers = [
				],
				primary_approvers = [
					SingleUser(
						odata_type = "#microsoft.graph.singleUser",
						user_id = "08a551cb-575a-4343-b914-f6e42798bd20",
					),
				],
			),
		],
	),
	questions = [
		AccessPackageMultipleChoiceQuestion(
			odata_type = "#microsoft.graph.accessPackageMultipleChoiceQuestion",
			sequence = 1,
			is_required = True,
			is_answer_editable = True,
			text = "What country are you working from?",
			is_multiple_selection_allowed = False,
			choices = [
				AccessPackageAnswerChoice(
					odata_type = "microsoft.graph.accessPackageAnswerChoice",
					actual_value = "KE",
					text = "Kenya",
				),
				AccessPackageAnswerChoice(
					odata_type = "microsoft.graph.accessPackageAnswerChoice",
					actual_value = "US",
					text = "United States",
				),
				AccessPackageAnswerChoice(
					odata_type = "microsoft.graph.accessPackageAnswerChoice",
					actual_value = "GY",
					text = "Guyana",
				),
				AccessPackageAnswerChoice(
					odata_type = "microsoft.graph.accessPackageAnswerChoice",
					actual_value = "BD",
					text = "Bangladesh",
				),
				AccessPackageAnswerChoice(
					odata_type = "microsoft.graph.accessPackageAnswerChoice",
					actual_value = "JP",
					text = "Japan",
				),
			],
		),
		AccessPackageTextInputQuestion(
			odata_type = "#microsoft.graph.accessPackageTextInputQuestion",
			sequence = 2,
			is_required = True,
			is_answer_editable = True,
			text = "What do you do for work?",
			localizations = [
				AccessPackageLocalizedText(
					language_code = "fr-CA",
					text = "Que fais-tu comme travail?",
				),
			],
			is_single_line_question = False,
			regex_pattern = "[a-zA-Z]+[a-zA-Z\s]*",
		),
	],
	access_package = AccessPackage(
		id = "977c7ff4-ef8f-4910-9d31-49048ddf3120",
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "id": "24e5711e-92f0-41e2-912d-9f4e005f36cc",
    "displayName": "A Policy With Questions",
    "allowedTargetScope": "allMemberUsers",
    "createdDateTime": "2022-09-30T20:32:07.1949218Z",
    "modifiedDateTime": "2022-09-30T20:32:07.4173893Z",
}
```

### Example 5: Create a policy and specify the stages to trigger predefined access package custom extensions

In the following example, the predefined **accessPackageCustomWorkflowExtension** object is triggered by the creation or approval of an access package assignment request. The identifier in the **customExtension** property corresponds to the ID of the **accessPackageCustomWorkflowExtension** object.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentPolicies/
Content-type: application/json

{
    "displayName": "customExtensionStageSettings policy",
    "description": "policy with specified stages for custom extension assignment",
    "allowedTargetScope": "notSpecified",
    "specificAllowedTargets": [],
    "expiration": {
        "endDateTime": null,
        "duration": null,
        "type": "noExpiration"
    },
    "requestorSettings": {
        "enableTargetsToSelfAddAccess": false,
        "enableTargetsToSelfUpdateAccess": false,
        "enableTargetsToSelfRemoveAccess": false,
        "allowCustomAssignmentSchedule": true,
        "enableOnBehalfRequestorsToAddAccess": false,
        "enableOnBehalfRequestorsToUpdateAccess": false,
        "enableOnBehalfRequestorsToRemoveAccess": false,
        "onBehalfRequestors": []
    },
    "requestApprovalSettings": {
        "isApprovalRequiredForAdd": false,
        "isApprovalRequiredForUpdate": false,
        "stages": []
    },
    "accessPackage": {
        "id": "5ad1eb64-15f7-4614-b419-05d11ee266bf"
    },
    "customExtensionStageSettings": [
        {
            "stage": "assignmentRequestCreated",
            "customExtension": {
                "@odata.type": "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
                "id": "bebe7873-1f0d-4db9-b6c3-01f7ebfe8476"
            }
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentPolicy
{
	DisplayName = "customExtensionStageSettings policy",
	Description = "policy with specified stages for custom extension assignment",
	AllowedTargetScope = AllowedTargetScope.NotSpecified,
	SpecificAllowedTargets = new List<SubjectSet>
	{
	},
	Expiration = new ExpirationPattern
	{
		EndDateTime = null,
		Duration = null,
		Type = ExpirationPatternType.NoExpiration,
	},
	RequestorSettings = new AccessPackageAssignmentRequestorSettings
	{
		EnableTargetsToSelfAddAccess = false,
		EnableTargetsToSelfUpdateAccess = false,
		EnableTargetsToSelfRemoveAccess = false,
		AllowCustomAssignmentSchedule = true,
		EnableOnBehalfRequestorsToAddAccess = false,
		EnableOnBehalfRequestorsToUpdateAccess = false,
		EnableOnBehalfRequestorsToRemoveAccess = false,
		OnBehalfRequestors = new List<SubjectSet>
		{
		},
	},
	RequestApprovalSettings = new AccessPackageAssignmentApprovalSettings
	{
		IsApprovalRequiredForAdd = false,
		IsApprovalRequiredForUpdate = false,
		Stages = new List<AccessPackageApprovalStage>
		{
		},
	},
	AccessPackage = new AccessPackage
	{
		Id = "5ad1eb64-15f7-4614-b419-05d11ee266bf",
	},
	CustomExtensionStageSettings = new List<CustomExtensionStageSetting>
	{
		new CustomExtensionStageSetting
		{
			Stage = AccessPackageCustomExtensionStage.AssignmentRequestCreated,
			CustomExtension = new AccessPackageAssignmentRequestWorkflowExtension
			{
				OdataType = "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
				Id = "bebe7873-1f0d-4db9-b6c3-01f7ebfe8476",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
displayName := "customExtensionStageSettings policy"
requestBody.SetDisplayName(&displayName) 
description := "policy with specified stages for custom extension assignment"
requestBody.SetDescription(&description) 
allowedTargetScope := graphmodels.NOTSPECIFIED_ALLOWEDTARGETSCOPE 
requestBody.SetAllowedTargetScope(&allowedTargetScope) 
specificAllowedTargets := []graphmodels.SubjectSetable {

}
requestBody.SetSpecificAllowedTargets(specificAllowedTargets)
expiration := graphmodels.NewExpirationPattern()
endDateTime := null
expiration.SetEndDateTime(&endDateTime) 
duration := null
expiration.SetDuration(&duration) 
type := graphmodels.NOEXPIRATION_EXPIRATIONPATTERNTYPE 
expiration.SetType(&type) 
requestBody.SetExpiration(expiration)
requestorSettings := graphmodels.NewAccessPackageAssignmentRequestorSettings()
enableTargetsToSelfAddAccess := false
requestorSettings.SetEnableTargetsToSelfAddAccess(&enableTargetsToSelfAddAccess) 
enableTargetsToSelfUpdateAccess := false
requestorSettings.SetEnableTargetsToSelfUpdateAccess(&enableTargetsToSelfUpdateAccess) 
enableTargetsToSelfRemoveAccess := false
requestorSettings.SetEnableTargetsToSelfRemoveAccess(&enableTargetsToSelfRemoveAccess) 
allowCustomAssignmentSchedule := true
requestorSettings.SetAllowCustomAssignmentSchedule(&allowCustomAssignmentSchedule) 
enableOnBehalfRequestorsToAddAccess := false
requestorSettings.SetEnableOnBehalfRequestorsToAddAccess(&enableOnBehalfRequestorsToAddAccess) 
enableOnBehalfRequestorsToUpdateAccess := false
requestorSettings.SetEnableOnBehalfRequestorsToUpdateAccess(&enableOnBehalfRequestorsToUpdateAccess) 
enableOnBehalfRequestorsToRemoveAccess := false
requestorSettings.SetEnableOnBehalfRequestorsToRemoveAccess(&enableOnBehalfRequestorsToRemoveAccess) 
onBehalfRequestors := []graphmodels.SubjectSetable {

}
requestorSettings.SetOnBehalfRequestors(onBehalfRequestors)
requestBody.SetRequestorSettings(requestorSettings)
requestApprovalSettings := graphmodels.NewAccessPackageAssignmentApprovalSettings()
isApprovalRequiredForAdd := false
requestApprovalSettings.SetIsApprovalRequiredForAdd(&isApprovalRequiredForAdd) 
isApprovalRequiredForUpdate := false
requestApprovalSettings.SetIsApprovalRequiredForUpdate(&isApprovalRequiredForUpdate) 
stages := []graphmodels.AccessPackageApprovalStageable {

}
requestApprovalSettings.SetStages(stages)
requestBody.SetRequestApprovalSettings(requestApprovalSettings)
accessPackage := graphmodels.NewAccessPackage()
id := "5ad1eb64-15f7-4614-b419-05d11ee266bf"
accessPackage.SetId(&id) 
requestBody.SetAccessPackage(accessPackage)


customExtensionStageSetting := graphmodels.NewCustomExtensionStageSetting()
stage := graphmodels.ASSIGNMENTREQUESTCREATED_ACCESSPACKAGECUSTOMEXTENSIONSTAGE 
customExtensionStageSetting.SetStage(&stage) 
customExtension := graphmodels.NewAccessPackageAssignmentRequestWorkflowExtension()
id := "bebe7873-1f0d-4db9-b6c3-01f7ebfe8476"
customExtension.SetId(&id) 
customExtensionStageSetting.SetCustomExtension(customExtension)

customExtensionStageSettings := []graphmodels.CustomExtensionStageSettingable {
	customExtensionStageSetting,
}
requestBody.SetCustomExtensionStageSettings(customExtensionStageSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentPolicies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setDisplayName("customExtensionStageSettings policy");
accessPackageAssignmentPolicy.setDescription("policy with specified stages for custom extension assignment");
accessPackageAssignmentPolicy.setAllowedTargetScope(AllowedTargetScope.NotSpecified);
LinkedList<SubjectSet> specificAllowedTargets = new LinkedList<SubjectSet>();
accessPackageAssignmentPolicy.setSpecificAllowedTargets(specificAllowedTargets);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setEndDateTime(null);
expiration.setDuration(null);
expiration.setType(ExpirationPatternType.NoExpiration);
accessPackageAssignmentPolicy.setExpiration(expiration);
AccessPackageAssignmentRequestorSettings requestorSettings = new AccessPackageAssignmentRequestorSettings();
requestorSettings.setEnableTargetsToSelfAddAccess(false);
requestorSettings.setEnableTargetsToSelfUpdateAccess(false);
requestorSettings.setEnableTargetsToSelfRemoveAccess(false);
requestorSettings.setAllowCustomAssignmentSchedule(true);
requestorSettings.setEnableOnBehalfRequestorsToAddAccess(false);
requestorSettings.setEnableOnBehalfRequestorsToUpdateAccess(false);
requestorSettings.setEnableOnBehalfRequestorsToRemoveAccess(false);
LinkedList<SubjectSet> onBehalfRequestors = new LinkedList<SubjectSet>();
requestorSettings.setOnBehalfRequestors(onBehalfRequestors);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
AccessPackageAssignmentApprovalSettings requestApprovalSettings = new AccessPackageAssignmentApprovalSettings();
requestApprovalSettings.setIsApprovalRequiredForAdd(false);
requestApprovalSettings.setIsApprovalRequiredForUpdate(false);
LinkedList<AccessPackageApprovalStage> stages = new LinkedList<AccessPackageApprovalStage>();
requestApprovalSettings.setStages(stages);
accessPackageAssignmentPolicy.setRequestApprovalSettings(requestApprovalSettings);
AccessPackage accessPackage = new AccessPackage();
accessPackage.setId("5ad1eb64-15f7-4614-b419-05d11ee266bf");
accessPackageAssignmentPolicy.setAccessPackage(accessPackage);
LinkedList<CustomExtensionStageSetting> customExtensionStageSettings = new LinkedList<CustomExtensionStageSetting>();
CustomExtensionStageSetting customExtensionStageSetting = new CustomExtensionStageSetting();
customExtensionStageSetting.setStage(AccessPackageCustomExtensionStage.AssignmentRequestCreated);
AccessPackageAssignmentRequestWorkflowExtension customExtension = new AccessPackageAssignmentRequestWorkflowExtension();
customExtension.setOdataType("#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension");
customExtension.setId("bebe7873-1f0d-4db9-b6c3-01f7ebfe8476");
customExtensionStageSetting.setCustomExtension(customExtension);
customExtensionStageSettings.add(customExtensionStageSetting);
accessPackageAssignmentPolicy.setCustomExtensionStageSettings(customExtensionStageSettings);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().assignmentPolicies().post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
    displayName: 'customExtensionStageSettings policy',
    description: 'policy with specified stages for custom extension assignment',
    allowedTargetScope: 'notSpecified',
    specificAllowedTargets: [],
    expiration: {
        endDateTime: null,
        duration: null,
        type: 'noExpiration'
    },
    requestorSettings: {
        enableTargetsToSelfAddAccess: false,
        enableTargetsToSelfUpdateAccess: false,
        enableTargetsToSelfRemoveAccess: false,
        allowCustomAssignmentSchedule: true,
        enableOnBehalfRequestorsToAddAccess: false,
        enableOnBehalfRequestorsToUpdateAccess: false,
        enableOnBehalfRequestorsToRemoveAccess: false,
        onBehalfRequestors: []
    },
    requestApprovalSettings: {
        isApprovalRequiredForAdd: false,
        isApprovalRequiredForUpdate: false,
        stages: []
    },
    accessPackage: {
        id: '5ad1eb64-15f7-4614-b419-05d11ee266bf'
    },
    customExtensionStageSettings: [
        {
            stage: 'assignmentRequestCreated',
            customExtension: {
                '@odata.type': '#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension',
                id: 'bebe7873-1f0d-4db9-b6c3-01f7ebfe8476'
            }
        }
    ]
};

await client.api('/identityGovernance/entitlementManagement/assignmentPolicies/')
	.post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Generated\Models\AllowedTargetScope;
use Microsoft\Graph\Generated\Models\SubjectSet;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequestorSettings;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentApprovalSettings;
use Microsoft\Graph\Generated\Models\AccessPackageApprovalStage;
use Microsoft\Graph\Generated\Models\AccessPackage;
use Microsoft\Graph\Generated\Models\CustomExtensionStageSetting;
use Microsoft\Graph\Generated\Models\AccessPackageCustomExtensionStage;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequestWorkflowExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setDisplayName('customExtensionStageSettings policy');
$requestBody->setDescription('policy with specified stages for custom extension assignment');
$requestBody->setAllowedTargetScope(new AllowedTargetScope('notSpecified'));
$requestBody->setSpecificAllowedTargets([	]);
$expiration = new ExpirationPattern();
$expiration->setEndDateTime(null);
$expiration->setDuration(null);
$expiration->setType(new ExpirationPatternType('noExpiration'));
$requestBody->setExpiration($expiration);
$requestorSettings = new AccessPackageAssignmentRequestorSettings();
$requestorSettings->setEnableTargetsToSelfAddAccess(false);
$requestorSettings->setEnableTargetsToSelfUpdateAccess(false);
$requestorSettings->setEnableTargetsToSelfRemoveAccess(false);
$requestorSettings->setAllowCustomAssignmentSchedule(true);
$requestorSettings->setEnableOnBehalfRequestorsToAddAccess(false);
$requestorSettings->setEnableOnBehalfRequestorsToUpdateAccess(false);
$requestorSettings->setEnableOnBehalfRequestorsToRemoveAccess(false);
$requestorSettings->setOnBehalfRequestors([	]);
$requestBody->setRequestorSettings($requestorSettings);
$requestApprovalSettings = new AccessPackageAssignmentApprovalSettings();
$requestApprovalSettings->setIsApprovalRequiredForAdd(false);
$requestApprovalSettings->setIsApprovalRequiredForUpdate(false);
$requestApprovalSettings->setStages([	]);
$requestBody->setRequestApprovalSettings($requestApprovalSettings);
$accessPackage = new AccessPackage();
$accessPackage->setId('5ad1eb64-15f7-4614-b419-05d11ee266bf');
$requestBody->setAccessPackage($accessPackage);
$customExtensionStageSettingsCustomExtensionStageSetting1 = new CustomExtensionStageSetting();
$customExtensionStageSettingsCustomExtensionStageSetting1->setStage(new AccessPackageCustomExtensionStage('assignmentRequestCreated'));
$customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension = new AccessPackageAssignmentRequestWorkflowExtension();
$customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension->setOdataType('#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension');
$customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension->setId('bebe7873-1f0d-4db9-b6c3-01f7ebfe8476');
$customExtensionStageSettingsCustomExtensionStageSetting1->setCustomExtension($customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension);
$customExtensionStageSettingsArray []= $customExtensionStageSettingsCustomExtensionStageSetting1;
$requestBody->setCustomExtensionStageSettings($customExtensionStageSettingsArray);


$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentPolicies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "customExtensionStageSettings policy"
	description = "policy with specified stages for custom extension assignment"
	allowedTargetScope = "notSpecified"
	specificAllowedTargets = @(
	)
	expiration = @{
		endDateTime = $null
		duration = $null
		type = "noExpiration"
	}
	requestorSettings = @{
		enableTargetsToSelfAddAccess = $false
		enableTargetsToSelfUpdateAccess = $false
		enableTargetsToSelfRemoveAccess = $false
		allowCustomAssignmentSchedule = $true
		enableOnBehalfRequestorsToAddAccess = $false
		enableOnBehalfRequestorsToUpdateAccess = $false
		enableOnBehalfRequestorsToRemoveAccess = $false
		onBehalfRequestors = @(
		)
	}
	requestApprovalSettings = @{
		isApprovalRequiredForAdd = $false
		isApprovalRequiredForUpdate = $false
		stages = @(
		)
	}
	accessPackage = @{
		id = "5ad1eb64-15f7-4614-b419-05d11ee266bf"
	}
	customExtensionStageSettings = @(
		@{
			stage = "assignmentRequestCreated"
			customExtension = @{
				"@odata.type" = "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension"
				id = "bebe7873-1f0d-4db9-b6c3-01f7ebfe8476"
			}
		}
	)
}

New-MgEntitlementManagementAssignmentPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph.generated.models.allowed_target_scope import AllowedTargetScope
from msgraph.generated.models.subject_set import SubjectSet
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
from msgraph.generated.models.access_package_assignment_requestor_settings import AccessPackageAssignmentRequestorSettings
from msgraph.generated.models.access_package_assignment_approval_settings import AccessPackageAssignmentApprovalSettings
from msgraph.generated.models.access_package_approval_stage import AccessPackageApprovalStage
from msgraph.generated.models.access_package import AccessPackage
from msgraph.generated.models.custom_extension_stage_setting import CustomExtensionStageSetting
from msgraph.generated.models.access_package_custom_extension_stage import AccessPackageCustomExtensionStage
from msgraph.generated.models.access_package_assignment_request_workflow_extension import AccessPackageAssignmentRequestWorkflowExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	display_name = "customExtensionStageSettings policy",
	description = "policy with specified stages for custom extension assignment",
	allowed_target_scope = AllowedTargetScope.NotSpecified,
	specific_allowed_targets = [
	],
	expiration = ExpirationPattern(
		end_date_time = None,
		duration = None,
		type = ExpirationPatternType.NoExpiration,
	),
	requestor_settings = AccessPackageAssignmentRequestorSettings(
		enable_targets_to_self_add_access = False,
		enable_targets_to_self_update_access = False,
		enable_targets_to_self_remove_access = False,
		allow_custom_assignment_schedule = True,
		enable_on_behalf_requestors_to_add_access = False,
		enable_on_behalf_requestors_to_update_access = False,
		enable_on_behalf_requestors_to_remove_access = False,
		on_behalf_requestors = [
		],
	),
	request_approval_settings = AccessPackageAssignmentApprovalSettings(
		is_approval_required_for_add = False,
		is_approval_required_for_update = False,
		stages = [
		],
	),
	access_package = AccessPackage(
		id = "5ad1eb64-15f7-4614-b419-05d11ee266bf",
	),
	custom_extension_stage_settings = [
		CustomExtensionStageSetting(
			stage = AccessPackageCustomExtensionStage.AssignmentRequestCreated,
			custom_extension = AccessPackageAssignmentRequestWorkflowExtension(
				odata_type = "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
				id = "bebe7873-1f0d-4db9-b6c3-01f7ebfe8476",
			),
		),
	],
)

result = await graph_client.identity_governance.entitlement_management.assignment_policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The **customExtensionStageSettings** object isn't returned by default. To retrieve this object, use the [GET accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-1.0) method with `$expand`. For more information, see [Example 2: Retrieve the custom extension stage settings for a policy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-1.0#example-2-retrieve-the-custom-extension-stage-settings-for-a-policy).

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "d0324cbb-24a2-4edb-acca-fee5384c6a5e",
  "displayName": "customExtensionStageSettings policy",
  "description": "policy with specified stages for custom extension assignment",
  "canExtend": false,
  "durationInDays": 0,
  "expirationDateTime": null,
  "accessPackageId": "5ad1eb64-15f7-4614-b419-05d11ee266bf",
  "accessReviewSettings": null,
  "questions": [],
  "requestorSettings": {
    "scopeType": "AllExistingDirectorySubjects",
    "acceptRequests": true,
    "allowedRequestors": []
  },
  "requestApprovalSettings": {
    "isApprovalRequired": false,
    "isApprovalRequiredForExtension": false,
    "isRequestorJustificationRequired": false,
    "approvalMode": "NoApproval",
    "approvalStages": []
  },
  "customExtensionStageSettings": [
        {
            "stage": "assignmentRequestCreated",
            "customExtension": {
                "@odata.type": "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
                "id": "bebe7873-1f0d-4db9-b6c3-01f7ebfe8476"
            }
        }
    ]
}
```

### Example 6: Create a policy used to determine approvers dynamically from a Logic App

In the following example, the policy is created for an access package assignment that is determining the approver dynamically via a logic app called from a custom extension.

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

```msgraph
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentPolicies/
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/$entity",
    "displayName": "Dynamic approver policy",
    "description": "Dynamic approver policy",
    "canExtend": false,
    "durationInDays": 0,
    "expirationDateTime": null,
    "accessPackageId": "fc29cdca-57f6-47e3-b20c-3fa18e4826ac",
    "accessReviewSettings": null,
    "questions": [],
    "accessPackageNotificationSettings": {
        "isAssignmentNotificationDisabled": false
    },
    "verifiableCredentialSettings": {
        "credentialTypes": []
    },
    "requestorSettings": {
        "scopeType": "AllExistingDirectorySubjects",
        "acceptRequests": true,
        "allowedRequestors": []
    },
    "requestApprovalSettings": {
        "isApprovalRequired": true,
        "isApprovalRequiredForExtension": false,
        "isRequestorJustificationRequired": true,
        "approvalMode": "SingleStage",
        "approvalStages": [
            {
                "@odata.type": "#microsoft.graph.accessPackageDynamicApprovalStage",
                "customExtension": {
                    "@odata.type": "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
                    "id": "52036a43-10b5-444d-a1a2-d4f240420239"
                }
            }
        ]
    },
    "customExtensionStageSettings": [
        {
            "stage": "assignmentRequestDeterminingApprovalRequirements",
            "customExtension": {
            "@odata.type": "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
            "id": "52036a43-10b5-444d-a1a2-d4f240420239"
            }
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new AccessPackageAssignmentPolicy
{
	DisplayName = "Dynamic approver policy",
	Description = "Dynamic approver policy",
	Questions = new List<AccessPackageQuestion>
	{
	},
	RequestorSettings = new AccessPackageAssignmentRequestorSettings
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"scopeType" , "AllExistingDirectorySubjects"
			},
			{
				"acceptRequests" , true
			},
			{
				"allowedRequestors" , new List<object>
				{
				}
			},
		},
	},
	RequestApprovalSettings = new AccessPackageAssignmentApprovalSettings
	{
		IsRequestorJustificationRequired = true,
		AdditionalData = new Dictionary<string, object>
		{
			{
				"isApprovalRequired" , true
			},
			{
				"isApprovalRequiredForExtension" , false
			},
			{
				"approvalMode" , "SingleStage"
			},
			{
				"approvalStages" , new List<object>
				{
					new UntypedObject(new Dictionary<string, UntypedNode>
					{
						{
							"@odata.type", new UntypedString("#microsoft.graph.accessPackageDynamicApprovalStage")
						},
						{
							"customExtension", new UntypedObject(new Dictionary<string, UntypedNode>
							{
								{
									"@odata.type", new UntypedString("#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension")
								},
								{
									"id", new UntypedString("52036a43-10b5-444d-a1a2-d4f240420239")
								},
							})
						},
					}),
				}
			},
		},
	},
	CustomExtensionStageSettings = new List<CustomExtensionStageSetting>
	{
		new CustomExtensionStageSetting
		{
			Stage = AccessPackageCustomExtensionStage.AssignmentRequestCreated,
			CustomExtension = new AccessPackageAssignmentRequestWorkflowExtension
			{
				OdataType = "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
				Id = "52036a43-10b5-444d-a1a2-d4f240420239",
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@odata.context" , "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/$entity"
		},
		{
			"canExtend" , false
		},
		{
			"durationInDays" , 0
		},
		{
			"expirationDateTime" , null
		},
		{
			"accessPackageId" , "fc29cdca-57f6-47e3-b20c-3fa18e4826ac"
		},
		{
			"accessReviewSettings" , null
		},
		{
			"accessPackageNotificationSettings" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"isAssignmentNotificationDisabled", new UntypedBoolean(false)
				},
			})
		},
		{
			"verifiableCredentialSettings" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"credentialTypes", new UntypedArray(new List<UntypedNode>
					{
					})
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentPolicies.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setDisplayName("Dynamic approver policy");
accessPackageAssignmentPolicy.setDescription("Dynamic approver policy");
LinkedList<AccessPackageQuestion> questions = new LinkedList<AccessPackageQuestion>();
accessPackageAssignmentPolicy.setQuestions(questions);
AccessPackageAssignmentRequestorSettings requestorSettings = new AccessPackageAssignmentRequestorSettings();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("scopeType", "AllExistingDirectorySubjects");
additionalData.put("acceptRequests", true);
LinkedList<Object> allowedRequestors = new LinkedList<Object>();
additionalData.put("allowedRequestors", allowedRequestors);
requestorSettings.setAdditionalData(additionalData);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
AccessPackageAssignmentApprovalSettings requestApprovalSettings = new AccessPackageAssignmentApprovalSettings();
requestApprovalSettings.setIsRequestorJustificationRequired(true);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("isApprovalRequired", true);
additionalData1.put("isApprovalRequiredForExtension", false);
additionalData1.put("approvalMode", "SingleStage");
LinkedList<Object> approvalStages = new LinkedList<Object>();
 property = new ();
property.setOdataType("#microsoft.graph.accessPackageDynamicApprovalStage");
 customExtension = new ();
customExtension.setOdataType("#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension");
customExtension.setId("52036a43-10b5-444d-a1a2-d4f240420239");
property.setCustomExtension(customExtension);
approvalStages.add(property);
additionalData1.put("approvalStages", approvalStages);
requestApprovalSettings.setAdditionalData(additionalData1);
accessPackageAssignmentPolicy.setRequestApprovalSettings(requestApprovalSettings);
LinkedList<CustomExtensionStageSetting> customExtensionStageSettings = new LinkedList<CustomExtensionStageSetting>();
CustomExtensionStageSetting customExtensionStageSetting = new CustomExtensionStageSetting();
customExtensionStageSetting.setStage(AccessPackageCustomExtensionStage.AssignmentRequestCreated);
AccessPackageAssignmentRequestWorkflowExtension customExtension1 = new AccessPackageAssignmentRequestWorkflowExtension();
customExtension1.setOdataType("#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension");
customExtension1.setId("52036a43-10b5-444d-a1a2-d4f240420239");
customExtensionStageSetting.setCustomExtension(customExtension1);
customExtensionStageSettings.add(customExtensionStageSetting);
accessPackageAssignmentPolicy.setCustomExtensionStageSettings(customExtensionStageSettings);
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("@odata.context", "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/$entity");
additionalData2.put("canExtend", false);
additionalData2.put("durationInDays", 0);
additionalData2.put("expirationDateTime", null);
additionalData2.put("accessPackageId", "fc29cdca-57f6-47e3-b20c-3fa18e4826ac");
additionalData2.put("accessReviewSettings", null);
 accessPackageNotificationSettings = new ();
accessPackageNotificationSettings.setIsAssignmentNotificationDisabled(false);
additionalData2.put("accessPackageNotificationSettings", accessPackageNotificationSettings);
 verifiableCredentialSettings = new ();
LinkedList<Object> credentialTypes = new LinkedList<Object>();
verifiableCredentialSettings.setCredentialTypes(credentialTypes);
additionalData2.put("verifiableCredentialSettings", verifiableCredentialSettings);
accessPackageAssignmentPolicy.setAdditionalData(additionalData2);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().assignmentPolicies().post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
    '@odata.context': 'https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/$entity',
    displayName: 'Dynamic approver policy',
    description: 'Dynamic approver policy',
    canExtend: false,
    durationInDays: 0,
    expirationDateTime: null,
    accessPackageId: 'fc29cdca-57f6-47e3-b20c-3fa18e4826ac',
    accessReviewSettings: null,
    questions: [],
    accessPackageNotificationSettings: {
        isAssignmentNotificationDisabled: false
    },
    verifiableCredentialSettings: {
        credentialTypes: []
    },
    requestorSettings: {
        scopeType: 'AllExistingDirectorySubjects',
        acceptRequests: true,
        allowedRequestors: []
    },
    requestApprovalSettings: {
        isApprovalRequired: true,
        isApprovalRequiredForExtension: false,
        isRequestorJustificationRequired: true,
        approvalMode: 'SingleStage',
        approvalStages: [
            {
                '@odata.type': '#microsoft.graph.accessPackageDynamicApprovalStage',
                customExtension: {
                    '@odata.type': '#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension',
                    id: '52036a43-10b5-444d-a1a2-d4f240420239'
                }
            }
        ]
    },
    customExtensionStageSettings: [
        {
            stage: 'assignmentRequestDeterminingApprovalRequirements',
            customExtension: {
            '@odata.type': '#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension',
            id: '52036a43-10b5-444d-a1a2-d4f240420239'
            }
        }
    ]
};

await client.api('/identityGovernance/entitlementManagement/assignmentPolicies/')
	.post(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Generated\Models\AccessPackageQuestion;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequestorSettings;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentApprovalSettings;
use Microsoft\Graph\Generated\Models\CustomExtensionStageSetting;
use Microsoft\Graph\Generated\Models\AccessPackageCustomExtensionStage;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequestWorkflowExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setDisplayName('Dynamic approver policy');
$requestBody->setDescription('Dynamic approver policy');
$requestBody->setQuestions([	]);
$requestorSettings = new AccessPackageAssignmentRequestorSettings();
$additionalData = [
	'scopeType' => 'AllExistingDirectorySubjects',
	'acceptRequests' => true,
	'allowedRequestors' => [],
];
$requestorSettings->setAdditionalData($additionalData);
$requestBody->setRequestorSettings($requestorSettings);
$requestApprovalSettings = new AccessPackageAssignmentApprovalSettings();
$requestApprovalSettings->setIsRequestorJustificationRequired(true);
$additionalData = [
	'isApprovalRequired' => true,
	'isApprovalRequiredForExtension' => false,
	'approvalMode' => 'SingleStage',
	'approvalStages' => [
			[
				'@odata.type' => '#microsoft.graph.accessPackageDynamicApprovalStage',
				'customExtension' => [
					'@odata.type' => '#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension',
					'id' => '52036a43-10b5-444d-a1a2-d4f240420239',
				],
			],
		],
];
$requestApprovalSettings->setAdditionalData($additionalData);
$requestBody->setRequestApprovalSettings($requestApprovalSettings);
$customExtensionStageSettingsCustomExtensionStageSetting1 = new CustomExtensionStageSetting();
$customExtensionStageSettingsCustomExtensionStageSetting1->setStage(new AccessPackageCustomExtensionStage('assignmentRequestDeterminingApprovalRequirements'));
$customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension = new AccessPackageAssignmentRequestWorkflowExtension();
$customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension->setOdataType('#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension');
$customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension->setId('52036a43-10b5-444d-a1a2-d4f240420239');
$customExtensionStageSettingsCustomExtensionStageSetting1->setCustomExtension($customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension);
$customExtensionStageSettingsArray []= $customExtensionStageSettingsCustomExtensionStageSetting1;
$requestBody->setCustomExtensionStageSettings($customExtensionStageSettingsArray);

$additionalData = [
'@odata.context' => 'https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/$entity',
'canExtend' => false,
'durationInDays' => 0,
'expirationDateTime' => null,
'accessPackageId' => 'fc29cdca-57f6-47e3-b20c-3fa18e4826ac',
'accessReviewSettings' => null,
'accessPackageNotificationSettings' => [
	'isAssignmentNotificationDisabled' => false,
],
'verifiableCredentialSettings' => [
	'credentialTypes' => [],
],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentPolicies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	"@odata.context" = "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/$entity"
	displayName = "Dynamic approver policy"
	description = "Dynamic approver policy"
	canExtend = $false
	durationInDays = 
	expirationDateTime = $null
	accessPackageId = "fc29cdca-57f6-47e3-b20c-3fa18e4826ac"
	accessReviewSettings = $null
	questions = @(
	)
	accessPackageNotificationSettings = @{
		isAssignmentNotificationDisabled = $false
	}
	verifiableCredentialSettings = @{
		credentialTypes = @(
		)
	}
	requestorSettings = @{
		scopeType = "AllExistingDirectorySubjects"
		acceptRequests = $true
		allowedRequestors = @(
		)
	}
	requestApprovalSettings = @{
		isApprovalRequired = $true
		isApprovalRequiredForExtension = $false
		isRequestorJustificationRequired = $true
		approvalMode = "SingleStage"
		approvalStages = @(
			@{
				"@odata.type" = "#microsoft.graph.accessPackageDynamicApprovalStage"
				customExtension = @{
					"@odata.type" = "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension"
					id = "52036a43-10b5-444d-a1a2-d4f240420239"
				}
			}
		)
	}
	customExtensionStageSettings = @(
		@{
			stage = "assignmentRequestDeterminingApprovalRequirements"
			customExtension = @{
				"@odata.type" = "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension"
				id = "52036a43-10b5-444d-a1a2-d4f240420239"
			}
		}
	)
}

New-MgEntitlementManagementAssignmentPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph.generated.models.access_package_question import AccessPackageQuestion
from msgraph.generated.models.access_package_assignment_requestor_settings import AccessPackageAssignmentRequestorSettings
from msgraph.generated.models.access_package_assignment_approval_settings import AccessPackageAssignmentApprovalSettings
from msgraph.generated.models.custom_extension_stage_setting import CustomExtensionStageSetting
from msgraph.generated.models.access_package_custom_extension_stage import AccessPackageCustomExtensionStage
from msgraph.generated.models.access_package_assignment_request_workflow_extension import AccessPackageAssignmentRequestWorkflowExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	display_name = "Dynamic approver policy",
	description = "Dynamic approver policy",
	questions = [
	],
	requestor_settings = AccessPackageAssignmentRequestorSettings(
		additional_data = {
				"scope_type" : "AllExistingDirectorySubjects",
				"accept_requests" : True,
				"allowed_requestors" : [
				],
		}
	),
	request_approval_settings = AccessPackageAssignmentApprovalSettings(
		is_requestor_justification_required = True,
		additional_data = {
				"is_approval_required" : True,
				"is_approval_required_for_extension" : False,
				"approval_mode" : "SingleStage",
				"approval_stages" : [
					{
							"@odata_type" : "#microsoft.graph.accessPackageDynamicApprovalStage",
							"custom_extension" : {
									"@odata_type" : "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
									"id" : "52036a43-10b5-444d-a1a2-d4f240420239",
							},
					},
				],
		}
	),
	custom_extension_stage_settings = [
		CustomExtensionStageSetting(
			stage = AccessPackageCustomExtensionStage.AssignmentRequestCreated,
			custom_extension = AccessPackageAssignmentRequestWorkflowExtension(
				odata_type = "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
				id = "52036a43-10b5-444d-a1a2-d4f240420239",
			),
		),
	],
	additional_data = {
			"@odata_context" : "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/$entity",
			"can_extend" : False,
			"duration_in_days" : 0,
			"expiration_date_time" : None,
			"access_package_id" : "fc29cdca-57f6-47e3-b20c-3fa18e4826ac",
			"access_review_settings" : None,
			"access_package_notification_settings" : {
					"is_assignment_notification_disabled" : False,
			},
			"verifiable_credential_settings" : {
					"credential_types" : [
					],
			},
	}
)

result = await graph_client.identity_governance.entitlement_management.assignment_policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The **customExtensionStageSettings** object isn't returned by default. To retrieve this object, use the [GET accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-1.0) method with `$expand`. For more information, see [Example 2: Retrieve the custom extension stage settings for a policy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-1.0#example-2-retrieve-the-custom-extension-stage-settings-for-a-policy).

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "d0324cbb-24a2-4edb-acca-fee5384c6a5e",
  "displayName": "Dynamic approver policy",
  "description": "Dynamic approver policy",
  "canExtend": false,
  "durationInDays": 0,
  "expirationDateTime": null,
  "accessPackageId": "fc29cdca-57f6-47e3-b20c-3fa18e4826ac",
  "accessReviewSettings": null,
  "questions": [],
  "requestorSettings": {
    "scopeType": "AllExistingDirectorySubjects",
    "acceptRequests": true,
    "allowedRequestors": []
  },
  "requestApprovalSettings": {
    "isApprovalRequired": false,
    "isApprovalRequiredForExtension": false,
    "isRequestorJustificationRequired": false,
    "approvalMode": "NoApproval",
    "approvalStages": []
  },
  "customExtensionStageSettings": [
        {
            "stage": "assignmentRequestCreated",
            "customExtension": {
                "@odata.type": "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
                "id": "52036a43-10b5-444d-a1a2-d4f240420239"
            }
        }
    ]
}
```
