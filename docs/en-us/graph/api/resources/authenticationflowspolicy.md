<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationflowspolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# authenticationFlowsPolicy resource type

Namespace: microsoft.graph

Represents the [policy configuration of self-service sign-up experience](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignupauthenticationflowconfiguration?view=graph-rest-1.0) at a tenant level that lets external users request to sign up for approval. It contains information, such as the identifier, display name, and description, and indicates whether self-service sign-up is enabled for the policy.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/authenticationflowspolicy-get?view=graph-rest-1.0) | authenticationFlowsPolicy | Get the authentication flows policy configuration. |
| [Update](https://learn.microsoft.com/en-us/graph/api/authenticationflowspolicy-update?view=graph-rest-1.0) | authenticationFlowsPolicy | Update the authentication flows policy configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Inherited property. A description of the policy. Optional. Read-only. |
| displayName | String | Inherited property. The human-readable name of the policy. Optional. Read-only. |
| id | String | Inherited property. The identifier of the authentication flows policy. Optional. Read-only. |
| selfServiceSignUp | [selfServiceSignUpAuthenticationFlowConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignupauthenticationflowconfiguration?view=graph-rest-1.0) | Contains [selfServiceSignUpAuthenticationFlowConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignupauthenticationflowconfiguration?view=graph-rest-1.0) settings that convey whether self-service sign-up is enabled or disabled. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
   "description":"String",
   "displayName":"String",
   "id":"String (identifier)",
   "selfServiceSignUp":{
      "@odata.type":"#microsoft.graph.selfServiceSignUpAuthenticationFlowConfiguration"
   }
}
```
