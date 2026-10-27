<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatecustomextensionhandler?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# onPasswordUpdateCustomExtensionHandler resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a handler that invokes a custom authentication extension API after a user completes a self-service password reset. The handler enables an external system to synchronize the updated credential.

This type is configured through the **handler** property of an [onPasswordUpdateListener](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatelistener?view=graph-rest-beta).

Inherits from [onPasswordUpdateHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatehandler?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuration | [customExtensionOverwriteConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionoverwriteconfiguration?view=graph-rest-beta) | Configuration that overrides the default settings from the referenced custom extension, such as timeout and retry values. |
| expirationDateTime | DateTimeOffset | The date and time at which the listener stops invoking the custom extension. The value must be in the future and can't be more than six months after the create or PATCH request. Renew the value by updating the listener. After the value passes, the callout is skipped until the listener is renewed or recreated. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customExtension | [onPasswordUpdateCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatecustomextension?view=graph-rest-beta) | Reference to the custom authentication extension that is invoked to synchronize the updated credential. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPasswordUpdateCustomExtensionHandler",
  "configuration": {
    "@odata.type": "microsoft.graph.customExtensionOverwriteConfiguration"
  },
  "expirationDateTime": "String (timestamp)",
  "customExtension": {
    "@odata.type": "microsoft.graph.onPasswordUpdateCustomExtension"
  }
}
```
