<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartlistener?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# onAttributeCollectionStartListener resource type

Namespace: microsoft.graph

A listener for the start of the user attribute collection stage of a sign up flow represented by an [externalUsersSelfServiceSignUpEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0) object. This event is triggered when the user clicks the sign up button.

Inherits from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationEventsFlowId | String | The identifier of the authenticationEventsFlow object. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | The conditions on which this authenticationEventListener should trigger. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| displayName | String | The display name of the listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |
| handler | [onAttributeCollectionStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstarthandler?view=graph-rest-1.0) | Configuration for what to invoke if the event resolves to this listener. |
| id | String | Identifier for this authenticationEventListener. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| priority | Int32 | The priority of this handler. Between 0 \(lower priority\) and 1000 \(higher priority\). Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onAttributeCollectionStartListener",
  "id": "String (identifier)",
  "displayName": "String",
  "priority": "Integer",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "authenticationEventsFlowId": "String",
  "handler": {
    "@odata.type": "microsoft.graph.onAttributeCollectionStartHandler"
  }
}
```

## Related content

- [Custom authentication extensions for attribute collection start and submit events](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-attribute-collection)
- [OnAttributeCollectionStart event reference](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-onattributecollectionstart-reference)
