<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onauthenticationmethodloadstartlistener?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# onAuthenticationMethodLoadStartListener resource type

Namespace: microsoft.graph

A listener for when authentication methods are ready to be presented to the user in an authentication flow. If this listener isn't specified, the default option is email one time passcode \(OTP\). May be part of an [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0).

Inherits from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationEventsFlowId | String | Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | Required. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| displayName | String | The display name of the listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| handler | [onAuthenticationMethodLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onauthenticationmethodloadstarthandler?view=graph-rest-1.0) | Required. Configuration for what to invoke if the event resolves to this listener. This property lets us define potential handler configurations per-event. |
| id | String | Required. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onAuthenticationMethodLoadStartListener",
  "id": "String (identifier)",
  "displayName": "String",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "authenticationEventsFlowId": "String",
  "handler": {
    "@odata.type": "microsoft.graph.onAuthenticationMethodLoadStartHandler"
  }
}
```
