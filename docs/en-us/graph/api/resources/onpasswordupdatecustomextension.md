<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatecustomextension?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# onPasswordUpdateCustomExtension resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a [custom authentication extension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-beta) for the **onPasswordUpdate** event. This extension allows organizations to notify an external system after a user completes a self-service password reset \(SSPR\), enabling the external system to synchronize the updated credential.

When a user completes SSPR, this extension calls a customer-provided API endpoint with an encrypted reference to the new password. The external system decrypts the reference and propagates the credential without changing the user-visible SSPR result.

The [onPasswordUpdateCustomExtensionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordupdatecustomextensionhandler?view=graph-rest-beta) references this resource through its **customExtension** relationship.

Inherits from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-beta) | Configuration for securing the API call to the external system. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-beta). |
| behaviorOnError | [customExtensionBehaviorOnError](https://learn.microsoft.com/en-us/graph/api/resources/customextensionbehavioronerror?view=graph-rest-beta) | Error handling behavior when the external API fails or is unreachable. Inherited from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-beta). |
| clientConfiguration | [customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-beta) | HTTP client configuration, including timeout and retry settings. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-beta). |
| description | String | Description of the custom authentication extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-beta). |
| displayName | String | Display name for the custom authentication extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-beta). |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-beta) | HTTP endpoint configuration for the external API. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-beta). |
| id | String | Unique identifier for the custom authentication extension. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPasswordUpdateCustomExtension",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "authenticationConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionAuthenticationConfiguration"
  },
  "endpointConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionEndpointConfiguration"
  },
  "clientConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionClientConfiguration"
  },
  "behaviorOnError": {
    "@odata.type": "microsoft.graph.customExtensionBehaviorOnError"
  }
}
```
