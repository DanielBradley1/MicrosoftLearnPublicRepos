<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-credentialuserregistrationssummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# credentialUserRegistrationsSummary resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a summary of Microsoft Entra credential user registrations for a given managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List credential user registration summaries](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-credentialuserregistrationssummaries?view=graph-rest-beta) | [microsoft.graph.managedTenants.credentialUserRegistrationsSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-credentialuserregistrationssummary?view=graph-rest-beta) collection | Get a list of the [credentialUserRegistrationsSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-credentialuserregistrationssummary?view=graph-rest-beta) objects and their properties. |
| [Get credential user registrations summary](https://learn.microsoft.com/en-us/graph/api/managedtenants-credentialuserregistrationssummary-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.credentialUserRegistrationsSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-credentialuserregistrationssummary?view=graph-rest-beta) | Read the properties and relationships of a [credentialUserRegistrationsSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-credentialuserregistrationssummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for this entity. Required. Read-only. |
| lastRefreshedDateTime | DateTimeOffset | Date and time the entity was last updated in the multi-tenant management platform. Optional. Read-only. |
| mfaAndSsprCapableUserCount | Int32 | The number of users that are capable of performing multi-factor authentication or self service password reset. Optional. Read-only. |
| mfaConditionalAccessPolicyState | String | The state of a conditional access policy that enforces multi-factor authentication. Optional. Read-only. |
| mfaExcludedUserCount | Int32 | The number of users in the multi-factor authentication exclusion security group \(Microsoft 365 Lighthouse - MFA exclusions\). Optional. Read-only. |
| mfaRegisteredUserCount | Int32 | The number of users registered for multi-factor authentication. Optional. Read-only. |
| securityDefaultsEnabled | Boolean | A flag indicating whether Identity Security Defaults is enabled. Optional. Read-only. |
| ssprEnabledUserCount | Int32 | The number of users enabled for self service password reset. Optional. Read-only. |
| ssprRegisteredUserCount | Int32 | The number of users registered for self service password reset. Optional. Read-only. |
| tenantDisplayName | String | The display name for the managed tenant. Required. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Required. Read-only. |
| tenantLicenseType | String | The license type associated with the tenant; for example, `AADFree`, `AADPremium1`, `AADPremium2`. |
| totalUserCount | Int32 | The total number of users in the given managed tenant. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.credentialUserRegistrationsSummary",
  "id": "String (identifier)",
  "tenantId": "String",
  "tenantDisplayName": "String",
  "mfaAndSsprCapableUserCount": "Integer",
  "mfaExcludedUserCount": "Integer",
  "ssprEnabledUserCount": "Integer",
  "mfaRegisteredUserCount": "Integer",
  "ssprRegisteredUserCount": "Integer",
  "totalUserCount": "Integer",
  "securityDefaultsEnabled": "Boolean",
  "mfaConditionalAccessPolicyState": "String",
  "lastRefreshedDateTime": "String (timestamp)"
}
```
