<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartcustomextension?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-30 -->

# onTokenIssuanceStartCustomExtension resource type

Namespace: microsoft.graph

Custom extension to invoke when handling the event when a token is about to be issued to your application.

Inherits from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0).

[Try out this event in the Woodgrove demo tenant](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-overview#token-issuance-start).

## Methods

None.

For the list of API operations for managing this resource type, see the [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | The authentication configuration for this custom authentication extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| claimsForTokenConfiguration | [onTokenIssuanceStartReturnClaim](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartreturnclaim?view=graph-rest-1.0) collection | Collection of claims to be returned by the API called by this custom authentication extension. Used to populate claims mapping experience in Microsoft Entra admin center. Optional. |
| clientConfiguration | [customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0) | The connection settings for the custom authentication extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| description | String | Description for the custom authentication extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| displayName | String | Display name for the custom authentication extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | Configuration for the API endpoint that the custom authentication extension will call. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| id | String | Identifier for onTokenIssuanceStartCustomExtension. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onTokenIssuanceStartCustomExtension",
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
  "claimsForTokenConfiguration": [
    {
      "@odata.type": "microsoft.graph.onTokenIssuanceStartReturnClaim"
    }
  ]
}
```
