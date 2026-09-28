<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamsuserconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-19 -->

# teamsUserConfiguration resource type

Namespace: microsoft.graph.teamsAdministration

Contains information of users who have accounts hosted on Microsoft Teams.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/teamsadministration-teamsadminroot-list-userconfigurations?view=graph-rest-1.0) | [microsoft.graph.teamsAdministration.teamsUserConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamsuserconfiguration?view=graph-rest-1.0) collection | Get [user configurations](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamsuserconfiguration?view=graph-rest-1.0) for all Teams users who belong to a tenant. |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamsadministration-teamsuserconfiguration-get?view=graph-rest-1.0) | [microsoft.graph.teamsAdministration.teamsUserConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamsuserconfiguration?view=graph-rest-1.0) | Read the Teams [user configurations](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamsuserconfiguration?view=graph-rest-1.0) for a specific user using their ID \(the user's identifier\). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountType | microsoft.graph.teamsAdministration.accountType | The type of the account in the Teams context. The possible values are: `user`, `resourceAccount`, `guest`, `sfbOnPremUser`, `unknown`, `unknownFutureValue`, `ineligibleUser`. Use the `Prefer: include-unknown-enum-members` request header to get the following value from this enum [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `ineligibleUser`. |
| createdDateTime | DateTimeOffset | The date and time when the user was created. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| effectivePolicyAssignments | [microsoft.graph.teamsAdministration.effectivePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-effectivepolicyassignment?view=graph-rest-1.0) collection | Contains the user's effective policy assignments, with each assignment including **policyType** and **policyAssignment** details. |
| featureTypes | String collection | The Teams features enabled for a given user based on licensing or service plan. |
| id | String | The unique identifier \(GUID\) for a user in Microsoft Entra. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnterpriseVoiceEnabled | Boolean | Indicates whether voice capability is enabled. |
| modifiedDateTime | DateTimeOffset | The date and time when the user's details were last modified. The system updates this value each time the user's details are changed. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| telephoneNumbers | [microsoft.graph.teamsAdministration.assignedTelephoneNumber](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-assignedtelephonenumber?view=graph-rest-1.0) collection | Includes both the phone number and its corresponding assignment category. The assignment category can include values such as `primary`, `private`, and `alternate`. |
| tenantId | String | The unique identifier of the tenant in Entra to which this user is assigned. |
| userPrincipalName | String | The sign-in address of the user. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| user | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | Represents an Entra user account. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAdministration.teamsUserConfiguration",
  "accountType": "String",
  "createdDateTime": "String (timestamp)",
  "effectivePolicyAssignments": [{"@odata.type": "microsoft.graph.teamsAdministration.effectivePolicyAssignment"}],
  "featureTypes": ["String"],
  "id": "String (identifier)",
  "isEnterpriseVoiceEnabled": "Boolean",
  "modifiedDateTime": "String (timestamp)",
  "telephoneNumbers": [{"@odata.type": "microsoft.graph.teamsAdministration.assignedTelephoneNumber"}],
  "tenantId": "String",
  "userPrincipalName": "String"
}
```
