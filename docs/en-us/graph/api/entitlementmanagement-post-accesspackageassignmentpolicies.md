<!-- Source: https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-accesspackageassignmentpolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-20 -->

# Create accessPackageAssignmentPolicy

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-beta) object in [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-beta).

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
POST /identityGovernance/entitlementManagement/accessPackageAssignmentPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-beta) object.

## Response

If successful, this method returns a 200-series response code and a new [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies
Content-type: application/json

{
  "accessPackageId": "56ff43fd-6b05-48df-9634-956a777fce6d",
  "displayName": "direct",
  "description": "direct assignments by administrator",
  "accessReviewSettings": null,
  "requestorSettings": {
    "scopeType": "NoSubjects",
    "acceptRequests": true,
    "allowedRequestors": []
  },
  "requestApprovalSettings": {
    "isApprovalRequired": false,
    "isApprovalRequiredForExtension": false,
    "isRequestorJustificationRequired": false,
    "approvalMode": "NoApproval",
    "approvalStages": []
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageAssignmentPolicy
{
	AccessPackageId = "56ff43fd-6b05-48df-9634-956a777fce6d",
	DisplayName = "direct",
	Description = "direct assignments by administrator",
	AccessReviewSettings = null,
	RequestorSettings = new RequestorSettings
	{
		ScopeType = "NoSubjects",
		AcceptRequests = true,
		AllowedRequestors = new List<UserSet>
		{
		},
	},
	RequestApprovalSettings = new ApprovalSettings
	{
		IsApprovalRequired = false,
		IsApprovalRequiredForExtension = false,
		IsRequestorJustificationRequired = false,
		ApprovalMode = "NoApproval",
		ApprovalStages = new List<ApprovalStage>
		{
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
accessPackageId := "56ff43fd-6b05-48df-9634-956a777fce6d"
requestBody.SetAccessPackageId(&accessPackageId) 
displayName := "direct"
requestBody.SetDisplayName(&displayName) 
description := "direct assignments by administrator"
requestBody.SetDescription(&description) 
accessReviewSettings := null
requestBody.SetAccessReviewSettings(&accessReviewSettings) 
requestorSettings := graphmodels.NewRequestorSettings()
scopeType := "NoSubjects"
requestorSettings.SetScopeType(&scopeType) 
acceptRequests := true
requestorSettings.SetAcceptRequests(&acceptRequests) 
allowedRequestors := []graphmodels.UserSetable {

}
requestorSettings.SetAllowedRequestors(allowedRequestors)
requestBody.SetRequestorSettings(requestorSettings)
requestApprovalSettings := graphmodels.NewApprovalSettings()
isApprovalRequired := false
requestApprovalSettings.SetIsApprovalRequired(&isApprovalRequired) 
isApprovalRequiredForExtension := false
requestApprovalSettings.SetIsApprovalRequiredForExtension(&isApprovalRequiredForExtension) 
isRequestorJustificationRequired := false
requestApprovalSettings.SetIsRequestorJustificationRequired(&isRequestorJustificationRequired) 
approvalMode := "NoApproval"
requestApprovalSettings.SetApprovalMode(&approvalMode) 
approvalStages := []graphmodels.ApprovalStageable {

}
requestApprovalSettings.SetApprovalStages(approvalStages)
requestBody.SetRequestApprovalSettings(requestApprovalSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setAccessPackageId("56ff43fd-6b05-48df-9634-956a777fce6d");
accessPackageAssignmentPolicy.setDisplayName("direct");
accessPackageAssignmentPolicy.setDescription("direct assignments by administrator");
accessPackageAssignmentPolicy.setAccessReviewSettings(null);
RequestorSettings requestorSettings = new RequestorSettings();
requestorSettings.setScopeType("NoSubjects");
requestorSettings.setAcceptRequests(true);
LinkedList<UserSet> allowedRequestors = new LinkedList<UserSet>();
requestorSettings.setAllowedRequestors(allowedRequestors);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
ApprovalSettings requestApprovalSettings = new ApprovalSettings();
requestApprovalSettings.setIsApprovalRequired(false);
requestApprovalSettings.setIsApprovalRequiredForExtension(false);
requestApprovalSettings.setIsRequestorJustificationRequired(false);
requestApprovalSettings.setApprovalMode("NoApproval");
LinkedList<ApprovalStage> approvalStages = new LinkedList<ApprovalStage>();
requestApprovalSettings.setApprovalStages(approvalStages);
accessPackageAssignmentPolicy.setRequestApprovalSettings(requestApprovalSettings);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentPolicies().post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
  accessPackageId: '56ff43fd-6b05-48df-9634-956a777fce6d',
  displayName: 'direct',
  description: 'direct assignments by administrator',
  accessReviewSettings: null,
  requestorSettings: {
    scopeType: 'NoSubjects',
    acceptRequests: true,
    allowedRequestors: []
  },
  requestApprovalSettings: {
    isApprovalRequired: false,
    isApprovalRequiredForExtension: false,
    isRequestorJustificationRequired: false,
    approvalMode: 'NoApproval',
    approvalStages: []
  }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies')
	.version('beta')
	.post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Beta\Generated\Models\RequestorSettings;
use Microsoft\Graph\Beta\Generated\Models\UserSet;
use Microsoft\Graph\Beta\Generated\Models\ApprovalSettings;
use Microsoft\Graph\Beta\Generated\Models\ApprovalStage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setAccessPackageId('56ff43fd-6b05-48df-9634-956a777fce6d');
$requestBody->setDisplayName('direct');
$requestBody->setDescription('direct assignments by administrator');
$requestBody->setAccessReviewSettings(null);
$requestorSettings = new RequestorSettings();
$requestorSettings->setScopeType('NoSubjects');
$requestorSettings->setAcceptRequests(true);
$requestorSettings->setAllowedRequestors([	]);
$requestBody->setRequestorSettings($requestorSettings);
$requestApprovalSettings = new ApprovalSettings();
$requestApprovalSettings->setIsApprovalRequired(false);
$requestApprovalSettings->setIsApprovalRequiredForExtension(false);
$requestApprovalSettings->setIsRequestorJustificationRequired(false);
$requestApprovalSettings->setApprovalMode('NoApproval');
$requestApprovalSettings->setApprovalStages([	]);
$requestBody->setRequestApprovalSettings($requestApprovalSettings);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	accessPackageId = "56ff43fd-6b05-48df-9634-956a777fce6d"
	displayName = "direct"
	description = "direct assignments by administrator"
	accessReviewSettings = $null
	requestorSettings = @{
		scopeType = "NoSubjects"
		acceptRequests = $true
		allowedRequestors = @(
		)
	}
	requestApprovalSettings = @{
		isApprovalRequired = $false
		isApprovalRequiredForExtension = $false
		isRequestorJustificationRequired = $false
		approvalMode = "NoApproval"
		approvalStages = @(
		)
	}
}

New-MgBetaEntitlementManagementAccessPackageAssignmentPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph_beta.generated.models.requestor_settings import RequestorSettings
from msgraph_beta.generated.models.user_set import UserSet
from msgraph_beta.generated.models.approval_settings import ApprovalSettings
from msgraph_beta.generated.models.approval_stage import ApprovalStage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	access_package_id = "56ff43fd-6b05-48df-9634-956a777fce6d",
	display_name = "direct",
	description = "direct assignments by administrator",
	access_review_settings = None,
	requestor_settings = RequestorSettings(
		scope_type = "NoSubjects",
		accept_requests = True,
		allowed_requestors = [
		],
	),
	request_approval_settings = ApprovalSettings(
		is_approval_required = False,
		is_approval_required_for_extension = False,
		is_requestor_justification_required = False,
		approval_mode = "NoApproval",
		approval_stages = [
		],
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_policies.post(request_body)
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
  "id": "4c02f928-7752-49aa-8fc8-e286d973a965",
  "accessPackageId": "56ff43fd-6b05-48df-9634-956a777fce6d",
  "displayName": "direct",
  "description": "direct assignments by administrator"
}
```

### Example 2: Create a policy for users from other organizations to request

The following example shows a more complex policy with two-stage approvals and access reviews.

#### Request

The following example shows a request to create an access package assignment policy.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies
Content-type: application/json

{
    "accessPackageId": "string (identifier)",
    "displayName": "Users from connected organizations can request",
    "description": "Allow users from configured connected organizations to request and be approved by their sponsors",
    "canExtend": false,
    "durationInDays": 365,
    "expirationDateTime": null,
    "requestorSettings": {
        "scopeType": "AllExistingConnectedOrganizationSubjects",
        "acceptRequests": true,
        "allowedRequestors": []
    },
    "requestApprovalSettings": {
        "isApprovalRequired": true,
        "isApprovalRequiredForExtension": false,
        "isRequestorJustificationRequired": true,
        "approvalMode": "Serial",
        "approvalStages": [
            {
                "approvalStageTimeOutInDays": 14,
                "isApproverJustificationRequired": true,
                "isEscalationEnabled": true,
                "escalationTimeInMinutes": 11520,
                "primaryApprovers": [
                    {
                        "@odata.type": "#microsoft.graph.groupMembers",
                        "isBackup": true,
                        "id": "string (identifier)",
                        "description": "group for users from connected organizations which have no external sponsor"
                    },
                    {
                        "@odata.type": "#microsoft.graph.externalSponsors",
                        "isBackup": false
                    }
                ],
                "escalationApprovers": [
                    {
                        "@odata.type": "#microsoft.graph.singleUser",
                        "isBackup": true,
                        "id": "string (identifier)",
                        "description": "user if the external sponsor does not respond"
                    }
                ]
            },
            {
                "approvalStageTimeOutInDays": 14,
                "isApproverJustificationRequired": true,
                "isEscalationEnabled": true,
                "escalationTimeInMinutes": 11520,
                "primaryApprovers": [
                    {
                        "@odata.type": "#microsoft.graph.groupMembers",
                        "isBackup": true,
                        "id": "string (identifier)",
                        "description": "group for users from connected organizations which have no internal sponsor"
                    },
                    {
                        "@odata.type": "#microsoft.graph.internalSponsors",
                        "isBackup": false
                    }
                ],
                "escalationApprovers": [
                    {
                        "@odata.type": "#microsoft.graph.singleUser",
                        "isBackup": true,
                        "id": "string (identifier)",
                        "description": "user if the internal sponsor does not respond"
                    }
                ]
            }
        ]
    },
    "accessReviewSettings": {
        "isEnabled": true,
        "recurrenceType": "quarterly",
        "reviewerType": "Self",
        "startDateTime": "2020-04-01T07:59:59.998Z",
        "durationInDays": 25,
        "reviewers": []
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageAssignmentPolicy
{
	AccessPackageId = "string (identifier)",
	DisplayName = "Users from connected organizations can request",
	Description = "Allow users from configured connected organizations to request and be approved by their sponsors",
	CanExtend = false,
	DurationInDays = 365,
	ExpirationDateTime = null,
	RequestorSettings = new RequestorSettings
	{
		ScopeType = "AllExistingConnectedOrganizationSubjects",
		AcceptRequests = true,
		AllowedRequestors = new List<UserSet>
		{
		},
	},
	RequestApprovalSettings = new ApprovalSettings
	{
		IsApprovalRequired = true,
		IsApprovalRequiredForExtension = false,
		IsRequestorJustificationRequired = true,
		ApprovalMode = "Serial",
		ApprovalStages = new List<ApprovalStage>
		{
			new ApprovalStage
			{
				ApprovalStageTimeOutInDays = 14,
				IsApproverJustificationRequired = true,
				IsEscalationEnabled = true,
				EscalationTimeInMinutes = 11520,
				PrimaryApprovers = new List<UserSet>
				{
					new GroupMembers
					{
						OdataType = "#microsoft.graph.groupMembers",
						IsBackup = true,
						Id = "string (identifier)",
						Description = "group for users from connected organizations which have no external sponsor",
					},
					new ExternalSponsors
					{
						OdataType = "#microsoft.graph.externalSponsors",
						IsBackup = false,
					},
				},
				EscalationApprovers = new List<UserSet>
				{
					new SingleUser
					{
						OdataType = "#microsoft.graph.singleUser",
						IsBackup = true,
						Id = "string (identifier)",
						Description = "user if the external sponsor does not respond",
					},
				},
			},
			new ApprovalStage
			{
				ApprovalStageTimeOutInDays = 14,
				IsApproverJustificationRequired = true,
				IsEscalationEnabled = true,
				EscalationTimeInMinutes = 11520,
				PrimaryApprovers = new List<UserSet>
				{
					new GroupMembers
					{
						OdataType = "#microsoft.graph.groupMembers",
						IsBackup = true,
						Id = "string (identifier)",
						Description = "group for users from connected organizations which have no internal sponsor",
					},
					new InternalSponsors
					{
						OdataType = "#microsoft.graph.internalSponsors",
						IsBackup = false,
					},
				},
				EscalationApprovers = new List<UserSet>
				{
					new SingleUser
					{
						OdataType = "#microsoft.graph.singleUser",
						IsBackup = true,
						Id = "string (identifier)",
						Description = "user if the internal sponsor does not respond",
					},
				},
			},
		},
	},
	AccessReviewSettings = new AssignmentReviewSettings
	{
		IsEnabled = true,
		RecurrenceType = "quarterly",
		ReviewerType = "Self",
		StartDateTime = DateTimeOffset.Parse("2020-04-01T07:59:59.998Z"),
		DurationInDays = 25,
		Reviewers = new List<UserSet>
		{
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
accessPackageId := "string (identifier)"
requestBody.SetAccessPackageId(&accessPackageId) 
displayName := "Users from connected organizations can request"
requestBody.SetDisplayName(&displayName) 
description := "Allow users from configured connected organizations to request and be approved by their sponsors"
requestBody.SetDescription(&description) 
canExtend := false
requestBody.SetCanExtend(&canExtend) 
durationInDays := int32(365)
requestBody.SetDurationInDays(&durationInDays) 
expirationDateTime := null
requestBody.SetExpirationDateTime(&expirationDateTime) 
requestorSettings := graphmodels.NewRequestorSettings()
scopeType := "AllExistingConnectedOrganizationSubjects"
requestorSettings.SetScopeType(&scopeType) 
acceptRequests := true
requestorSettings.SetAcceptRequests(&acceptRequests) 
allowedRequestors := []graphmodels.UserSetable {

}
requestorSettings.SetAllowedRequestors(allowedRequestors)
requestBody.SetRequestorSettings(requestorSettings)
requestApprovalSettings := graphmodels.NewApprovalSettings()
isApprovalRequired := true
requestApprovalSettings.SetIsApprovalRequired(&isApprovalRequired) 
isApprovalRequiredForExtension := false
requestApprovalSettings.SetIsApprovalRequiredForExtension(&isApprovalRequiredForExtension) 
isRequestorJustificationRequired := true
requestApprovalSettings.SetIsRequestorJustificationRequired(&isRequestorJustificationRequired) 
approvalMode := "Serial"
requestApprovalSettings.SetApprovalMode(&approvalMode) 


approvalStage := graphmodels.NewApprovalStage()
approvalStageTimeOutInDays := int32(14)
approvalStage.SetApprovalStageTimeOutInDays(&approvalStageTimeOutInDays) 
isApproverJustificationRequired := true
approvalStage.SetIsApproverJustificationRequired(&isApproverJustificationRequired) 
isEscalationEnabled := true
approvalStage.SetIsEscalationEnabled(&isEscalationEnabled) 
escalationTimeInMinutes := int32(11520)
approvalStage.SetEscalationTimeInMinutes(&escalationTimeInMinutes) 


userSet := graphmodels.NewGroupMembers()
isBackup := true
userSet.SetIsBackup(&isBackup) 
id := "string (identifier)"
userSet.SetId(&id) 
description := "group for users from connected organizations which have no external sponsor"
userSet.SetDescription(&description) 
userSet1 := graphmodels.NewExternalSponsors()
isBackup := false
userSet1.SetIsBackup(&isBackup) 

primaryApprovers := []graphmodels.UserSetable {
	userSet,
	userSet1,
}
approvalStage.SetPrimaryApprovers(primaryApprovers)


userSet := graphmodels.NewSingleUser()
isBackup := true
userSet.SetIsBackup(&isBackup) 
id := "string (identifier)"
userSet.SetId(&id) 
description := "user if the external sponsor does not respond"
userSet.SetDescription(&description) 

escalationApprovers := []graphmodels.UserSetable {
	userSet,
}
approvalStage.SetEscalationApprovers(escalationApprovers)
approvalStage1 := graphmodels.NewApprovalStage()
approvalStageTimeOutInDays := int32(14)
approvalStage1.SetApprovalStageTimeOutInDays(&approvalStageTimeOutInDays) 
isApproverJustificationRequired := true
approvalStage1.SetIsApproverJustificationRequired(&isApproverJustificationRequired) 
isEscalationEnabled := true
approvalStage1.SetIsEscalationEnabled(&isEscalationEnabled) 
escalationTimeInMinutes := int32(11520)
approvalStage1.SetEscalationTimeInMinutes(&escalationTimeInMinutes) 


userSet := graphmodels.NewGroupMembers()
isBackup := true
userSet.SetIsBackup(&isBackup) 
id := "string (identifier)"
userSet.SetId(&id) 
description := "group for users from connected organizations which have no internal sponsor"
userSet.SetDescription(&description) 
userSet1 := graphmodels.NewInternalSponsors()
isBackup := false
userSet1.SetIsBackup(&isBackup) 

primaryApprovers := []graphmodels.UserSetable {
	userSet,
	userSet1,
}
approvalStage1.SetPrimaryApprovers(primaryApprovers)


userSet := graphmodels.NewSingleUser()
isBackup := true
userSet.SetIsBackup(&isBackup) 
id := "string (identifier)"
userSet.SetId(&id) 
description := "user if the internal sponsor does not respond"
userSet.SetDescription(&description) 

escalationApprovers := []graphmodels.UserSetable {
	userSet,
}
approvalStage1.SetEscalationApprovers(escalationApprovers)

approvalStages := []graphmodels.ApprovalStageable {
	approvalStage,
	approvalStage1,
}
requestApprovalSettings.SetApprovalStages(approvalStages)
requestBody.SetRequestApprovalSettings(requestApprovalSettings)
accessReviewSettings := graphmodels.NewAssignmentReviewSettings()
isEnabled := true
accessReviewSettings.SetIsEnabled(&isEnabled) 
recurrenceType := "quarterly"
accessReviewSettings.SetRecurrenceType(&recurrenceType) 
reviewerType := "Self"
accessReviewSettings.SetReviewerType(&reviewerType) 
startDateTime , err := time.Parse(time.RFC3339, "2020-04-01T07:59:59.998Z")
accessReviewSettings.SetStartDateTime(&startDateTime) 
durationInDays := int32(25)
accessReviewSettings.SetDurationInDays(&durationInDays) 
reviewers := []graphmodels.UserSetable {

}
accessReviewSettings.SetReviewers(reviewers)
requestBody.SetAccessReviewSettings(accessReviewSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setAccessPackageId("string (identifier)");
accessPackageAssignmentPolicy.setDisplayName("Users from connected organizations can request");
accessPackageAssignmentPolicy.setDescription("Allow users from configured connected organizations to request and be approved by their sponsors");
accessPackageAssignmentPolicy.setCanExtend(false);
accessPackageAssignmentPolicy.setDurationInDays(365);
accessPackageAssignmentPolicy.setExpirationDateTime(null);
RequestorSettings requestorSettings = new RequestorSettings();
requestorSettings.setScopeType("AllExistingConnectedOrganizationSubjects");
requestorSettings.setAcceptRequests(true);
LinkedList<UserSet> allowedRequestors = new LinkedList<UserSet>();
requestorSettings.setAllowedRequestors(allowedRequestors);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
ApprovalSettings requestApprovalSettings = new ApprovalSettings();
requestApprovalSettings.setIsApprovalRequired(true);
requestApprovalSettings.setIsApprovalRequiredForExtension(false);
requestApprovalSettings.setIsRequestorJustificationRequired(true);
requestApprovalSettings.setApprovalMode("Serial");
LinkedList<ApprovalStage> approvalStages = new LinkedList<ApprovalStage>();
ApprovalStage approvalStage = new ApprovalStage();
approvalStage.setApprovalStageTimeOutInDays(14);
approvalStage.setIsApproverJustificationRequired(true);
approvalStage.setIsEscalationEnabled(true);
approvalStage.setEscalationTimeInMinutes(11520);
LinkedList<UserSet> primaryApprovers = new LinkedList<UserSet>();
GroupMembers userSet = new GroupMembers();
userSet.setOdataType("#microsoft.graph.groupMembers");
userSet.setIsBackup(true);
userSet.setId("string (identifier)");
userSet.setDescription("group for users from connected organizations which have no external sponsor");
primaryApprovers.add(userSet);
ExternalSponsors userSet1 = new ExternalSponsors();
userSet1.setOdataType("#microsoft.graph.externalSponsors");
userSet1.setIsBackup(false);
primaryApprovers.add(userSet1);
approvalStage.setPrimaryApprovers(primaryApprovers);
LinkedList<UserSet> escalationApprovers = new LinkedList<UserSet>();
SingleUser userSet2 = new SingleUser();
userSet2.setOdataType("#microsoft.graph.singleUser");
userSet2.setIsBackup(true);
userSet2.setId("string (identifier)");
userSet2.setDescription("user if the external sponsor does not respond");
escalationApprovers.add(userSet2);
approvalStage.setEscalationApprovers(escalationApprovers);
approvalStages.add(approvalStage);
ApprovalStage approvalStage1 = new ApprovalStage();
approvalStage1.setApprovalStageTimeOutInDays(14);
approvalStage1.setIsApproverJustificationRequired(true);
approvalStage1.setIsEscalationEnabled(true);
approvalStage1.setEscalationTimeInMinutes(11520);
LinkedList<UserSet> primaryApprovers1 = new LinkedList<UserSet>();
GroupMembers userSet3 = new GroupMembers();
userSet3.setOdataType("#microsoft.graph.groupMembers");
userSet3.setIsBackup(true);
userSet3.setId("string (identifier)");
userSet3.setDescription("group for users from connected organizations which have no internal sponsor");
primaryApprovers1.add(userSet3);
InternalSponsors userSet4 = new InternalSponsors();
userSet4.setOdataType("#microsoft.graph.internalSponsors");
userSet4.setIsBackup(false);
primaryApprovers1.add(userSet4);
approvalStage1.setPrimaryApprovers(primaryApprovers1);
LinkedList<UserSet> escalationApprovers1 = new LinkedList<UserSet>();
SingleUser userSet5 = new SingleUser();
userSet5.setOdataType("#microsoft.graph.singleUser");
userSet5.setIsBackup(true);
userSet5.setId("string (identifier)");
userSet5.setDescription("user if the internal sponsor does not respond");
escalationApprovers1.add(userSet5);
approvalStage1.setEscalationApprovers(escalationApprovers1);
approvalStages.add(approvalStage1);
requestApprovalSettings.setApprovalStages(approvalStages);
accessPackageAssignmentPolicy.setRequestApprovalSettings(requestApprovalSettings);
AssignmentReviewSettings accessReviewSettings = new AssignmentReviewSettings();
accessReviewSettings.setIsEnabled(true);
accessReviewSettings.setRecurrenceType("quarterly");
accessReviewSettings.setReviewerType("Self");
OffsetDateTime startDateTime = OffsetDateTime.parse("2020-04-01T07:59:59.998Z");
accessReviewSettings.setStartDateTime(startDateTime);
accessReviewSettings.setDurationInDays(25);
LinkedList<UserSet> reviewers = new LinkedList<UserSet>();
accessReviewSettings.setReviewers(reviewers);
accessPackageAssignmentPolicy.setAccessReviewSettings(accessReviewSettings);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentPolicies().post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
    accessPackageId: 'string (identifier)',
    displayName: 'Users from connected organizations can request',
    description: 'Allow users from configured connected organizations to request and be approved by their sponsors',
    canExtend: false,
    durationInDays: 365,
    expirationDateTime: null,
    requestorSettings: {
        scopeType: 'AllExistingConnectedOrganizationSubjects',
        acceptRequests: true,
        allowedRequestors: []
    },
    requestApprovalSettings: {
        isApprovalRequired: true,
        isApprovalRequiredForExtension: false,
        isRequestorJustificationRequired: true,
        approvalMode: 'Serial',
        approvalStages: [
            {
                approvalStageTimeOutInDays: 14,
                isApproverJustificationRequired: true,
                isEscalationEnabled: true,
                escalationTimeInMinutes: 11520,
                primaryApprovers: [
                    {
                        '@odata.type': '#microsoft.graph.groupMembers',
                        isBackup: true,
                        id: 'string (identifier)',
                        description: 'group for users from connected organizations which have no external sponsor'
                    },
                    {
                        '@odata.type': '#microsoft.graph.externalSponsors',
                        isBackup: false
                    }
                ],
                escalationApprovers: [
                    {
                        '@odata.type': '#microsoft.graph.singleUser',
                        isBackup: true,
                        id: 'string (identifier)',
                        description: 'user if the external sponsor does not respond'
                    }
                ]
            },
            {
                approvalStageTimeOutInDays: 14,
                isApproverJustificationRequired: true,
                isEscalationEnabled: true,
                escalationTimeInMinutes: 11520,
                primaryApprovers: [
                    {
                        '@odata.type': '#microsoft.graph.groupMembers',
                        isBackup: true,
                        id: 'string (identifier)',
                        description: 'group for users from connected organizations which have no internal sponsor'
                    },
                    {
                        '@odata.type': '#microsoft.graph.internalSponsors',
                        isBackup: false
                    }
                ],
                escalationApprovers: [
                    {
                        '@odata.type': '#microsoft.graph.singleUser',
                        isBackup: true,
                        id: 'string (identifier)',
                        description: 'user if the internal sponsor does not respond'
                    }
                ]
            }
        ]
    },
    accessReviewSettings: {
        isEnabled: true,
        recurrenceType: 'quarterly',
        reviewerType: 'Self',
        startDateTime: '2020-04-01T07:59:59.998Z',
        durationInDays: 25,
        reviewers: []
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies')
	.version('beta')
	.post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Beta\Generated\Models\RequestorSettings;
use Microsoft\Graph\Beta\Generated\Models\UserSet;
use Microsoft\Graph\Beta\Generated\Models\ApprovalSettings;
use Microsoft\Graph\Beta\Generated\Models\ApprovalStage;
use Microsoft\Graph\Beta\Generated\Models\GroupMembers;
use Microsoft\Graph\Beta\Generated\Models\ExternalSponsors;
use Microsoft\Graph\Beta\Generated\Models\SingleUser;
use Microsoft\Graph\Beta\Generated\Models\InternalSponsors;
use Microsoft\Graph\Beta\Generated\Models\AssignmentReviewSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setAccessPackageId('string (identifier)');
$requestBody->setDisplayName('Users from connected organizations can request');
$requestBody->setDescription('Allow users from configured connected organizations to request and be approved by their sponsors');
$requestBody->setCanExtend(false);
$requestBody->setDurationInDays(365);
$requestBody->setExpirationDateTime(null);
$requestorSettings = new RequestorSettings();
$requestorSettings->setScopeType('AllExistingConnectedOrganizationSubjects');
$requestorSettings->setAcceptRequests(true);
$requestorSettings->setAllowedRequestors([	]);
$requestBody->setRequestorSettings($requestorSettings);
$requestApprovalSettings = new ApprovalSettings();
$requestApprovalSettings->setIsApprovalRequired(true);
$requestApprovalSettings->setIsApprovalRequiredForExtension(false);
$requestApprovalSettings->setIsRequestorJustificationRequired(true);
$requestApprovalSettings->setApprovalMode('Serial');
$approvalStagesApprovalStage1 = new ApprovalStage();
$approvalStagesApprovalStage1->setApprovalStageTimeOutInDays(14);
$approvalStagesApprovalStage1->setIsApproverJustificationRequired(true);
$approvalStagesApprovalStage1->setIsEscalationEnabled(true);
$approvalStagesApprovalStage1->setEscalationTimeInMinutes(11520);
$primaryApproversUserSet1 = new GroupMembers();
$primaryApproversUserSet1->setOdataType('#microsoft.graph.groupMembers');
$primaryApproversUserSet1->setIsBackup(true);
$primaryApproversUserSet1->setId('string (identifier)');
$primaryApproversUserSet1->setDescription('group for users from connected organizations which have no external sponsor');
$primaryApproversArray []= $primaryApproversUserSet1;
$primaryApproversUserSet2 = new ExternalSponsors();
$primaryApproversUserSet2->setOdataType('#microsoft.graph.externalSponsors');
$primaryApproversUserSet2->setIsBackup(false);
$primaryApproversArray []= $primaryApproversUserSet2;
$approvalStagesApprovalStage1->setPrimaryApprovers($primaryApproversArray);

$escalationApproversUserSet1 = new SingleUser();
$escalationApproversUserSet1->setOdataType('#microsoft.graph.singleUser');
$escalationApproversUserSet1->setIsBackup(true);
$escalationApproversUserSet1->setId('string (identifier)');
$escalationApproversUserSet1->setDescription('user if the external sponsor does not respond');
$escalationApproversArray []= $escalationApproversUserSet1;
$approvalStagesApprovalStage1->setEscalationApprovers($escalationApproversArray);

$approvalStagesArray []= $approvalStagesApprovalStage1;
$approvalStagesApprovalStage2 = new ApprovalStage();
$approvalStagesApprovalStage2->setApprovalStageTimeOutInDays(14);
$approvalStagesApprovalStage2->setIsApproverJustificationRequired(true);
$approvalStagesApprovalStage2->setIsEscalationEnabled(true);
$approvalStagesApprovalStage2->setEscalationTimeInMinutes(11520);
$primaryApproversUserSet1 = new GroupMembers();
$primaryApproversUserSet1->setOdataType('#microsoft.graph.groupMembers');
$primaryApproversUserSet1->setIsBackup(true);
$primaryApproversUserSet1->setId('string (identifier)');
$primaryApproversUserSet1->setDescription('group for users from connected organizations which have no internal sponsor');
$primaryApproversArray []= $primaryApproversUserSet1;
$primaryApproversUserSet2 = new InternalSponsors();
$primaryApproversUserSet2->setOdataType('#microsoft.graph.internalSponsors');
$primaryApproversUserSet2->setIsBackup(false);
$primaryApproversArray []= $primaryApproversUserSet2;
$approvalStagesApprovalStage2->setPrimaryApprovers($primaryApproversArray);

$escalationApproversUserSet1 = new SingleUser();
$escalationApproversUserSet1->setOdataType('#microsoft.graph.singleUser');
$escalationApproversUserSet1->setIsBackup(true);
$escalationApproversUserSet1->setId('string (identifier)');
$escalationApproversUserSet1->setDescription('user if the internal sponsor does not respond');
$escalationApproversArray []= $escalationApproversUserSet1;
$approvalStagesApprovalStage2->setEscalationApprovers($escalationApproversArray);

$approvalStagesArray []= $approvalStagesApprovalStage2;
$requestApprovalSettings->setApprovalStages($approvalStagesArray);

$requestBody->setRequestApprovalSettings($requestApprovalSettings);
$accessReviewSettings = new AssignmentReviewSettings();
$accessReviewSettings->setIsEnabled(true);
$accessReviewSettings->setRecurrenceType('quarterly');
$accessReviewSettings->setReviewerType('Self');
$accessReviewSettings->setStartDateTime(new \DateTime('2020-04-01T07:59:59.998Z'));
$accessReviewSettings->setDurationInDays(25);
$accessReviewSettings->setReviewers([]);
$requestBody->setAccessReviewSettings($accessReviewSettings);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	accessPackageId = "string (identifier)"
	displayName = "Users from connected organizations can request"
	description = "Allow users from configured connected organizations to request and be approved by their sponsors"
	canExtend = $false
	durationInDays = 365
	expirationDateTime = $null
	requestorSettings = @{
		scopeType = "AllExistingConnectedOrganizationSubjects"
		acceptRequests = $true
		allowedRequestors = @(
		)
	}
	requestApprovalSettings = @{
		isApprovalRequired = $true
		isApprovalRequiredForExtension = $false
		isRequestorJustificationRequired = $true
		approvalMode = "Serial"
		approvalStages = @(
			@{
				approvalStageTimeOutInDays = 14
				isApproverJustificationRequired = $true
				isEscalationEnabled = $true
				escalationTimeInMinutes = 11520
				primaryApprovers = @(
					@{
						"@odata.type" = "#microsoft.graph.groupMembers"
						isBackup = $true
						id = "string (identifier)"
						description = "group for users from connected organizations which have no external sponsor"
					}
					@{
						"@odata.type" = "#microsoft.graph.externalSponsors"
						isBackup = $false
					}
				)
				escalationApprovers = @(
					@{
						"@odata.type" = "#microsoft.graph.singleUser"
						isBackup = $true
						id = "string (identifier)"
						description = "user if the external sponsor does not respond"
					}
				)
			}
			@{
				approvalStageTimeOutInDays = 14
				isApproverJustificationRequired = $true
				isEscalationEnabled = $true
				escalationTimeInMinutes = 11520
				primaryApprovers = @(
					@{
						"@odata.type" = "#microsoft.graph.groupMembers"
						isBackup = $true
						id = "string (identifier)"
						description = "group for users from connected organizations which have no internal sponsor"
					}
					@{
						"@odata.type" = "#microsoft.graph.internalSponsors"
						isBackup = $false
					}
				)
				escalationApprovers = @(
					@{
						"@odata.type" = "#microsoft.graph.singleUser"
						isBackup = $true
						id = "string (identifier)"
						description = "user if the internal sponsor does not respond"
					}
				)
			}
		)
	}
	accessReviewSettings = @{
		isEnabled = $true
		recurrenceType = "quarterly"
		reviewerType = "Self"
		startDateTime = [System.DateTime]::Parse("2020-04-01T07:59:59.998Z")
		durationInDays = 25
		reviewers = @(
		)
	}
}

New-MgBetaEntitlementManagementAccessPackageAssignmentPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph_beta.generated.models.requestor_settings import RequestorSettings
from msgraph_beta.generated.models.user_set import UserSet
from msgraph_beta.generated.models.approval_settings import ApprovalSettings
from msgraph_beta.generated.models.approval_stage import ApprovalStage
from msgraph_beta.generated.models.group_members import GroupMembers
from msgraph_beta.generated.models.external_sponsors import ExternalSponsors
from msgraph_beta.generated.models.single_user import SingleUser
from msgraph_beta.generated.models.internal_sponsors import InternalSponsors
from msgraph_beta.generated.models.assignment_review_settings import AssignmentReviewSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	access_package_id = "string (identifier)",
	display_name = "Users from connected organizations can request",
	description = "Allow users from configured connected organizations to request and be approved by their sponsors",
	can_extend = False,
	duration_in_days = 365,
	expiration_date_time = None,
	requestor_settings = RequestorSettings(
		scope_type = "AllExistingConnectedOrganizationSubjects",
		accept_requests = True,
		allowed_requestors = [
		],
	),
	request_approval_settings = ApprovalSettings(
		is_approval_required = True,
		is_approval_required_for_extension = False,
		is_requestor_justification_required = True,
		approval_mode = "Serial",
		approval_stages = [
			ApprovalStage(
				approval_stage_time_out_in_days = 14,
				is_approver_justification_required = True,
				is_escalation_enabled = True,
				escalation_time_in_minutes = 11520,
				primary_approvers = [
					GroupMembers(
						odata_type = "#microsoft.graph.groupMembers",
						is_backup = True,
						id = "string (identifier)",
						description = "group for users from connected organizations which have no external sponsor",
					),
					ExternalSponsors(
						odata_type = "#microsoft.graph.externalSponsors",
						is_backup = False,
					),
				],
				escalation_approvers = [
					SingleUser(
						odata_type = "#microsoft.graph.singleUser",
						is_backup = True,
						id = "string (identifier)",
						description = "user if the external sponsor does not respond",
					),
				],
			),
			ApprovalStage(
				approval_stage_time_out_in_days = 14,
				is_approver_justification_required = True,
				is_escalation_enabled = True,
				escalation_time_in_minutes = 11520,
				primary_approvers = [
					GroupMembers(
						odata_type = "#microsoft.graph.groupMembers",
						is_backup = True,
						id = "string (identifier)",
						description = "group for users from connected organizations which have no internal sponsor",
					),
					InternalSponsors(
						odata_type = "#microsoft.graph.internalSponsors",
						is_backup = False,
					),
				],
				escalation_approvers = [
					SingleUser(
						odata_type = "#microsoft.graph.singleUser",
						is_backup = True,
						id = "string (identifier)",
						description = "user if the internal sponsor does not respond",
					),
				],
			),
		],
	),
	access_review_settings = AssignmentReviewSettings(
		is_enabled = True,
		recurrence_type = "quarterly",
		reviewer_type = "Self",
		start_date_time = "2020-04-01T07:59:59.998Z",
		duration_in_days = 25,
		reviewers = [
		],
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_policies.post(request_body)
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
  "id": "4c02f928-7752-49aa-8fc8-e286d973a965",
  "accessPackageId": "string (identifier)",
  "displayName": "Users from connected organizations can request",
  "description": "Allow users from configured connected organizations to request and be approved by their sponsors"
}
```

### Example 3: Create assignment policy with questions

Questions configured in an assignment policy will be asked to requestors in scope of the policy. Their answers will be shown to their approvers. Question IDs are read-only and are included in the response by default.

#### Request

The following example shows a request to create an access package assignment policy.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies
Content-type: application/json

{
    "accessPackageId": "b2eba9a1-b357-42ee-83a8-336522ed6cbf",
    "displayName": "Users from connected organizations can request",
    "description": "Allow users from configured connected organizations to request and be approved by their sponsors",
    "canExtend": false,
    "durationInDays": 365,
    "expirationDateTime": null,
    "requestorSettings": {
        "scopeType": "AllExistingConnectedOrganizationSubjects",
        "acceptRequests": true
    },
    "requestApprovalSettings": {
        "isApprovalRequired": true,
        "isApprovalRequiredForExtension": false,
        "isRequestorJustificationRequired": true,
        "approvalMode": "SingleStage",
        "approvalStages": [{
                "approvalStageTimeOutInDays": 14,
                "isApproverJustificationRequired": true,
                "isEscalationEnabled": false,
                "escalationTimeInMinutes": 11520,
                "primaryApprovers": [{
                        "@odata.type": "#microsoft.graph.groupMembers",
                        "isBackup": true,
                        "id": "d2dcb9a1-a445-42ee-83a8-476522ed6cbf",
                        "description": "group for users from connected organizations which have no external sponsor"
                    },
                    {
                        "@odata.type": "#microsoft.graph.externalSponsors",
                        "isBackup": false
                    }
                ]
            }
        ]
    },
    "questions": [{
        "isRequired": false,
        "text": {
            "defaultText": "what state are you from?",
            "localizedTexts": [{
                "text": "¿De qué estado eres?",
                "languageCode": "es"
            }]
        },
        "@odata.type": "#microsoft.graph.accessPackageMultipleChoiceQuestion",
        "choices": [{
            "actualValue": "AZ",
            "displayValue": {
                "localizedTexts": [{
                    "text": "Arizona",
                    "languageCode": "es"
                }]
            }
        }, {
            "actualValue": "CA",
            "displayValue": {
                "localizedTexts": [{
                    "text": "California",
                    "languageCode": "es"
                }]
            }
        }, {
            "actualValue": "OH",
            "displayValue": {
                "localizedTexts": [{
                    "text": "Ohio",
                    "languageCode": "es"
                }]
            }
        }],
        "allowsMultipleSelection": false
    }, {
        "isRequired": false,
        "text": {
            "defaultText": "Who is your manager?",
            "localizedTexts": [{
                "text": "por qué necesita acceso a este paquete",
                "languageCode": "es"
            }]
        },
        "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
        "isSingleLineQuestion": false
    }]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageAssignmentPolicy
{
	AccessPackageId = "b2eba9a1-b357-42ee-83a8-336522ed6cbf",
	DisplayName = "Users from connected organizations can request",
	Description = "Allow users from configured connected organizations to request and be approved by their sponsors",
	CanExtend = false,
	DurationInDays = 365,
	ExpirationDateTime = null,
	RequestorSettings = new RequestorSettings
	{
		ScopeType = "AllExistingConnectedOrganizationSubjects",
		AcceptRequests = true,
	},
	RequestApprovalSettings = new ApprovalSettings
	{
		IsApprovalRequired = true,
		IsApprovalRequiredForExtension = false,
		IsRequestorJustificationRequired = true,
		ApprovalMode = "SingleStage",
		ApprovalStages = new List<ApprovalStage>
		{
			new ApprovalStage
			{
				ApprovalStageTimeOutInDays = 14,
				IsApproverJustificationRequired = true,
				IsEscalationEnabled = false,
				EscalationTimeInMinutes = 11520,
				PrimaryApprovers = new List<UserSet>
				{
					new GroupMembers
					{
						OdataType = "#microsoft.graph.groupMembers",
						IsBackup = true,
						Id = "d2dcb9a1-a445-42ee-83a8-476522ed6cbf",
						Description = "group for users from connected organizations which have no external sponsor",
					},
					new ExternalSponsors
					{
						OdataType = "#microsoft.graph.externalSponsors",
						IsBackup = false,
					},
				},
			},
		},
	},
	Questions = new List<AccessPackageQuestion>
	{
		new AccessPackageMultipleChoiceQuestion
		{
			IsRequired = false,
			Text = new AccessPackageLocalizedContent
			{
				DefaultText = "what state are you from?",
				LocalizedTexts = new List<AccessPackageLocalizedText>
				{
					new AccessPackageLocalizedText
					{
						Text = "¿De qué estado eres?",
						LanguageCode = "es",
					},
				},
			},
			OdataType = "#microsoft.graph.accessPackageMultipleChoiceQuestion",
			Choices = new List<AccessPackageAnswerChoice>
			{
				new AccessPackageAnswerChoice
				{
					ActualValue = "AZ",
					DisplayValue = new AccessPackageLocalizedContent
					{
						LocalizedTexts = new List<AccessPackageLocalizedText>
						{
							new AccessPackageLocalizedText
							{
								Text = "Arizona",
								LanguageCode = "es",
							},
						},
					},
				},
				new AccessPackageAnswerChoice
				{
					ActualValue = "CA",
					DisplayValue = new AccessPackageLocalizedContent
					{
						LocalizedTexts = new List<AccessPackageLocalizedText>
						{
							new AccessPackageLocalizedText
							{
								Text = "California",
								LanguageCode = "es",
							},
						},
					},
				},
				new AccessPackageAnswerChoice
				{
					ActualValue = "OH",
					DisplayValue = new AccessPackageLocalizedContent
					{
						LocalizedTexts = new List<AccessPackageLocalizedText>
						{
							new AccessPackageLocalizedText
							{
								Text = "Ohio",
								LanguageCode = "es",
							},
						},
					},
				},
			},
			AllowsMultipleSelection = false,
		},
		new AccessPackageTextInputQuestion
		{
			IsRequired = false,
			Text = new AccessPackageLocalizedContent
			{
				DefaultText = "Who is your manager?",
				LocalizedTexts = new List<AccessPackageLocalizedText>
				{
					new AccessPackageLocalizedText
					{
						Text = "por qué necesita acceso a este paquete",
						LanguageCode = "es",
					},
				},
			},
			OdataType = "#microsoft.graph.accessPackageTextInputQuestion",
			IsSingleLineQuestion = false,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
accessPackageId := "b2eba9a1-b357-42ee-83a8-336522ed6cbf"
requestBody.SetAccessPackageId(&accessPackageId) 
displayName := "Users from connected organizations can request"
requestBody.SetDisplayName(&displayName) 
description := "Allow users from configured connected organizations to request and be approved by their sponsors"
requestBody.SetDescription(&description) 
canExtend := false
requestBody.SetCanExtend(&canExtend) 
durationInDays := int32(365)
requestBody.SetDurationInDays(&durationInDays) 
expirationDateTime := null
requestBody.SetExpirationDateTime(&expirationDateTime) 
requestorSettings := graphmodels.NewRequestorSettings()
scopeType := "AllExistingConnectedOrganizationSubjects"
requestorSettings.SetScopeType(&scopeType) 
acceptRequests := true
requestorSettings.SetAcceptRequests(&acceptRequests) 
requestBody.SetRequestorSettings(requestorSettings)
requestApprovalSettings := graphmodels.NewApprovalSettings()
isApprovalRequired := true
requestApprovalSettings.SetIsApprovalRequired(&isApprovalRequired) 
isApprovalRequiredForExtension := false
requestApprovalSettings.SetIsApprovalRequiredForExtension(&isApprovalRequiredForExtension) 
isRequestorJustificationRequired := true
requestApprovalSettings.SetIsRequestorJustificationRequired(&isRequestorJustificationRequired) 
approvalMode := "SingleStage"
requestApprovalSettings.SetApprovalMode(&approvalMode) 


approvalStage := graphmodels.NewApprovalStage()
approvalStageTimeOutInDays := int32(14)
approvalStage.SetApprovalStageTimeOutInDays(&approvalStageTimeOutInDays) 
isApproverJustificationRequired := true
approvalStage.SetIsApproverJustificationRequired(&isApproverJustificationRequired) 
isEscalationEnabled := false
approvalStage.SetIsEscalationEnabled(&isEscalationEnabled) 
escalationTimeInMinutes := int32(11520)
approvalStage.SetEscalationTimeInMinutes(&escalationTimeInMinutes) 


userSet := graphmodels.NewGroupMembers()
isBackup := true
userSet.SetIsBackup(&isBackup) 
id := "d2dcb9a1-a445-42ee-83a8-476522ed6cbf"
userSet.SetId(&id) 
description := "group for users from connected organizations which have no external sponsor"
userSet.SetDescription(&description) 
userSet1 := graphmodels.NewExternalSponsors()
isBackup := false
userSet1.SetIsBackup(&isBackup) 

primaryApprovers := []graphmodels.UserSetable {
	userSet,
	userSet1,
}
approvalStage.SetPrimaryApprovers(primaryApprovers)

approvalStages := []graphmodels.ApprovalStageable {
	approvalStage,
}
requestApprovalSettings.SetApprovalStages(approvalStages)
requestBody.SetRequestApprovalSettings(requestApprovalSettings)


accessPackageQuestion := graphmodels.NewAccessPackageMultipleChoiceQuestion()
isRequired := false
accessPackageQuestion.SetIsRequired(&isRequired) 
text := graphmodels.NewAccessPackageLocalizedContent()
defaultText := "what state are you from?"
text.SetDefaultText(&defaultText) 


accessPackageLocalizedText := graphmodels.NewAccessPackageLocalizedText()
text := "¿De qué estado eres?"
accessPackageLocalizedText.SetText(&text) 
languageCode := "es"
accessPackageLocalizedText.SetLanguageCode(&languageCode) 

localizedTexts := []graphmodels.AccessPackageLocalizedTextable {
	accessPackageLocalizedText,
}
text.SetLocalizedTexts(localizedTexts)
accessPackageQuestion.SetText(text)


accessPackageAnswerChoice := graphmodels.NewAccessPackageAnswerChoice()
actualValue := "AZ"
accessPackageAnswerChoice.SetActualValue(&actualValue) 
displayValue := graphmodels.NewAccessPackageLocalizedContent()


accessPackageLocalizedText := graphmodels.NewAccessPackageLocalizedText()
text := "Arizona"
accessPackageLocalizedText.SetText(&text) 
languageCode := "es"
accessPackageLocalizedText.SetLanguageCode(&languageCode) 

localizedTexts := []graphmodels.AccessPackageLocalizedTextable {
	accessPackageLocalizedText,
}
displayValue.SetLocalizedTexts(localizedTexts)
accessPackageAnswerChoice.SetDisplayValue(displayValue)
accessPackageAnswerChoice1 := graphmodels.NewAccessPackageAnswerChoice()
actualValue := "CA"
accessPackageAnswerChoice1.SetActualValue(&actualValue) 
displayValue := graphmodels.NewAccessPackageLocalizedContent()


accessPackageLocalizedText := graphmodels.NewAccessPackageLocalizedText()
text := "California"
accessPackageLocalizedText.SetText(&text) 
languageCode := "es"
accessPackageLocalizedText.SetLanguageCode(&languageCode) 

localizedTexts := []graphmodels.AccessPackageLocalizedTextable {
	accessPackageLocalizedText,
}
displayValue.SetLocalizedTexts(localizedTexts)
accessPackageAnswerChoice1.SetDisplayValue(displayValue)
accessPackageAnswerChoice2 := graphmodels.NewAccessPackageAnswerChoice()
actualValue := "OH"
accessPackageAnswerChoice2.SetActualValue(&actualValue) 
displayValue := graphmodels.NewAccessPackageLocalizedContent()


accessPackageLocalizedText := graphmodels.NewAccessPackageLocalizedText()
text := "Ohio"
accessPackageLocalizedText.SetText(&text) 
languageCode := "es"
accessPackageLocalizedText.SetLanguageCode(&languageCode) 

localizedTexts := []graphmodels.AccessPackageLocalizedTextable {
	accessPackageLocalizedText,
}
displayValue.SetLocalizedTexts(localizedTexts)
accessPackageAnswerChoice2.SetDisplayValue(displayValue)

choices := []graphmodels.AccessPackageAnswerChoiceable {
	accessPackageAnswerChoice,
	accessPackageAnswerChoice1,
	accessPackageAnswerChoice2,
}
accessPackageQuestion.SetChoices(choices)
allowsMultipleSelection := false
accessPackageQuestion.SetAllowsMultipleSelection(&allowsMultipleSelection) 
accessPackageQuestion1 := graphmodels.NewAccessPackageTextInputQuestion()
isRequired := false
accessPackageQuestion1.SetIsRequired(&isRequired) 
text := graphmodels.NewAccessPackageLocalizedContent()
defaultText := "Who is your manager?"
text.SetDefaultText(&defaultText) 


accessPackageLocalizedText := graphmodels.NewAccessPackageLocalizedText()
text := "por qué necesita acceso a este paquete"
accessPackageLocalizedText.SetText(&text) 
languageCode := "es"
accessPackageLocalizedText.SetLanguageCode(&languageCode) 

localizedTexts := []graphmodels.AccessPackageLocalizedTextable {
	accessPackageLocalizedText,
}
text.SetLocalizedTexts(localizedTexts)
accessPackageQuestion1.SetText(text)
isSingleLineQuestion := false
accessPackageQuestion1.SetIsSingleLineQuestion(&isSingleLineQuestion) 

questions := []graphmodels.AccessPackageQuestionable {
	accessPackageQuestion,
	accessPackageQuestion1,
}
requestBody.SetQuestions(questions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setAccessPackageId("b2eba9a1-b357-42ee-83a8-336522ed6cbf");
accessPackageAssignmentPolicy.setDisplayName("Users from connected organizations can request");
accessPackageAssignmentPolicy.setDescription("Allow users from configured connected organizations to request and be approved by their sponsors");
accessPackageAssignmentPolicy.setCanExtend(false);
accessPackageAssignmentPolicy.setDurationInDays(365);
accessPackageAssignmentPolicy.setExpirationDateTime(null);
RequestorSettings requestorSettings = new RequestorSettings();
requestorSettings.setScopeType("AllExistingConnectedOrganizationSubjects");
requestorSettings.setAcceptRequests(true);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
ApprovalSettings requestApprovalSettings = new ApprovalSettings();
requestApprovalSettings.setIsApprovalRequired(true);
requestApprovalSettings.setIsApprovalRequiredForExtension(false);
requestApprovalSettings.setIsRequestorJustificationRequired(true);
requestApprovalSettings.setApprovalMode("SingleStage");
LinkedList<ApprovalStage> approvalStages = new LinkedList<ApprovalStage>();
ApprovalStage approvalStage = new ApprovalStage();
approvalStage.setApprovalStageTimeOutInDays(14);
approvalStage.setIsApproverJustificationRequired(true);
approvalStage.setIsEscalationEnabled(false);
approvalStage.setEscalationTimeInMinutes(11520);
LinkedList<UserSet> primaryApprovers = new LinkedList<UserSet>();
GroupMembers userSet = new GroupMembers();
userSet.setOdataType("#microsoft.graph.groupMembers");
userSet.setIsBackup(true);
userSet.setId("d2dcb9a1-a445-42ee-83a8-476522ed6cbf");
userSet.setDescription("group for users from connected organizations which have no external sponsor");
primaryApprovers.add(userSet);
ExternalSponsors userSet1 = new ExternalSponsors();
userSet1.setOdataType("#microsoft.graph.externalSponsors");
userSet1.setIsBackup(false);
primaryApprovers.add(userSet1);
approvalStage.setPrimaryApprovers(primaryApprovers);
approvalStages.add(approvalStage);
requestApprovalSettings.setApprovalStages(approvalStages);
accessPackageAssignmentPolicy.setRequestApprovalSettings(requestApprovalSettings);
LinkedList<AccessPackageQuestion> questions = new LinkedList<AccessPackageQuestion>();
AccessPackageMultipleChoiceQuestion accessPackageQuestion = new AccessPackageMultipleChoiceQuestion();
accessPackageQuestion.setIsRequired(false);
AccessPackageLocalizedContent text = new AccessPackageLocalizedContent();
text.setDefaultText("what state are you from?");
LinkedList<AccessPackageLocalizedText> localizedTexts = new LinkedList<AccessPackageLocalizedText>();
AccessPackageLocalizedText accessPackageLocalizedText = new AccessPackageLocalizedText();
accessPackageLocalizedText.setText("¿De qué estado eres?");
accessPackageLocalizedText.setLanguageCode("es");
localizedTexts.add(accessPackageLocalizedText);
text.setLocalizedTexts(localizedTexts);
accessPackageQuestion.setText(text);
accessPackageQuestion.setOdataType("#microsoft.graph.accessPackageMultipleChoiceQuestion");
LinkedList<AccessPackageAnswerChoice> choices = new LinkedList<AccessPackageAnswerChoice>();
AccessPackageAnswerChoice accessPackageAnswerChoice = new AccessPackageAnswerChoice();
accessPackageAnswerChoice.setActualValue("AZ");
AccessPackageLocalizedContent displayValue = new AccessPackageLocalizedContent();
LinkedList<AccessPackageLocalizedText> localizedTexts1 = new LinkedList<AccessPackageLocalizedText>();
AccessPackageLocalizedText accessPackageLocalizedText1 = new AccessPackageLocalizedText();
accessPackageLocalizedText1.setText("Arizona");
accessPackageLocalizedText1.setLanguageCode("es");
localizedTexts1.add(accessPackageLocalizedText1);
displayValue.setLocalizedTexts(localizedTexts1);
accessPackageAnswerChoice.setDisplayValue(displayValue);
choices.add(accessPackageAnswerChoice);
AccessPackageAnswerChoice accessPackageAnswerChoice1 = new AccessPackageAnswerChoice();
accessPackageAnswerChoice1.setActualValue("CA");
AccessPackageLocalizedContent displayValue1 = new AccessPackageLocalizedContent();
LinkedList<AccessPackageLocalizedText> localizedTexts2 = new LinkedList<AccessPackageLocalizedText>();
AccessPackageLocalizedText accessPackageLocalizedText2 = new AccessPackageLocalizedText();
accessPackageLocalizedText2.setText("California");
accessPackageLocalizedText2.setLanguageCode("es");
localizedTexts2.add(accessPackageLocalizedText2);
displayValue1.setLocalizedTexts(localizedTexts2);
accessPackageAnswerChoice1.setDisplayValue(displayValue1);
choices.add(accessPackageAnswerChoice1);
AccessPackageAnswerChoice accessPackageAnswerChoice2 = new AccessPackageAnswerChoice();
accessPackageAnswerChoice2.setActualValue("OH");
AccessPackageLocalizedContent displayValue2 = new AccessPackageLocalizedContent();
LinkedList<AccessPackageLocalizedText> localizedTexts3 = new LinkedList<AccessPackageLocalizedText>();
AccessPackageLocalizedText accessPackageLocalizedText3 = new AccessPackageLocalizedText();
accessPackageLocalizedText3.setText("Ohio");
accessPackageLocalizedText3.setLanguageCode("es");
localizedTexts3.add(accessPackageLocalizedText3);
displayValue2.setLocalizedTexts(localizedTexts3);
accessPackageAnswerChoice2.setDisplayValue(displayValue2);
choices.add(accessPackageAnswerChoice2);
accessPackageQuestion.setChoices(choices);
accessPackageQuestion.setAllowsMultipleSelection(false);
questions.add(accessPackageQuestion);
AccessPackageTextInputQuestion accessPackageQuestion1 = new AccessPackageTextInputQuestion();
accessPackageQuestion1.setIsRequired(false);
AccessPackageLocalizedContent text5 = new AccessPackageLocalizedContent();
text5.setDefaultText("Who is your manager?");
LinkedList<AccessPackageLocalizedText> localizedTexts4 = new LinkedList<AccessPackageLocalizedText>();
AccessPackageLocalizedText accessPackageLocalizedText4 = new AccessPackageLocalizedText();
accessPackageLocalizedText4.setText("por qué necesita acceso a este paquete");
accessPackageLocalizedText4.setLanguageCode("es");
localizedTexts4.add(accessPackageLocalizedText4);
text5.setLocalizedTexts(localizedTexts4);
accessPackageQuestion1.setText(text5);
accessPackageQuestion1.setOdataType("#microsoft.graph.accessPackageTextInputQuestion");
accessPackageQuestion1.setIsSingleLineQuestion(false);
questions.add(accessPackageQuestion1);
accessPackageAssignmentPolicy.setQuestions(questions);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentPolicies().post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
    accessPackageId: 'b2eba9a1-b357-42ee-83a8-336522ed6cbf',
    displayName: 'Users from connected organizations can request',
    description: 'Allow users from configured connected organizations to request and be approved by their sponsors',
    canExtend: false,
    durationInDays: 365,
    expirationDateTime: null,
    requestorSettings: {
        scopeType: 'AllExistingConnectedOrganizationSubjects',
        acceptRequests: true
    },
    requestApprovalSettings: {
        isApprovalRequired: true,
        isApprovalRequiredForExtension: false,
        isRequestorJustificationRequired: true,
        approvalMode: 'SingleStage',
        approvalStages: [{
                approvalStageTimeOutInDays: 14,
                isApproverJustificationRequired: true,
                isEscalationEnabled: false,
                escalationTimeInMinutes: 11520,
                primaryApprovers: [{
                        '@odata.type': '#microsoft.graph.groupMembers',
                        isBackup: true,
                        id: 'd2dcb9a1-a445-42ee-83a8-476522ed6cbf',
                        description: 'group for users from connected organizations which have no external sponsor'
                    },
                    {
                        '@odata.type': '#microsoft.graph.externalSponsors',
                        isBackup: false
                    }
                ]
            }
        ]
    },
    questions: [{
        isRequired: false,
        text: {
            defaultText: 'what state are you from?',
            localizedTexts: [{
                text: '¿De qué estado eres?',
                languageCode: 'es'
            }]
        },
        '@odata.type': '#microsoft.graph.accessPackageMultipleChoiceQuestion',
        choices: [{
            actualValue: 'AZ',
            displayValue: {
                localizedTexts: [{
                    text: 'Arizona',
                    languageCode: 'es'
                }]
            }
        }, {
            actualValue: 'CA',
            displayValue: {
                localizedTexts: [{
                    text: 'California',
                    languageCode: 'es'
                }]
            }
        }, {
            actualValue: 'OH',
            displayValue: {
                localizedTexts: [{
                    text: 'Ohio',
                    languageCode: 'es'
                }]
            }
        }],
        allowsMultipleSelection: false
    }, {
        isRequired: false,
        text: {
            defaultText: 'Who is your manager?',
            localizedTexts: [{
                text: 'por qué necesita acceso a este paquete',
                languageCode: 'es'
            }]
        },
        '@odata.type': '#microsoft.graph.accessPackageTextInputQuestion',
        isSingleLineQuestion: false
    }]
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies')
	.version('beta')
	.post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Beta\Generated\Models\RequestorSettings;
use Microsoft\Graph\Beta\Generated\Models\ApprovalSettings;
use Microsoft\Graph\Beta\Generated\Models\ApprovalStage;
use Microsoft\Graph\Beta\Generated\Models\UserSet;
use Microsoft\Graph\Beta\Generated\Models\GroupMembers;
use Microsoft\Graph\Beta\Generated\Models\ExternalSponsors;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageQuestion;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageMultipleChoiceQuestion;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageLocalizedContent;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageLocalizedText;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAnswerChoice;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageTextInputQuestion;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setAccessPackageId('b2eba9a1-b357-42ee-83a8-336522ed6cbf');
$requestBody->setDisplayName('Users from connected organizations can request');
$requestBody->setDescription('Allow users from configured connected organizations to request and be approved by their sponsors');
$requestBody->setCanExtend(false);
$requestBody->setDurationInDays(365);
$requestBody->setExpirationDateTime(null);
$requestorSettings = new RequestorSettings();
$requestorSettings->setScopeType('AllExistingConnectedOrganizationSubjects');
$requestorSettings->setAcceptRequests(true);
$requestBody->setRequestorSettings($requestorSettings);
$requestApprovalSettings = new ApprovalSettings();
$requestApprovalSettings->setIsApprovalRequired(true);
$requestApprovalSettings->setIsApprovalRequiredForExtension(false);
$requestApprovalSettings->setIsRequestorJustificationRequired(true);
$requestApprovalSettings->setApprovalMode('SingleStage');
$approvalStagesApprovalStage1 = new ApprovalStage();
$approvalStagesApprovalStage1->setApprovalStageTimeOutInDays(14);
$approvalStagesApprovalStage1->setIsApproverJustificationRequired(true);
$approvalStagesApprovalStage1->setIsEscalationEnabled(false);
$approvalStagesApprovalStage1->setEscalationTimeInMinutes(11520);
$primaryApproversUserSet1 = new GroupMembers();
$primaryApproversUserSet1->setOdataType('#microsoft.graph.groupMembers');
$primaryApproversUserSet1->setIsBackup(true);
$primaryApproversUserSet1->setId('d2dcb9a1-a445-42ee-83a8-476522ed6cbf');
$primaryApproversUserSet1->setDescription('group for users from connected organizations which have no external sponsor');
$primaryApproversArray []= $primaryApproversUserSet1;
$primaryApproversUserSet2 = new ExternalSponsors();
$primaryApproversUserSet2->setOdataType('#microsoft.graph.externalSponsors');
$primaryApproversUserSet2->setIsBackup(false);
$primaryApproversArray []= $primaryApproversUserSet2;
$approvalStagesApprovalStage1->setPrimaryApprovers($primaryApproversArray);

$approvalStagesArray []= $approvalStagesApprovalStage1;
$requestApprovalSettings->setApprovalStages($approvalStagesArray);

$requestBody->setRequestApprovalSettings($requestApprovalSettings);
$questionsAccessPackageQuestion1 = new AccessPackageMultipleChoiceQuestion();
$questionsAccessPackageQuestion1->setIsRequired(false);
$questionsAccessPackageQuestion1Text = new AccessPackageLocalizedContent();
$questionsAccessPackageQuestion1Text->setDefaultText('what state are you from?');
$localizedTextsAccessPackageLocalizedText1 = new AccessPackageLocalizedText();
$localizedTextsAccessPackageLocalizedText1->setText('¿De qué estado eres?');
$localizedTextsAccessPackageLocalizedText1->setLanguageCode('es');
$localizedTextsArray []= $localizedTextsAccessPackageLocalizedText1;
$questionsAccessPackageQuestion1Text->setLocalizedTexts($localizedTextsArray);

$questionsAccessPackageQuestion1->setText($questionsAccessPackageQuestion1Text);
$questionsAccessPackageQuestion1->setOdataType('#microsoft.graph.accessPackageMultipleChoiceQuestion');
$choicesAccessPackageAnswerChoice1 = new AccessPackageAnswerChoice();
$choicesAccessPackageAnswerChoice1->setActualValue('AZ');
$choicesAccessPackageAnswerChoice1DisplayValue = new AccessPackageLocalizedContent();
$localizedTextsAccessPackageLocalizedText1 = new AccessPackageLocalizedText();
$localizedTextsAccessPackageLocalizedText1->setText('Arizona');
$localizedTextsAccessPackageLocalizedText1->setLanguageCode('es');
$localizedTextsArray []= $localizedTextsAccessPackageLocalizedText1;
$choicesAccessPackageAnswerChoice1DisplayValue->setLocalizedTexts($localizedTextsArray);

$choicesAccessPackageAnswerChoice1->setDisplayValue($choicesAccessPackageAnswerChoice1DisplayValue);
$choicesArray []= $choicesAccessPackageAnswerChoice1;
$choicesAccessPackageAnswerChoice2 = new AccessPackageAnswerChoice();
$choicesAccessPackageAnswerChoice2->setActualValue('CA');
$choicesAccessPackageAnswerChoice2DisplayValue = new AccessPackageLocalizedContent();
$localizedTextsAccessPackageLocalizedText1 = new AccessPackageLocalizedText();
$localizedTextsAccessPackageLocalizedText1->setText('California');
$localizedTextsAccessPackageLocalizedText1->setLanguageCode('es');
$localizedTextsArray []= $localizedTextsAccessPackageLocalizedText1;
$choicesAccessPackageAnswerChoice2DisplayValue->setLocalizedTexts($localizedTextsArray);

$choicesAccessPackageAnswerChoice2->setDisplayValue($choicesAccessPackageAnswerChoice2DisplayValue);
$choicesArray []= $choicesAccessPackageAnswerChoice2;
$choicesAccessPackageAnswerChoice3 = new AccessPackageAnswerChoice();
$choicesAccessPackageAnswerChoice3->setActualValue('OH');
$choicesAccessPackageAnswerChoice3DisplayValue = new AccessPackageLocalizedContent();
$localizedTextsAccessPackageLocalizedText1 = new AccessPackageLocalizedText();
$localizedTextsAccessPackageLocalizedText1->setText('Ohio');
$localizedTextsAccessPackageLocalizedText1->setLanguageCode('es');
$localizedTextsArray []= $localizedTextsAccessPackageLocalizedText1;
$choicesAccessPackageAnswerChoice3DisplayValue->setLocalizedTexts($localizedTextsArray);

$choicesAccessPackageAnswerChoice3->setDisplayValue($choicesAccessPackageAnswerChoice3DisplayValue);
$choicesArray []= $choicesAccessPackageAnswerChoice3;
$questionsAccessPackageQuestion1->setChoices($choicesArray);

$questionsAccessPackageQuestion1->setAllowsMultipleSelection(false);
$questionsArray []= $questionsAccessPackageQuestion1;
$questionsAccessPackageQuestion2 = new AccessPackageTextInputQuestion();
$questionsAccessPackageQuestion2->setIsRequired(false);
$questionsAccessPackageQuestion2Text = new AccessPackageLocalizedContent();
$questionsAccessPackageQuestion2Text->setDefaultText('Who is your manager?');
$localizedTextsAccessPackageLocalizedText1 = new AccessPackageLocalizedText();
$localizedTextsAccessPackageLocalizedText1->setText('por qué necesita acceso a este paquete');
$localizedTextsAccessPackageLocalizedText1->setLanguageCode('es');
$localizedTextsArray []= $localizedTextsAccessPackageLocalizedText1;
$questionsAccessPackageQuestion2Text->setLocalizedTexts($localizedTextsArray);

$questionsAccessPackageQuestion2->setText($questionsAccessPackageQuestion2Text);
$questionsAccessPackageQuestion2->setOdataType('#microsoft.graph.accessPackageTextInputQuestion');
$questionsAccessPackageQuestion2->setIsSingleLineQuestion(false);
$questionsArray []= $questionsAccessPackageQuestion2;
$requestBody->setQuestions($questionsArray);


$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	accessPackageId = "b2eba9a1-b357-42ee-83a8-336522ed6cbf"
	displayName = "Users from connected organizations can request"
	description = "Allow users from configured connected organizations to request and be approved by their sponsors"
	canExtend = $false
	durationInDays = 365
	expirationDateTime = $null
	requestorSettings = @{
		scopeType = "AllExistingConnectedOrganizationSubjects"
		acceptRequests = $true
	}
	requestApprovalSettings = @{
		isApprovalRequired = $true
		isApprovalRequiredForExtension = $false
		isRequestorJustificationRequired = $true
		approvalMode = "SingleStage"
		approvalStages = @(
			@{
				approvalStageTimeOutInDays = 14
				isApproverJustificationRequired = $true
				isEscalationEnabled = $false
				escalationTimeInMinutes = 11520
				primaryApprovers = @(
					@{
						"@odata.type" = "#microsoft.graph.groupMembers"
						isBackup = $true
						id = "d2dcb9a1-a445-42ee-83a8-476522ed6cbf"
						description = "group for users from connected organizations which have no external sponsor"
					}
					@{
						"@odata.type" = "#microsoft.graph.externalSponsors"
						isBackup = $false
					}
				)
			}
		)
	}
	questions = @(
		@{
			isRequired = $false
			text = @{
				defaultText = "what state are you from?"
				localizedTexts = @(
					@{
						text = "¿De qué estado eres?"
						languageCode = "es"
					}
				)
			}
			"@odata.type" = "#microsoft.graph.accessPackageMultipleChoiceQuestion"
			choices = @(
				@{
					actualValue = "AZ"
					displayValue = @{
						localizedTexts = @(
							@{
								text = "Arizona"
								languageCode = "es"
							}
						)
					}
				}
				@{
					actualValue = "CA"
					displayValue = @{
						localizedTexts = @(
							@{
								text = "California"
								languageCode = "es"
							}
						)
					}
				}
				@{
					actualValue = "OH"
					displayValue = @{
						localizedTexts = @(
							@{
								text = "Ohio"
								languageCode = "es"
							}
						)
					}
				}
			)
			allowsMultipleSelection = $false
		}
		@{
			isRequired = $false
			text = @{
				defaultText = "Who is your manager?"
				localizedTexts = @(
					@{
						text = "por qué necesita acceso a este paquete"
						languageCode = "es"
					}
				)
			}
			"@odata.type" = "#microsoft.graph.accessPackageTextInputQuestion"
			isSingleLineQuestion = $false
		}
	)
}

New-MgBetaEntitlementManagementAccessPackageAssignmentPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph_beta.generated.models.requestor_settings import RequestorSettings
from msgraph_beta.generated.models.approval_settings import ApprovalSettings
from msgraph_beta.generated.models.approval_stage import ApprovalStage
from msgraph_beta.generated.models.user_set import UserSet
from msgraph_beta.generated.models.group_members import GroupMembers
from msgraph_beta.generated.models.external_sponsors import ExternalSponsors
from msgraph_beta.generated.models.access_package_question import AccessPackageQuestion
from msgraph_beta.generated.models.access_package_multiple_choice_question import AccessPackageMultipleChoiceQuestion
from msgraph_beta.generated.models.access_package_localized_content import AccessPackageLocalizedContent
from msgraph_beta.generated.models.access_package_localized_text import AccessPackageLocalizedText
from msgraph_beta.generated.models.access_package_answer_choice import AccessPackageAnswerChoice
from msgraph_beta.generated.models.access_package_text_input_question import AccessPackageTextInputQuestion
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	access_package_id = "b2eba9a1-b357-42ee-83a8-336522ed6cbf",
	display_name = "Users from connected organizations can request",
	description = "Allow users from configured connected organizations to request and be approved by their sponsors",
	can_extend = False,
	duration_in_days = 365,
	expiration_date_time = None,
	requestor_settings = RequestorSettings(
		scope_type = "AllExistingConnectedOrganizationSubjects",
		accept_requests = True,
	),
	request_approval_settings = ApprovalSettings(
		is_approval_required = True,
		is_approval_required_for_extension = False,
		is_requestor_justification_required = True,
		approval_mode = "SingleStage",
		approval_stages = [
			ApprovalStage(
				approval_stage_time_out_in_days = 14,
				is_approver_justification_required = True,
				is_escalation_enabled = False,
				escalation_time_in_minutes = 11520,
				primary_approvers = [
					GroupMembers(
						odata_type = "#microsoft.graph.groupMembers",
						is_backup = True,
						id = "d2dcb9a1-a445-42ee-83a8-476522ed6cbf",
						description = "group for users from connected organizations which have no external sponsor",
					),
					ExternalSponsors(
						odata_type = "#microsoft.graph.externalSponsors",
						is_backup = False,
					),
				],
			),
		],
	),
	questions = [
		AccessPackageMultipleChoiceQuestion(
			is_required = False,
			text = AccessPackageLocalizedContent(
				default_text = "what state are you from?",
				localized_texts = [
					AccessPackageLocalizedText(
						text = "¿De qué estado eres?",
						language_code = "es",
					),
				],
			),
			odata_type = "#microsoft.graph.accessPackageMultipleChoiceQuestion",
			choices = [
				AccessPackageAnswerChoice(
					actual_value = "AZ",
					display_value = AccessPackageLocalizedContent(
						localized_texts = [
							AccessPackageLocalizedText(
								text = "Arizona",
								language_code = "es",
							),
						],
					),
				),
				AccessPackageAnswerChoice(
					actual_value = "CA",
					display_value = AccessPackageLocalizedContent(
						localized_texts = [
							AccessPackageLocalizedText(
								text = "California",
								language_code = "es",
							),
						],
					),
				),
				AccessPackageAnswerChoice(
					actual_value = "OH",
					display_value = AccessPackageLocalizedContent(
						localized_texts = [
							AccessPackageLocalizedText(
								text = "Ohio",
								language_code = "es",
							),
						],
					),
				),
			],
			allows_multiple_selection = False,
		),
		AccessPackageTextInputQuestion(
			is_required = False,
			text = AccessPackageLocalizedContent(
				default_text = "Who is your manager?",
				localized_texts = [
					AccessPackageLocalizedText(
						text = "por qué necesita acceso a este paquete",
						language_code = "es",
					),
				],
			),
			odata_type = "#microsoft.graph.accessPackageTextInputQuestion",
			is_single_line_question = False,
		),
	],
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_policies.post(request_body)
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
  "id": "4c02f928-7752-49aa-8fc8-e286d973a965",
  "accessPackageId": "string (identifier)",
  "displayName": "Users from connected organizations can request",
  "description": "Allow users from configured connected organizations to request and be approved by their sponsors",
  "questions": [{
        "id" : "BD3F6B95-458D-4BC8-A9A6-8D4B29F64F3D",
        "isRequired": false,
        "text": {
            "defaultText": "what state are you from?",
            "localizedTexts": [{
                "text": "¿De qué estado eres?",
                "languageCode": "es"
            }]
        },
        "@odata.type": "#microsoft.graph.accessPackageMultipleChoiceQuestion",
        "choices": [{
            "actualValue": "AZ",
            "displayValue": {
                "localizedTexts": [{
                    "text": "Arizona?",
                    "languageCode": "es"
                }]
            }
        }, {
            "actualValue": "CA",
            "displayValue": {
                "localizedTexts": [{
                    "text": "California",
                    "languageCode": "es"
                }]
            }
        }, {
            "actualValue": "OH",
            "displayValue": {
                "localizedTexts": [{
                    "text": "Ohio",
                    "languageCode": "es"
                }]
            }
        }],
        "allowsMultipleSelection": false
    }, {
        "id" : "F652C13C-A660-4E4C-A1E0-CE9FEC6EE57A",
        "isRequired": false,
        "text": {
            "defaultText": "Who is your manager?",
            "localizedTexts": [{
                "text": "por qué necesita acceso a este paquete",
                "languageCode": "es"
            }]
        },
        "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
        "isSingleLineQuestion": false
    }]
}
```

### Example 4: Create a policy and specify the stages to trigger pre-defined custom workflow extensions

#### Request

In the following example, the pre-defined **customAccessPackageWorkflowExtension** object is triggered when an access package assigned request is created and when it's granted. The identifier provided within the **customExtension** field is the **customAccessPackageWorkflowExtension** object's ID.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies
Content-type: application/json

{
  "displayName": "extension-policy",
  "description": "test",
  "accessPackageId": "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
  "expiration": {
    "type": "afterDuration",
    "duration": "P365D"
  },
  "canExtend": false,
  "requestApprovalSettings": null,
  "requestorSettings": {
    "acceptRequests": true,
    "scopeType": "AllExistingDirectorySubjects",
    "allowedRequestors": [],
    "isOnBehalfAllowed": false
  },
  "accessReviewSettings": null,
  "questions": [],
  "customExtensionHandlers": [
    {
      "stage": "assignmentRequestCreated",
      "customExtension": {
        "id": "219f57b6-7983-45a1-be01-2c228b7a43f8"
      }
    },
    {
      "stage": "assignmentRequestGranted",
      "customExtension": {
        "id": "219f57b6-7983-45a1-be01-2c228b7a43f8"
      }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new AccessPackageAssignmentPolicy
{
	DisplayName = "extension-policy",
	Description = "test",
	AccessPackageId = "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
	CanExtend = false,
	RequestApprovalSettings = null,
	RequestorSettings = new RequestorSettings
	{
		AcceptRequests = true,
		ScopeType = "AllExistingDirectorySubjects",
		AllowedRequestors = new List<UserSet>
		{
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"isOnBehalfAllowed" , false
			},
		},
	},
	AccessReviewSettings = null,
	Questions = new List<AccessPackageQuestion>
	{
	},
	CustomExtensionHandlers = new List<CustomExtensionHandler>
	{
		new CustomExtensionHandler
		{
			Stage = AccessPackageCustomExtensionStage.AssignmentRequestCreated,
			CustomExtension = new CustomAccessPackageWorkflowExtension
			{
				Id = "219f57b6-7983-45a1-be01-2c228b7a43f8",
			},
		},
		new CustomExtensionHandler
		{
			Stage = AccessPackageCustomExtensionStage.AssignmentRequestGranted,
			CustomExtension = new CustomAccessPackageWorkflowExtension
			{
				Id = "219f57b6-7983-45a1-be01-2c228b7a43f8",
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"expiration" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"type", new UntypedString("afterDuration")
				},
				{
					"duration", new UntypedString("P365D")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
displayName := "extension-policy"
requestBody.SetDisplayName(&displayName) 
description := "test"
requestBody.SetDescription(&description) 
accessPackageId := "ba5807c7-2aa9-4c8a-907e-4a17ee587500"
requestBody.SetAccessPackageId(&accessPackageId) 
canExtend := false
requestBody.SetCanExtend(&canExtend) 
requestApprovalSettings := null
requestBody.SetRequestApprovalSettings(&requestApprovalSettings) 
requestorSettings := graphmodels.NewRequestorSettings()
acceptRequests := true
requestorSettings.SetAcceptRequests(&acceptRequests) 
scopeType := "AllExistingDirectorySubjects"
requestorSettings.SetScopeType(&scopeType) 
allowedRequestors := []graphmodels.UserSetable {

}
requestorSettings.SetAllowedRequestors(allowedRequestors)
additionalData := map[string]interface{}{
	isOnBehalfAllowed := false
requestorSettings.SetIsOnBehalfAllowed(&isOnBehalfAllowed) 
}
requestorSettings.SetAdditionalData(additionalData)
requestBody.SetRequestorSettings(requestorSettings)
accessReviewSettings := null
requestBody.SetAccessReviewSettings(&accessReviewSettings) 
questions := []graphmodels.AccessPackageQuestionable {

}
requestBody.SetQuestions(questions)


customExtensionHandler := graphmodels.NewCustomExtensionHandler()
stage := graphmodels.ASSIGNMENTREQUESTCREATED_ACCESSPACKAGECUSTOMEXTENSIONSTAGE 
customExtensionHandler.SetStage(&stage) 
customExtension := graphmodels.NewCustomAccessPackageWorkflowExtension()
id := "219f57b6-7983-45a1-be01-2c228b7a43f8"
customExtension.SetId(&id) 
customExtensionHandler.SetCustomExtension(customExtension)
customExtensionHandler1 := graphmodels.NewCustomExtensionHandler()
stage := graphmodels.ASSIGNMENTREQUESTGRANTED_ACCESSPACKAGECUSTOMEXTENSIONSTAGE 
customExtensionHandler1.SetStage(&stage) 
customExtension := graphmodels.NewCustomAccessPackageWorkflowExtension()
id := "219f57b6-7983-45a1-be01-2c228b7a43f8"
customExtension.SetId(&id) 
customExtensionHandler1.SetCustomExtension(customExtension)

customExtensionHandlers := []graphmodels.CustomExtensionHandlerable {
	customExtensionHandler,
	customExtensionHandler1,
}
requestBody.SetCustomExtensionHandlers(customExtensionHandlers)
additionalData := map[string]interface{}{
expiration := graph.New()
type := "afterDuration"
expiration.SetType(&type) 
duration := "P365D"
expiration.SetDuration(&duration) 
	requestBody.SetExpiration(expiration)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setDisplayName("extension-policy");
accessPackageAssignmentPolicy.setDescription("test");
accessPackageAssignmentPolicy.setAccessPackageId("ba5807c7-2aa9-4c8a-907e-4a17ee587500");
accessPackageAssignmentPolicy.setCanExtend(false);
accessPackageAssignmentPolicy.setRequestApprovalSettings(null);
RequestorSettings requestorSettings = new RequestorSettings();
requestorSettings.setAcceptRequests(true);
requestorSettings.setScopeType("AllExistingDirectorySubjects");
LinkedList<UserSet> allowedRequestors = new LinkedList<UserSet>();
requestorSettings.setAllowedRequestors(allowedRequestors);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("isOnBehalfAllowed", false);
requestorSettings.setAdditionalData(additionalData);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
accessPackageAssignmentPolicy.setAccessReviewSettings(null);
LinkedList<AccessPackageQuestion> questions = new LinkedList<AccessPackageQuestion>();
accessPackageAssignmentPolicy.setQuestions(questions);
LinkedList<CustomExtensionHandler> customExtensionHandlers = new LinkedList<CustomExtensionHandler>();
CustomExtensionHandler customExtensionHandler = new CustomExtensionHandler();
customExtensionHandler.setStage(AccessPackageCustomExtensionStage.AssignmentRequestCreated);
CustomAccessPackageWorkflowExtension customExtension = new CustomAccessPackageWorkflowExtension();
customExtension.setId("219f57b6-7983-45a1-be01-2c228b7a43f8");
customExtensionHandler.setCustomExtension(customExtension);
customExtensionHandlers.add(customExtensionHandler);
CustomExtensionHandler customExtensionHandler1 = new CustomExtensionHandler();
customExtensionHandler1.setStage(AccessPackageCustomExtensionStage.AssignmentRequestGranted);
CustomAccessPackageWorkflowExtension customExtension1 = new CustomAccessPackageWorkflowExtension();
customExtension1.setId("219f57b6-7983-45a1-be01-2c228b7a43f8");
customExtensionHandler1.setCustomExtension(customExtension1);
customExtensionHandlers.add(customExtensionHandler1);
accessPackageAssignmentPolicy.setCustomExtensionHandlers(customExtensionHandlers);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
 expiration = new ();
expiration.setType("afterDuration");
expiration.setDuration("P365D");
additionalData1.put("expiration", expiration);
accessPackageAssignmentPolicy.setAdditionalData(additionalData1);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentPolicies().post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
  displayName: 'extension-policy',
  description: 'test',
  accessPackageId: 'ba5807c7-2aa9-4c8a-907e-4a17ee587500',
  expiration: {
    type: 'afterDuration',
    duration: 'P365D'
  },
  canExtend: false,
  requestApprovalSettings: null,
  requestorSettings: {
    acceptRequests: true,
    scopeType: 'AllExistingDirectorySubjects',
    allowedRequestors: [],
    isOnBehalfAllowed: false
  },
  accessReviewSettings: null,
  questions: [],
  customExtensionHandlers: [
    {
      stage: 'assignmentRequestCreated',
      customExtension: {
        id: '219f57b6-7983-45a1-be01-2c228b7a43f8'
      }
    },
    {
      stage: 'assignmentRequestGranted',
      customExtension: {
        id: '219f57b6-7983-45a1-be01-2c228b7a43f8'
      }
    }
  ]
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies')
	.version('beta')
	.post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Beta\Generated\Models\RequestorSettings;
use Microsoft\Graph\Beta\Generated\Models\UserSet;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageQuestion;
use Microsoft\Graph\Beta\Generated\Models\CustomExtensionHandler;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageCustomExtensionStage;
use Microsoft\Graph\Beta\Generated\Models\CustomAccessPackageWorkflowExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setDisplayName('extension-policy');
$requestBody->setDescription('test');
$requestBody->setAccessPackageId('ba5807c7-2aa9-4c8a-907e-4a17ee587500');
$requestBody->setCanExtend(false);
$requestBody->setRequestApprovalSettings(null);
$requestorSettings = new RequestorSettings();
$requestorSettings->setAcceptRequests(true);
$requestorSettings->setScopeType('AllExistingDirectorySubjects');
$requestorSettings->setAllowedRequestors([	]);
$additionalData = [
	'isOnBehalfAllowed' => false,
];
$requestorSettings->setAdditionalData($additionalData);
$requestBody->setRequestorSettings($requestorSettings);
$requestBody->setAccessReviewSettings(null);
$requestBody->setQuestions([	]);
$customExtensionHandlersCustomExtensionHandler1 = new CustomExtensionHandler();
$customExtensionHandlersCustomExtensionHandler1->setStage(new AccessPackageCustomExtensionStage('assignmentRequestCreated'));
$customExtensionHandlersCustomExtensionHandler1CustomExtension = new CustomAccessPackageWorkflowExtension();
$customExtensionHandlersCustomExtensionHandler1CustomExtension->setId('219f57b6-7983-45a1-be01-2c228b7a43f8');
$customExtensionHandlersCustomExtensionHandler1->setCustomExtension($customExtensionHandlersCustomExtensionHandler1CustomExtension);
$customExtensionHandlersArray []= $customExtensionHandlersCustomExtensionHandler1;
$customExtensionHandlersCustomExtensionHandler2 = new CustomExtensionHandler();
$customExtensionHandlersCustomExtensionHandler2->setStage(new AccessPackageCustomExtensionStage('assignmentRequestGranted'));
$customExtensionHandlersCustomExtensionHandler2CustomExtension = new CustomAccessPackageWorkflowExtension();
$customExtensionHandlersCustomExtensionHandler2CustomExtension->setId('219f57b6-7983-45a1-be01-2c228b7a43f8');
$customExtensionHandlersCustomExtensionHandler2->setCustomExtension($customExtensionHandlersCustomExtensionHandler2CustomExtension);
$customExtensionHandlersArray []= $customExtensionHandlersCustomExtensionHandler2;
$requestBody->setCustomExtensionHandlers($customExtensionHandlersArray);

$additionalData = [
'expiration' => [
	'type' => 'afterDuration',
	'duration' => 'P365D',
],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	displayName = "extension-policy"
	description = "test"
	accessPackageId = "ba5807c7-2aa9-4c8a-907e-4a17ee587500"
	expiration = @{
		type = "afterDuration"
		duration = "P365D"
	}
	canExtend = $false
	requestApprovalSettings = $null
	requestorSettings = @{
		acceptRequests = $true
		scopeType = "AllExistingDirectorySubjects"
		allowedRequestors = @(
		)
		isOnBehalfAllowed = $false
	}
	accessReviewSettings = $null
	questions = @(
	)
	customExtensionHandlers = @(
		@{
			stage = "assignmentRequestCreated"
			customExtension = @{
				id = "219f57b6-7983-45a1-be01-2c228b7a43f8"
			}
		}
		@{
			stage = "assignmentRequestGranted"
			customExtension = @{
				id = "219f57b6-7983-45a1-be01-2c228b7a43f8"
			}
		}
	)
}

New-MgBetaEntitlementManagementAccessPackageAssignmentPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph_beta.generated.models.requestor_settings import RequestorSettings
from msgraph_beta.generated.models.user_set import UserSet
from msgraph_beta.generated.models.access_package_question import AccessPackageQuestion
from msgraph_beta.generated.models.custom_extension_handler import CustomExtensionHandler
from msgraph_beta.generated.models.access_package_custom_extension_stage import AccessPackageCustomExtensionStage
from msgraph_beta.generated.models.custom_access_package_workflow_extension import CustomAccessPackageWorkflowExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	display_name = "extension-policy",
	description = "test",
	access_package_id = "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
	can_extend = False,
	request_approval_settings = None,
	requestor_settings = RequestorSettings(
		accept_requests = True,
		scope_type = "AllExistingDirectorySubjects",
		allowed_requestors = [
		],
		additional_data = {
				"is_on_behalf_allowed" : False,
		}
	),
	access_review_settings = None,
	questions = [
	],
	custom_extension_handlers = [
		CustomExtensionHandler(
			stage = AccessPackageCustomExtensionStage.AssignmentRequestCreated,
			custom_extension = CustomAccessPackageWorkflowExtension(
				id = "219f57b6-7983-45a1-be01-2c228b7a43f8",
			),
		),
		CustomExtensionHandler(
			stage = AccessPackageCustomExtensionStage.AssignmentRequestGranted,
			custom_extension = CustomAccessPackageWorkflowExtension(
				id = "219f57b6-7983-45a1-be01-2c228b7a43f8",
			),
		),
	],
	additional_data = {
			"expiration" : {
					"type" : "afterDuration",
					"duration" : "P365D",
			},
	}
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_policies.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The **customExtensionHandlers** object isn't returned by default. To retrieve this object, use the **GET** method with `$expand`. For more information, see [Retrieve the custom extension handlers for a policy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-beta#example-2-retrieve-the-custom-extension-handlers-for-a-policy)

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "d0324cbb-24a2-4edb-acca-fee5384c6a5e",
  "displayName": "extension-policy",
  "description": "test",
  "canExtend": false,
  "durationInDays": 0,
  "expirationDateTime": null,
  "accessPackageId": "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
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
  }
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
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies
Content-type: application/json

{
  "displayName": "extension-policy",
  "description": "test",
  "accessPackageId": "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
  "expiration": {
    "type": "afterDuration",
    "duration": "P365D"
  },
  "canExtend": false,
  "requestApprovalSettings": null,
  "requestorSettings": {
    "acceptRequests": true,
    "scopeType": "AllExistingDirectorySubjects",
    "allowedRequestors": [],
    "isOnBehalfAllowed": false
  },
  "accessReviewSettings": null,
  "questions": [],
  "customExtensionStageSettings": [
    {
      "stage": "assignmentRequestCreated",
      "customExtension": {
        "id": "219f57b6-7983-45a1-be01-2c228b7a43f8"
      }
    },
    {
      "stage": "assignmentRequestGranted",
      "customExtension": {
        "id": "219f57b6-7983-45a1-be01-2c228b7a43f8"
      }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new AccessPackageAssignmentPolicy
{
	DisplayName = "extension-policy",
	Description = "test",
	AccessPackageId = "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
	CanExtend = false,
	RequestApprovalSettings = null,
	RequestorSettings = new RequestorSettings
	{
		AcceptRequests = true,
		ScopeType = "AllExistingDirectorySubjects",
		AllowedRequestors = new List<UserSet>
		{
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"isOnBehalfAllowed" , false
			},
		},
	},
	AccessReviewSettings = null,
	Questions = new List<AccessPackageQuestion>
	{
	},
	CustomExtensionStageSettings = new List<CustomExtensionStageSetting>
	{
		new CustomExtensionStageSetting
		{
			Stage = AccessPackageCustomExtensionStage.AssignmentRequestCreated,
			CustomExtension = new CustomCalloutExtension
			{
				Id = "219f57b6-7983-45a1-be01-2c228b7a43f8",
			},
		},
		new CustomExtensionStageSetting
		{
			Stage = AccessPackageCustomExtensionStage.AssignmentRequestGranted,
			CustomExtension = new CustomCalloutExtension
			{
				Id = "219f57b6-7983-45a1-be01-2c228b7a43f8",
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"expiration" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"type", new UntypedString("afterDuration")
				},
				{
					"duration", new UntypedString("P365D")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
displayName := "extension-policy"
requestBody.SetDisplayName(&displayName) 
description := "test"
requestBody.SetDescription(&description) 
accessPackageId := "ba5807c7-2aa9-4c8a-907e-4a17ee587500"
requestBody.SetAccessPackageId(&accessPackageId) 
canExtend := false
requestBody.SetCanExtend(&canExtend) 
requestApprovalSettings := null
requestBody.SetRequestApprovalSettings(&requestApprovalSettings) 
requestorSettings := graphmodels.NewRequestorSettings()
acceptRequests := true
requestorSettings.SetAcceptRequests(&acceptRequests) 
scopeType := "AllExistingDirectorySubjects"
requestorSettings.SetScopeType(&scopeType) 
allowedRequestors := []graphmodels.UserSetable {

}
requestorSettings.SetAllowedRequestors(allowedRequestors)
additionalData := map[string]interface{}{
	isOnBehalfAllowed := false
requestorSettings.SetIsOnBehalfAllowed(&isOnBehalfAllowed) 
}
requestorSettings.SetAdditionalData(additionalData)
requestBody.SetRequestorSettings(requestorSettings)
accessReviewSettings := null
requestBody.SetAccessReviewSettings(&accessReviewSettings) 
questions := []graphmodels.AccessPackageQuestionable {

}
requestBody.SetQuestions(questions)


customExtensionStageSetting := graphmodels.NewCustomExtensionStageSetting()
stage := graphmodels.ASSIGNMENTREQUESTCREATED_ACCESSPACKAGECUSTOMEXTENSIONSTAGE 
customExtensionStageSetting.SetStage(&stage) 
customExtension := graphmodels.NewCustomCalloutExtension()
id := "219f57b6-7983-45a1-be01-2c228b7a43f8"
customExtension.SetId(&id) 
customExtensionStageSetting.SetCustomExtension(customExtension)
customExtensionStageSetting1 := graphmodels.NewCustomExtensionStageSetting()
stage := graphmodels.ASSIGNMENTREQUESTGRANTED_ACCESSPACKAGECUSTOMEXTENSIONSTAGE 
customExtensionStageSetting1.SetStage(&stage) 
customExtension := graphmodels.NewCustomCalloutExtension()
id := "219f57b6-7983-45a1-be01-2c228b7a43f8"
customExtension.SetId(&id) 
customExtensionStageSetting1.SetCustomExtension(customExtension)

customExtensionStageSettings := []graphmodels.CustomExtensionStageSettingable {
	customExtensionStageSetting,
	customExtensionStageSetting1,
}
requestBody.SetCustomExtensionStageSettings(customExtensionStageSettings)
additionalData := map[string]interface{}{
expiration := graph.New()
type := "afterDuration"
expiration.SetType(&type) 
duration := "P365D"
expiration.SetDuration(&duration) 
	requestBody.SetExpiration(expiration)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setDisplayName("extension-policy");
accessPackageAssignmentPolicy.setDescription("test");
accessPackageAssignmentPolicy.setAccessPackageId("ba5807c7-2aa9-4c8a-907e-4a17ee587500");
accessPackageAssignmentPolicy.setCanExtend(false);
accessPackageAssignmentPolicy.setRequestApprovalSettings(null);
RequestorSettings requestorSettings = new RequestorSettings();
requestorSettings.setAcceptRequests(true);
requestorSettings.setScopeType("AllExistingDirectorySubjects");
LinkedList<UserSet> allowedRequestors = new LinkedList<UserSet>();
requestorSettings.setAllowedRequestors(allowedRequestors);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("isOnBehalfAllowed", false);
requestorSettings.setAdditionalData(additionalData);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
accessPackageAssignmentPolicy.setAccessReviewSettings(null);
LinkedList<AccessPackageQuestion> questions = new LinkedList<AccessPackageQuestion>();
accessPackageAssignmentPolicy.setQuestions(questions);
LinkedList<CustomExtensionStageSetting> customExtensionStageSettings = new LinkedList<CustomExtensionStageSetting>();
CustomExtensionStageSetting customExtensionStageSetting = new CustomExtensionStageSetting();
customExtensionStageSetting.setStage(AccessPackageCustomExtensionStage.AssignmentRequestCreated);
CustomCalloutExtension customExtension = new CustomCalloutExtension();
customExtension.setId("219f57b6-7983-45a1-be01-2c228b7a43f8");
customExtensionStageSetting.setCustomExtension(customExtension);
customExtensionStageSettings.add(customExtensionStageSetting);
CustomExtensionStageSetting customExtensionStageSetting1 = new CustomExtensionStageSetting();
customExtensionStageSetting1.setStage(AccessPackageCustomExtensionStage.AssignmentRequestGranted);
CustomCalloutExtension customExtension1 = new CustomCalloutExtension();
customExtension1.setId("219f57b6-7983-45a1-be01-2c228b7a43f8");
customExtensionStageSetting1.setCustomExtension(customExtension1);
customExtensionStageSettings.add(customExtensionStageSetting1);
accessPackageAssignmentPolicy.setCustomExtensionStageSettings(customExtensionStageSettings);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
 expiration = new ();
expiration.setType("afterDuration");
expiration.setDuration("P365D");
additionalData1.put("expiration", expiration);
accessPackageAssignmentPolicy.setAdditionalData(additionalData1);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentPolicies().post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
  displayName: 'extension-policy',
  description: 'test',
  accessPackageId: 'ba5807c7-2aa9-4c8a-907e-4a17ee587500',
  expiration: {
    type: 'afterDuration',
    duration: 'P365D'
  },
  canExtend: false,
  requestApprovalSettings: null,
  requestorSettings: {
    acceptRequests: true,
    scopeType: 'AllExistingDirectorySubjects',
    allowedRequestors: [],
    isOnBehalfAllowed: false
  },
  accessReviewSettings: null,
  questions: [],
  customExtensionStageSettings: [
    {
      stage: 'assignmentRequestCreated',
      customExtension: {
        id: '219f57b6-7983-45a1-be01-2c228b7a43f8'
      }
    },
    {
      stage: 'assignmentRequestGranted',
      customExtension: {
        id: '219f57b6-7983-45a1-be01-2c228b7a43f8'
      }
    }
  ]
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies')
	.version('beta')
	.post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Beta\Generated\Models\RequestorSettings;
use Microsoft\Graph\Beta\Generated\Models\UserSet;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageQuestion;
use Microsoft\Graph\Beta\Generated\Models\CustomExtensionStageSetting;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageCustomExtensionStage;
use Microsoft\Graph\Beta\Generated\Models\CustomCalloutExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setDisplayName('extension-policy');
$requestBody->setDescription('test');
$requestBody->setAccessPackageId('ba5807c7-2aa9-4c8a-907e-4a17ee587500');
$requestBody->setCanExtend(false);
$requestBody->setRequestApprovalSettings(null);
$requestorSettings = new RequestorSettings();
$requestorSettings->setAcceptRequests(true);
$requestorSettings->setScopeType('AllExistingDirectorySubjects');
$requestorSettings->setAllowedRequestors([	]);
$additionalData = [
	'isOnBehalfAllowed' => false,
];
$requestorSettings->setAdditionalData($additionalData);
$requestBody->setRequestorSettings($requestorSettings);
$requestBody->setAccessReviewSettings(null);
$requestBody->setQuestions([	]);
$customExtensionStageSettingsCustomExtensionStageSetting1 = new CustomExtensionStageSetting();
$customExtensionStageSettingsCustomExtensionStageSetting1->setStage(new AccessPackageCustomExtensionStage('assignmentRequestCreated'));
$customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension = new CustomCalloutExtension();
$customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension->setId('219f57b6-7983-45a1-be01-2c228b7a43f8');
$customExtensionStageSettingsCustomExtensionStageSetting1->setCustomExtension($customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension);
$customExtensionStageSettingsArray []= $customExtensionStageSettingsCustomExtensionStageSetting1;
$customExtensionStageSettingsCustomExtensionStageSetting2 = new CustomExtensionStageSetting();
$customExtensionStageSettingsCustomExtensionStageSetting2->setStage(new AccessPackageCustomExtensionStage('assignmentRequestGranted'));
$customExtensionStageSettingsCustomExtensionStageSetting2CustomExtension = new CustomCalloutExtension();
$customExtensionStageSettingsCustomExtensionStageSetting2CustomExtension->setId('219f57b6-7983-45a1-be01-2c228b7a43f8');
$customExtensionStageSettingsCustomExtensionStageSetting2->setCustomExtension($customExtensionStageSettingsCustomExtensionStageSetting2CustomExtension);
$customExtensionStageSettingsArray []= $customExtensionStageSettingsCustomExtensionStageSetting2;
$requestBody->setCustomExtensionStageSettings($customExtensionStageSettingsArray);

$additionalData = [
'expiration' => [
	'type' => 'afterDuration',
	'duration' => 'P365D',
],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	displayName = "extension-policy"
	description = "test"
	accessPackageId = "ba5807c7-2aa9-4c8a-907e-4a17ee587500"
	expiration = @{
		type = "afterDuration"
		duration = "P365D"
	}
	canExtend = $false
	requestApprovalSettings = $null
	requestorSettings = @{
		acceptRequests = $true
		scopeType = "AllExistingDirectorySubjects"
		allowedRequestors = @(
		)
		isOnBehalfAllowed = $false
	}
	accessReviewSettings = $null
	questions = @(
	)
	customExtensionStageSettings = @(
		@{
			stage = "assignmentRequestCreated"
			customExtension = @{
				id = "219f57b6-7983-45a1-be01-2c228b7a43f8"
			}
		}
		@{
			stage = "assignmentRequestGranted"
			customExtension = @{
				id = "219f57b6-7983-45a1-be01-2c228b7a43f8"
			}
		}
	)
}

New-MgBetaEntitlementManagementAccessPackageAssignmentPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph_beta.generated.models.requestor_settings import RequestorSettings
from msgraph_beta.generated.models.user_set import UserSet
from msgraph_beta.generated.models.access_package_question import AccessPackageQuestion
from msgraph_beta.generated.models.custom_extension_stage_setting import CustomExtensionStageSetting
from msgraph_beta.generated.models.access_package_custom_extension_stage import AccessPackageCustomExtensionStage
from msgraph_beta.generated.models.custom_callout_extension import CustomCalloutExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	display_name = "extension-policy",
	description = "test",
	access_package_id = "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
	can_extend = False,
	request_approval_settings = None,
	requestor_settings = RequestorSettings(
		accept_requests = True,
		scope_type = "AllExistingDirectorySubjects",
		allowed_requestors = [
		],
		additional_data = {
				"is_on_behalf_allowed" : False,
		}
	),
	access_review_settings = None,
	questions = [
	],
	custom_extension_stage_settings = [
		CustomExtensionStageSetting(
			stage = AccessPackageCustomExtensionStage.AssignmentRequestCreated,
			custom_extension = CustomCalloutExtension(
				id = "219f57b6-7983-45a1-be01-2c228b7a43f8",
			),
		),
		CustomExtensionStageSetting(
			stage = AccessPackageCustomExtensionStage.AssignmentRequestGranted,
			custom_extension = CustomCalloutExtension(
				id = "219f57b6-7983-45a1-be01-2c228b7a43f8",
			),
		),
	],
	additional_data = {
			"expiration" : {
					"type" : "afterDuration",
					"duration" : "P365D",
			},
	}
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_policies.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The **customExtensionStageSettings** object isn't returned by default. To retrieve this object, use the [GET accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-beta) method with `$expand`. For more information, see [Example 3: Retrieve the custom extension stage settings for a policy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-beta#example-3-retrieve-the-custom-extension-stage-settings-for-a-policy).

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "d0324cbb-24a2-4edb-acca-fee5384c6a5e",
  "displayName": "extension-policy",
  "description": "test",
  "canExtend": false,
  "durationInDays": 0,
  "expirationDateTime": null,
  "accessPackageId": "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
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
  }
}
```

### Example 6: Create a policy with a verifiable credential requirement

#### Request

The following example shows how to create an access package policy with a verifiable credential requirement.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies
Content-type: application/json

{
  "displayName": "policy-with-verified-id",
  "description": "test",
  "accessPackageId": "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
  "expiration": {
    "type": "afterDuration",
    "duration": "P365D"
  },
  "canExtend": false,
  "requestApprovalSettings": null,
  "requestorSettings": {
    "acceptRequests": true,
    "scopeType": "AllExistingDirectorySubjects",
    "allowedRequestors": [],
    "isOnBehalfAllowed": false
  },
  "accessReviewSettings": null,
  "questions": [],
  "customExtensionHandlers": [],
  "verifiableCredentialSettings":
  {
    "credentialTypes":[{
      "issuers": ["did:ion:EiAlrenrtD3Lsw0GlbzS1O2YFdy3Xtu8yo35W<SNIP>..."],
      "credentialType": "VerifiedCredentialExpert"
    }]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new AccessPackageAssignmentPolicy
{
	DisplayName = "policy-with-verified-id",
	Description = "test",
	AccessPackageId = "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
	CanExtend = false,
	RequestApprovalSettings = null,
	RequestorSettings = new RequestorSettings
	{
		AcceptRequests = true,
		ScopeType = "AllExistingDirectorySubjects",
		AllowedRequestors = new List<UserSet>
		{
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"isOnBehalfAllowed" , false
			},
		},
	},
	AccessReviewSettings = null,
	Questions = new List<AccessPackageQuestion>
	{
	},
	CustomExtensionHandlers = new List<CustomExtensionHandler>
	{
	},
	VerifiableCredentialSettings = new VerifiableCredentialSettings
	{
		CredentialTypes = new List<VerifiableCredentialType>
		{
			new VerifiableCredentialType
			{
				Issuers = new List<string>
				{
					"did:ion:EiAlrenrtD3Lsw0GlbzS1O2YFdy3Xtu8yo35W<SNIP>...",
				},
				CredentialType = "VerifiedCredentialExpert",
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"expiration" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"type", new UntypedString("afterDuration")
				},
				{
					"duration", new UntypedString("P365D")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
displayName := "policy-with-verified-id"
requestBody.SetDisplayName(&displayName) 
description := "test"
requestBody.SetDescription(&description) 
accessPackageId := "ba5807c7-2aa9-4c8a-907e-4a17ee587500"
requestBody.SetAccessPackageId(&accessPackageId) 
canExtend := false
requestBody.SetCanExtend(&canExtend) 
requestApprovalSettings := null
requestBody.SetRequestApprovalSettings(&requestApprovalSettings) 
requestorSettings := graphmodels.NewRequestorSettings()
acceptRequests := true
requestorSettings.SetAcceptRequests(&acceptRequests) 
scopeType := "AllExistingDirectorySubjects"
requestorSettings.SetScopeType(&scopeType) 
allowedRequestors := []graphmodels.UserSetable {

}
requestorSettings.SetAllowedRequestors(allowedRequestors)
additionalData := map[string]interface{}{
	isOnBehalfAllowed := false
requestorSettings.SetIsOnBehalfAllowed(&isOnBehalfAllowed) 
}
requestorSettings.SetAdditionalData(additionalData)
requestBody.SetRequestorSettings(requestorSettings)
accessReviewSettings := null
requestBody.SetAccessReviewSettings(&accessReviewSettings) 
questions := []graphmodels.AccessPackageQuestionable {

}
requestBody.SetQuestions(questions)
customExtensionHandlers := []graphmodels.CustomExtensionHandlerable {

}
requestBody.SetCustomExtensionHandlers(customExtensionHandlers)
verifiableCredentialSettings := graphmodels.NewVerifiableCredentialSettings()


verifiableCredentialType := graphmodels.NewVerifiableCredentialType()
issuers := []string {
	"did:ion:EiAlrenrtD3Lsw0GlbzS1O2YFdy3Xtu8yo35W<SNIP>...",
}
verifiableCredentialType.SetIssuers(issuers)
credentialType := "VerifiedCredentialExpert"
verifiableCredentialType.SetCredentialType(&credentialType) 

credentialTypes := []graphmodels.VerifiableCredentialTypeable {
	verifiableCredentialType,
}
verifiableCredentialSettings.SetCredentialTypes(credentialTypes)
requestBody.SetVerifiableCredentialSettings(verifiableCredentialSettings)
additionalData := map[string]interface{}{
expiration := graph.New()
type := "afterDuration"
expiration.SetType(&type) 
duration := "P365D"
expiration.SetDuration(&duration) 
	requestBody.SetExpiration(expiration)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setDisplayName("policy-with-verified-id");
accessPackageAssignmentPolicy.setDescription("test");
accessPackageAssignmentPolicy.setAccessPackageId("ba5807c7-2aa9-4c8a-907e-4a17ee587500");
accessPackageAssignmentPolicy.setCanExtend(false);
accessPackageAssignmentPolicy.setRequestApprovalSettings(null);
RequestorSettings requestorSettings = new RequestorSettings();
requestorSettings.setAcceptRequests(true);
requestorSettings.setScopeType("AllExistingDirectorySubjects");
LinkedList<UserSet> allowedRequestors = new LinkedList<UserSet>();
requestorSettings.setAllowedRequestors(allowedRequestors);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("isOnBehalfAllowed", false);
requestorSettings.setAdditionalData(additionalData);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
accessPackageAssignmentPolicy.setAccessReviewSettings(null);
LinkedList<AccessPackageQuestion> questions = new LinkedList<AccessPackageQuestion>();
accessPackageAssignmentPolicy.setQuestions(questions);
LinkedList<CustomExtensionHandler> customExtensionHandlers = new LinkedList<CustomExtensionHandler>();
accessPackageAssignmentPolicy.setCustomExtensionHandlers(customExtensionHandlers);
VerifiableCredentialSettings verifiableCredentialSettings = new VerifiableCredentialSettings();
LinkedList<VerifiableCredentialType> credentialTypes = new LinkedList<VerifiableCredentialType>();
VerifiableCredentialType verifiableCredentialType = new VerifiableCredentialType();
LinkedList<String> issuers = new LinkedList<String>();
issuers.add("did:ion:EiAlrenrtD3Lsw0GlbzS1O2YFdy3Xtu8yo35W<SNIP>...");
verifiableCredentialType.setIssuers(issuers);
verifiableCredentialType.setCredentialType("VerifiedCredentialExpert");
credentialTypes.add(verifiableCredentialType);
verifiableCredentialSettings.setCredentialTypes(credentialTypes);
accessPackageAssignmentPolicy.setVerifiableCredentialSettings(verifiableCredentialSettings);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
 expiration = new ();
expiration.setType("afterDuration");
expiration.setDuration("P365D");
additionalData1.put("expiration", expiration);
accessPackageAssignmentPolicy.setAdditionalData(additionalData1);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentPolicies().post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
  displayName: 'policy-with-verified-id',
  description: 'test',
  accessPackageId: 'ba5807c7-2aa9-4c8a-907e-4a17ee587500',
  expiration: {
    type: 'afterDuration',
    duration: 'P365D'
  },
  canExtend: false,
  requestApprovalSettings: null,
  requestorSettings: {
    acceptRequests: true,
    scopeType: 'AllExistingDirectorySubjects',
    allowedRequestors: [],
    isOnBehalfAllowed: false
  },
  accessReviewSettings: null,
  questions: [],
  customExtensionHandlers: [],
  verifiableCredentialSettings: 
  {
    credentialTypes: [{
      issuers: ['did:ion:EiAlrenrtD3Lsw0GlbzS1O2YFdy3Xtu8yo35W<SNIP>...'],
      credentialType: 'VerifiedCredentialExpert'
    }]
  }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies')
	.version('beta')
	.post(accessPackageAssignmentPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Beta\Generated\Models\RequestorSettings;
use Microsoft\Graph\Beta\Generated\Models\UserSet;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageQuestion;
use Microsoft\Graph\Beta\Generated\Models\CustomExtensionHandler;
use Microsoft\Graph\Beta\Generated\Models\VerifiableCredentialSettings;
use Microsoft\Graph\Beta\Generated\Models\VerifiableCredentialType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setDisplayName('policy-with-verified-id');
$requestBody->setDescription('test');
$requestBody->setAccessPackageId('ba5807c7-2aa9-4c8a-907e-4a17ee587500');
$requestBody->setCanExtend(false);
$requestBody->setRequestApprovalSettings(null);
$requestorSettings = new RequestorSettings();
$requestorSettings->setAcceptRequests(true);
$requestorSettings->setScopeType('AllExistingDirectorySubjects');
$requestorSettings->setAllowedRequestors([	]);
$additionalData = [
	'isOnBehalfAllowed' => false,
];
$requestorSettings->setAdditionalData($additionalData);
$requestBody->setRequestorSettings($requestorSettings);
$requestBody->setAccessReviewSettings(null);
$requestBody->setQuestions([	]);
$requestBody->setCustomExtensionHandlers([	]);
$verifiableCredentialSettings = new VerifiableCredentialSettings();
$credentialTypesVerifiableCredentialType1 = new VerifiableCredentialType();
$credentialTypesVerifiableCredentialType1->setIssuers(['did:ion:EiAlrenrtD3Lsw0GlbzS1O2YFdy3Xtu8yo35W<SNIP>...', 	]);
$credentialTypesVerifiableCredentialType1->setCredentialType('VerifiedCredentialExpert');
$credentialTypesArray []= $credentialTypesVerifiableCredentialType1;
$verifiableCredentialSettings->setCredentialTypes($credentialTypesArray);

$requestBody->setVerifiableCredentialSettings($verifiableCredentialSettings);
$additionalData = [
'expiration' => [
	'type' => 'afterDuration',
	'duration' => 'P365D',
],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	displayName = "policy-with-verified-id"
	description = "test"
	accessPackageId = "ba5807c7-2aa9-4c8a-907e-4a17ee587500"
	expiration = @{
		type = "afterDuration"
		duration = "P365D"
	}
	canExtend = $false
	requestApprovalSettings = $null
	requestorSettings = @{
		acceptRequests = $true
		scopeType = "AllExistingDirectorySubjects"
		allowedRequestors = @(
		)
		isOnBehalfAllowed = $false
	}
	accessReviewSettings = $null
	questions = @(
	)
	customExtensionHandlers = @(
	)
	verifiableCredentialSettings = @{
		credentialTypes = @(
			@{
				issuers = @(
				"did:ion:EiAlrenrtD3Lsw0GlbzS1O2YFdy3Xtu8yo35W<SNIP>..."
			)
			credentialType = "VerifiedCredentialExpert"
		}
	)
}
}

New-MgBetaEntitlementManagementAccessPackageAssignmentPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph_beta.generated.models.requestor_settings import RequestorSettings
from msgraph_beta.generated.models.user_set import UserSet
from msgraph_beta.generated.models.access_package_question import AccessPackageQuestion
from msgraph_beta.generated.models.custom_extension_handler import CustomExtensionHandler
from msgraph_beta.generated.models.verifiable_credential_settings import VerifiableCredentialSettings
from msgraph_beta.generated.models.verifiable_credential_type import VerifiableCredentialType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	display_name = "policy-with-verified-id",
	description = "test",
	access_package_id = "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
	can_extend = False,
	request_approval_settings = None,
	requestor_settings = RequestorSettings(
		accept_requests = True,
		scope_type = "AllExistingDirectorySubjects",
		allowed_requestors = [
		],
		additional_data = {
				"is_on_behalf_allowed" : False,
		}
	),
	access_review_settings = None,
	questions = [
	],
	custom_extension_handlers = [
	],
	verifiable_credential_settings = VerifiableCredentialSettings(
		credential_types = [
			VerifiableCredentialType(
				issuers = [
					"did:ion:EiAlrenrtD3Lsw0GlbzS1O2YFdy3Xtu8yo35W<SNIP>...",
				],
				credential_type = "VerifiedCredentialExpert",
			),
		],
	),
	additional_data = {
			"expiration" : {
					"type" : "afterDuration",
					"duration" : "P365D",
			},
	}
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_policies.post(request_body)
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
  "id": "d0324cbb-24a2-4edb-acca-fee5384c6a5e",
  "displayName": "extension-policy",
  "description": "test",
  "canExtend": false,
  "durationInDays": 0,
  "expirationDateTime": null,
  "accessPackageId": "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
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
  "customExtensionHandlers": [],
  "verifiableCredentialSettings": {
    "credentialTypes":[{
      "issuers": ["did:ion:EiAlrenrtD3Lsw0GlbzS1O2YFdy3Xtu8yo35W<SNIP>..."],
      "credentialType": "VerifiedCredentialExpert"
    }]
  }
}
```

## Example 7: Create a policy used to determine approvers dynamically from a Logic App

In the following example, the policy is created for an access package assignment that is determining the approver dynamically via a logic app called from a custom extension.

#### Request

The following example shows a request.

```msgraph
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/assignmentPolicies/
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/$entity",
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

#### Response

The following example shows the response. The **customExtensionStageSettings** object isn't returned by default. To retrieve this object, use the [GET accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-beta) method with `$expand`. For more information, see [Example 2: Retrieve the custom extension stage settings for a policy](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-get?view=graph-rest-beta#example-3-retrieve-the-custom-extension-stage-settings-for-a-policy).

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
