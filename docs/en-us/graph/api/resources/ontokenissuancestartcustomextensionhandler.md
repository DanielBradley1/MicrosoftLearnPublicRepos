<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartcustomextensionhandler?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# onTokenIssuanceStartCustomExtensionHandler resource type

Namespace: microsoft.graph

Custom extension handler for the event when a token is about to be issued to your application.

Inherits from [onTokenIssuanceStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestarthandler?view=graph-rest-1.0).

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customExtension | [onTokenIssuanceStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartcustomextension?view=graph-rest-1.0) | The custom extension to invoke to handle the event when a token is about to be issued to your application. This object is autoexpanded. |
| configuration | [customExtensionOverwriteConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionoverwriteconfiguration?view=graph-rest-1.0) | Configuration regarding properties of the custom extension which can be overwritten per event listener. If no values are provided, the properties on the custom extension are used. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onTokenIssuanceStartCustomExtensionHandler",
  "customExtension": {
    "@odata.type": "#microsoft.graph.onTokenIssuanceStartCustomExtension",
  },
  "configuration": {
    "@odata.type": "#microsoft.graph.customExtensionOverwriteConfiguration",
  },
}
```
