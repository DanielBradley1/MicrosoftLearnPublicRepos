<!-- Source: https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update unifiedRoleManagementPolicy

Namespace: microsoft.graph

Update the details of a role management policy [unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicy?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

### For PIM for Microsoft Entra roles

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | RoleManagementPolicy.ReadWrite.Directory, RoleManagement.ReadWrite.Directory |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | RoleManagementPolicy.ReadWrite.Directory, RoleManagement.ReadWrite.Directory |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- For read operations: *Global Reader*, *Security Operator*, *Security Reader*, *Security Administrator*, or *Privileged Role Administrator*
- For write operations: *Privileged Role Administrator*

### For PIM for Groups

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | RoleManagementPolicy.ReadWrite.AzureADGroup |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | RoleManagementPolicy.ReadWrite.AzureADGroup |

## HTTP request

To update the details of a role management policy for either Microsoft Entra roles or groups:

```http
PATCH /policies/roleManagementPolicies/{unifiedRoleManagementPolicyId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| rules | [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) collection | The list of policy rules to be updated. |

## Response

If successful, this method returns a `200 OK` response code and an [unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicy?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update the details of a policy defined in PIM for Microsoft Entra roles

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
PATCH https://graph.microsoft.com/v1.0/policies/roleManagementPolicies/DirectoryRole_2132228a-d66e-401c-ab8a-a8ae31254a36_0f8c4bbc-4f1a-421c-b63d-a68f571b7fab
Content-Type: application/json

{
  "rules": [
    {
      "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
      "id": "Approval_EndUser_Assignment",
      "target": {
        "caller": "EndUser",
        "operations": [
          "All"
        ],
        "level": "Assignment",
        "inheritableSettings": [],
        "enforcedSettings": []
      },
      "setting": {
        "isApprovalRequired": false,
        "isApprovalRequiredForExtension": false,
        "isRequestorJustificationRequired": true,
        "approvalMode": "SingleStage",
        "approvalStages": [
          {
            "approvalStageTimeOutInDays": 1,
            "isApproverJustificationRequired": true,
            "escalationTimeInMinutes": 0,
            "isEscalationEnabled": false,
            "primaryApprovers": [],
            "escalationApprovers": []
          }
        ]
      }
    },
    {
      "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule",
      "id": "AuthenticationContext_EndUser_Assignment",
      "isEnabled": false,
      "claimValue": "",
      "target": {
        "caller": "EndUser",
        "operations": [
          "All"
        ],
        "level": "Assignment",
        "inheritableSettings": [],
        "enforcedSettings": []
      }
    },
    {
      "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
      "id": "Enablement_Admin_Eligibility",
      "enabledRules": [],
      "target": {
        "caller": "Admin",
        "operations": [
          "All"
        ],
        "level": "Eligibility",
        "inheritableSettings": [],
        "enforcedSettings": []
      }
    },
    {
      "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
      "id": "Expiration_Admin_Eligibility",
      "isExpirationRequired": false,
      "maximumDuration": "P365D",
      "target": {
        "caller": "Admin",
        "operations": [
          "All"
        ],
        "level": "Eligibility",
        "inheritableSettings": [],
        "enforcedSettings": []
      }
    },
    {
      "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
      "id": "Notification_Admin_Admin_Eligibility",
      "notificationType": "Email",
      "recipientType": "Admin",
      "notificationLevel": "All",
      "isDefaultRecipientsEnabled": true,
      "notificationRecipients": [],
      "target": {
        "caller": "Admin",
        "operations": [
          "All"
        ],
        "level": "Eligibility",
        "inheritableSettings": [],
        "enforcedSettings": []
      }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleManagementPolicy
{
	Rules = new List<UnifiedRoleManagementPolicyRule>
	{
		new UnifiedRoleManagementPolicyApprovalRule
		{
			OdataType = "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
			Id = "Approval_EndUser_Assignment",
			Target = new UnifiedRoleManagementPolicyRuleTarget
			{
				Caller = "EndUser",
				Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
				{
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				},
				Level = "Assignment",
				InheritableSettings = new List<string>
				{
				},
				EnforcedSettings = new List<string>
				{
				},
			},
			Setting = new ApprovalSettings
			{
				IsApprovalRequired = false,
				IsApprovalRequiredForExtension = false,
				IsRequestorJustificationRequired = true,
				ApprovalMode = "SingleStage",
				ApprovalStages = new List<UnifiedApprovalStage>
				{
					new UnifiedApprovalStage
					{
						ApprovalStageTimeOutInDays = 1,
						IsApproverJustificationRequired = true,
						EscalationTimeInMinutes = 0,
						IsEscalationEnabled = false,
						PrimaryApprovers = new List<SubjectSet>
						{
						},
						EscalationApprovers = new List<SubjectSet>
						{
						},
					},
				},
			},
		},
		new UnifiedRoleManagementPolicyAuthenticationContextRule
		{
			OdataType = "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule",
			Id = "AuthenticationContext_EndUser_Assignment",
			IsEnabled = false,
			ClaimValue = "",
			Target = new UnifiedRoleManagementPolicyRuleTarget
			{
				Caller = "EndUser",
				Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
				{
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				},
				Level = "Assignment",
				InheritableSettings = new List<string>
				{
				},
				EnforcedSettings = new List<string>
				{
				},
			},
		},
		new UnifiedRoleManagementPolicyEnablementRule
		{
			OdataType = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
			Id = "Enablement_Admin_Eligibility",
			EnabledRules = new List<string>
			{
			},
			Target = new UnifiedRoleManagementPolicyRuleTarget
			{
				Caller = "Admin",
				Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
				{
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				},
				Level = "Eligibility",
				InheritableSettings = new List<string>
				{
				},
				EnforcedSettings = new List<string>
				{
				},
			},
		},
		new UnifiedRoleManagementPolicyExpirationRule
		{
			OdataType = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
			Id = "Expiration_Admin_Eligibility",
			IsExpirationRequired = false,
			MaximumDuration = TimeSpan.Parse("P365D"),
			Target = new UnifiedRoleManagementPolicyRuleTarget
			{
				Caller = "Admin",
				Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
				{
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				},
				Level = "Eligibility",
				InheritableSettings = new List<string>
				{
				},
				EnforcedSettings = new List<string>
				{
				},
			},
		},
		new UnifiedRoleManagementPolicyNotificationRule
		{
			OdataType = "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
			Id = "Notification_Admin_Admin_Eligibility",
			NotificationType = "Email",
			RecipientType = "Admin",
			NotificationLevel = "All",
			IsDefaultRecipientsEnabled = true,
			NotificationRecipients = new List<string>
			{
			},
			Target = new UnifiedRoleManagementPolicyRuleTarget
			{
				Caller = "Admin",
				Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
				{
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				},
				Level = "Eligibility",
				InheritableSettings = new List<string>
				{
				},
				EnforcedSettings = new List<string>
				{
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicies["{unifiedRoleManagementPolicy-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUnifiedRoleManagementPolicy()


unifiedRoleManagementPolicyRule := graphmodels.NewUnifiedRoleManagementPolicyApprovalRule()
id := "Approval_EndUser_Assignment"
unifiedRoleManagementPolicyRule.SetId(&id) 
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "EndUser"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Assignment"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
unifiedRoleManagementPolicyRule.SetTarget(target)
setting := graphmodels.NewApprovalSettings()
isApprovalRequired := false
setting.SetIsApprovalRequired(&isApprovalRequired) 
isApprovalRequiredForExtension := false
setting.SetIsApprovalRequiredForExtension(&isApprovalRequiredForExtension) 
isRequestorJustificationRequired := true
setting.SetIsRequestorJustificationRequired(&isRequestorJustificationRequired) 
approvalMode := "SingleStage"
setting.SetApprovalMode(&approvalMode) 


unifiedApprovalStage := graphmodels.NewUnifiedApprovalStage()
approvalStageTimeOutInDays := int32(1)
unifiedApprovalStage.SetApprovalStageTimeOutInDays(&approvalStageTimeOutInDays) 
isApproverJustificationRequired := true
unifiedApprovalStage.SetIsApproverJustificationRequired(&isApproverJustificationRequired) 
escalationTimeInMinutes := int32(0)
unifiedApprovalStage.SetEscalationTimeInMinutes(&escalationTimeInMinutes) 
isEscalationEnabled := false
unifiedApprovalStage.SetIsEscalationEnabled(&isEscalationEnabled) 
primaryApprovers := []graphmodels.SubjectSetable {

}
unifiedApprovalStage.SetPrimaryApprovers(primaryApprovers)
escalationApprovers := []graphmodels.SubjectSetable {

}
unifiedApprovalStage.SetEscalationApprovers(escalationApprovers)

approvalStages := []graphmodels.UnifiedApprovalStageable {
	unifiedApprovalStage,
}
setting.SetApprovalStages(approvalStages)
unifiedRoleManagementPolicyRule.SetSetting(setting)
unifiedRoleManagementPolicyRule1 := graphmodels.NewUnifiedRoleManagementPolicyAuthenticationContextRule()
id := "AuthenticationContext_EndUser_Assignment"
unifiedRoleManagementPolicyRule1.SetId(&id) 
isEnabled := false
unifiedRoleManagementPolicyRule1.SetIsEnabled(&isEnabled) 
claimValue := ""
unifiedRoleManagementPolicyRule1.SetClaimValue(&claimValue) 
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "EndUser"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Assignment"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
unifiedRoleManagementPolicyRule1.SetTarget(target)
unifiedRoleManagementPolicyRule2 := graphmodels.NewUnifiedRoleManagementPolicyEnablementRule()
id := "Enablement_Admin_Eligibility"
unifiedRoleManagementPolicyRule2.SetId(&id) 
enabledRules := []string {

}
unifiedRoleManagementPolicyRule2.SetEnabledRules(enabledRules)
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "Admin"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Eligibility"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
unifiedRoleManagementPolicyRule2.SetTarget(target)
unifiedRoleManagementPolicyRule3 := graphmodels.NewUnifiedRoleManagementPolicyExpirationRule()
id := "Expiration_Admin_Eligibility"
unifiedRoleManagementPolicyRule3.SetId(&id) 
isExpirationRequired := false
unifiedRoleManagementPolicyRule3.SetIsExpirationRequired(&isExpirationRequired) 
maximumDuration , err := abstractions.ParseISODuration("P365D")
unifiedRoleManagementPolicyRule3.SetMaximumDuration(&maximumDuration) 
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "Admin"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Eligibility"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
unifiedRoleManagementPolicyRule3.SetTarget(target)
unifiedRoleManagementPolicyRule4 := graphmodels.NewUnifiedRoleManagementPolicyNotificationRule()
id := "Notification_Admin_Admin_Eligibility"
unifiedRoleManagementPolicyRule4.SetId(&id) 
notificationType := "Email"
unifiedRoleManagementPolicyRule4.SetNotificationType(&notificationType) 
recipientType := "Admin"
unifiedRoleManagementPolicyRule4.SetRecipientType(&recipientType) 
notificationLevel := "All"
unifiedRoleManagementPolicyRule4.SetNotificationLevel(&notificationLevel) 
isDefaultRecipientsEnabled := true
unifiedRoleManagementPolicyRule4.SetIsDefaultRecipientsEnabled(&isDefaultRecipientsEnabled) 
notificationRecipients := []string {

}
unifiedRoleManagementPolicyRule4.SetNotificationRecipients(notificationRecipients)
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "Admin"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Eligibility"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
unifiedRoleManagementPolicyRule4.SetTarget(target)

rules := []graphmodels.UnifiedRoleManagementPolicyRuleable {
	unifiedRoleManagementPolicyRule,
	unifiedRoleManagementPolicyRule1,
	unifiedRoleManagementPolicyRule2,
	unifiedRoleManagementPolicyRule3,
	unifiedRoleManagementPolicyRule4,
}
requestBody.SetRules(rules)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleManagementPolicies, err := graphClient.Policies().RoleManagementPolicies().ByUnifiedRoleManagementPolicyId("unifiedRoleManagementPolicy-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicy unifiedRoleManagementPolicy = new UnifiedRoleManagementPolicy();
LinkedList<UnifiedRoleManagementPolicyRule> rules = new LinkedList<UnifiedRoleManagementPolicyRule>();
UnifiedRoleManagementPolicyApprovalRule unifiedRoleManagementPolicyRule = new UnifiedRoleManagementPolicyApprovalRule();
unifiedRoleManagementPolicyRule.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyApprovalRule");
unifiedRoleManagementPolicyRule.setId("Approval_EndUser_Assignment");
UnifiedRoleManagementPolicyRuleTarget target = new UnifiedRoleManagementPolicyRuleTarget();
target.setCaller("EndUser");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target.setOperations(operations);
target.setLevel("Assignment");
LinkedList<String> inheritableSettings = new LinkedList<String>();
target.setInheritableSettings(inheritableSettings);
LinkedList<String> enforcedSettings = new LinkedList<String>();
target.setEnforcedSettings(enforcedSettings);
unifiedRoleManagementPolicyRule.setTarget(target);
ApprovalSettings setting = new ApprovalSettings();
setting.setIsApprovalRequired(false);
setting.setIsApprovalRequiredForExtension(false);
setting.setIsRequestorJustificationRequired(true);
setting.setApprovalMode("SingleStage");
LinkedList<UnifiedApprovalStage> approvalStages = new LinkedList<UnifiedApprovalStage>();
UnifiedApprovalStage unifiedApprovalStage = new UnifiedApprovalStage();
unifiedApprovalStage.setApprovalStageTimeOutInDays(1);
unifiedApprovalStage.setIsApproverJustificationRequired(true);
unifiedApprovalStage.setEscalationTimeInMinutes(0);
unifiedApprovalStage.setIsEscalationEnabled(false);
LinkedList<SubjectSet> primaryApprovers = new LinkedList<SubjectSet>();
unifiedApprovalStage.setPrimaryApprovers(primaryApprovers);
LinkedList<SubjectSet> escalationApprovers = new LinkedList<SubjectSet>();
unifiedApprovalStage.setEscalationApprovers(escalationApprovers);
approvalStages.add(unifiedApprovalStage);
setting.setApprovalStages(approvalStages);
unifiedRoleManagementPolicyRule.setSetting(setting);
rules.add(unifiedRoleManagementPolicyRule);
UnifiedRoleManagementPolicyAuthenticationContextRule unifiedRoleManagementPolicyRule1 = new UnifiedRoleManagementPolicyAuthenticationContextRule();
unifiedRoleManagementPolicyRule1.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule");
unifiedRoleManagementPolicyRule1.setId("AuthenticationContext_EndUser_Assignment");
unifiedRoleManagementPolicyRule1.setIsEnabled(false);
unifiedRoleManagementPolicyRule1.setClaimValue("");
UnifiedRoleManagementPolicyRuleTarget target1 = new UnifiedRoleManagementPolicyRuleTarget();
target1.setCaller("EndUser");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations1 = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations1.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target1.setOperations(operations1);
target1.setLevel("Assignment");
LinkedList<String> inheritableSettings1 = new LinkedList<String>();
target1.setInheritableSettings(inheritableSettings1);
LinkedList<String> enforcedSettings1 = new LinkedList<String>();
target1.setEnforcedSettings(enforcedSettings1);
unifiedRoleManagementPolicyRule1.setTarget(target1);
rules.add(unifiedRoleManagementPolicyRule1);
UnifiedRoleManagementPolicyEnablementRule unifiedRoleManagementPolicyRule2 = new UnifiedRoleManagementPolicyEnablementRule();
unifiedRoleManagementPolicyRule2.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyEnablementRule");
unifiedRoleManagementPolicyRule2.setId("Enablement_Admin_Eligibility");
LinkedList<String> enabledRules = new LinkedList<String>();
unifiedRoleManagementPolicyRule2.setEnabledRules(enabledRules);
UnifiedRoleManagementPolicyRuleTarget target2 = new UnifiedRoleManagementPolicyRuleTarget();
target2.setCaller("Admin");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations2 = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations2.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target2.setOperations(operations2);
target2.setLevel("Eligibility");
LinkedList<String> inheritableSettings2 = new LinkedList<String>();
target2.setInheritableSettings(inheritableSettings2);
LinkedList<String> enforcedSettings2 = new LinkedList<String>();
target2.setEnforcedSettings(enforcedSettings2);
unifiedRoleManagementPolicyRule2.setTarget(target2);
rules.add(unifiedRoleManagementPolicyRule2);
UnifiedRoleManagementPolicyExpirationRule unifiedRoleManagementPolicyRule3 = new UnifiedRoleManagementPolicyExpirationRule();
unifiedRoleManagementPolicyRule3.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyExpirationRule");
unifiedRoleManagementPolicyRule3.setId("Expiration_Admin_Eligibility");
unifiedRoleManagementPolicyRule3.setIsExpirationRequired(false);
PeriodAndDuration maximumDuration = PeriodAndDuration.ofDuration(Duration.parse("P365D"));
unifiedRoleManagementPolicyRule3.setMaximumDuration(maximumDuration);
UnifiedRoleManagementPolicyRuleTarget target3 = new UnifiedRoleManagementPolicyRuleTarget();
target3.setCaller("Admin");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations3 = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations3.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target3.setOperations(operations3);
target3.setLevel("Eligibility");
LinkedList<String> inheritableSettings3 = new LinkedList<String>();
target3.setInheritableSettings(inheritableSettings3);
LinkedList<String> enforcedSettings3 = new LinkedList<String>();
target3.setEnforcedSettings(enforcedSettings3);
unifiedRoleManagementPolicyRule3.setTarget(target3);
rules.add(unifiedRoleManagementPolicyRule3);
UnifiedRoleManagementPolicyNotificationRule unifiedRoleManagementPolicyRule4 = new UnifiedRoleManagementPolicyNotificationRule();
unifiedRoleManagementPolicyRule4.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyNotificationRule");
unifiedRoleManagementPolicyRule4.setId("Notification_Admin_Admin_Eligibility");
unifiedRoleManagementPolicyRule4.setNotificationType("Email");
unifiedRoleManagementPolicyRule4.setRecipientType("Admin");
unifiedRoleManagementPolicyRule4.setNotificationLevel("All");
unifiedRoleManagementPolicyRule4.setIsDefaultRecipientsEnabled(true);
LinkedList<String> notificationRecipients = new LinkedList<String>();
unifiedRoleManagementPolicyRule4.setNotificationRecipients(notificationRecipients);
UnifiedRoleManagementPolicyRuleTarget target4 = new UnifiedRoleManagementPolicyRuleTarget();
target4.setCaller("Admin");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations4 = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations4.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target4.setOperations(operations4);
target4.setLevel("Eligibility");
LinkedList<String> inheritableSettings4 = new LinkedList<String>();
target4.setInheritableSettings(inheritableSettings4);
LinkedList<String> enforcedSettings4 = new LinkedList<String>();
target4.setEnforcedSettings(enforcedSettings4);
unifiedRoleManagementPolicyRule4.setTarget(target4);
rules.add(unifiedRoleManagementPolicyRule4);
unifiedRoleManagementPolicy.setRules(rules);
UnifiedRoleManagementPolicy result = graphClient.policies().roleManagementPolicies().byUnifiedRoleManagementPolicyId("{unifiedRoleManagementPolicy-id}").patch(unifiedRoleManagementPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleManagementPolicy = {
  rules: [
    {
      '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyApprovalRule',
      id: 'Approval_EndUser_Assignment',
      target: {
        caller: 'EndUser',
        operations: [
          'All'
        ],
        level: 'Assignment',
        inheritableSettings: [],
        enforcedSettings: []
      },
      setting: {
        isApprovalRequired: false,
        isApprovalRequiredForExtension: false,
        isRequestorJustificationRequired: true,
        approvalMode: 'SingleStage',
        approvalStages: [
          {
            approvalStageTimeOutInDays: 1,
            isApproverJustificationRequired: true,
            escalationTimeInMinutes: 0,
            isEscalationEnabled: false,
            primaryApprovers: [],
            escalationApprovers: []
          }
        ]
      }
    },
    {
      '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule',
      id: 'AuthenticationContext_EndUser_Assignment',
      isEnabled: false,
      claimValue: '',
      target: {
        caller: 'EndUser',
        operations: [
          'All'
        ],
        level: 'Assignment',
        inheritableSettings: [],
        enforcedSettings: []
      }
    },
    {
      '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyEnablementRule',
      id: 'Enablement_Admin_Eligibility',
      enabledRules: [],
      target: {
        caller: 'Admin',
        operations: [
          'All'
        ],
        level: 'Eligibility',
        inheritableSettings: [],
        enforcedSettings: []
      }
    },
    {
      '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyExpirationRule',
      id: 'Expiration_Admin_Eligibility',
      isExpirationRequired: false,
      maximumDuration: 'P365D',
      target: {
        caller: 'Admin',
        operations: [
          'All'
        ],
        level: 'Eligibility',
        inheritableSettings: [],
        enforcedSettings: []
      }
    },
    {
      '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyNotificationRule',
      id: 'Notification_Admin_Admin_Eligibility',
      notificationType: 'Email',
      recipientType: 'Admin',
      notificationLevel: 'All',
      isDefaultRecipientsEnabled: true,
      notificationRecipients: [],
      target: {
        caller: 'Admin',
        operations: [
          'All'
        ],
        level: 'Eligibility',
        inheritableSettings: [],
        enforcedSettings: []
      }
    }
  ]
};

await client.api('/policies/roleManagementPolicies/DirectoryRole_2132228a-d66e-401c-ab8a-a8ae31254a36_0f8c4bbc-4f1a-421c-b63d-a68f571b7fab')
	.update(unifiedRoleManagementPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicy;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyApprovalRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTarget;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTargetOperations;
use Microsoft\Graph\Generated\Models\ApprovalSettings;
use Microsoft\Graph\Generated\Models\UnifiedApprovalStage;
use Microsoft\Graph\Generated\Models\SubjectSet;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyAuthenticationContextRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyEnablementRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyExpirationRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyNotificationRule;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleManagementPolicy();
$rulesUnifiedRoleManagementPolicyRule1 = new UnifiedRoleManagementPolicyApprovalRule();
$rulesUnifiedRoleManagementPolicyRule1->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyApprovalRule');
$rulesUnifiedRoleManagementPolicyRule1->setId('Approval_EndUser_Assignment');
$rulesUnifiedRoleManagementPolicyRule1Target = new UnifiedRoleManagementPolicyRuleTarget();
$rulesUnifiedRoleManagementPolicyRule1Target->setCaller('EndUser');
$rulesUnifiedRoleManagementPolicyRule1Target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),	]);
$rulesUnifiedRoleManagementPolicyRule1Target->setLevel('Assignment');
$rulesUnifiedRoleManagementPolicyRule1Target->setInheritableSettings([	]);
$rulesUnifiedRoleManagementPolicyRule1Target->setEnforcedSettings([	]);
$rulesUnifiedRoleManagementPolicyRule1->setTarget($rulesUnifiedRoleManagementPolicyRule1Target);
$rulesUnifiedRoleManagementPolicyRule1Setting = new ApprovalSettings();
$rulesUnifiedRoleManagementPolicyRule1Setting->setIsApprovalRequired(false);
$rulesUnifiedRoleManagementPolicyRule1Setting->setIsApprovalRequiredForExtension(false);
$rulesUnifiedRoleManagementPolicyRule1Setting->setIsRequestorJustificationRequired(true);
$rulesUnifiedRoleManagementPolicyRule1Setting->setApprovalMode('SingleStage');
$approvalStagesUnifiedApprovalStage1 = new UnifiedApprovalStage();
$approvalStagesUnifiedApprovalStage1->setApprovalStageTimeOutInDays(1);
$approvalStagesUnifiedApprovalStage1->setIsApproverJustificationRequired(true);
$approvalStagesUnifiedApprovalStage1->setEscalationTimeInMinutes(0);
$approvalStagesUnifiedApprovalStage1->setIsEscalationEnabled(false);
$approvalStagesUnifiedApprovalStage1->setPrimaryApprovers([	]);
$approvalStagesUnifiedApprovalStage1->setEscalationApprovers([	]);
$approvalStagesArray []= $approvalStagesUnifiedApprovalStage1;
$rulesUnifiedRoleManagementPolicyRule1Setting->setApprovalStages($approvalStagesArray);

$rulesUnifiedRoleManagementPolicyRule1->setSetting($rulesUnifiedRoleManagementPolicyRule1Setting);
$rulesArray []= $rulesUnifiedRoleManagementPolicyRule1;
$rulesUnifiedRoleManagementPolicyRule2 = new UnifiedRoleManagementPolicyAuthenticationContextRule();
$rulesUnifiedRoleManagementPolicyRule2->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule');
$rulesUnifiedRoleManagementPolicyRule2->setId('AuthenticationContext_EndUser_Assignment');
$rulesUnifiedRoleManagementPolicyRule2->setIsEnabled(false);
$rulesUnifiedRoleManagementPolicyRule2->setClaimValue('');
$rulesUnifiedRoleManagementPolicyRule2Target = new UnifiedRoleManagementPolicyRuleTarget();
$rulesUnifiedRoleManagementPolicyRule2Target->setCaller('EndUser');
$rulesUnifiedRoleManagementPolicyRule2Target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),]);
$rulesUnifiedRoleManagementPolicyRule2Target->setLevel('Assignment');
$rulesUnifiedRoleManagementPolicyRule2Target->setInheritableSettings([]);
$rulesUnifiedRoleManagementPolicyRule2Target->setEnforcedSettings([]);
$rulesUnifiedRoleManagementPolicyRule2->setTarget($rulesUnifiedRoleManagementPolicyRule2Target);
$rulesArray []= $rulesUnifiedRoleManagementPolicyRule2;
$rulesUnifiedRoleManagementPolicyRule3 = new UnifiedRoleManagementPolicyEnablementRule();
$rulesUnifiedRoleManagementPolicyRule3->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyEnablementRule');
$rulesUnifiedRoleManagementPolicyRule3->setId('Enablement_Admin_Eligibility');
$rulesUnifiedRoleManagementPolicyRule3->setEnabledRules([]);
$rulesUnifiedRoleManagementPolicyRule3Target = new UnifiedRoleManagementPolicyRuleTarget();
$rulesUnifiedRoleManagementPolicyRule3Target->setCaller('Admin');
$rulesUnifiedRoleManagementPolicyRule3Target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),]);
$rulesUnifiedRoleManagementPolicyRule3Target->setLevel('Eligibility');
$rulesUnifiedRoleManagementPolicyRule3Target->setInheritableSettings([]);
$rulesUnifiedRoleManagementPolicyRule3Target->setEnforcedSettings([]);
$rulesUnifiedRoleManagementPolicyRule3->setTarget($rulesUnifiedRoleManagementPolicyRule3Target);
$rulesArray []= $rulesUnifiedRoleManagementPolicyRule3;
$rulesUnifiedRoleManagementPolicyRule4 = new UnifiedRoleManagementPolicyExpirationRule();
$rulesUnifiedRoleManagementPolicyRule4->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyExpirationRule');
$rulesUnifiedRoleManagementPolicyRule4->setId('Expiration_Admin_Eligibility');
$rulesUnifiedRoleManagementPolicyRule4->setIsExpirationRequired(false);
$rulesUnifiedRoleManagementPolicyRule4->setMaximumDuration(new \DateInterval('P365D'));
$rulesUnifiedRoleManagementPolicyRule4Target = new UnifiedRoleManagementPolicyRuleTarget();
$rulesUnifiedRoleManagementPolicyRule4Target->setCaller('Admin');
$rulesUnifiedRoleManagementPolicyRule4Target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),]);
$rulesUnifiedRoleManagementPolicyRule4Target->setLevel('Eligibility');
$rulesUnifiedRoleManagementPolicyRule4Target->setInheritableSettings([]);
$rulesUnifiedRoleManagementPolicyRule4Target->setEnforcedSettings([]);
$rulesUnifiedRoleManagementPolicyRule4->setTarget($rulesUnifiedRoleManagementPolicyRule4Target);
$rulesArray []= $rulesUnifiedRoleManagementPolicyRule4;
$rulesUnifiedRoleManagementPolicyRule5 = new UnifiedRoleManagementPolicyNotificationRule();
$rulesUnifiedRoleManagementPolicyRule5->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyNotificationRule');
$rulesUnifiedRoleManagementPolicyRule5->setId('Notification_Admin_Admin_Eligibility');
$rulesUnifiedRoleManagementPolicyRule5->setNotificationType('Email');
$rulesUnifiedRoleManagementPolicyRule5->setRecipientType('Admin');
$rulesUnifiedRoleManagementPolicyRule5->setNotificationLevel('All');
$rulesUnifiedRoleManagementPolicyRule5->setIsDefaultRecipientsEnabled(true);
$rulesUnifiedRoleManagementPolicyRule5->setNotificationRecipients([]);
$rulesUnifiedRoleManagementPolicyRule5Target = new UnifiedRoleManagementPolicyRuleTarget();
$rulesUnifiedRoleManagementPolicyRule5Target->setCaller('Admin');
$rulesUnifiedRoleManagementPolicyRule5Target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),]);
$rulesUnifiedRoleManagementPolicyRule5Target->setLevel('Eligibility');
$rulesUnifiedRoleManagementPolicyRule5Target->setInheritableSettings([]);
$rulesUnifiedRoleManagementPolicyRule5Target->setEnforcedSettings([]);
$rulesUnifiedRoleManagementPolicyRule5->setTarget($rulesUnifiedRoleManagementPolicyRule5Target);
$rulesArray []= $rulesUnifiedRoleManagementPolicyRule5;
$requestBody->setRules($rulesArray);


$result = $graphServiceClient->policies()->roleManagementPolicies()->byUnifiedRoleManagementPolicyId('unifiedRoleManagementPolicy-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	rules = @(
		@{
			"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule"
			id = "Approval_EndUser_Assignment"
			target = @{
				caller = "EndUser"
				operations = @(
				"All"
			)
			level = "Assignment"
			inheritableSettings = @(
			)
			enforcedSettings = @(
			)
		}
		setting = @{
			isApprovalRequired = $false
			isApprovalRequiredForExtension = $false
			isRequestorJustificationRequired = $true
			approvalMode = "SingleStage"
			approvalStages = @(
				@{
					approvalStageTimeOutInDays = 
					isApproverJustificationRequired = $true
					escalationTimeInMinutes = 
					isEscalationEnabled = $false
					primaryApprovers = @(
					)
					escalationApprovers = @(
					)
				}
			)
		}
	}
	@{
		"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule"
		id = "AuthenticationContext_EndUser_Assignment"
		isEnabled = $false
		claimValue = ""
		target = @{
			caller = "EndUser"
			operations = @(
			"All"
		)
		level = "Assignment"
		inheritableSettings = @(
		)
		enforcedSettings = @(
		)
	}
}
@{
	"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule"
	id = "Enablement_Admin_Eligibility"
	enabledRules = @(
	)
	target = @{
		caller = "Admin"
		operations = @(
		"All"
	)
	level = "Eligibility"
	inheritableSettings = @(
	)
	enforcedSettings = @(
	)
}
}
@{
"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule"
id = "Expiration_Admin_Eligibility"
isExpirationRequired = $false
maximumDuration = "P365D"
target = @{
	caller = "Admin"
	operations = @(
	"All"
)
level = "Eligibility"
inheritableSettings = @(
)
enforcedSettings = @(
)
}
}
@{
"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule"
id = "Notification_Admin_Admin_Eligibility"
notificationType = "Email"
recipientType = "Admin"
notificationLevel = "All"
isDefaultRecipientsEnabled = $true
notificationRecipients = @(
)
target = @{
caller = "Admin"
operations = @(
"All"
)
level = "Eligibility"
inheritableSettings = @(
)
enforcedSettings = @(
)
}
}
)
}

Update-MgPolicyRoleManagementPolicy -UnifiedRoleManagementPolicyId $unifiedRoleManagementPolicyId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_management_policy import UnifiedRoleManagementPolicy
from msgraph.generated.models.unified_role_management_policy_rule import UnifiedRoleManagementPolicyRule
from msgraph.generated.models.unified_role_management_policy_approval_rule import UnifiedRoleManagementPolicyApprovalRule
from msgraph.generated.models.unified_role_management_policy_rule_target import UnifiedRoleManagementPolicyRuleTarget
from msgraph.generated.models.unified_role_management_policy_rule_target_operations import UnifiedRoleManagementPolicyRuleTargetOperations
from msgraph.generated.models.approval_settings import ApprovalSettings
from msgraph.generated.models.unified_approval_stage import UnifiedApprovalStage
from msgraph.generated.models.subject_set import SubjectSet
from msgraph.generated.models.unified_role_management_policy_authentication_context_rule import UnifiedRoleManagementPolicyAuthenticationContextRule
from msgraph.generated.models.unified_role_management_policy_enablement_rule import UnifiedRoleManagementPolicyEnablementRule
from msgraph.generated.models.unified_role_management_policy_expiration_rule import UnifiedRoleManagementPolicyExpirationRule
from msgraph.generated.models.unified_role_management_policy_notification_rule import UnifiedRoleManagementPolicyNotificationRule
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleManagementPolicy(
	rules = [
		UnifiedRoleManagementPolicyApprovalRule(
			odata_type = "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
			id = "Approval_EndUser_Assignment",
			target = UnifiedRoleManagementPolicyRuleTarget(
				caller = "EndUser",
				operations = [
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				],
				level = "Assignment",
				inheritable_settings = [
				],
				enforced_settings = [
				],
			),
			setting = ApprovalSettings(
				is_approval_required = False,
				is_approval_required_for_extension = False,
				is_requestor_justification_required = True,
				approval_mode = "SingleStage",
				approval_stages = [
					UnifiedApprovalStage(
						approval_stage_time_out_in_days = 1,
						is_approver_justification_required = True,
						escalation_time_in_minutes = 0,
						is_escalation_enabled = False,
						primary_approvers = [
						],
						escalation_approvers = [
						],
					),
				],
			),
		),
		UnifiedRoleManagementPolicyAuthenticationContextRule(
			odata_type = "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule",
			id = "AuthenticationContext_EndUser_Assignment",
			is_enabled = False,
			claim_value = "",
			target = UnifiedRoleManagementPolicyRuleTarget(
				caller = "EndUser",
				operations = [
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				],
				level = "Assignment",
				inheritable_settings = [
				],
				enforced_settings = [
				],
			),
		),
		UnifiedRoleManagementPolicyEnablementRule(
			odata_type = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
			id = "Enablement_Admin_Eligibility",
			enabled_rules = [
			],
			target = UnifiedRoleManagementPolicyRuleTarget(
				caller = "Admin",
				operations = [
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				],
				level = "Eligibility",
				inheritable_settings = [
				],
				enforced_settings = [
				],
			),
		),
		UnifiedRoleManagementPolicyExpirationRule(
			odata_type = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
			id = "Expiration_Admin_Eligibility",
			is_expiration_required = False,
			maximum_duration = "P365D",
			target = UnifiedRoleManagementPolicyRuleTarget(
				caller = "Admin",
				operations = [
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				],
				level = "Eligibility",
				inheritable_settings = [
				],
				enforced_settings = [
				],
			),
		),
		UnifiedRoleManagementPolicyNotificationRule(
			odata_type = "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
			id = "Notification_Admin_Admin_Eligibility",
			notification_type = "Email",
			recipient_type = "Admin",
			notification_level = "All",
			is_default_recipients_enabled = True,
			notification_recipients = [
			],
			target = UnifiedRoleManagementPolicyRuleTarget(
				caller = "Admin",
				operations = [
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				],
				level = "Eligibility",
				inheritable_settings = [
				],
				enforced_settings = [
				],
			),
		),
	],
)

result = await graph_client.policies.role_management_policies.by_unified_role_management_policy_id('unifiedRoleManagementPolicy-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicies/$entity",
    "id": "DirectoryRole_2132228a-d66e-401c-ab8a-a8ae31254a36_0f8c4bbc-4f1a-421c-b63d-a68f571b7fab",
    "displayName": "DirectoryRole",
    "description": "DirectoryRole",
    "isOrganizationDefault": false,
    "scopeId": "/",
    "scopeType": "DirectoryRole",
    "lastModifiedDateTime": "2023-10-01T19:27:32.663Z",
    "lastModifiedBy": {
        "displayName": "Test User 1",
        "id": null
    }
}
```

### Example 2: Update the details of a policy defined in PIM for Groups

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
PATCH https://graph.microsoft.com/v1.0/policies/roleManagementPolicies/Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369
Content-Type: application/json

{
  "rules": [
    {
      "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
      "id": "Approval_EndUser_Assignment",
      "target": {
        "caller": "EndUser",
        "operations": [
          "All"
        ],
        "level": "Assignment",
        "inheritableSettings": [],
        "enforcedSettings": []
      },
      "setting": {
        "isApprovalRequired": true,
        "isApprovalRequiredForExtension": false,
        "isRequestorJustificationRequired": true,
        "approvalMode": "SingleStage",
        "approvalStages": [
          {
            "approvalStageTimeOutInDays": 1,
            "isApproverJustificationRequired": true,
            "escalationTimeInMinutes": 0,
            "isEscalationEnabled": false,
            "primaryApprovers": [
              {
                "@odata.type": "#microsoft.graph.singleUser",
                "isBackup": false,
                "id": "c277c8cb-6bb7-42e5-a17f-0add9a718151",
                "description": null
              }
            ],
            "escalationApprovers": []
          }
        ]
      }
    },
    {
      "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule",
      "id": "AuthenticationContext_EndUser_Assignment",
      "isEnabled": false,
      "claimValue": "",
      "target": {
        "caller": "EndUser",
        "operations": [
          "All"
        ],
        "level": "Assignment",
        "inheritableSettings": [],
        "enforcedSettings": []
      }
    },
    {
      "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
      "id": "Enablement_Admin_Eligibility",
      "enabledRules": [],
      "target": {
        "caller": "Admin",
        "operations": [
          "All"
        ],
        "level": "Eligibility",
        "inheritableSettings": [],
        "enforcedSettings": []
      }
    },
    {
      "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
      "id": "Expiration_Admin_Eligibility",
      "isExpirationRequired": true,
      "maximumDuration": "P365D",
      "target": {
        "caller": "Admin",
        "operations": [
          "All"
        ],
        "level": "Eligibility",
        "inheritableSettings": [],
        "enforcedSettings": []
      }
    },
    {
      "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
      "id": "Notification_Admin_Admin_Eligibility",
      "notificationType": "Email",
      "recipientType": "Admin",
      "notificationLevel": "All",
      "isDefaultRecipientsEnabled": true,
      "notificationRecipients": [],
      "target": {
        "caller": "Admin",
        "operations": [
          "All"
        ],
        "level": "Eligibility",
        "inheritableSettings": [],
        "enforcedSettings": []
      }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleManagementPolicy
{
	Rules = new List<UnifiedRoleManagementPolicyRule>
	{
		new UnifiedRoleManagementPolicyApprovalRule
		{
			OdataType = "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
			Id = "Approval_EndUser_Assignment",
			Target = new UnifiedRoleManagementPolicyRuleTarget
			{
				Caller = "EndUser",
				Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
				{
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				},
				Level = "Assignment",
				InheritableSettings = new List<string>
				{
				},
				EnforcedSettings = new List<string>
				{
				},
			},
			Setting = new ApprovalSettings
			{
				IsApprovalRequired = true,
				IsApprovalRequiredForExtension = false,
				IsRequestorJustificationRequired = true,
				ApprovalMode = "SingleStage",
				ApprovalStages = new List<UnifiedApprovalStage>
				{
					new UnifiedApprovalStage
					{
						ApprovalStageTimeOutInDays = 1,
						IsApproverJustificationRequired = true,
						EscalationTimeInMinutes = 0,
						IsEscalationEnabled = false,
						PrimaryApprovers = new List<SubjectSet>
						{
							new SingleUser
							{
								OdataType = "#microsoft.graph.singleUser",
								Description = null,
								AdditionalData = new Dictionary<string, object>
								{
									{
										"isBackup" , false
									},
									{
										"id" , "c277c8cb-6bb7-42e5-a17f-0add9a718151"
									},
								},
							},
						},
						EscalationApprovers = new List<SubjectSet>
						{
						},
					},
				},
			},
		},
		new UnifiedRoleManagementPolicyAuthenticationContextRule
		{
			OdataType = "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule",
			Id = "AuthenticationContext_EndUser_Assignment",
			IsEnabled = false,
			ClaimValue = "",
			Target = new UnifiedRoleManagementPolicyRuleTarget
			{
				Caller = "EndUser",
				Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
				{
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				},
				Level = "Assignment",
				InheritableSettings = new List<string>
				{
				},
				EnforcedSettings = new List<string>
				{
				},
			},
		},
		new UnifiedRoleManagementPolicyEnablementRule
		{
			OdataType = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
			Id = "Enablement_Admin_Eligibility",
			EnabledRules = new List<string>
			{
			},
			Target = new UnifiedRoleManagementPolicyRuleTarget
			{
				Caller = "Admin",
				Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
				{
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				},
				Level = "Eligibility",
				InheritableSettings = new List<string>
				{
				},
				EnforcedSettings = new List<string>
				{
				},
			},
		},
		new UnifiedRoleManagementPolicyExpirationRule
		{
			OdataType = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
			Id = "Expiration_Admin_Eligibility",
			IsExpirationRequired = true,
			MaximumDuration = TimeSpan.Parse("P365D"),
			Target = new UnifiedRoleManagementPolicyRuleTarget
			{
				Caller = "Admin",
				Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
				{
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				},
				Level = "Eligibility",
				InheritableSettings = new List<string>
				{
				},
				EnforcedSettings = new List<string>
				{
				},
			},
		},
		new UnifiedRoleManagementPolicyNotificationRule
		{
			OdataType = "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
			Id = "Notification_Admin_Admin_Eligibility",
			NotificationType = "Email",
			RecipientType = "Admin",
			NotificationLevel = "All",
			IsDefaultRecipientsEnabled = true,
			NotificationRecipients = new List<string>
			{
			},
			Target = new UnifiedRoleManagementPolicyRuleTarget
			{
				Caller = "Admin",
				Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
				{
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				},
				Level = "Eligibility",
				InheritableSettings = new List<string>
				{
				},
				EnforcedSettings = new List<string>
				{
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicies["{unifiedRoleManagementPolicy-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUnifiedRoleManagementPolicy()


unifiedRoleManagementPolicyRule := graphmodels.NewUnifiedRoleManagementPolicyApprovalRule()
id := "Approval_EndUser_Assignment"
unifiedRoleManagementPolicyRule.SetId(&id) 
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "EndUser"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Assignment"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
unifiedRoleManagementPolicyRule.SetTarget(target)
setting := graphmodels.NewApprovalSettings()
isApprovalRequired := true
setting.SetIsApprovalRequired(&isApprovalRequired) 
isApprovalRequiredForExtension := false
setting.SetIsApprovalRequiredForExtension(&isApprovalRequiredForExtension) 
isRequestorJustificationRequired := true
setting.SetIsRequestorJustificationRequired(&isRequestorJustificationRequired) 
approvalMode := "SingleStage"
setting.SetApprovalMode(&approvalMode) 


unifiedApprovalStage := graphmodels.NewUnifiedApprovalStage()
approvalStageTimeOutInDays := int32(1)
unifiedApprovalStage.SetApprovalStageTimeOutInDays(&approvalStageTimeOutInDays) 
isApproverJustificationRequired := true
unifiedApprovalStage.SetIsApproverJustificationRequired(&isApproverJustificationRequired) 
escalationTimeInMinutes := int32(0)
unifiedApprovalStage.SetEscalationTimeInMinutes(&escalationTimeInMinutes) 
isEscalationEnabled := false
unifiedApprovalStage.SetIsEscalationEnabled(&isEscalationEnabled) 


subjectSet := graphmodels.NewSingleUser()
description := null
subjectSet.SetDescription(&description) 
additionalData := map[string]interface{}{
	isBackup := false
subjectSet.SetIsBackup(&isBackup) 
	"id" : "c277c8cb-6bb7-42e5-a17f-0add9a718151", 
}
subjectSet.SetAdditionalData(additionalData)

primaryApprovers := []graphmodels.SubjectSetable {
	subjectSet,
}
unifiedApprovalStage.SetPrimaryApprovers(primaryApprovers)
escalationApprovers := []graphmodels.SubjectSetable {

}
unifiedApprovalStage.SetEscalationApprovers(escalationApprovers)

approvalStages := []graphmodels.UnifiedApprovalStageable {
	unifiedApprovalStage,
}
setting.SetApprovalStages(approvalStages)
unifiedRoleManagementPolicyRule.SetSetting(setting)
unifiedRoleManagementPolicyRule1 := graphmodels.NewUnifiedRoleManagementPolicyAuthenticationContextRule()
id := "AuthenticationContext_EndUser_Assignment"
unifiedRoleManagementPolicyRule1.SetId(&id) 
isEnabled := false
unifiedRoleManagementPolicyRule1.SetIsEnabled(&isEnabled) 
claimValue := ""
unifiedRoleManagementPolicyRule1.SetClaimValue(&claimValue) 
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "EndUser"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Assignment"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
unifiedRoleManagementPolicyRule1.SetTarget(target)
unifiedRoleManagementPolicyRule2 := graphmodels.NewUnifiedRoleManagementPolicyEnablementRule()
id := "Enablement_Admin_Eligibility"
unifiedRoleManagementPolicyRule2.SetId(&id) 
enabledRules := []string {

}
unifiedRoleManagementPolicyRule2.SetEnabledRules(enabledRules)
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "Admin"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Eligibility"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
unifiedRoleManagementPolicyRule2.SetTarget(target)
unifiedRoleManagementPolicyRule3 := graphmodels.NewUnifiedRoleManagementPolicyExpirationRule()
id := "Expiration_Admin_Eligibility"
unifiedRoleManagementPolicyRule3.SetId(&id) 
isExpirationRequired := true
unifiedRoleManagementPolicyRule3.SetIsExpirationRequired(&isExpirationRequired) 
maximumDuration , err := abstractions.ParseISODuration("P365D")
unifiedRoleManagementPolicyRule3.SetMaximumDuration(&maximumDuration) 
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "Admin"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Eligibility"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
unifiedRoleManagementPolicyRule3.SetTarget(target)
unifiedRoleManagementPolicyRule4 := graphmodels.NewUnifiedRoleManagementPolicyNotificationRule()
id := "Notification_Admin_Admin_Eligibility"
unifiedRoleManagementPolicyRule4.SetId(&id) 
notificationType := "Email"
unifiedRoleManagementPolicyRule4.SetNotificationType(&notificationType) 
recipientType := "Admin"
unifiedRoleManagementPolicyRule4.SetRecipientType(&recipientType) 
notificationLevel := "All"
unifiedRoleManagementPolicyRule4.SetNotificationLevel(&notificationLevel) 
isDefaultRecipientsEnabled := true
unifiedRoleManagementPolicyRule4.SetIsDefaultRecipientsEnabled(&isDefaultRecipientsEnabled) 
notificationRecipients := []string {

}
unifiedRoleManagementPolicyRule4.SetNotificationRecipients(notificationRecipients)
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "Admin"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Eligibility"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
unifiedRoleManagementPolicyRule4.SetTarget(target)

rules := []graphmodels.UnifiedRoleManagementPolicyRuleable {
	unifiedRoleManagementPolicyRule,
	unifiedRoleManagementPolicyRule1,
	unifiedRoleManagementPolicyRule2,
	unifiedRoleManagementPolicyRule3,
	unifiedRoleManagementPolicyRule4,
}
requestBody.SetRules(rules)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleManagementPolicies, err := graphClient.Policies().RoleManagementPolicies().ByUnifiedRoleManagementPolicyId("unifiedRoleManagementPolicy-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicy unifiedRoleManagementPolicy = new UnifiedRoleManagementPolicy();
LinkedList<UnifiedRoleManagementPolicyRule> rules = new LinkedList<UnifiedRoleManagementPolicyRule>();
UnifiedRoleManagementPolicyApprovalRule unifiedRoleManagementPolicyRule = new UnifiedRoleManagementPolicyApprovalRule();
unifiedRoleManagementPolicyRule.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyApprovalRule");
unifiedRoleManagementPolicyRule.setId("Approval_EndUser_Assignment");
UnifiedRoleManagementPolicyRuleTarget target = new UnifiedRoleManagementPolicyRuleTarget();
target.setCaller("EndUser");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target.setOperations(operations);
target.setLevel("Assignment");
LinkedList<String> inheritableSettings = new LinkedList<String>();
target.setInheritableSettings(inheritableSettings);
LinkedList<String> enforcedSettings = new LinkedList<String>();
target.setEnforcedSettings(enforcedSettings);
unifiedRoleManagementPolicyRule.setTarget(target);
ApprovalSettings setting = new ApprovalSettings();
setting.setIsApprovalRequired(true);
setting.setIsApprovalRequiredForExtension(false);
setting.setIsRequestorJustificationRequired(true);
setting.setApprovalMode("SingleStage");
LinkedList<UnifiedApprovalStage> approvalStages = new LinkedList<UnifiedApprovalStage>();
UnifiedApprovalStage unifiedApprovalStage = new UnifiedApprovalStage();
unifiedApprovalStage.setApprovalStageTimeOutInDays(1);
unifiedApprovalStage.setIsApproverJustificationRequired(true);
unifiedApprovalStage.setEscalationTimeInMinutes(0);
unifiedApprovalStage.setIsEscalationEnabled(false);
LinkedList<SubjectSet> primaryApprovers = new LinkedList<SubjectSet>();
SingleUser subjectSet = new SingleUser();
subjectSet.setOdataType("#microsoft.graph.singleUser");
subjectSet.setDescription(null);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("isBackup", false);
additionalData.put("id", "c277c8cb-6bb7-42e5-a17f-0add9a718151");
subjectSet.setAdditionalData(additionalData);
primaryApprovers.add(subjectSet);
unifiedApprovalStage.setPrimaryApprovers(primaryApprovers);
LinkedList<SubjectSet> escalationApprovers = new LinkedList<SubjectSet>();
unifiedApprovalStage.setEscalationApprovers(escalationApprovers);
approvalStages.add(unifiedApprovalStage);
setting.setApprovalStages(approvalStages);
unifiedRoleManagementPolicyRule.setSetting(setting);
rules.add(unifiedRoleManagementPolicyRule);
UnifiedRoleManagementPolicyAuthenticationContextRule unifiedRoleManagementPolicyRule1 = new UnifiedRoleManagementPolicyAuthenticationContextRule();
unifiedRoleManagementPolicyRule1.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule");
unifiedRoleManagementPolicyRule1.setId("AuthenticationContext_EndUser_Assignment");
unifiedRoleManagementPolicyRule1.setIsEnabled(false);
unifiedRoleManagementPolicyRule1.setClaimValue("");
UnifiedRoleManagementPolicyRuleTarget target1 = new UnifiedRoleManagementPolicyRuleTarget();
target1.setCaller("EndUser");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations1 = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations1.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target1.setOperations(operations1);
target1.setLevel("Assignment");
LinkedList<String> inheritableSettings1 = new LinkedList<String>();
target1.setInheritableSettings(inheritableSettings1);
LinkedList<String> enforcedSettings1 = new LinkedList<String>();
target1.setEnforcedSettings(enforcedSettings1);
unifiedRoleManagementPolicyRule1.setTarget(target1);
rules.add(unifiedRoleManagementPolicyRule1);
UnifiedRoleManagementPolicyEnablementRule unifiedRoleManagementPolicyRule2 = new UnifiedRoleManagementPolicyEnablementRule();
unifiedRoleManagementPolicyRule2.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyEnablementRule");
unifiedRoleManagementPolicyRule2.setId("Enablement_Admin_Eligibility");
LinkedList<String> enabledRules = new LinkedList<String>();
unifiedRoleManagementPolicyRule2.setEnabledRules(enabledRules);
UnifiedRoleManagementPolicyRuleTarget target2 = new UnifiedRoleManagementPolicyRuleTarget();
target2.setCaller("Admin");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations2 = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations2.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target2.setOperations(operations2);
target2.setLevel("Eligibility");
LinkedList<String> inheritableSettings2 = new LinkedList<String>();
target2.setInheritableSettings(inheritableSettings2);
LinkedList<String> enforcedSettings2 = new LinkedList<String>();
target2.setEnforcedSettings(enforcedSettings2);
unifiedRoleManagementPolicyRule2.setTarget(target2);
rules.add(unifiedRoleManagementPolicyRule2);
UnifiedRoleManagementPolicyExpirationRule unifiedRoleManagementPolicyRule3 = new UnifiedRoleManagementPolicyExpirationRule();
unifiedRoleManagementPolicyRule3.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyExpirationRule");
unifiedRoleManagementPolicyRule3.setId("Expiration_Admin_Eligibility");
unifiedRoleManagementPolicyRule3.setIsExpirationRequired(true);
PeriodAndDuration maximumDuration = PeriodAndDuration.ofDuration(Duration.parse("P365D"));
unifiedRoleManagementPolicyRule3.setMaximumDuration(maximumDuration);
UnifiedRoleManagementPolicyRuleTarget target3 = new UnifiedRoleManagementPolicyRuleTarget();
target3.setCaller("Admin");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations3 = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations3.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target3.setOperations(operations3);
target3.setLevel("Eligibility");
LinkedList<String> inheritableSettings3 = new LinkedList<String>();
target3.setInheritableSettings(inheritableSettings3);
LinkedList<String> enforcedSettings3 = new LinkedList<String>();
target3.setEnforcedSettings(enforcedSettings3);
unifiedRoleManagementPolicyRule3.setTarget(target3);
rules.add(unifiedRoleManagementPolicyRule3);
UnifiedRoleManagementPolicyNotificationRule unifiedRoleManagementPolicyRule4 = new UnifiedRoleManagementPolicyNotificationRule();
unifiedRoleManagementPolicyRule4.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyNotificationRule");
unifiedRoleManagementPolicyRule4.setId("Notification_Admin_Admin_Eligibility");
unifiedRoleManagementPolicyRule4.setNotificationType("Email");
unifiedRoleManagementPolicyRule4.setRecipientType("Admin");
unifiedRoleManagementPolicyRule4.setNotificationLevel("All");
unifiedRoleManagementPolicyRule4.setIsDefaultRecipientsEnabled(true);
LinkedList<String> notificationRecipients = new LinkedList<String>();
unifiedRoleManagementPolicyRule4.setNotificationRecipients(notificationRecipients);
UnifiedRoleManagementPolicyRuleTarget target4 = new UnifiedRoleManagementPolicyRuleTarget();
target4.setCaller("Admin");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations4 = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations4.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target4.setOperations(operations4);
target4.setLevel("Eligibility");
LinkedList<String> inheritableSettings4 = new LinkedList<String>();
target4.setInheritableSettings(inheritableSettings4);
LinkedList<String> enforcedSettings4 = new LinkedList<String>();
target4.setEnforcedSettings(enforcedSettings4);
unifiedRoleManagementPolicyRule4.setTarget(target4);
rules.add(unifiedRoleManagementPolicyRule4);
unifiedRoleManagementPolicy.setRules(rules);
UnifiedRoleManagementPolicy result = graphClient.policies().roleManagementPolicies().byUnifiedRoleManagementPolicyId("{unifiedRoleManagementPolicy-id}").patch(unifiedRoleManagementPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleManagementPolicy = {
  rules: [
    {
      '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyApprovalRule',
      id: 'Approval_EndUser_Assignment',
      target: {
        caller: 'EndUser',
        operations: [
          'All'
        ],
        level: 'Assignment',
        inheritableSettings: [],
        enforcedSettings: []
      },
      setting: {
        isApprovalRequired: true,
        isApprovalRequiredForExtension: false,
        isRequestorJustificationRequired: true,
        approvalMode: 'SingleStage',
        approvalStages: [
          {
            approvalStageTimeOutInDays: 1,
            isApproverJustificationRequired: true,
            escalationTimeInMinutes: 0,
            isEscalationEnabled: false,
            primaryApprovers: [
              {
                '@odata.type': '#microsoft.graph.singleUser',
                isBackup: false,
                id: 'c277c8cb-6bb7-42e5-a17f-0add9a718151',
                description: null
              }
            ],
            escalationApprovers: []
          }
        ]
      }
    },
    {
      '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule',
      id: 'AuthenticationContext_EndUser_Assignment',
      isEnabled: false,
      claimValue: '',
      target: {
        caller: 'EndUser',
        operations: [
          'All'
        ],
        level: 'Assignment',
        inheritableSettings: [],
        enforcedSettings: []
      }
    },
    {
      '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyEnablementRule',
      id: 'Enablement_Admin_Eligibility',
      enabledRules: [],
      target: {
        caller: 'Admin',
        operations: [
          'All'
        ],
        level: 'Eligibility',
        inheritableSettings: [],
        enforcedSettings: []
      }
    },
    {
      '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyExpirationRule',
      id: 'Expiration_Admin_Eligibility',
      isExpirationRequired: true,
      maximumDuration: 'P365D',
      target: {
        caller: 'Admin',
        operations: [
          'All'
        ],
        level: 'Eligibility',
        inheritableSettings: [],
        enforcedSettings: []
      }
    },
    {
      '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyNotificationRule',
      id: 'Notification_Admin_Admin_Eligibility',
      notificationType: 'Email',
      recipientType: 'Admin',
      notificationLevel: 'All',
      isDefaultRecipientsEnabled: true,
      notificationRecipients: [],
      target: {
        caller: 'Admin',
        operations: [
          'All'
        ],
        level: 'Eligibility',
        inheritableSettings: [],
        enforcedSettings: []
      }
    }
  ]
};

await client.api('/policies/roleManagementPolicies/Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369')
	.update(unifiedRoleManagementPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicy;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyApprovalRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTarget;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTargetOperations;
use Microsoft\Graph\Generated\Models\ApprovalSettings;
use Microsoft\Graph\Generated\Models\UnifiedApprovalStage;
use Microsoft\Graph\Generated\Models\SubjectSet;
use Microsoft\Graph\Generated\Models\SingleUser;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyAuthenticationContextRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyEnablementRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyExpirationRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyNotificationRule;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleManagementPolicy();
$rulesUnifiedRoleManagementPolicyRule1 = new UnifiedRoleManagementPolicyApprovalRule();
$rulesUnifiedRoleManagementPolicyRule1->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyApprovalRule');
$rulesUnifiedRoleManagementPolicyRule1->setId('Approval_EndUser_Assignment');
$rulesUnifiedRoleManagementPolicyRule1Target = new UnifiedRoleManagementPolicyRuleTarget();
$rulesUnifiedRoleManagementPolicyRule1Target->setCaller('EndUser');
$rulesUnifiedRoleManagementPolicyRule1Target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),	]);
$rulesUnifiedRoleManagementPolicyRule1Target->setLevel('Assignment');
$rulesUnifiedRoleManagementPolicyRule1Target->setInheritableSettings([	]);
$rulesUnifiedRoleManagementPolicyRule1Target->setEnforcedSettings([	]);
$rulesUnifiedRoleManagementPolicyRule1->setTarget($rulesUnifiedRoleManagementPolicyRule1Target);
$rulesUnifiedRoleManagementPolicyRule1Setting = new ApprovalSettings();
$rulesUnifiedRoleManagementPolicyRule1Setting->setIsApprovalRequired(true);
$rulesUnifiedRoleManagementPolicyRule1Setting->setIsApprovalRequiredForExtension(false);
$rulesUnifiedRoleManagementPolicyRule1Setting->setIsRequestorJustificationRequired(true);
$rulesUnifiedRoleManagementPolicyRule1Setting->setApprovalMode('SingleStage');
$approvalStagesUnifiedApprovalStage1 = new UnifiedApprovalStage();
$approvalStagesUnifiedApprovalStage1->setApprovalStageTimeOutInDays(1);
$approvalStagesUnifiedApprovalStage1->setIsApproverJustificationRequired(true);
$approvalStagesUnifiedApprovalStage1->setEscalationTimeInMinutes(0);
$approvalStagesUnifiedApprovalStage1->setIsEscalationEnabled(false);
$primaryApproversSubjectSet1 = new SingleUser();
$primaryApproversSubjectSet1->setOdataType('#microsoft.graph.singleUser');
$primaryApproversSubjectSet1->setDescription(null);
$additionalData = [
	'isBackup' => false,
	'id' => 'c277c8cb-6bb7-42e5-a17f-0add9a718151',
];
$primaryApproversSubjectSet1->setAdditionalData($additionalData);
$primaryApproversArray []= $primaryApproversSubjectSet1;
$approvalStagesUnifiedApprovalStage1->setPrimaryApprovers($primaryApproversArray);

$approvalStagesUnifiedApprovalStage1->setEscalationApprovers([]);
$approvalStagesArray []= $approvalStagesUnifiedApprovalStage1;
$rulesUnifiedRoleManagementPolicyRule1Setting->setApprovalStages($approvalStagesArray);

$rulesUnifiedRoleManagementPolicyRule1->setSetting($rulesUnifiedRoleManagementPolicyRule1Setting);
$rulesArray []= $rulesUnifiedRoleManagementPolicyRule1;
$rulesUnifiedRoleManagementPolicyRule2 = new UnifiedRoleManagementPolicyAuthenticationContextRule();
$rulesUnifiedRoleManagementPolicyRule2->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule');
$rulesUnifiedRoleManagementPolicyRule2->setId('AuthenticationContext_EndUser_Assignment');
$rulesUnifiedRoleManagementPolicyRule2->setIsEnabled(false);
$rulesUnifiedRoleManagementPolicyRule2->setClaimValue('');
$rulesUnifiedRoleManagementPolicyRule2Target = new UnifiedRoleManagementPolicyRuleTarget();
$rulesUnifiedRoleManagementPolicyRule2Target->setCaller('EndUser');
$rulesUnifiedRoleManagementPolicyRule2Target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),]);
$rulesUnifiedRoleManagementPolicyRule2Target->setLevel('Assignment');
$rulesUnifiedRoleManagementPolicyRule2Target->setInheritableSettings([]);
$rulesUnifiedRoleManagementPolicyRule2Target->setEnforcedSettings([]);
$rulesUnifiedRoleManagementPolicyRule2->setTarget($rulesUnifiedRoleManagementPolicyRule2Target);
$rulesArray []= $rulesUnifiedRoleManagementPolicyRule2;
$rulesUnifiedRoleManagementPolicyRule3 = new UnifiedRoleManagementPolicyEnablementRule();
$rulesUnifiedRoleManagementPolicyRule3->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyEnablementRule');
$rulesUnifiedRoleManagementPolicyRule3->setId('Enablement_Admin_Eligibility');
$rulesUnifiedRoleManagementPolicyRule3->setEnabledRules([]);
$rulesUnifiedRoleManagementPolicyRule3Target = new UnifiedRoleManagementPolicyRuleTarget();
$rulesUnifiedRoleManagementPolicyRule3Target->setCaller('Admin');
$rulesUnifiedRoleManagementPolicyRule3Target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),]);
$rulesUnifiedRoleManagementPolicyRule3Target->setLevel('Eligibility');
$rulesUnifiedRoleManagementPolicyRule3Target->setInheritableSettings([]);
$rulesUnifiedRoleManagementPolicyRule3Target->setEnforcedSettings([]);
$rulesUnifiedRoleManagementPolicyRule3->setTarget($rulesUnifiedRoleManagementPolicyRule3Target);
$rulesArray []= $rulesUnifiedRoleManagementPolicyRule3;
$rulesUnifiedRoleManagementPolicyRule4 = new UnifiedRoleManagementPolicyExpirationRule();
$rulesUnifiedRoleManagementPolicyRule4->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyExpirationRule');
$rulesUnifiedRoleManagementPolicyRule4->setId('Expiration_Admin_Eligibility');
$rulesUnifiedRoleManagementPolicyRule4->setIsExpirationRequired(true);
$rulesUnifiedRoleManagementPolicyRule4->setMaximumDuration(new \DateInterval('P365D'));
$rulesUnifiedRoleManagementPolicyRule4Target = new UnifiedRoleManagementPolicyRuleTarget();
$rulesUnifiedRoleManagementPolicyRule4Target->setCaller('Admin');
$rulesUnifiedRoleManagementPolicyRule4Target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),]);
$rulesUnifiedRoleManagementPolicyRule4Target->setLevel('Eligibility');
$rulesUnifiedRoleManagementPolicyRule4Target->setInheritableSettings([]);
$rulesUnifiedRoleManagementPolicyRule4Target->setEnforcedSettings([]);
$rulesUnifiedRoleManagementPolicyRule4->setTarget($rulesUnifiedRoleManagementPolicyRule4Target);
$rulesArray []= $rulesUnifiedRoleManagementPolicyRule4;
$rulesUnifiedRoleManagementPolicyRule5 = new UnifiedRoleManagementPolicyNotificationRule();
$rulesUnifiedRoleManagementPolicyRule5->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyNotificationRule');
$rulesUnifiedRoleManagementPolicyRule5->setId('Notification_Admin_Admin_Eligibility');
$rulesUnifiedRoleManagementPolicyRule5->setNotificationType('Email');
$rulesUnifiedRoleManagementPolicyRule5->setRecipientType('Admin');
$rulesUnifiedRoleManagementPolicyRule5->setNotificationLevel('All');
$rulesUnifiedRoleManagementPolicyRule5->setIsDefaultRecipientsEnabled(true);
$rulesUnifiedRoleManagementPolicyRule5->setNotificationRecipients([]);
$rulesUnifiedRoleManagementPolicyRule5Target = new UnifiedRoleManagementPolicyRuleTarget();
$rulesUnifiedRoleManagementPolicyRule5Target->setCaller('Admin');
$rulesUnifiedRoleManagementPolicyRule5Target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),]);
$rulesUnifiedRoleManagementPolicyRule5Target->setLevel('Eligibility');
$rulesUnifiedRoleManagementPolicyRule5Target->setInheritableSettings([]);
$rulesUnifiedRoleManagementPolicyRule5Target->setEnforcedSettings([]);
$rulesUnifiedRoleManagementPolicyRule5->setTarget($rulesUnifiedRoleManagementPolicyRule5Target);
$rulesArray []= $rulesUnifiedRoleManagementPolicyRule5;
$requestBody->setRules($rulesArray);


