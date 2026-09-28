<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onphonemethodloadstartlistener?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-09 -->

# onPhoneMethodLoadStartListener resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A listener for when calling codes are enabled or disabled for telephony services in an external identities user flow for Microsoft Entra external tenants. If this listener isn't specified, the default list of calling regions are enabled for MFA.

Inherits from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationEventsFlowId | String | Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta). |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-beta) | Required. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta). |
| handler | [onPhoneMethodLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onphonemethodloadstarthandler?view=graph-rest-beta) | Required. Configuration for what to invoke if the event resolves to this listener. |
| id | String | Required. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta). |
| displayName | String | The display name of the listener. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta). |
| priority | Int32 | Required. Inherited from [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPhoneMethodLoadStartListener",
  "id": "String (identifier)",
  "displayName": "String",
  "priority": "Integer",
  "conditions": {
    "@odata.type": "microsoft.graph.authenticationConditions"
  },
  "authenticationEventsFlowId": "String",
  "handler": {
    "@odata.type": "microsoft.graph.onPhoneMethodLoadStartHandler"
  }
}
```
