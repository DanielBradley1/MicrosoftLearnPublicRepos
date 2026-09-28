<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onotpsendcustomextension?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# onOtpSendCustomExtension resource type

Namespace: microsoft.graph

Used for creating a new custom extension based on the **onEmailOtpSend** event.

Inherits from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0).

For more information, see [Configure a custom email provider for one time passcode send events \(preview\)](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-email-otp-get-started).

## Methods

None.

For the list of API operations for managing this resource type, see the [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | The authentication configuration for this custom extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| behaviorOnError | [customExtensionBehaviorOnError](https://learn.microsoft.com/en-us/graph/api/resources/customextensionbehavioronerror?view=graph-rest-1.0) | Let to configure behavior if the call to custom authentication extension returns error. Inherited from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0). Optional. |
| clientConfiguration | [customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0) | The connection settings that define how long Microsoft Entra ID can wait for a response from an external app. After this time, Microsoft Entra ID shuts down the connection when trying to trigger the external app. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| description | String | The description for the custom extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| displayName | String | The display name for the custom extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | The configuration for the API endpoint that the custom extension calls. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| id | String | Identifier for this authenticationEventListener. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onOtpSendCustomExtension",
  "id": "String (identifier)",
  "authenticationConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionAuthenticationConfiguration"
  },
  "clientConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionClientConfiguration"
  },
  "description": "String",
  "displayName": "String",
  "endpointConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionEndpointConfiguration"
  },
  "behaviorOnError": {
    "@odata.type": "microsoft.graph.customExtensionBehaviorOnError"
  }
}
```
