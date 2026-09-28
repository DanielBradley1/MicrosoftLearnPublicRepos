<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-07 -->

# authenticationEventsFlow resource type

Namespace: microsoft.graph

Represents a multi-event policy, that is, a **user flow**, and holds the handler configuration for multiple events. Each property of name *eventType* is optional and corresponds to the handler configuration on the event listener. This resource allows for managing multiple [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) objects under the same priority and condition set. This resource provides a better-managed view of checking which event listeners are executed under a certain circumstance.

If no handler is set for an event, then this policy doesn't effect that event in any authentication, and no listener is created for that event.

Additionally, this entity works as an orchestration step for the various event listeners it manages. For each event listener that it manages, it creates, modifies, or deletes the event listener accordingly. This means on creation time, it creates multiple event listeners and manages any rollback scenarios for any failing requests.

This resource is an abstract type from which the [externalUsersSelfServiceSignUpEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0) object type is derived.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identitycontainer-list-authenticationeventsflows?view=graph-rest-1.0) | [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) collection | Retrieve a list of the [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) objects and their properties. Only objects of the [externalUserSelfServiceSignupEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0) subtype are available. |
| [Create](https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-authenticationeventsflows?view=graph-rest-1.0) | [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) | Create a new [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) object. Only objects of the [externalUserSelfServiceSignupEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0) subtype are supported. |
| [Get](https://learn.microsoft.com/en-us/graph/api/authenticationeventsflow-get?view=graph-rest-1.0) | [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) | Read the properties and relationships of an [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) object. Only objects of the [externalUserSelfServiceSignupEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0) subtype are available. |
| [Update](https://learn.microsoft.com/en-us/graph/api/authenticationeventsflow-update?view=graph-rest-1.0) | None | Update the properties of an [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) object. Only objects of the [externalUserSelfServiceSignupEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0) subtype are available. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/authenticationeventsflow-delete?view=graph-rest-1.0) | None | Delete an [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) object. Only objects of the [externalUserSelfServiceSignupEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0) subtype are supported. |
| **Identity providers in a user flow** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/onauthenticationmethodloadstartexternalusersselfservicesignup-list-identityproviders?view=graph-rest-1.0) | [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0) collection | Get the identity providers that are defined for an external identities self-service sign-up user flow that's represented by an **externalUsersSelfServiceSignupEventsFlow** object type. |
| [Add](https://learn.microsoft.com/en-us/graph/api/onauthenticationmethodloadstartexternalusersselfservicesignup-post-identityproviders?view=graph-rest-1.0) | None | Add an identity provider to an external identities self-service sign-up user flow that's represented by an **externalUsersSelfServiceSignupEventsFlow** object type. The identity provider must first be configured in the tenant. |
| [Remove](https://learn.microsoft.com/en-us/graph/api/onauthenticationmethodloadstartexternalusersselfservicesignup-delete-identityproviders?view=graph-rest-1.0) | None | Remove an identity provider from an external identities self-service sign-up user flow that's represented by an **externalUsersSelfServiceSignupEventsFlow** object type. |
| **User flow attributes** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/identityuserflowattribute-list?view=graph-rest-1.0) | identityUserFlowAttributes collection | Retrieve all built-in and custom user flow attributes. |
| [Create](https://learn.microsoft.com/en-us/graph/api/identityuserflowattribute-post?view=graph-rest-1.0) | identityUserFlowAttribute | Create a new custom user flow attribute. |
| [Get](https://learn.microsoft.com/en-us/graph/api/identityuserflowattribute-get?view=graph-rest-1.0) | identityUserFlowAttribute | Retrieve properties of a user flow attribute. |
| [Update](https://learn.microsoft.com/en-us/graph/api/identityuserflowattribute-update?view=graph-rest-1.0) | None | Update a custom user flow attribute. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/identityuserflowattribute-delete?view=graph-rest-1.0) | None | Delete a custom user flow attribute. |
| [List attributes in a user flow](https://learn.microsoft.com/en-us/graph/api/onattributecollectionexternalusersselfservicesignup-list-attributes?view=graph-rest-1.0) | None | Get the collection of **identityUserFlowAttribute** objects associated with an external identities self-service sign-up user flow that's represented by an **externalUsersSelfServiceSignupEventsFlow** object. |
| [Add attribute to a user flow](https://learn.microsoft.com/en-us/graph/api/onattributecollectionexternalusersselfservicesignup-post-attributes?view=graph-rest-1.0) | None | Add an **identityUserFlowAttribute** object associated with an external identities self-service sign-up user flow that's represented by an **externalUsersSelfServiceSignupEventsFlow** object. |
| [Remove attribute from a user flow](https://learn.microsoft.com/en-us/graph/api/onattributecollectionexternalusersselfservicesignup-delete-attributes?view=graph-rest-1.0) | None | Remove an **identityUserFlowAttribute** object associated with an external identities self-service sign-up user flow that's represented by an **externalUsersSelfServiceSignupEventsFlow** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Autogenerated. |
| displayName | String | Required. The display name for the events policy. |
| description | String | The description of the events policy. |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | The conditions representing the context of the authentication request that's used to decide whether the events policy is invoked.  <br>  <br>Supports `$filter` \(`eq`\). See [support for filtering on user flows](#support-for-filtering-on-user-flows) for syntax information. |

### Support for filtering on user flows

- Filter on identityProviders: `?$filter=microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAuthenticationMethodLoadStart/microsoft.graph.onAuthenticationMethodLoadStartExternalUsersSelfServiceSignUp/identityProviders/any(idp:idp/id eq '{identityProvider-id}')`
- Filter on attributes: `?$filter=microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/onAttributeCollection/microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp/attributes/any(attribute:attribute/id eq '{attribute-ID}')`
- Filter on linked applications: `?$filter=microsoft.graph.externalUsersSelfServiceSignUpEventsFlow/conditions/applications/includeApplications/any(appId:appId/appId eq '{appId}')`

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationEventsFlow",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  }
}
```
