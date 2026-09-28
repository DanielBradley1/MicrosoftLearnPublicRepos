<!-- Source: https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentpolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update accessPackageAssignmentPolicy

Namespace: microsoft.graph

Update an existing [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) object to change one or more of its properties, such as the display name or description.

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
PUT /identityGovernance/entitlementManagement/assignmentPolicies/{accessPackageAssignmentPolicyId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) object.

The following table shows the properties that are required when you update an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| accessPackage | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) | Access package containing this policy. Only the **id** property is required. |
| displayName | String | The display name of the policy. Required. |
| description | String | The description of the policy. Required. |
| allowedTargetScope | allowedTargetScope | Who is allowed to request the access package through this policy. The possible values are: `notSpecified`, `specificDirectoryUsers`, `specificConnectedOrganizationUsers`, `specificDirectoryServicePrincipals`, `allMemberUsers`, `allDirectoryUsers`, `allDirectoryServicePrincipals`, `allConfiguredConnectedOrganizationUsers`, `allExternalUsers`, `unknownFutureValue`. Required. |
| automaticRequestSettings | [accessPackageAutomaticRequestSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageautomaticrequestsettings?view=graph-rest-1.0) | This property is only present for an auto assignment policy; if absent, this is a request-based policy. Required. |
| specificAllowedTargets | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | The principals that can be assigned access from an access package through this policy. Required. |
| expiration | [expirationPattern](https://learn.microsoft.com/en-us/graph/api/resources/expirationpattern?view=graph-rest-1.0) | The expiration date for assignments created in this policy. Required. |
| notificationSettings | [accessPackageNotificationSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagenotificationsettings?view=graph-rest-1.0) | Represents the settings for email notifications for requests to an access package. |
| requestorSettings | [accessPackageAssignmentRequestorSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestorsettings?view=graph-rest-1.0) | Provides additional settings to select who can create a request for an access package assignment through this policy, and what they can include in their request. Required. |
| requestApprovalSettings | [accessPackageAssignmentApprovalSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentapprovalsettings?view=graph-rest-1.0) | Specifies the settings for approval of requests for an access package assignment through this policy. For example, if approval is required for new requests. Required. |
| reviewSettings | [accessPackageAssignmentReviewSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentreviewsettings?view=graph-rest-1.0) | Settings for access reviews of assignments through this policy. Required. |
| questions | [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0) collection | Questions that are posed to the requestor. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update the details of a policy

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
PUT https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentPolicies/87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187
Content-Type: application/json

{
  "id":"87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187",
  "displayName": "All Users",
  "description": "All users can request for access to the directory.",
  "allowedTargetScope": "allDirectoryUsers",
  "automaticRequestSettings": null,
  "specificAllowedTargets": [],
  "expiration": {
      "type": "noExpiration"
  },
  "requestorSettings": {
      "enableTargetsToSelfAddAccess": true,
      "enableTargetsToSelfUpdateAccess": false,
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
              "durationBeforeAutomaticDenial": "P2D",
              "isApproverJustificationRequired": false,
              "isEscalationEnabled": false,
              "durationBeforeEscalation": "PT0S",
              "primaryApprovers": [
                  {
                      "@odata.type": "#microsoft.graph.requestorManager",
                      "managerLevel": 1
                  }
              ],
              "fallbackPrimaryApprovers": [
                  {
                      "@odata.type": "#microsoft.graph.singleUser",
                      "userId": "e6bf4d7d-6824-4dd0-809d-5bf42d4817c2",
                      "description": "user"
                  }
              ],
              "escalationApprovers": [],
              "fallbackEscalationApprovers": []
          }
      ]
  },
  "accessPackage": {
        "id": "49d2c59b-0a81-463d-a8ec-ddad3935d8a0"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentPolicy
{
	Id = "87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187",
	DisplayName = "All Users",
	Description = "All users can request for access to the directory.",
	AllowedTargetScope = AllowedTargetScope.AllDirectoryUsers,
	AutomaticRequestSettings = null,
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
		EnableTargetsToSelfUpdateAccess = false,
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
				DurationBeforeAutomaticDenial = TimeSpan.Parse("P2D"),
				IsApproverJustificationRequired = false,
				IsEscalationEnabled = false,
				DurationBeforeEscalation = TimeSpan.Parse("PT0S"),
				PrimaryApprovers = new List<SubjectSet>
				{
					new RequestorManager
					{
						OdataType = "#microsoft.graph.requestorManager",
						ManagerLevel = 1,
					},
				},
				FallbackPrimaryApprovers = new List<SubjectSet>
				{
					new SingleUser
					{
						OdataType = "#microsoft.graph.singleUser",
						UserId = "e6bf4d7d-6824-4dd0-809d-5bf42d4817c2",
						Description = "user",
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
	AccessPackage = new AccessPackage
	{
		Id = "49d2c59b-0a81-463d-a8ec-ddad3935d8a0",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentPolicies["{accessPackageAssignmentPolicy-id}"].PutAsync(requestBody);
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
id := "87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187"
requestBody.SetId(&id) 
displayName := "All Users"
requestBody.SetDisplayName(&displayName) 
description := "All users can request for access to the directory."
requestBody.SetDescription(&description) 
allowedTargetScope := graphmodels.ALLDIRECTORYUSERS_ALLOWEDTARGETSCOPE 
requestBody.SetAllowedTargetScope(&allowedTargetScope) 
automaticRequestSettings := null
requestBody.SetAutomaticRequestSettings(&automaticRequestSettings) 
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
enableTargetsToSelfUpdateAccess := false
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
durationBeforeAutomaticDenial , err := abstractions.ParseISODuration("P2D")
accessPackageApprovalStage.SetDurationBeforeAutomaticDenial(&durationBeforeAutomaticDenial) 
isApproverJustificationRequired := false
accessPackageApprovalStage.SetIsApproverJustificationRequired(&isApproverJustificationRequired) 
isEscalationEnabled := false
accessPackageApprovalStage.SetIsEscalationEnabled(&isEscalationEnabled) 
durationBeforeEscalation , err := abstractions.ParseISODuration("PT0S")
accessPackageApprovalStage.SetDurationBeforeEscalation(&durationBeforeEscalation) 


subjectSet := graphmodels.NewRequestorManager()
managerLevel := int32(1)
subjectSet.SetManagerLevel(&managerLevel) 

primaryApprovers := []graphmodels.SubjectSetable {
	subjectSet,
}
accessPackageApprovalStage.SetPrimaryApprovers(primaryApprovers)


subjectSet := graphmodels.NewSingleUser()
userId := "e6bf4d7d-6824-4dd0-809d-5bf42d4817c2"
subjectSet.SetUserId(&userId) 
description := "user"
subjectSet.SetDescription(&description) 

fallbackPrimaryApprovers := []graphmodels.SubjectSetable {
	subjectSet,
}
accessPackageApprovalStage.SetFallbackPrimaryApprovers(fallbackPrimaryApprovers)
escalationApprovers := []graphmodels.SubjectSetable {

}
accessPackageApprovalStage.SetEscalationApprovers(escalationApprovers)
fallbackEscalationApprovers := []graphmodels.SubjectSetable {

}
accessPackageApprovalStage.SetFallbackEscalationApprovers(fallbackEscalationApprovers)

stages := []graphmodels.AccessPackageApprovalStageable {
	accessPackageApprovalStage,
}
requestApprovalSettings.SetStages(stages)
requestBody.SetRequestApprovalSettings(requestApprovalSettings)
accessPackage := graphmodels.NewAccessPackage()
id := "49d2c59b-0a81-463d-a8ec-ddad3935d8a0"
accessPackage.SetId(&id) 
requestBody.SetAccessPackage(accessPackage)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentPolicies().ByAccessPackageAssignmentPolicyId("accessPackageAssignmentPolicy-id").Put(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setId("87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187");
accessPackageAssignmentPolicy.setDisplayName("All Users");
accessPackageAssignmentPolicy.setDescription("All users can request for access to the directory.");
accessPackageAssignmentPolicy.setAllowedTargetScope(AllowedTargetScope.AllDirectoryUsers);
accessPackageAssignmentPolicy.setAutomaticRequestSettings(null);
LinkedList<SubjectSet> specificAllowedTargets = new LinkedList<SubjectSet>();
accessPackageAssignmentPolicy.setSpecificAllowedTargets(specificAllowedTargets);
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.NoExpiration);
accessPackageAssignmentPolicy.setExpiration(expiration);
AccessPackageAssignmentRequestorSettings requestorSettings = new AccessPackageAssignmentRequestorSettings();
requestorSettings.setEnableTargetsToSelfAddAccess(true);
requestorSettings.setEnableTargetsToSelfUpdateAccess(false);
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
PeriodAndDuration durationBeforeAutomaticDenial = PeriodAndDuration.ofDuration(Duration.parse("P2D"));
accessPackageApprovalStage.setDurationBeforeAutomaticDenial(durationBeforeAutomaticDenial);
accessPackageApprovalStage.setIsApproverJustificationRequired(false);
accessPackageApprovalStage.setIsEscalationEnabled(false);
PeriodAndDuration durationBeforeEscalation = PeriodAndDuration.ofDuration(Duration.parse("PT0S"));
accessPackageApprovalStage.setDurationBeforeEscalation(durationBeforeEscalation);
LinkedList<SubjectSet> primaryApprovers = new LinkedList<SubjectSet>();
RequestorManager subjectSet = new RequestorManager();
subjectSet.setOdataType("#microsoft.graph.requestorManager");
subjectSet.setManagerLevel(1);
primaryApprovers.add(subjectSet);
accessPackageApprovalStage.setPrimaryApprovers(primaryApprovers);
LinkedList<SubjectSet> fallbackPrimaryApprovers = new LinkedList<SubjectSet>();
SingleUser subjectSet1 = new SingleUser();
subjectSet1.setOdataType("#microsoft.graph.singleUser");
subjectSet1.setUserId("e6bf4d7d-6824-4dd0-809d-5bf42d4817c2");
subjectSet1.setDescription("user");
fallbackPrimaryApprovers.add(subjectSet1);
accessPackageApprovalStage.setFallbackPrimaryApprovers(fallbackPrimaryApprovers);
LinkedList<SubjectSet> escalationApprovers = new LinkedList<SubjectSet>();
accessPackageApprovalStage.setEscalationApprovers(escalationApprovers);
LinkedList<SubjectSet> fallbackEscalationApprovers = new LinkedList<SubjectSet>();
accessPackageApprovalStage.setFallbackEscalationApprovers(fallbackEscalationApprovers);
stages.add(accessPackageApprovalStage);
requestApprovalSettings.setStages(stages);
accessPackageAssignmentPolicy.setRequestApprovalSettings(requestApprovalSettings);
AccessPackage accessPackage = new AccessPackage();
accessPackage.setId("49d2c59b-0a81-463d-a8ec-ddad3935d8a0");
accessPackageAssignmentPolicy.setAccessPackage(accessPackage);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().assignmentPolicies().byAccessPackageAssignmentPolicyId("{accessPackageAssignmentPolicy-id}").put(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
  id: '87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187',
  displayName: 'All Users',
  description: 'All users can request for access to the directory.',
  allowedTargetScope: 'allDirectoryUsers',
  automaticRequestSettings: null,
  specificAllowedTargets: [],
  expiration: {
      type: 'noExpiration'
  },
  requestorSettings: {
      enableTargetsToSelfAddAccess: true,
      enableTargetsToSelfUpdateAccess: false,
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
              durationBeforeAutomaticDenial: 'P2D',
              isApproverJustificationRequired: false,
              isEscalationEnabled: false,
              durationBeforeEscalation: 'PT0S',
              primaryApprovers: [
                  {
                      '@odata.type': '#microsoft.graph.requestorManager',
                      managerLevel: 1
                  }
              ],
              fallbackPrimaryApprovers: [
                  {
                      '@odata.type': '#microsoft.graph.singleUser',
                      userId: 'e6bf4d7d-6824-4dd0-809d-5bf42d4817c2',
                      description: 'user'
                  }
              ],
              escalationApprovers: [],
              fallbackEscalationApprovers: []
          }
      ]
  },
  accessPackage: {
        id: '49d2c59b-0a81-463d-a8ec-ddad3935d8a0'
  }
};

await client.api('/identityGovernance/entitlementManagement/assignmentPolicies/87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187')
	.put(accessPackageAssignmentPolicy);
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
use Microsoft\Graph\Generated\Models\RequestorManager;
use Microsoft\Graph\Generated\Models\SingleUser;
use Microsoft\Graph\Generated\Models\AccessPackage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setId('87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187');
$requestBody->setDisplayName('All Users');
$requestBody->setDescription('All users can request for access to the directory.');
$requestBody->setAllowedTargetScope(new AllowedTargetScope('allDirectoryUsers'));
$requestBody->setAutomaticRequestSettings(null);
$requestBody->setSpecificAllowedTargets([	]);
$expiration = new ExpirationPattern();
$expiration->setType(new ExpirationPatternType('noExpiration'));
$requestBody->setExpiration($expiration);
$requestorSettings = new AccessPackageAssignmentRequestorSettings();
$requestorSettings->setEnableTargetsToSelfAddAccess(true);
$requestorSettings->setEnableTargetsToSelfUpdateAccess(false);
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
$stagesAccessPackageApprovalStage1->setDurationBeforeAutomaticDenial(new \DateInterval('P2D'));
$stagesAccessPackageApprovalStage1->setIsApproverJustificationRequired(false);
$stagesAccessPackageApprovalStage1->setIsEscalationEnabled(false);
$stagesAccessPackageApprovalStage1->setDurationBeforeEscalation(new \DateInterval('PT0S'));
$primaryApproversSubjectSet1 = new RequestorManager();
$primaryApproversSubjectSet1->setOdataType('#microsoft.graph.requestorManager');
$primaryApproversSubjectSet1->setManagerLevel(1);
$primaryApproversArray []= $primaryApproversSubjectSet1;
$stagesAccessPackageApprovalStage1->setPrimaryApprovers($primaryApproversArray);

$fallbackPrimaryApproversSubjectSet1 = new SingleUser();
$fallbackPrimaryApproversSubjectSet1->setOdataType('#microsoft.graph.singleUser');
$fallbackPrimaryApproversSubjectSet1->setUserId('e6bf4d7d-6824-4dd0-809d-5bf42d4817c2');
$fallbackPrimaryApproversSubjectSet1->setDescription('user');
$fallbackPrimaryApproversArray []= $fallbackPrimaryApproversSubjectSet1;
$stagesAccessPackageApprovalStage1->setFallbackPrimaryApprovers($fallbackPrimaryApproversArray);

$stagesAccessPackageApprovalStage1->setEscalationApprovers([]);
$stagesAccessPackageApprovalStage1->setFallbackEscalationApprovers([]);
$stagesArray []= $stagesAccessPackageApprovalStage1;
$requestApprovalSettings->setStages($stagesArray);

$requestBody->setRequestApprovalSettings($requestApprovalSettings);
$accessPackage = new AccessPackage();
$accessPackage->setId('49d2c59b-0a81-463d-a8ec-ddad3935d8a0');
$requestBody->setAccessPackage($accessPackage);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentPolicies()->byAccessPackageAssignmentPolicyId('accessPackageAssignmentPolicy-id')->put($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	id = "87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187"
	displayName = "All Users"
	description = "All users can request for access to the directory."
	allowedTargetScope = "allDirectoryUsers"
	automaticRequestSettings = $null
	specificAllowedTargets = @(
	)
	expiration = @{
		type = "noExpiration"
	}
	requestorSettings = @{
		enableTargetsToSelfAddAccess = $true
		enableTargetsToSelfUpdateAccess = $false
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
				durationBeforeAutomaticDenial = "P2D"
				isApproverJustificationRequired = $false
				isEscalationEnabled = $false
				durationBeforeEscalation = "PT0S"
				primaryApprovers = @(
					@{
						"@odata.type" = "#microsoft.graph.requestorManager"
						managerLevel = 
					}
				)
				fallbackPrimaryApprovers = @(
					@{
						"@odata.type" = "#microsoft.graph.singleUser"
						userId = "e6bf4d7d-6824-4dd0-809d-5bf42d4817c2"
						description = "user"
					}
				)
				escalationApprovers = @(
				)
				fallbackEscalationApprovers = @(
				)
			}
		)
	}
	accessPackage = @{
		id = "49d2c59b-0a81-463d-a8ec-ddad3935d8a0"
	}
}

Set-MgEntitlementManagementAssignmentPolicy -AccessPackageAssignmentPolicyId $accessPackageAssignmentPolicyId -BodyParameter $params
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
from msgraph.generated.models.requestor_manager import RequestorManager
from msgraph.generated.models.single_user import SingleUser
from msgraph.generated.models.access_package import AccessPackage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	id = "87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187",
	display_name = "All Users",
	description = "All users can request for access to the directory.",
	allowed_target_scope = AllowedTargetScope.AllDirectoryUsers,
	automatic_request_settings = None,
	specific_allowed_targets = [
	],
	expiration = ExpirationPattern(
		type = ExpirationPatternType.NoExpiration,
	),
	requestor_settings = AccessPackageAssignmentRequestorSettings(
		enable_targets_to_self_add_access = True,
		enable_targets_to_self_update_access = False,
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
				duration_before_automatic_denial = "P2D",
				is_approver_justification_required = False,
				is_escalation_enabled = False,
				duration_before_escalation = "PT0S",
				primary_approvers = [
					RequestorManager(
						odata_type = "#microsoft.graph.requestorManager",
						manager_level = 1,
					),
				],
				fallback_primary_approvers = [
					SingleUser(
						odata_type = "#microsoft.graph.singleUser",
						user_id = "e6bf4d7d-6824-4dd0-809d-5bf42d4817c2",
						description = "user",
					),
				],
				escalation_approvers = [
				],
				fallback_escalation_approvers = [
				],
			),
		],
	),
	access_package = AccessPackage(
		id = "49d2c59b-0a81-463d-a8ec-ddad3935d8a0",
	),
)

