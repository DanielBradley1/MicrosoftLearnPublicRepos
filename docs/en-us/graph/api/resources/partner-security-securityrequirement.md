<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-31 -->

# securityRequirement resource type

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the base type for security requirement objects.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityscore-list-requirements?view=graph-rest-beta) | [microsoft.graph.partner.security.securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta) collection | Get a list of the [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/partner-security-securityrequirement-get?view=graph-rest-beta) | [microsoft.graph.partner.security.securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta) | Read the properties and relationships of a [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionUrl | String | The link to the site where the admin can take action on the requirement. |
| complianceStatus | microsoft.graph.partner.security.complianceStatus | Indicates whether the partner is compliant with this requirement. The possible values are: `compliant`, `noncomplaint`, `unknownFutureValue`. |
| helpUrl | String | The link to documentation for the requirement. |
| id | String | The unique identifier for the requirement. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| maxScore | Int64 | The maximum score possible for the requirement. |
| requirementType | microsoft.graph.partner.security.securityRequirementType | The type of requirement. The possible values are: `mfaEnforcedForAdmins`, `mfaEnforcedForAdminsOfCustomers`, `securityAlertsPromptlyResolved`, `securityContactProvided`, `spendingBudgetSetForCustomerAzureSubscriptions`, `unknownFutureValue`. |
| score | Int64 | The score received for this requirement. |
| state | microsoft.graph.partner.security.securityRequirementState | Indicates whether the requirement is in preview or is fully released. The possible values are: `active`, `preview`, `unknownFutureValue`. |
| updatedDateTime | DateTimeOffset | The date the requirement properties were last updated. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partner.security.securityRequirement",
  "id": "String (identifier)",
  "requirementType": "String",
  "complianceStatus": "String",
  "actionUrl": "String",
  "helpUrl": "String",
  "score": "Integer",
  "maxScore": "Integer",
  "state": "String",
  "updatedDateTime": "String (timestamp)"
}
```
