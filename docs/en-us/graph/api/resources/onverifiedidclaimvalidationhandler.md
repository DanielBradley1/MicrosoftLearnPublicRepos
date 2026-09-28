<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationhandler?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# onVerifiedIdClaimValidationHandler resource type

Namespace: microsoft.graph

Represents an abstract base type for handlers that can be invoked when an [onVerifiedIdClaimValidation authentication event](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationlistener?view=graph-rest-1.0) occurs. This resource type defines the contract for all handlers that process Verified ID claim validation events in the authentication flow.

Concrete implementations of this handler type include:

- [onVerifiedIdClaimValidationCustomExtensionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationcustomextensionhandler?view=graph-rest-1.0) - Invokes a custom extension API for validating claims from Verified ID credential presentations

This abstract type can't be instantiated directly. Use one of the derived types to configure a handler for the **onVerifiedIdClaimValidation** event.

## Properties

This abstract type has no properties. Derived types might define other properties.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onVerifiedIdClaimValidationHandler"
}
```
