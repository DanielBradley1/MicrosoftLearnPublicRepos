<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# customAuthenticationExtension resource type

Namespace: microsoft.graph

Custom authentication extensions define interactions with external systems during a user authentication session. This is an abstract type from which the following types are derived.

- [onTokenIssuanceStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartcustomextension?view=graph-rest-1.0) resource type.
- [onAttributeCollectionStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartcustomextension?view=graph-rest-1.0) resource type.
- [onAttributeCollectionSubmitCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmitcustomextension?view=graph-rest-1.0) resource type.
- [onOtpSendCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onotpsendcustomextension?view=graph-rest-1.0) resource type.
- [onPasswordSubmitCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmitcustomextension?view=graph-rest-1.0) resource type.
- [onVerifiedIdClaimValidationCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationcustomextension?view=graph-rest-1.0) resource type.

Inherits from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0).

Learn how to use this API when [Configuring a custom claim provider token issuance event \(preview\)](https://learn.microsoft.com/en-us/azure/active-directory/develop/custom-extension-get-started?tabs=microsoft-graph?toc=/graph/toc.json&context=graph/context).

Note

You can have a maximum of 100 custom extension policies.

[Learn more about custom authentication extensions](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-overview) and how to use this API when [Configuring a custom claim provider token issuance event \(preview\)](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-configuration?toc=/graph/toc.json&context=graph/context).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identitycontainer-list-customauthenticationextensions?view=graph-rest-1.0) | [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) collection | Retrieve a list of the object types that are derived from **customAuthenticationExtension**. |
| [Create](https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-customauthenticationextensions?view=graph-rest-1.0) | [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) | Create a new object type that is derived from **customAuthenticationExtension**. |
| [Get](https://learn.microsoft.com/en-us/graph/api/customauthenticationextension-get?view=graph-rest-1.0) | [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) | Read the properties and relationships of an object type that is derived from **customAuthenticationExtension**. |
| [Update](https://learn.microsoft.com/en-us/graph/api/customauthenticationextension-update?view=graph-rest-1.0) | None | Update the properties of an object type that is derived from **customAuthenticationExtension**. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/customauthenticationextension-delete?view=graph-rest-1.0) | None | Delete an object type that is derived from **customAuthenticationExtension**. |
| [Validate authentication configuration](https://learn.microsoft.com/en-us/graph/api/customauthenticationextension-validateauthenticationconfiguration?view=graph-rest-1.0) | [authenticationConfigurationValidation](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconfigurationvalidation?view=graph-rest-1.0) | Check the validity of the endpoint and authentication configuration for a [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | The authentication configuration for the customAuthenticationExtension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| behaviorOnError | [customExtensionBehaviorOnError](https://learn.microsoft.com/en-us/graph/api/resources/customextensionbehavioronerror?view=graph-rest-1.0) | The behaviour on error for the custom authentication extension. |
| clientConfiguration | [customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0) | The connection settings for the customAuthenticationExtension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| description | String | The description of the customAuthenticationExtension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| displayName | String | The display name for the customAuthenticationExtension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | The HTTP endpoint that this custom extension calls. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| id | String | Identifier for the customAuthenticationExtension. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customAuthenticationExtension",
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

## Related content

- [Configure a custom claim provider token issuance event \(preview\)](https://learn.microsoft.com/en-us/azure/active-directory/develop/custom-extension-get-started?tabs=microsoft-graph?toc=/graph/toc.json&context=graph/context)
