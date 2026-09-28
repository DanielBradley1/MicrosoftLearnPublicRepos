<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartcustomextensionhandler?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-04-12 -->

# onAttributeCollectionStartCustomExtensionHandler resource type

Namespace: microsoft.graph

Used for creating a new custom extension based on the **onAttributeCollectionStart** event to configure the collection of attributes upon user sign-up via the [externalUsersSelfServiceSignUpEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0) object. This event and custom extension enables the sign-up flow to block a user from continuing sign-up based on the federated identity or email and prefill attributes to be collected with prespecified values.

Inherits from [onAttributeCollectionStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstarthandler?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuration | [customExtensionOverwriteConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionoverwriteconfiguration?view=graph-rest-1.0) | Configuration regarding properties of the custom extension that are can be overwritten per event listener. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customExtension | [onAttributeCollectionStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartcustomextension?view=graph-rest-1.0) | Used for creating a new custom extension based on the **onAttributeCollectionStart** event to configure the collection of attributes upon user sign-up. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onAttributeCollectionStartCustomExtensionHandler",
  "configuration": {
    "@odata.type": "microsoft.graph.customExtensionOverwriteConfiguration"
  }
}
```