$result = $graphServiceClient->policies()->roleManagementPolicies()->byUnifiedRoleManagementPolicyId('unifiedRoleManagementPolicy-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	rules = @(
		@{
			"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule"
			id = "Approval_EndUser_Assignment"
			target = @{
				caller = "EndUser"
				operations = @(
				"All"
			)
			level = "Assignment"
			inheritableSettings = @(
			)
			enforcedSettings = @(
			)
		}
		setting = @{
			isApprovalRequired = $true
			isApprovalRequiredForExtension = $false
			isRequestorJustificationRequired = $true
			approvalMode = "SingleStage"
			approvalStages = @(
				@{
					approvalStageTimeOutInDays = 
					isApproverJustificationRequired = $true
					escalationTimeInMinutes = 
					isEscalationEnabled = $false
					primaryApprovers = @(
						@{
							"@odata.type" = "#microsoft.graph.singleUser"
							isBackup = $false
							id = "c277c8cb-6bb7-42e5-a17f-0add9a718151"
							description = $null
						}
					)
					escalationApprovers = @(
					)
				}
			)
		}
	}
	@{
		"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule"
		id = "AuthenticationContext_EndUser_Assignment"
		isEnabled = $false
		claimValue = ""
		target = @{
			caller = "EndUser"
			operations = @(
			"All"
		)
		level = "Assignment"
		inheritableSettings = @(
		)
		enforcedSettings = @(
		)
	}
}
@{
	"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule"
	id = "Enablement_Admin_Eligibility"
	enabledRules = @(
	)
	target = @{
		caller = "Admin"
		operations = @(
		"All"
	)
	level = "Eligibility"
	inheritableSettings = @(
	)
	enforcedSettings = @(
	)
}
}
@{
"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule"
id = "Expiration_Admin_Eligibility"
isExpirationRequired = $true
maximumDuration = "P365D"
target = @{
	caller = "Admin"
	operations = @(
	"All"
)
level = "Eligibility"
inheritableSettings = @(
)
enforcedSettings = @(
)
}
}
@{
"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule"
id = "Notification_Admin_Admin_Eligibility"
notificationType = "Email"
recipientType = "Admin"
notificationLevel = "All"
isDefaultRecipientsEnabled = $true
notificationRecipients = @(
)
target = @{
caller = "Admin"
operations = @(
"All"
)
level = "Eligibility"
inheritableSettings = @(
)
enforcedSettings = @(
)
}
}
)
}

