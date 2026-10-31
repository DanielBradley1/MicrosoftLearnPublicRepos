<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# roleManagementCustomCalloutExtension resource type

Namespace: microsoft.graph

Represents a custom workflow extension for Privileged Identity Management \(PIM\) role management operations. Use this resource to integrate external approval, ticketing, compliance, audit, or notification systems into role assignment lifecycle events for Microsoft Entra roles, Azure resources, and groups.

Inherits from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/privilegedaccessroot-list-customextensions?view=graph-rest-1.0) | [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0) collection | Get a list of PIM custom extensions. |
| [Create](https://learn.microsoft.com/en-us/graph/api/privilegedaccessroot-post-customextensions?view=graph-rest-1.0) | [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0) | Create a PIM custom extension. |
| [Get](https://learn.microsoft.com/en-us/graph/api/rolemanagementcustomcalloutextension-get?view=graph-rest-1.0) | [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0) | Retrieve a PIM custom extension. |
| [Update](https://learn.microsoft.com/en-us/graph/api/rolemanagementcustomcalloutextension-update?view=graph-rest-1.0) | [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0) | Update a PIM custom extension. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/rolemanagementcustomcalloutextension-delete?view=graph-rest-1.0) | None | Delete a PIM custom extension. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | The authentication configuration used to secure calls to the external app. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| clientConfiguration | [customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0) | The HTTP connection settings for calls to the external app. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| customAttributes | String collection | The custom attribute names to include in the callout payload. |
| description | String | The description of the custom extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| displayName | String | The display name of the custom extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | The configuration for the external endpoint that PIM calls. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). |
| id | String | The unique identifier for the custom extension. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | When `true`, enables the custom extension. When `false`, disables it. Nullable. |
| resourceType | [customExtensionResourceType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#customextensionresourcetype-values) | The PIM provider to which the extension applies. The possible values are: `entraRoles`, `azureResources`, `entraGroups`, `unknownFutureValue`, `applicationAuthorization`, `appRoles`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `applicationAuthorization`, `appRoles`. Supports `$filter` \(`eq`\). |
| type | [customCalloutExtensionType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#customcalloutextensiontype-values) | The role assignment lifecycle stage at which PIM invokes the extension. The possible values are: `preApproval`, `postApproval`, `grant`, `revoke`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.roleManagementCustomCalloutExtension",
  "id": "String (identifier)",
  "authenticationConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionAuthenticationConfiguration"
  },
  "clientConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionClientConfiguration"
  },
  "customAttributes": ["String"],
  "description": "String",
  "displayName": "String",
  "endpointConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionEndpointConfiguration"
  },
  "isEnabled": "Boolean",
  "resourceType": "String",
  "type": "String"
}
```
