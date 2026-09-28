<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-customersspendingbudgetsecurityrequirement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-31 -->

# customersSpendingBudgetSecurityRequirement resource type

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the security requirement to have a customer spending budget for all customers. All of a partner's customers are expected to have a spending budget set by the partner to track and control Azure spending.

This requirement aggregates the partner's customers and tracks if they have an Azure spending budget.

Inherits from [microsoft.graph.partner.security.securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionUrl | String | The link to the site where the admin can take action on the requirement. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |
| complianceStatus | microsoft.graph.partner.security.complianceStatus | Indicates whether the partner is compliant with this requirement. Inherited from [microsoft.graph.partner.security.securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). The possible values are: `compliant`, `noncomplaint`, `unknownFutureValue`. |
| customersWithSpendBudgetCount | Int64 | The number of customers with a spending budget set. |
| helpUrl | String | The link to documentation for the requirement. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |
| id | String | The unique identifier for the requirement. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |
| maxScore | Int64 | The maximum score possible for the requirement. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |
| requirementType | microsoft.graph.partner.security.securityRequirementType | The value of this property is always `spendingBudgetSetForCustomerAzureSubscriptions` for this resource. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). The possible values are: `mfaEnforcedForAdmins`, `mfaEnforcedForAdminsOfCustomers`, `securityAlertsPromptlyResolved`, `securityContactProvided`, `spendingBudgetSetForCustomerAzureSubscriptions`, `unknownFutureValue`. |
| score | Int64 | The score received for this requirement. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |
| state | microsoft.graph.partner.security.securityRequirementState | Indicates whether the requirement is in preview or is fully released. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). The possible values are: `active`, `preview`, `unknownFutureValue`. |
| totalCustomersCount | Int64 | The total number of customers associated with the partner. |
| updatedDateTime | DateTimeOffset | The date the requirement properties were last updated. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partner.security.customersSpendingBudgetSecurityRequirement",
  "id": "String (identifier)",
  "requirementType": "String",
  "complianceStatus": "String",
  "actionUrl": "String",
  "helpUrl": "String",
  "score": "Integer",
  "maxScore": "Integer",
  "state": "String",
  "updatedDateTime": "String (timestamp)",
  "totalCustomersCount": "Integer",
  "customersWithSpendBudgetCount": "Integer"
}
```
