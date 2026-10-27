<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatelistener?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# onPasswordUpdateListener resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an [authentication event listener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta) that triggers after a user completes a self-service password reset \(SSPR\). This listener allows organizations to notify an external system of the password update for selected applications.

When a password update occurs, the listener evaluates its configured conditions to determine whether to invoke the associated handler.

Inherits from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationEventsFlowId | String | Identifier of the authentication events flow. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta). |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-beta) | Conditions that determine when this listener is active, such as which applications trigger the event. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta). |
| displayName | String | Display name for the authentication event listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta). |
| handler | [onPasswordUpdateHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatehandler?view=graph-rest-beta) | Configuration for the handler to invoke when this listener is triggered. This is typically an [onPasswordUpdateCustomExtensionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatecustomextensionhandler?view=graph-rest-beta). |
| id | String | Unique identifier for the authentication event listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta). |
| priority | Int32 | Priority of this listener relative to other listeners for the same event. Lower values indicate higher priority. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPasswordUpdateListener",
  "id": "String (identifier)",
  "displayName": "String",
  "priority": "Integer",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "authenticationEventsFlowId": "String",
  "handler": {
    "@odata.type": "microsoft.graph.onPasswordUpdateHandler"
  }
}
```
