<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestrequirements?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageAssignmentRequestRequirements resource type

Namespace: microsoft.graph

Represents requirements that a caller must fulfill in order to successfully create an **accessPackageAssignmentRequest** for the **accessPackage** specified as part of the URL. Requirements are determined by evaluating policies associated with the **accessPackage**.

This object is returned by the [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) [getApplicablePolicyRequirements](https://learn.microsoft.com/en-us/graph/api/accesspackage-getapplicablepolicyrequirements?view=graph-rest-1.0) action for the **accessPackage** in the request URL.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowCustomAssignmentSchedule | Boolean | Indicates whether the requestor is allowed to set a custom schedule. |
| isApprovalRequiredForAdd | Boolean | Indicates whether a request to add must be approved by an approver. |
| isApprovalRequiredForUpdate | Boolean | Indicates whether a request to update must be approved by an approver. |
| isRequestorJustificationRequired | Boolean | Indicates whether requestors must justify requesting access to an access package. |
| policyDescription | String | The description of the policy that the user is trying to request access using. |
| policyDisplayName | String | The display name of the policy that the user is trying to request access using. |
| policyId | String | The identifier of the policy that these requirements are associated with. This identifier can be used when creating a new assignment request. |
| questions | [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0) collection | Questions that are configured on the policy. The questions can be required or optional; callers can determine whether a question is required or optional based on the **isRequired** property on **accessPackageQuestion**. |
| schedule | [entitlementManagementSchedule](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagementschedule?view=graph-rest-1.0) | Schedule restrictions enforced, if any. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentRequestRequirements",
  "allowCustomAssignmentSchedule": "Boolean",
  "isApprovalRequiredForAdd": "Boolean",
  "isApprovalRequiredForUpdate": "Boolean",
  "isRequestorJustificationRequired": "Boolean",
  "policyDisplayName": "String",
  "policyDescription": "String",
  "policyId": "String",
  "schedule": {
    "@odata.type": "microsoft.graph.entitlementManagementSchedule"
  },
  "questions": [
    {
      "@odata.type": "microsoft.graph.accessPackageQuestion"
    }
  ]
}
```
