<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-12 -->

# operationApprovalPolicy resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The OperationApprovalPolicy entity allows an administrator to configure which operations require admin approval and the set of admins who can perform that approval. Creating a policy enables the multiple admin approval service to catch requests which are targeted by the specific policy type defined.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List operationApprovalPolicies](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalpolicy-list?view=graph-rest-beta) | [operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta) collection | List properties and relationships of the [operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta) objects. |
| [Get operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalpolicy-get?view=graph-rest-beta) | [operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta) | Read properties and relationships of the [operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta) object. |
| [Create operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalpolicy-create?view=graph-rest-beta) | [operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta) | Create a new [operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta) object. |
| [Delete operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalpolicy-delete?view=graph-rest-beta) | None | Deletes a [operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta). |
| [Update operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalpolicy-update?view=graph-rest-beta) | [operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta) | Update the properties of a [operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta) object. |
| [retrieveApprovableOperations function](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalpolicy-retrieveapprovableoperations?view=graph-rest-beta) | [operationApprovalPolicySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicyset?view=graph-rest-beta) collection |  |
| [retrieveOperationsRequiringApproval function](https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalpolicy-retrieveoperationsrequiringapproval?view=graph-rest-beta) | [operationApprovalPolicySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicyset?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the policy. This ID is assigned at when the policy is created. Read-only. This property is read-only. |
| displayName | String | Indicates the display name of the policy. Maximum length of the display name is 128 characters. This property is required when the policy is created, and is defined by the IT Admins to identify the policy. |
| description | String | Indicates the description of the policy. Maximum length of the description is 1024 characters. This property is not required, but can be used by the IT Admin to describe the policy. |
| lastModifiedDateTime | DateTimeOffset | Indicates the last DateTime that the policy was modified. The value cannot be modified and is automatically populated whenever values in the request are updated. For example, when the 'policyType' property changes from `apps` to `scripts`. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Returned by default. Read-only. This property is read-only. |
| policyType | [operationApprovalPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicytype?view=graph-rest-beta) | The policy type for the OperationApprovalPolicy. Possible values are: `unknown`, `app`, `script`, `operationApprovalPolicy`. Possible values are: `unknown`, `deviceAction`, `deviceWipe`, `deviceRetire`, `deviceRetireNonCompliant`, `deviceDelete`, `deviceLock`, `deviceErase`, `deviceDisableActivationLock`, `windowsEnrollment`, `compliancePolicy`, `configurationPolicy`, `appProtectionPolicy`, `policySet`, `filter`, `endpointSecurityPolicy`, `app`, `script`, `role`, `deviceResetPasscode`, `unknownFutureValue`, `operationApprovalPolicy`, `autopilot`, `windows365`, `deviceEnrollment`, `deviceUpdate`, `enrollmentRestriction`, `tenantConfiguration`, `tunnel`, `endpointPrivilegeManagement`, `deviceSecurityAction`. |
| policyPlatform | [operationApprovalPolicyPlatform](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicyplatform?view=graph-rest-beta) | Indicates the applicable platform for the policy. Possible values are: `notApplicable`, `androidDeviceAdministrator`, `androidEnterprise`, `iOSiPadOS`, `macOS`, `windows10AndLater`, `windows81AndLater`, `windows10X`. Default value is `notApplicable`. Possible values are: `notApplicable`, `androidDeviceAdministrator`, `androidEnterprise`, `iOSiPadOS`, `macOS`, `windows10AndLater`, `windows81AndLater`, `windows10X`, `unknownFutureValue`. |
| policySet | [operationApprovalPolicySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicyset?view=graph-rest-beta) | Indicates areas of the Intune UX that could support MAA UX for the current logged in IT Admin. This property is required, and is defined by the IT Admins in order to correctly show the expected experience. |
| approverGroupIds | String collection | The Microsoft Entra ID \(Azure AD\) security group IDs for the approvers for the policy. This property is required when the policy is created, and is defined by the IT Admins to define the possible approvers for the policy. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.operationApprovalPolicy",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "policyType": "String",
  "policyPlatform": "String",
  "policySet": {
    "@odata.type": "microsoft.graph.operationApprovalPolicySet",
    "policyType": "String",
    "policyPlatform": "String"
  },
  "approverGroupIds": [
    "String"
  ]
}
```
