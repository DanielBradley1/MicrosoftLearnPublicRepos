<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmitlistener?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# onPasswordSubmitListener resource type

Namespace: microsoft.graph

Represents an event listener that triggers during password submission in the authentication flow. This listener enables organizations to intercept password submission events for specific applications and invoke custom logic, such as validating credentials against a legacy authentication system for Just-In-Time \(JIT\) user migration.

When configured, this listener activates during the sign-in process when a user submits their password. The listener evaluates the conditions to determine if it should invoke the configured handler for the authentication event.

Inherits from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationEventsFlowId | String | Identifier of the authentication events flow. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | Conditions that determine when this listener is active, such as which applications trigger the event. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| displayName | String | Display name for the authentication event listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| handler | [onPasswordSubmitHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmithandler?view=graph-rest-1.0) | Configuration for the handler to invoke when this listener is triggered. For JIT migration scenarios, this is typically an [onPasswordMigrationCustomExtensionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordmigrationcustomextensionhandler?view=graph-rest-1.0). |
| id | String | Unique identifier for the authentication event listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPasswordSubmitListener",
  "id": "String (identifier)",
  "displayName": "String",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "authenticationEventsFlowId": "String",
  "handler": {
    "@odata.type": "microsoft.graph.onPasswordSubmitHandler"
  }
}
```
