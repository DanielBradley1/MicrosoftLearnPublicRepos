<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# authenticationEventListener resource type

Namespace: microsoft.graph

To customize the authentication process, listeners can be registered which specify that for some event, on some conditions, some custom logic can be invoked. This is an abstract type from which the following types are derived.

- [onTokenIssuanceStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartlistener?view=graph-rest-1.0) resource type
- [onInteractiveAuthFlowStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/oninteractiveauthflowstartlistener?view=graph-rest-1.0) resource type
- [onAuthenticationMethodLoadStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onauthenticationmethodloadstartlistener?view=graph-rest-1.0) resource type
- [onAttributeCollectionListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionlistener?view=graph-rest-1.0) resource type
- [onUserCreateStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onusercreatestartlistener?view=graph-rest-1.0) resource type
- [onAttributeCollectionStartListener](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartlistener?view=graph-rest-1.0) resource type
- [onAttributeCollectionSubmitListener](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmitlistener?view=graph-rest-1.0) resource type
- [onEmailOtpSendListener](https://learn.microsoft.com/en-us/graph/api/resources/onemailotpsendlistener?view=graph-rest-1.0) resource type
- [onFraudProtectionLoadStartListener](https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstartlistener?view=graph-rest-1.0) resource type
- [onPasswordSubmitListener](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmitlistener?view=graph-rest-1.0) resource type
- [onVerifiedIdClaimValidationListener](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationlistener?view=graph-rest-1.0) resource type

Note

You can have a maximum of 250 event listeners.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identitycontainer-list-authenticationeventlisteners?view=graph-rest-1.0) | [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) collection | Retrieve a list of the object types that are derived from **authenticationEventListener**. |
| [Create](https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-authenticationeventlisteners?view=graph-rest-1.0) | [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) | Create a new object type that is derived from **authenticationEventListener**. |
| [Get](https://learn.microsoft.com/en-us/graph/api/authenticationeventlistener-get?view=graph-rest-1.0) | [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) | Read the properties and relationships of an object type that is derived from **authenticationEventListener**. |
| [Update](https://learn.microsoft.com/en-us/graph/api/authenticationeventlistener-update?view=graph-rest-1.0) | None | Update the properties of an object type that is derived from **authenticationEventListener**. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/authenticationeventlistener-delete?view=graph-rest-1.0) | None | Delete an object type that is derived from **authenticationEventListener**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationEventsFlowId | String | The identifier of the [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) object. |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | The conditions on which this authenticationEventListener should trigger. |
| displayName | String | The display name of the listener. |
| id | String | Identifier for this authenticationEventListener. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationEventListener",
  "id": "String (identifier)",
  "displayName": "String",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "authenticationEventsFlowId": "String"
}
```
