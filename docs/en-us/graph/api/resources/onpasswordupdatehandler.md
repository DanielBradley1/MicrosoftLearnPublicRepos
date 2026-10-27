<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatehandler?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# onPasswordUpdateHandler resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the abstract base type for handlers configured through the **handler** property of an [onPasswordUpdateListener](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatelistener?view=graph-rest-beta). These handlers process the **onPasswordUpdate** authentication event after a user completes a self-service password reset.

Concrete implementations of this handler type include:

- [onPasswordUpdateCustomExtensionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatecustomextensionhandler?view=graph-rest-beta) - Invokes a custom extension API to synchronize the updated credential with an external system.

This abstract type can't be instantiated directly. Use a derived type to configure a handler for the **onPasswordUpdate** event.

## Properties

This abstract type has no properties. Derived types might define other properties.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPasswordUpdateHandler"
}
```
