<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstartlistener?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# onFraudProtectionLoadStartListener resource type

Namespace: microsoft.graph

A listener for fraud protection load start events in Microsoft Entra External ID. This resource enables you to configure actions and conditions that trigger at the start of a fraud protection check, such as during sign-up scenarios.

Inherits from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationEventsFlowId | String | The identifier of the authentication events flow associated with this listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | Defines the conditions under which this listener is triggered. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| displayName | String | The display name of the listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| handler | [onFraudProtectionLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstarthandler?view=graph-rest-1.0) | Configuration for what to invoke if the event resolves to this listener. |
| id | String | The unique identifier of the listener. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| priority | Int32 | Indicates the execution priority of the listener relative to other listeners. Between 0 \(lower priority\) and 1000 \(higher priority\). Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onFraudProtectionLoadStartListener",
  "id": "String (identifier)",
  "displayName": "String",
  "priority": "Integer",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "authenticationEventsFlowId": "String",
  "handler": {
    "@odata.type": "microsoft.graph.onFraudProtectionLoadStartHandler"
  }
}
```
