<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartcustomextension?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-30 -->

# onAttributeCollectionStartCustomExtension resource type

Namespace: microsoft.graph

Used for creating a new custom extension based on the **onAttributeCollectionStart** event. This can be used to prefill attributes or block sign-up.

Inherits from [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0).

[Try out this event in the Woodgrove demo tenant](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-overview#attribute-collection-start).

## Methods

None.

For the list of API operations for managing this resource type, see the [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | Configuration for securing the API call. For example, using OAuth client credentials flow. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| clientConfiguration | [customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0) | HTTP connection settings that define how long Microsoft Entra ID can wait for a connection, how many times you can retry a timed-out connection and the exception scenarios when retries are allowed. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| description | String | Description for the onAttributeCollectionStartCustomExtension object. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| displayName | String | Display name for the onAttributeCollectionStartCustomExtension object. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | The type and details for configuring the endpoint to call the app's workflow. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| id | String | Identifier for the onAttributeCollectionStartCustomExtension object. Inherited from entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onAttributeCollectionStartCustomExtension",
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
  }
}
```

## Related content

- [Custom authentication extensions for attribute collection start and submit events](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-attribute-collection)
- [OnAttributeCollectionStart event reference](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-onattributecollectionstart-reference)
