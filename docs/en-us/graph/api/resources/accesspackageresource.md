<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# accessPackageResource resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package resource is a reference to a resource associated with an access package catalog for which an access package can be configured to provide access. This can be a group, an app, or a SharePoint Online site. To request to associate a resource with an access package catalog, or remove a resource from a catalog, create an [accessPackageResourceRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerequest?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resources?view=graph-rest-1.0) | [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) collection | Retrieve a list of accessPackageResource objects in a catalog. |
| [Refresh](https://learn.microsoft.com/en-us/graph/api/accesspackageresource-refresh?view=graph-rest-1.0) | None | Refresh the resource information from the originSystem. |
| [List uploadSessions](https://learn.microsoft.com/en-us/graph/api/accesspackageresource-list-uploadsessions?view=graph-rest-1.0) | [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) collection | Get a list of the upload sessions created on an accessPackageResource. |
| [Create customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/accesspackageresource-post-uploadsessions?view=graph-rest-1.0) | [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) | Create a new upload session on an accessPackageResource. |
| [Delete customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/accesspackageresource-delete-uploadsessions?view=graph-rest-1.0) | None | Delete an upload session from an accessPackageResource. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attributes | [accessPackageResourceAttribute](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattribute?view=graph-rest-1.0) collection | Contains information about the attributes to be collected from the requestor and sent to the resource application. |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| description | String | A description for the resource. |
| displayName | String | The display name of the resource, such as the application name, group name or site name. |
| id | String | Read-only. |
| modifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| originId | String | The unique identifier of the resource in the origin system. For a Microsoft Entra group, this is the identifier of the group. |
| originSystem | String | The type of the resource in the origin system, such as `SharePointOnline`, `AadApplication` or `AadGroup`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| environment | [accessPackageResourceEnvironment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceenvironment?view=graph-rest-1.0) | Contains the environment information for the resource. This can be set using either the `@odata.bind` annotation or the environment's *originId*.Supports `$expand`. |
| externalOriginResourceConnector | [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0) | The connector that integrates with external origin systems to provision access to resources from those systems. Read-only. Nullable. |
| roles | [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-1.0) collection | Read-only. Nullable. Supports `$expand`. |
| scopes | [accessPackageResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcescope?view=graph-rest-1.0) collection | Read-only. Nullable. Supports `$expand`. |
| uploadSessions | [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) collection | The upload sessions for uploading external access data to this resource through the Bring Your Own Data \(BYOD\) flow. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
   "attributes": [
    {
      "@odata.type": "microsoft.graph.accessPackageResourceAttribute"
    }
   ],
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "modifiedDateTime": "String (timestamp)",
  "originId": "String",
  "originSystem": "String"
}
```
