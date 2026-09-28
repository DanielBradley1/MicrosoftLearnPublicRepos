<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartlistener?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# onTokenIssuanceStartListener resource type

Namespace: microsoft.graph

A listener for when a token is about to be issued to your application.

Inherits from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | The conditions on which onTokenIssuanceStartListener should trigger. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| displayName | String | The display name of the listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| handler | [onTokenIssuanceStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestarthandler?view=graph-rest-1.0) | The handler to invoke when conditions are met for this onTokenIssuanceStartListener. |
| id | String | Identifier for the onTokenIssuanceStartListener. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onTokenIssuanceStartListener",
  "id": "String (identifier)",
  "displayName": "String",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "handler": {
    "@odata.type": "microsoft.graph.onTokenIssuanceStartHandler"
  }
}
```
