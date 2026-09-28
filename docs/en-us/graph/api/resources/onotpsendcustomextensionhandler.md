<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onotpsendcustomextensionhandler?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# onOtpSendCustomExtensionHandler resource type

Namespace: microsoft.graph

Represents configuration information for creating a new custom extension based on the **onEmailOtpSend** event to configure the custom email provider for one time passcodes.

Inherits from [onOtpSendHandler](https://learn.microsoft.com/en-us/graph/api/resources/onotpsendhandler?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuration | [customExtensionOverwriteConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionoverwriteconfiguration?view=graph-rest-1.0) | Configuration regarding properties of the custom extension that are can be overwritten for the **onEmailOtpSendListener** event listener. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customExtension | [onOtpSendCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onotpsendcustomextension?view=graph-rest-1.0) | Used for creating a new custom extension based on the **onEmailOtpSend** event to configure the custom email provider for one time passcodes. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onOtpSendCustomExtensionHandler",
  "configuration": {
    "@odata.type": "microsoft.graph.customExtensionOverwriteConfiguration"
  }
}
```
