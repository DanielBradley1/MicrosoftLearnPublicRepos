<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onusercreatestartexternalusersselfservicesignup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-21 -->

# onUserCreateStartExternalUsersSelfServiceSignUp resource type

Namespace: microsoft.graph

This is a managed handler for the user creation step of a customized authentication flow for an application in a Microsoft Entra external tenant defined by a multi-event policy, [externalUsersSelfServiceSignUpEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0). It defines what type of user is created.

Inherits from [onUserCreateStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onusercreatestarthandler?view=graph-rest-1.0). Complex type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userTypeToCreate | String | The type of user to create. Maps to userType property of [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) object. The possible values are: `member`, `guest`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onUserCreateStartExternalUsersSelfServiceSignUp",
  "userTypeToCreate": "String"
}
```
