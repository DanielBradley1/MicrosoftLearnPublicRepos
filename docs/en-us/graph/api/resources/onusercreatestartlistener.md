<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onusercreatestartlistener?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# onUserCreateStartListener resource type

Namespace: microsoft.graph

A listener for when the user is about to be created in an authentication flow.

Inherits from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Required. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | Required. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| displayName | String | The display name of the listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| authenticationEventsFlowId | String | Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| handler | [onUserCreateStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onusercreatestarthandler?view=graph-rest-1.0) | Required. Configuration for what to invoke if the event resolves to this listener. This lets us define potential handler configurations per-event. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onUserCreateStartListener",
  "id": "String (identifier)",
  "displayName": "String",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "authenticationEventsFlowId": "String",
  "handler": {
    "@odata.type": "microsoft.graph.onUserCreateStartHandler"
  }
}
```