result = await graph_client.identity_governance.entitlement_management.assignment_policies.by_access_package_assignment_policy_id('accessPackageAssignmentPolicy-id').put(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "87e1c7f7-c7f7-87e1-f7c7-e187f7c7e187",
  "displayName": "All Users",
  "description": "All users can request for access to the directory."
}
```

### Example 2: Remove the customExtensionStageSettings from a policy

To remove the collection of **customExtensionStageSettings** and their associated custom workflow extension objects from a policy, assign an empty collection to the **customExtensionStageSettings** object.

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
PUT https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentPolicies/4540a08f-8ab5-43f6-a923-015275799197
Content-Type: application/json

{
    "id": "5540a08f-8ab5-43f6-a923-015275799197",
    "displayName": "policy with access package custom workflow extension",
    "description": "Run specified access package custom workflow extension at different stages.",
    "accessPackageId": "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
    "expiration": {
        "type": "afterDuration",
        "duration": "P365D"
    },
    "requestApprovalSettings": null,
    "requestorSettings": {
        "acceptRequests": true,
        "scopeType": "AllExistingDirectorySubjects",
        "allowedRequestors": []
    },
    "accessReviewSettings": null,
    "customExtensionStageSettings": []
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentPolicy
{
	Id = "5540a08f-8ab5-43f6-a923-015275799197",
	DisplayName = "policy with access package custom workflow extension",
	Description = "Run specified access package custom workflow extension at different stages.",
	Expiration = new ExpirationPattern
	{
		Type = ExpirationPatternType.AfterDuration,
		Duration = TimeSpan.Parse("P365D"),
	},
	RequestApprovalSettings = null,
	RequestorSettings = new AccessPackageAssignmentRequestorSettings
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"acceptRequests" , true
			},
			{
				"scopeType" , "AllExistingDirectorySubjects"
			},
			{
				"allowedRequestors" , new List<object>
				{
				}
			},
		},
	},
	CustomExtensionStageSettings = new List<CustomExtensionStageSetting>
	{
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"accessPackageId" , "ba5807c7-2aa9-4c8a-907e-4a17ee587500"
		},
		{
			"accessReviewSettings" , null
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentPolicies["{accessPackageAssignmentPolicy-id}"].PutAsync(requestBody);
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
accessPackageAssignmentPolicy.setId("5540a08f-8ab5-43f6-a923-015275799197");
accessPackageAssignmentPolicy.setDisplayName("policy with access package custom workflow extension");
accessPackageAssignmentPolicy.setDescription("Run specified access package custom workflow extension at different stages.");
ExpirationPattern expiration = new ExpirationPattern();
expiration.setType(ExpirationPatternType.AfterDuration);
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("P365D"));
expiration.setDuration(duration);
accessPackageAssignmentPolicy.setExpiration(expiration);
accessPackageAssignmentPolicy.setRequestApprovalSettings(null);
AccessPackageAssignmentRequestorSettings requestorSettings = new AccessPackageAssignmentRequestorSettings();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("acceptRequests", true);
additionalData.put("scopeType", "AllExistingDirectorySubjects");
LinkedList<Object> allowedRequestors = new LinkedList<Object>();
additionalData.put("allowedRequestors", allowedRequestors);
requestorSettings.setAdditionalData(additionalData);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
LinkedList<CustomExtensionStageSetting> customExtensionStageSettings = new LinkedList<CustomExtensionStageSetting>();
accessPackageAssignmentPolicy.setCustomExtensionStageSettings(customExtensionStageSettings);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("accessPackageId", "ba5807c7-2aa9-4c8a-907e-4a17ee587500");
additionalData1.put("accessReviewSettings", null);
accessPackageAssignmentPolicy.setAdditionalData(additionalData1);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().assignmentPolicies().byAccessPackageAssignmentPolicyId("{accessPackageAssignmentPolicy-id}").put(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
    id: '5540a08f-8ab5-43f6-a923-015275799197',
    displayName: 'policy with access package custom workflow extension',
    description: 'Run specified access package custom workflow extension at different stages.',
    accessPackageId: 'ba5807c7-2aa9-4c8a-907e-4a17ee587500',
    expiration: {
        type: 'afterDuration',
        duration: 'P365D'
    },
    requestApprovalSettings: null,
    requestorSettings: {
        acceptRequests: true,
        scopeType: 'AllExistingDirectorySubjects',
        allowedRequestors: []
    },
    accessReviewSettings: null,
    customExtensionStageSettings: []
};

await client.api('/identityGovernance/entitlementManagement/assignmentPolicies/4540a08f-8ab5-43f6-a923-015275799197')
	.put(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Generated\Models\ExpirationPatternType;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequestorSettings;
use Microsoft\Graph\Generated\Models\CustomExtensionStageSetting;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setId('5540a08f-8ab5-43f6-a923-015275799197');
$requestBody->setDisplayName('policy with access package custom workflow extension');
$requestBody->setDescription('Run specified access package custom workflow extension at different stages.');
$expiration = new ExpirationPattern();
$expiration->setType(new ExpirationPatternType('afterDuration'));
$expiration->setDuration(new \DateInterval('P365D'));
$requestBody->setExpiration($expiration);
$requestBody->setRequestApprovalSettings(null);
$requestorSettings = new AccessPackageAssignmentRequestorSettings();
$additionalData = [
	'acceptRequests' => true,
	'scopeType' => 'AllExistingDirectorySubjects',
	'allowedRequestors' => [],
];
$requestorSettings->setAdditionalData($additionalData);
$requestBody->setRequestorSettings($requestorSettings);
$requestBody->setCustomExtensionStageSettings([	]);
$additionalData = [
	'accessPackageId' => 'ba5807c7-2aa9-4c8a-907e-4a17ee587500',
	'accessReviewSettings' => null,
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentPolicies()->byAccessPackageAssignmentPolicyId('accessPackageAssignmentPolicy-id')->put($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	id = "5540a08f-8ab5-43f6-a923-015275799197"
	displayName = "policy with access package custom workflow extension"
	description = "Run specified access package custom workflow extension at different stages."
	accessPackageId = "ba5807c7-2aa9-4c8a-907e-4a17ee587500"
	expiration = @{
		type = "afterDuration"
		duration = "P365D"
	}
	requestApprovalSettings = $null
	requestorSettings = @{
		acceptRequests = $true
		scopeType = "AllExistingDirectorySubjects"
		allowedRequestors = @(
		)
	}
	accessReviewSettings = $null
	customExtensionStageSettings = @(
	)
}

Set-MgEntitlementManagementAssignmentPolicy -AccessPackageAssignmentPolicyId $accessPackageAssignmentPolicyId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph.generated.models.expiration_pattern import ExpirationPattern
from msgraph.generated.models.expiration_pattern_type import ExpirationPatternType
from msgraph.generated.models.access_package_assignment_requestor_settings import AccessPackageAssignmentRequestorSettings
from msgraph.generated.models.custom_extension_stage_setting import CustomExtensionStageSetting
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	id = "5540a08f-8ab5-43f6-a923-015275799197",
	display_name = "policy with access package custom workflow extension",
	description = "Run specified access package custom workflow extension at different stages.",
	expiration = ExpirationPattern(
		type = ExpirationPatternType.AfterDuration,
		duration = "P365D",
	),
	request_approval_settings = None,
	requestor_settings = AccessPackageAssignmentRequestorSettings(
		additional_data = {
				"accept_requests" : True,
				"scope_type" : "AllExistingDirectorySubjects",
				"allowed_requestors" : [
				],
		}
	),
	custom_extension_stage_settings = [
	],
	additional_data = {
			"access_package_id" : "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
			"access_review_settings" : None,
	}
)

result = await graph_client.identity_governance.entitlement_management.assignment_policies.by_access_package_assignment_policy_id('accessPackageAssignmentPolicy-id').put(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "4540a08f-8ab5-43f6-a923-015275799197",
    "displayName": "policy with access package custom workflow extension",
    "description": "Run specified access package custom workflow extension at different stages.",
    "accessPackageId": "ba5807c7-2aa9-4c8a-907e-4a17ee587500",
    "expiration": {
        "type": "afterDuration",
        "duration": "P365D"
    },
    "requestApprovalSettings": null,
    "requestorSettings": {
        "acceptRequests": true,
        "scopeType": "AllExistingDirectorySubjects",
        "allowedRequestors": []
    },
    "accessReviewSettings": null
}
```

