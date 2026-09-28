<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationlistener?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# onVerifiedIdClaimValidationListener resource type

Namespace: microsoft.graph

Represents an [event listener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) for the Verified ID claim validation step in the authentication flow. This listener allows organizations to validate claims from Verified ID credential presentations for specific applications by invoking custom logic that checks the claims against expected values.

When a user presents a Verified ID credential during sign-in, this listener evaluates the configured conditions to determine whether to invoke the handler for the authentication event.

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
| handler | [onVerifiedIdClaimValidationHandler](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationhandler?view=graph-rest-1.0) | Configuration for the handler to invoke when this listener is triggered. For Verified ID claim validation scenarios, this is typically an [onVerifiedIdClaimValidationCustomExtensionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationcustomextensionhandler?view=graph-rest-1.0). |
| id | String | Unique identifier for the authentication event listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| priority | Int32 | Priority of this listener relative to other listeners for the same event. Lower values indicate higher priority. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onVerifiedIdClaimValidationListener",
  "id": "String (identifier)",
  "displayName": "String",
  "priority": "Integer",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "authenticationEventsFlowId": "String",
  "handler": {
    "@odata.type": "microsoft.graph.onVerifiedIdClaimValidationHandler"
  }
}
```
