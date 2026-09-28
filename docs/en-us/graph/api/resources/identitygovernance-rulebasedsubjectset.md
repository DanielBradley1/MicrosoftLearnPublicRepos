<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-rulebasedsubjectset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# ruleBasedSubjectSet resource type

Namespace: microsoft.graph.identityGovernance

Specifies the rules that define the subjects in scope for a lifecycle workflow. This object is configured in the **scope** property of the [triggerAndScopeBasedConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-triggerandscopebasedconditions?view=graph-rest-1.0) resource.

Inherits from [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| rule | String | The rule for the subject set. Lifecycle Workflows supports a rich set of [user properties](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#properties) for configuring the rules using `$filter` query expressions. For more information, see [supported user and query parameters](#supported-user-properties-and-query-parameters). |

### Supported user properties and query parameters

Lifecycle Workflows supports the following user properties for configuring the rules that are in the scope of an execution condition. You can use the `$filter` OData query parameter with either the `eq`, `ne`, `in`, or `startsWith` operators. You can also combine the filter expressions using one of the following conjunction and disjunction operators:

- `and`
- `or`
- `and` and `not`
- `or` and `not`

| User property | Property type | Supports eq, ne, in | Supports startsWith |
| --- | --- | --- | --- |
| accountEnabled | Boolean | ✔️ |  |
| assignedPlans/any\(a:a/capabilityStatus\) | assignedPlan collection | ✔️ |  |
| assignedPlans/any\(a:a/service\) | assignedPlan collection | ✔️ |  |
| assignedPlans/any\(a:a/servicePlanId\) | assignedPlan collection | ✔️ |  |
| city | String | ✔️ | ✔️ |
| companyName | String | ✔️ | ✔️ |
| country | String | ✔️ | ✔️ |
| department | String | ✔️ | ✔️ |
| displayName | String | ✔️ | ✔️ |
| employeeId | String | ✔️ |  |
| employeeOrgData/costCenter | employeeOrgData | ✔️ |  |
| employeeOrgData/division | employeeOrgData | ✔️ |  |
| employeeType | String | ✔️ |  |
| faxNumber | String | ✔️ | ✔️ |
| givenName | String | ✔️ | ✔️ |
| jobTitle | String | ✔️ | ✔️ |
| mail | String | ✔️ | ✔️ |
| mailNickname | String | ✔️ | ✔️ |
| mobilePhone | String | ✔️ | ✔️ |
| officeLocation | String | ✔️ | ✔️ |
| onPremisesExtensionAttributes/extensionAttribute1 - 15 | onPremisesExtensionAttributes | ✔️ |  |
| onPremisesSecurityIdentifier | String | ✔️ |  |
| onPremisesSyncEnabled | Boolean | ✔️ |  |
| otherMails/any\(p:p\) | String Collection | ✔️ | ✔️ |
| postalCode | String | ✔️ | ✔️ |
| preferredLanguage | String | ✔️ | ✔️ |
| proxyAddresses/any\(p:p\) | String collection | ✔️ | ✔️ |
| state | String | ✔️ | ✔️ |
| streetAddress | String | ✔️ | ✔️ |
| surname | String | ✔️ | ✔️ |
| usageLocation | String | ✔️ | ✔️ |
| userPrincipalName | String | ✔️ | ✔️ |
| userType | String | ✔️ |  |

You can also configure rules using [Directory \(Microsoft Entra ID\) extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview#directory-azure-ad-extensions) and [custom security attributes](https://learn.microsoft.com/en-us/graph/api/resources/custom-security-attributes-overview). It is not supported to configure rules with schema extensions or open extensions.

Note

Using custom security attributes requires the Attribute Assignment Administrator role. For more information, see: [Attribute Assignment Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#attribute-assignment-administrator).

#### Examples of rules

| Example rule | Description |
| --- | --- |
| `"rule": "(department eq 'Marketing')"` | Run the workflow for users in the "Marketing" department. |
| `"rule": "(department ne 'Marketing')"` | Run the workflow for users not in the "Marketing" department. |
| `"rule": "(department in ('Marketing'))"` | Run the workflow for users in the "Marketing" department. |
| `"rule": "(accountEnabled eq true)"` | Run the workflow for users whose account is enabled. |
| `"rule": "(employeeOrgData/costCenter eq '100')"` | Run the workflow for users whose costCenter is `100`. |
| `"rule": "(otherMails/any(p:startsWith(p, 'Av')))"` | Run the workflow for users whose **otherMails** starts with `Av`. |
| `"rule": "(department eq 'Marketing') and (accountEnabled in (true))"` | Run the workflow for users in the marketing department and whose account is enabled. |
| `"rule": "(department eq 'Marketing') or (not (city eq 'Redmond'))"` | Run the workflow for users in the marketing department and whose city is not "Redmond". |
| `"rule": "(customSecurityAttributes/OnsightLocation/CustomerOnsite eq true)"` | Run the workflow for users who have the custom security attribute for **CustomerOnSite** set as `true`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
  "rule": "String"
}
```
