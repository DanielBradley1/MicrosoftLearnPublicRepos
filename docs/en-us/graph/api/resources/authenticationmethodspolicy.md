<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodspolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# authenticationMethodsPolicy resource type

Namespace: microsoft.graph

Defines authentication methods and the users that are allowed to use them to sign in and perform multifactor authentication \(MFA\) in Microsoft Entra ID.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/authenticationmethodspolicy-get?view=graph-rest-1.0) | [authenticationMethodsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodspolicy?view=graph-rest-1.0) | Read the properties and relationships of an [authenticationMethodsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodspolicy?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/authenticationmethodspolicy-update?view=graph-rest-1.0) | [authenticationMethodsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodspolicy?view=graph-rest-1.0) | Update the properties of an [authenticationMethodsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodspolicy?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description of the policy. Read-only. |
| displayName | String | The name of the policy. Read-only. |
| id | String | The identifier of the policy. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time of the last update to the policy. Read-only. |
| policyVersion | String | The version of the policy in use. Read-only. |
| registrationEnforcement | [registrationEnforcement](https://learn.microsoft.com/en-us/graph/api/resources/registrationenforcement?view=graph-rest-1.0) | Enforce registration at sign-in time. This property can be used to remind users to set up targeted authentication methods. |
| policyMigrationState | authenticationMethodsPolicyMigrationState | The state of migration of the authentication methods policy from the legacy multifactor authentication and self-service password reset \(SSPR\) policies. The possible values are:  <br><br><br><li><code>premigration</code> - means the authentication methods policy is used for authentication only, legacy policies are respected. </li><br><br><li><code>migrationInProgress</code> - means the authentication methods policy is used for both authentication and SSPR, legacy policies are respected. </li><br><br><li><code>migrationComplete</code> - means the authentication methods policy is used for authentication and SSPR, legacy policies are ignored. </li><br><br><li><code>unknownFutureValue</code> - Evolvable enumeration sentinel value. Do not use.</li> |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authenticationMethodConfigurations | [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0) collection | Represents the settings for each authentication method. Automatically expanded on `GET /policies/authenticationMethodsPolicy`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationMethodsPolicy",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "policyVersion": "String",
  "policyMigrationState": "String",
  "registrationEnforcement": {
    "@odata.type": "microsoft.graph.registrationEnforcement"
  } 
}
```
