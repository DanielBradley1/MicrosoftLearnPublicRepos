<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/oninteractiveauthflowstartexternalusersselfservicesignup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-21 -->

# onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp resource type

Namespace: microsoft.graph

This is a managed handler for the initiation of a customized authentication flow for an application on a Microsoft Entra external tenant. It defines whether a user can register \(sign-up\) or just sign-in, and is defined as part of a multi-event policy, [externalUsersSelfServiceSignUpEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0).

Inherits from [onInteractiveAuthFlowStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/oninteractiveauthflowstarthandler?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isSignUpAllowed | Boolean | Optional. Specifies whether the authentication flow includes an option to sign up \(create account\) and sign in. Default value is `false` meaning only sign in is enabled. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",
  "isSignUpAllowed": "Boolean"
}
```
