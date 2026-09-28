<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-04-12 -->

# externalUsersSelfServiceSignUpEventsFlow resource type

Namespace: microsoft.graph

Represents a self-service user flow for external identities within a Microsoft Entra External ID in workforce or external tenants. A user flow is implemented as a multi-event policy executing the specific events at specific points of user interaction.

Inherits from [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [authenticationEventsFlow resource type](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| displayName | String | Required. The display name for the events policy. Must be unique. Inherited from [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0). |
| description | String | Optional. The description of the events policy. Inherited from [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0). |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | Optional. The conditions representing the context of the authentication request which is used to decide whether the events policy is invoked. Inherited from [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0). |
| onInteractiveAuthFlowStart | [onInteractiveAuthFlowStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/oninteractiveauthflowstarthandler?view=graph-rest-1.0) | Required. The configuration for what to invoke when an authentication flow is ready to be initiated. |
| onAttributeCollection | [onAttributeCollectionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionhandler?view=graph-rest-1.0) | The configuration for what to invoke when attributes are ready to be collected from the user. |
| onAttributeCollectionStart | [onAttributeCollectionStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstarthandler?view=graph-rest-1.0) | The configuration for what to invoke when attribution collection starts. |
| onAttributeCollectionSubmit | [onAttributeCollectionSubmitHandler](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmithandler?view=graph-rest-1.0) | The configuration for what to invoke when attributes are submitted at the end of attribution collection. |
| onAuthenticationMethodLoadStart | [onAuthenticationMethodLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onauthenticationmethodloadstarthandler?view=graph-rest-1.0) | Required. The configuration for what to invoke when authentication methods are ready to be presented to the user. Must have at least one identity provider linked.  <br>  <br>Supports `$filter` \(`eq`\). See [support for filtering on user flows](#support-for-filtering-on-user-flows) for syntax information. |
| onUserCreateStart | [onUserCreateStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onusercreatestarthandler?view=graph-rest-1.0) | The configuration for what to invoke during user creation. |

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
  "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "onInteractiveAuthFlowStart": {
    "@odata.type": "microsoft.graph.onInteractiveAuthFlowStartHandler"
  },
  "onAuthenticationMethodLoadStart": {
    "@odata.type": "microsoft.graph.onAuthenticationMethodLoadStartHandler"
  },
  "onAttributeCollection": {
    "@odata.type": "microsoft.graph.onAttributeCollectionHandler"
  },
  "onAttributeCollectionStart": {
    "@odata.type": "microsoft.graph.onAttributeCollectionStartHandler"
  },
  "onAttributeCollectionSubmit": {
    "@odata.type": "microsoft.graph.onAttributeCollectionSubmitHandler"
  },
  "onUserCreateStart": {
    "@odata.type": "microsoft.graph.onUserCreateStartHandler"
  }
}
```