Update-MgPolicyRoleManagementPolicy -UnifiedRoleManagementPolicyId $unifiedRoleManagementPolicyId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_management_policy import UnifiedRoleManagementPolicy
from msgraph.generated.models.unified_role_management_policy_rule import UnifiedRoleManagementPolicyRule
from msgraph.generated.models.unified_role_management_policy_approval_rule import UnifiedRoleManagementPolicyApprovalRule
from msgraph.generated.models.unified_role_management_policy_rule_target import UnifiedRoleManagementPolicyRuleTarget
from msgraph.generated.models.unified_role_management_policy_rule_target_operations import UnifiedRoleManagementPolicyRuleTargetOperations
from msgraph.generated.models.approval_settings import ApprovalSettings
from msgraph.generated.models.unified_approval_stage import UnifiedApprovalStage
from msgraph.generated.models.subject_set import SubjectSet
from msgraph.generated.models.single_user import SingleUser
from msgraph.generated.models.unified_role_management_policy_authentication_context_rule import UnifiedRoleManagementPolicyAuthenticationContextRule
from msgraph.generated.models.unified_role_management_policy_enablement_rule import UnifiedRoleManagementPolicyEnablementRule
from msgraph.generated.models.unified_role_management_policy_expiration_rule import UnifiedRoleManagementPolicyExpirationRule
from msgraph.generated.models.unified_role_management_policy_notification_rule import UnifiedRoleManagementPolicyNotificationRule
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleManagementPolicy(
	rules = [
		UnifiedRoleManagementPolicyApprovalRule(
			odata_type = "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
			id = "Approval_EndUser_Assignment",
			target = UnifiedRoleManagementPolicyRuleTarget(
				caller = "EndUser",
				operations = [
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				],
				level = "Assignment",
				inheritable_settings = [
				],
				enforced_settings = [
				],
			),
			setting = ApprovalSettings(
				is_approval_required = True,
				is_approval_required_for_extension = False,
				is_requestor_justification_required = True,
				approval_mode = "SingleStage",
				approval_stages = [
					UnifiedApprovalStage(
						approval_stage_time_out_in_days = 1,
						is_approver_justification_required = True,
						escalation_time_in_minutes = 0,
						is_escalation_enabled = False,
						primary_approvers = [
							SingleUser(
								odata_type = "#microsoft.graph.singleUser",
								description = None,
								additional_data = {
										"is_backup" : False,
										"id" : "c277c8cb-6bb7-42e5-a17f-0add9a718151",
								}
							),
						],
						escalation_approvers = [
						],
					),
				],
			),
		),
		UnifiedRoleManagementPolicyAuthenticationContextRule(
			odata_type = "#microsoft.graph.unifiedRoleManagementPolicyAuthenticationContextRule",
			id = "AuthenticationContext_EndUser_Assignment",
			is_enabled = False,
			claim_value = "",
			target = UnifiedRoleManagementPolicyRuleTarget(
				caller = "EndUser",
				operations = [
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				],
				level = "Assignment",
				inheritable_settings = [
				],
				enforced_settings = [
				],
			),
		),
		UnifiedRoleManagementPolicyEnablementRule(
			odata_type = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
			id = "Enablement_Admin_Eligibility",
			enabled_rules = [
			],
			target = UnifiedRoleManagementPolicyRuleTarget(
				caller = "Admin",
				operations = [
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				],
				level = "Eligibility",
				inheritable_settings = [
				],
				enforced_settings = [
				],
			),
		),
		UnifiedRoleManagementPolicyExpirationRule(
			odata_type = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
			id = "Expiration_Admin_Eligibility",
			is_expiration_required = True,
			maximum_duration = "P365D",
			target = UnifiedRoleManagementPolicyRuleTarget(
				caller = "Admin",
				operations = [
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				],
				level = "Eligibility",
				inheritable_settings = [
				],
				enforced_settings = [
				],
			),
		),
		UnifiedRoleManagementPolicyNotificationRule(
			odata_type = "#microsoft.graph.unifiedRoleManagementPolicyNotificationRule",
			id = "Notification_Admin_Admin_Eligibility",
			notification_type = "Email",
			recipient_type = "Admin",
			notification_level = "All",
			is_default_recipients_enabled = True,
			notification_recipients = [
			],
			target = UnifiedRoleManagementPolicyRuleTarget(
				caller = "Admin",
				operations = [
					UnifiedRoleManagementPolicyRuleTargetOperations.All,
				],
				level = "Eligibility",
				inheritable_settings = [
				],
				enforced_settings = [
				],
			),
		),
	],
)

result = await graph_client.policies.role_management_policies.by_unified_role_management_policy_id('unifiedRoleManagementPolicy-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicies/$entity",
    "id": "Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369",
    "displayName": "Group",
    "description": "Group",
    "isOrganizationDefault": false,
    "scopeId": "60bba733-f09d-49b7-8445-32369aa066b3",
    "scopeType": "Group",
    "lastModifiedDateTime": "2023-10-01T23:29:43.687Z",
    "lastModifiedBy": {
        "displayName": "Test User 1",
        "id": null
    }
}
```
