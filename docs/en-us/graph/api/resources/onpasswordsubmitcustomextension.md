<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmitcustomextension?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# onPasswordSubmitCustomExtension resource type

Namespace: microsoft.graph

Represents a custom authentication extension for the **onPasswordSubmit** event. This extension enables organizations to validate user credentials against legacy authentication systems during the sign-in process, facilitating Just-In-Time \(JIT\) migration scenarios where passwords can't be exported from the legacy system.

When a user attempts to sign in, this extension calls a customer-provided API endpoint to validate the password against the legacy system. Upon successful validation, the user's credentials are persisted in Microsoft Entra ID, completing the migration for that user.

Inherits from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | Configuration for securing the API call to the external system. Inherited from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0). |
| behaviorOnError | [customExtensionBehaviorOnError](https://learn.microsoft.com/en-us/graph/api/resources/customextensionbehavioronerror?view=graph-rest-1.0) | Error handling behavior if the external API fails or is unreachable. Inherited from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0). |
| clientConfiguration | [customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0) | HTTP client configuration including timeout and retry settings. Inherited from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0). |
| description | String | Description of the custom authentication extension. Inherited from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0). |
| displayName | String | Display name for the custom authentication extension. Inherited from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0). |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | HTTP endpoint configuration for the external API. Inherited from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0). |
| id | String | Unique identifier for the custom authentication extension. Inherited from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPasswordSubmitCustomExtension",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "endpointConfiguration": {
    "@odata.type": "microsoft.graph.httpRequestEndpoint",
    "targetUrl": "String"
  },
  "authenticationConfiguration": {
    "@odata.type": "microsoft.graph.azureAdTokenAuthentication",
    "resourceId": "String"
  },
  "clientConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionClientConfiguration"
  },
  "behaviorOnError": {
    "@odata.type": "microsoft.graph.customExtensionBehaviorOnError"
  }
}
```
