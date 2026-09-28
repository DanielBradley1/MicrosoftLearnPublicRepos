<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# customTaskExtension resource type

Namespace: microsoft.graph.identityGovernance

Defines the attributes of a customTaskExtension that allows you to integrate Lifecycle Workflows with Azure Logic Apps. While Lifecycle Workflows provide multiple built-in tasks \(known as taskDefinitions\) to automate common scenarios during the user lifecycle, you may eventually reach the limits of these built-in tasks. You can create a customTaskExtension that contains information about an Azure Logic app, and trigger the Azure Logic app with the built-in task "Run a custom task extension" that references the corresponding customTaskExtension.

Inherits from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0).

For more information about using custom task extensions, refer to the links in the [see also](#related-content) section.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-customtaskextensions?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) collection | Get a list of the [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-post-customtaskextensions?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) | Create a new [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/identitygovernance-customtaskextension-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) | Read the properties and relationships of a [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/identitygovernance-customtaskextension-update?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) | Update the properties of a [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/identitygovernance-customtaskextension-delete?view=graph-rest-1.0) | None | Deletes a [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [microsoft.graph.customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | Configuration for securing the API call to the logic app. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Required. |
| callbackConfiguration | [microsoft.graph.identityGovernance.customTaskExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensioncallbackconfiguration?view=graph-rest-1.0) | The callback configuration for a custom task extension. |
| clientConfiguration | [microsoft.graph.customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0) | HTTP connection settings that define how long Microsoft Entra ID can wait for a connection to a logic app, how many times you can retry a timed-out connection and the exception scenarios when retries are allowed. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | When the custom task extension was created.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| description | String | Describes the purpose of the custom task extension for administrative use. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| displayName | String | A unique string that identifies the custom task extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Required.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| endpointConfiguration | [microsoft.graph.customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | Details for allowing the custom task extension to call the logic app. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| id | String | Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| lastModifiedDateTime | DateTimeOffset | When the custom extension was last modified.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| replyMode | microsoft.graph.identityGovernance.customTaskExtensionReplyMode | Specifies how the custom task extension replies to the lifecycle workflows service. The possible values are: `none`, `callback`, `response`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| createdBy | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The unique identifier of the Microsoft Entra user that created the custom task extension.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$expand`. |
| lastModifiedBy | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The unique identifier of the Microsoft Entra user that modified the custom task extension last.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.customTaskExtension",
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
  "callbackConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionCallbackConfiguration"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "replyMode": "String"
}
```

## Related content

- [Lifecycle Workflows Custom Task Extension \(Preview\)](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-extensibility)
