<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventhandlerresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# authenticationEventHandlerResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that defines the result of authentication to [event listeners](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-beta) in Microsoft Entra sign-ins. This object is configured in the **handlerResult** property of [appliedAuthenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/appliedauthenticationeventlistener?view=graph-rest-beta). This abstract type is inherited by the [customExtensionCalloutResult](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutresult?view=graph-rest-beta) resource type.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationEventHandlerResult"
}
```
