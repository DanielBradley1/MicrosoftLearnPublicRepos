<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appliedauthenticationeventlistener?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# appliedAuthenticationEventListener resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the [authentication event listeners](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta) such as Azure Logic Apps and Azure Functions that are triggered by the corresponding events. This object is configured in the **appliedEventListeners** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta) and [selfServiceSignUp](https://learn.microsoft.com/en-us/graph/api/resources/selfservicesignup?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| eventType | authenticationEventType | The type of authentication event that triggered the [custom authentication extension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-beta) request. The possible values are: `tokenIssuanceStart`, `pageRenderStart`, `unknownFutureValue`, `attributeCollectionStart`, `attributeCollectionSubmit`, `emailOtpSend`, `passwordSubmit`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `attributeCollectionStart`, `attributeCollectionSubmit`, `emailOtpSend`, `passwordSubmit`. |
| executedListenerId | String | ID of the [authentication event listener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta) that was executed. |
| handlerResult | [authenticationEventHandlerResult](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventhandlerresult?view=graph-rest-beta) | The result from the listening client, such as an Azure Logic App and Azure Functions, of this authentication event. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appliedAuthenticationEventListener",
  "eventType": "String",
  "executedListenerId": "String",
  "handlerResult": {
    "@odata.type": "microsoft.graph.authenticationEventHandlerResult"
  }
}
```
