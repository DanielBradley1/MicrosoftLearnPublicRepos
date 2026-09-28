<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# BaseItem resource type

Namespace: microsoft.graph

The **baseItem** resource is an abstract resource that contains a common set of properties shared among several other resources types. Resources that derive from **baseItem** include:

- [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0)
- [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0)
- [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0)
- [sharedDriveItem](https://learn.microsoft.com/en-us/graph/api/resources/shareddriveitem?view=graph-rest-1.0)

## JSON representation

Here's a JSON representation of a **baseItem** resource.

```json
{
  "createdBy": { "@odata.type": "microsoft.graph.identitySet" },
  "createdDateTime": "datetime",
  "description": "string",
  "eTag": "string",
  "id": "string (identifier)",
  "lastModifiedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "lastModifiedDateTime": "datetime",
  "name": "string",
  "parentReference": { "@odata.type": "microsoft.graph.itemReference" },
  "webUrl": "url"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, or application that created the item. Read-only. |
| createdDateTime | dateTimeOffset | Date and time of item creation. Read-only. |
| description | String | Provides a user-visible description of the item. Optional. |
| eTag | string | ETag for the item. Read-only. |
| id | string | The unique identifier of the drive. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application that last modified the item. Read-only. |
| lastModifiedDateTime | dateTimeOffset | Date and time the item was last modified. Read-only. |
| name | string | The name of the item. Read-write. |
| parentReference | [itemReference](https://learn.microsoft.com/en-us/graph/api/resources/itemreference?view=graph-rest-1.0) | Parent information, if the item has a parent. Read-write. |
| webUrl | string \(url\) | URL that either displays the resource in the browser \(for Office file formats\), or is a direct link to the file \(for other formats\). Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| createdByUser | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | Identity of the user who created the item. Read-only. |
| lastModifiedByUser | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | Identity of the user who last modified the item. Read-only. |

## Remarks

The `baseItem` type isn't expected to be used directly.
