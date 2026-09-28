<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# authenticationListener resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines a listener to evaluate when an authentication event happens in an authentication experience. An authenticationListener is abstract and is the base class of the various types of listeners you can evaluate during an authentication event.

You can create an [invokeUserFlowListener](https://learn.microsoft.com/en-us/graph/api/resources/invokeuserflowlistener?view=graph-rest-beta) for the onSignUpStart event, to associate an application with a user flow, thereby enabling a [self-service sign up](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/self-service-sign-up-overview) process. Once an application is associated with a user flow, users who go to that application are able to initiate a sign-up flow that provisions a guest account.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List listeners](https://learn.microsoft.com/en-us/graph/api/authenticationeventspolicy-list-onsignupstart?view=graph-rest-beta) | [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta) collection | Get the collection of authenticationListener resources supported by the onSignupStart event. |
| [Create listener](https://learn.microsoft.com/en-us/graph/api/authenticationeventspolicy-post-onsignupstart?view=graph-rest-beta) | [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta) | Create a new authenticationListener object for the onSignupStart event. |
| [Update listener](https://learn.microsoft.com/en-us/graph/api/authenticationlistener-update?view=graph-rest-beta) | [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta) | Update the specified listener defined for the onSignupStart event in the authentication pipeline. |
| [Put listener](https://learn.microsoft.com/en-us/graph/api/authenticationlistener-put?view=graph-rest-beta) | [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta) | Replace the properties of an authenticationListener object. |
| [Get listener](https://learn.microsoft.com/en-us/graph/api/authenticationlistener-get?view=graph-rest-beta) | [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta) | Get the specified listener defined for the onSignupStart event in the authentication pipeline. |
| [Delete listener](https://learn.microsoft.com/en-us/graph/api/authenticationlistener-delete?view=graph-rest-beta) | None | Delete the specified listener defined for the onSignupStart event in the authentication pipeline. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the action. |
| priority | Int32 | The priority of the listener. Determines the order of evaluation when an event has multiple listeners. The priority is evaluated from low to high. |
| sourceFilter | [authenticationSourceFilter](https://learn.microsoft.com/en-us/graph/api/resources/authenticationsourcefilter?view=graph-rest-beta) | Filter based on the source of the authentication that is used to determine whether the listener is evaluated, and is currently limited to evaluations based on application the user is authenticating to. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "priority": "Integer",
  "sourceFilter": {
    "@odata.type": "microsoft.graph.authenticationSourceFilter"
  }
}
```
