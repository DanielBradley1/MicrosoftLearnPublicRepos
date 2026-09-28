<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# customAccessPackageWorkflowExtension resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The customAccessPackageWorkflowExtension resource type and its associated methods is deprecated and will be retired on December 31, 2023. Use the [accessPackageAssignmentRequestWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestworkflowextension?view=graph-rest-beta) and [accessPackageAssignmentWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentworkflowextension?view=graph-rest-beta) resource types and their associated methods.

Defines the attributes of a logic app, which can be called at various stages of an access package request and assignment cycle. You can integrate logic apps with entitlement management to broaden your governance workflows beyond the core entitlement management use cases. The following use cases can be integrated with logic apps using this workflow:

- When an [access package is requested](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-beta)
- When an [access package request is granted](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-beta)
- When an [access package assignment expires](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-beta)

Inherits and derived from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-customaccesspackageworkflowextensions?view=graph-rest-beta) | [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) collection | Get a list of the [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-post-customaccesspackageworkflowextensions?view=graph-rest-beta) | [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) | Create a new [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/customaccesspackageworkflowextension-get?view=graph-rest-beta) | [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) | Read the properties and relationships of a [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/customaccesspackageworkflowextension-update?view=graph-rest-beta) | [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) | Update the properties of a [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/customaccesspackageworkflowextension-delete?view=graph-rest-beta) | None | Deletes a [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-beta) | Configuration for securing the API call to the logic app. For example, using OAuth client credentials flow. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-beta). |
| clientConfiguration | [customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-beta) | HTTP connection settings that define how long Microsoft Entra ID can wait for a connection to a logic app, how many times you can retry a timed-out connection and the exception scenarios when retries are allowed. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| description | String | Description for the customAccessPackageWorkflowExtension object. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-beta). Read-only. |
| displayName | String | Display name for the customAccessPackageWorkflowExtension object. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-beta). Read-only. Supports `$filter` \(`contains`\). |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-beta) | The type and details for configuring the endpoint to call the logic app's workflow. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-beta). |
| id | String | Identifier for the customAccessPackageWorkflowExtension object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customAccessPackageWorkflowExtension",
  "id": "String (identifier)",
  "displayName": "String",
  "clientConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionClientConfiguration"
  },
  "authenticationConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionAuthenticationConfiguration"
  },
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "endpointConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionEndpointConfiguration"
  }
}
```
