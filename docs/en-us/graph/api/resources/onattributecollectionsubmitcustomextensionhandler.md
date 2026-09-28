<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmitcustomextensionhandler?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-04-12 -->

# onAttributeCollectionSubmitCustomExtensionHandler resource type

Namespace: microsoft.graph

Used for creating a new custom extension based on the **onAttributeCollectionSubmit** event to configure the verification of attributes when they're submitted via the [externalUsersSelfServiceSignUpEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0) object. The custom extension can be used to do input validation checks on the attributes or allow the user to choose more attributes.

Inherits from [onAttributeCollectionSubmitHandler](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmithandler?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuration | [customExtensionOverwriteConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionoverwriteconfiguration?view=graph-rest-1.0) | Configuration regarding properties of the custom extension that can be overwritten per event listener. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customExtension | [onAttributeCollectionSubmitCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmitcustomextension?view=graph-rest-1.0) | Used for creating a new custom extension based on the **onAttributeCollectionSubmit** event to configure the collection of attributes upon user sign-up. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onAttributeCollectionSubmitCustomExtensionHandler",
  "configuration": {
    "@odata.type": "microsoft.graph.customExtensionOverwriteConfiguration"
  }
}
```