### Example 3: Update the customExtensionStageSettings for a policy

The following example shows how to update a policy to include a custom extension.

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
PUT https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/assignmentPolicies/f9afd2e3-7486-40df-9c35-aa2ae108c495
Content-Type: application/json

{
    "displayName": "API Created policy with updated customExtensionStageSettings",
    "description": "policy with updated customExtensionStageSettings",
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
        "id": "f9afd2e3-7486-40df-9c35-aa2ae108c495"
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
	DisplayName = "API Created policy with updated customExtensionStageSettings",
	Description = "policy with updated customExtensionStageSettings",
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
		Id = "f9afd2e3-7486-40df-9c35-aa2ae108c495",
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
var result = await graphClient.IdentityGovernance.EntitlementManagement.AssignmentPolicies["{accessPackageAssignmentPolicy-id}"].PutAsync(requestBody);
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
displayName := "API Created policy with updated customExtensionStageSettings"
requestBody.SetDisplayName(&displayName) 
description := "policy with updated customExtensionStageSettings"
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
id := "f9afd2e3-7486-40df-9c35-aa2ae108c495"
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
assignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AssignmentPolicies().ByAccessPackageAssignmentPolicyId("accessPackageAssignmentPolicy-id").Put(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setDisplayName("API Created policy with updated customExtensionStageSettings");
accessPackageAssignmentPolicy.setDescription("policy with updated customExtensionStageSettings");
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
accessPackage.setId("f9afd2e3-7486-40df-9c35-aa2ae108c495");
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
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().assignmentPolicies().byAccessPackageAssignmentPolicyId("{accessPackageAssignmentPolicy-id}").put(accessPackageAssignmentPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
    displayName: 'API Created policy with updated customExtensionStageSettings',
    description: 'policy with updated customExtensionStageSettings',
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
        id: 'f9afd2e3-7486-40df-9c35-aa2ae108c495'
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

await client.api('/identityGovernance/entitlementManagement/assignmentPolicies/f9afd2e3-7486-40df-9c35-aa2ae108c495')
	.put(accessPackageAssignmentPolicy);
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
$requestBody->setDisplayName('API Created policy with updated customExtensionStageSettings');
$requestBody->setDescription('policy with updated customExtensionStageSettings');
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
$accessPackage->setId('f9afd2e3-7486-40df-9c35-aa2ae108c495');
$requestBody->setAccessPackage($accessPackage);
$customExtensionStageSettingsCustomExtensionStageSetting1 = new CustomExtensionStageSetting();
$customExtensionStageSettingsCustomExtensionStageSetting1->setStage(new AccessPackageCustomExtensionStage('assignmentRequestCreated'));
$customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension = new AccessPackageAssignmentRequestWorkflowExtension();
$customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension->setOdataType('#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension');
$customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension->setId('bebe7873-1f0d-4db9-b6c3-01f7ebfe8476');
$customExtensionStageSettingsCustomExtensionStageSetting1->setCustomExtension($customExtensionStageSettingsCustomExtensionStageSetting1CustomExtension);
$customExtensionStageSettingsArray []= $customExtensionStageSettingsCustomExtensionStageSetting1;
$requestBody->setCustomExtensionStageSettings($customExtensionStageSettingsArray);


$result = $graphServiceClient->identityGovernance()->entitlementManagement()->assignmentPolicies()->byAccessPackageAssignmentPolicyId('accessPackageAssignmentPolicy-id')->put($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "API Created policy with updated customExtensionStageSettings"
	description = "policy with updated customExtensionStageSettings"
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
		id = "f9afd2e3-7486-40df-9c35-aa2ae108c495"
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

Set-MgEntitlementManagementAssignmentPolicy -AccessPackageAssignmentPolicyId $accessPackageAssignmentPolicyId -BodyParameter $params
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
	display_name = "API Created policy with updated customExtensionStageSettings",
	description = "policy with updated customExtensionStageSettings",
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
		id = "f9afd2e3-7486-40df-9c35-aa2ae108c495",
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

result = await graph_client.identity_governance.entitlement_management.assignment_policies.by_access_package_assignment_policy_id('accessPackageAssignmentPolicy-id').put(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "4540a08f-8ab5-43f6-a923-015275799197",
    "displayName": "API Created policy with updated customExtensionStageSettings",
    "description": "policy with updated customExtensionStageSettings",
    "accessPackageId": "f9afd2e3-7486-40df-9c35-aa2ae108c495",
    "expiration": {
        "type": "afterDuration",
        "duration": "P365D"
    },
    "requestApprovalSettings": null,
    "requestorSettings": {
        "acceptRequests": true,
        "scopeType": "AllExistingDirectorySubjects",
        "allowedRequestors": []
    },
    "accessReviewSettings": null,
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
