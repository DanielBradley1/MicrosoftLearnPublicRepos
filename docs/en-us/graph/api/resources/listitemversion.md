<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/listitemversion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# ListItemVersion resource type

Namespace: microsoft.graph

The **listItemVersion** resource represents a previous version of a [ListItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) resource.

## Tasks on ListItemVersion resources

The following tasks are available for listItemVersion resources.

| Common task | HTTP method |
| :--- | :--- |
| [List versions](https://learn.microsoft.com/en-us/graph/api/listitem-list-versions?view=graph-rest-1.0) | `GET /sites/{site-id}/lists/{list-id}/items/{item-id}/versions` |
| [Get version](https://learn.microsoft.com/en-us/graph/api/listitemversion-get?view=graph-rest-1.0) | `GET /sites/{site-id}/lists/{list-id}/items/{item-id}/versions/{version-id}` |
| [Restore version](https://learn.microsoft.com/en-us/graph/api/listitemversion-restore?view=graph-rest-1.0) | `POST /sites/{site-id}/lists/{list-id}/items/{item-id}/versions/{version-id}/restore` |

## JSON representation

```json
{
  "fields": { "@odata.type": "microsoft.graph.fieldValueSet" },
  "id": "string",
  "lastModifiedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "lastModifiedDateTime": "2016-01-01T15:20:01.125Z",
  "published": { "@odata.type": "microsoft.graph.publicationFacet" }
}
```

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| **id** | string | The ID of the version. Read-only. |
| **lastModifiedBy** | [IdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user which last modified the version. Read-only. |
| **lastModifiedDateTime** | [DateTimeOffset](https://learn.microsoft.com/en-us/graph/api/resources/timestamp?view=graph-rest-1.0) | Date and time the version was last modified. Read-only. |
| **published** | [PublicationFacet](https://learn.microsoft.com/en-us/graph/api/resources/publicationfacet?view=graph-rest-1.0) | Indicates the publication status of this particular version. Read-only. |

## Relationships

The following table defines the relationships that the **driveItemVersion** resource has to other resources.

| Relationship name | Type | Description |
| :--- | :--- | :--- |
| **fields** | [FieldValueSet](https://learn.microsoft.com/en-us/graph/api/resources/fieldvalueset?view=graph-rest-1.0) | A collection of the fields and values for this version of the list item. |
