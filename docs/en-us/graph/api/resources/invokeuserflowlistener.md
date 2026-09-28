<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/invokeuserflowlistener?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# invokeUserFlowListener resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

You can create an [invokeUserFlowListener](https://learn.microsoft.com/en-us/graph/api/resources/invokeuserflowlistener?view=graph-rest-beta) for the onSignUpStart event. The listener associates an application with a user flow, which enables [external identities self-service sign up](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/self-service-sign-up-overview) for the application. Once an application is associated with a user flow, users who go to that application are able to initiate a sign-up flow that provisions a guest account.

Inherits from the abstract base type [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the action. Inherited from [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta). |
| priority | Int32 | The priority of the action that is used to determine one out of multiple applicable actions. Inherited from [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta). |
| sourceFilter | [authenticationSourceFilter](https://learn.microsoft.com/en-us/graph/api/resources/authenticationsourcefilter?view=graph-rest-beta) | Filter based on the source of the authentication that is used to determine whether the listener is executed. Inherited from [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| userFlow | [b2xIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2xidentityuserflow?view=graph-rest-beta) | The user flow that is invoked when this action executes. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "priority": "Integer",
  "sourceFilter": {
    "@odata.type": "microsoft.graph.authenticationSourceFilter"
  },
  "userFlow": {
    "@odata.type": "microsoft.graph.b2xIdentityUserFlow"
  }
}
```
