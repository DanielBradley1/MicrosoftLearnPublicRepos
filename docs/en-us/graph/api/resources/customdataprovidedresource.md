<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# customDataProvidedResource resource type

Namespace: microsoft.graph

Represents an external application whose access data is provided through the Bring Your Own Data \(BYOD\) flow for catalog user access reviews. The **originSystem** of a customDataProvidedResource is always `CustomDataProvidedResource`.

Inherits from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0).

For more information, see [Include custom data provided resource in the catalog for catalog user Access Reviews](https://learn.microsoft.com/en-us/entra/id-governance/custom-data-resource-access-reviews).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List uploadSessions](https://learn.microsoft.com/en-us/graph/api/accesspackageresource-list-uploadsessions?view=graph-rest-1.0) | [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) collection | Get a list of the upload sessions created on a customDataProvidedResource. |
| [Create customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/accesspackageresource-post-uploadsessions?view=graph-rest-1.0) | [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) | Create a new upload session on a customDataProvidedResource. |
| [Delete customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/accesspackageresource-delete-uploadsessions?view=graph-rest-1.0) | None | Delete an upload session from a customDataProvidedResource. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attributes | [accessPackageResourceAttribute](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattribute?view=graph-rest-1.0) collection | Contains information about the attributes to be collected from the requestor and sent to the resource application. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |
| description | String | A description for the resource. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |
| displayName | String | The display name of the resource, such as the application name, group name, or site name. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |
| id | String | Read-only. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |
| modifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |
| notificationEndpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | The endpoint configuration of the logic app that is triggered when the access review for this resource goes into an initializing state. |
| originId | String | The unique identifier of the resource in the origin system. For a Microsoft Entra group, this is the identifier of the group. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |
| originSystem | String | The type of the resource in the origin system. For a customDataProvidedResource, the value is always `CustomDataProvidedResource`. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| environment | [accessPackageResourceEnvironment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceenvironment?view=graph-rest-1.0) | Contains the environment information for the resource. This can be set using either the `@odata.bind` annotation or the environment's *originId*. Supports `$expand`. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |
| roles | [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-1.0) collection | Read-only. Nullable. Supports `$expand`. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |
| scopes | [accessPackageResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcescope?view=graph-rest-1.0) collection | Read-only. Nullable. Supports `$expand`. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |
| uploadSessions | [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) collection | The upload sessions for uploading external access data to this resource through the Bring Your Own Data \(BYOD\) flow. Inherited from [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customDataProvidedResource",
  "id": "String (identifier)",
  "attributes": [
    {
      "@odata.type": "microsoft.graph.accessPackageResourceAttribute"
    }
  ],
  "displayName": "String",
  "description": "String",
  "originId": "String",
  "originSystem": "String",
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "notificationEndpointConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionEndpointConfiguration"
  }
}
```
