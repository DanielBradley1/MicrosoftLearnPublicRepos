<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmithandler?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# onPasswordSubmitHandler resource type

Namespace: microsoft.graph

Represents an abstract base type for handlers that can be invoked when an [onPasswordSubmit authentication event](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmitlistener?view=graph-rest-1.0) occurs. This resource type defines the contract for all handlers that process password submission events in the authentication flow.

Concrete implementations of this handler type include:

- [onPasswordMigrationCustomExtensionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordmigrationcustomextensionhandler?view=graph-rest-1.0) - Invokes a custom extension API for password validation during Just-In-Time migration scenarios

This abstract type can't be instantiated directly. Use one of the derived types to configure a handler for the **onPasswordSubmit** event.

## Properties

This abstract type has no properties. Derived types might define other properties.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPasswordSubmitHandler"
}
```
