<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationcustomextensionhandler?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# onVerifiedIdClaimValidationCustomExtensionHandler resource type

Namespace: microsoft.graph

Represents a handler that invokes a custom authentication extension API to validate claims from Verified ID credential presentations during the authentication flow. When triggered, this handler calls the configured custom extension API with the Verified ID claims context to determine whether the claims pass or fail validation.

Inherits from [onVerifiedIdClaimValidationHandler](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationhandler?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuration | [customExtensionOverwriteConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionoverwriteconfiguration?view=graph-rest-1.0) | Configuration that overrides the default settings from the referenced custom extension, such as timeout and retry values. Optional. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customExtension | [onVerifiedIdClaimValidationCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationcustomextension?view=graph-rest-1.0) | Reference to the custom authentication extension that is invoked to validate the Verified ID claims. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onVerifiedIdClaimValidationCustomExtensionHandler",
  "configuration": {
    "@odata.type": "microsoft.graph.customExtensionOverwriteConfiguration"
  },
  "customExtension": {
    "@odata.type": "microsoft.graph.onVerifiedIdClaimValidationCustomExtension"
  }
}
```
