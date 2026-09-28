<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onauthenticationmethodloadstartexternalusersselfservicesignup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp resource type

Namespace: microsoft.graph

This is a managed handler for the event when authentication methods are ready to be presented to an external user in a customized authentication flow for an application on a Microsoft Entra external tenant. This handler defines which identity providers and authentication methods the user can select for primary \(first-factor\) authentication, and is defined as part of a multi-event policy, [externalUsersSelfServiceSignUpEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0).

Inherits from [onAuthenticationMethodLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onauthenticationmethodloadstarthandler?view=graph-rest-1.0).

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identityProviders | [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0) collection | Required. The list of identity providers that user can sign in or sign up with. At least one identity provider must be specified. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp"
}
```
