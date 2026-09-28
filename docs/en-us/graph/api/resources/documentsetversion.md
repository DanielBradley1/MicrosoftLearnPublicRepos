<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# documentSetVersion resource type

Namespace: microsoft.graph

Represents the version of a document set item in a list.

Inherits from [listItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/listitemversion?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/listitem-list-documentsetversions?view=graph-rest-1.0) | [documentSetVersion](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0) collection | Get a list of the [versions of a document set](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0) item in a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/listitem-post-documentsetversions?view=graph-rest-1.0) | [documentSetVersion](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0) | Create a new [version of a document set](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0) item in a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/documentsetversion-get?view=graph-rest-1.0) | [documentSetVersion](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0) | Read the properties and relationships of a [documentSetVersion](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/documentsetversion-delete?view=graph-rest-1.0) | None | Delete a [version of a document set](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0) in a list. |
| [Restore](https://learn.microsoft.com/en-us/graph/api/documentsetversion-restore?view=graph-rest-1.0) | [documentSetVersion](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0) | Restore a [document set version](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| comment | string | Comment about the captured version. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | User who captured the version. |
| createdDateTime | dateTime | Date and time when this version was created. |
| id | string | The ID of the version. Read-only. Inherited from [listItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/listitemversion?view=graph-rest-1.0). |
| items | [documentSetVersionItem](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversionitem?view=graph-rest-1.0) collection | Items within the document set that are captured as part of this version. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user which last modified the version. Read-only. Inherited from [listItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/listitemversion?view=graph-rest-1.0). |
| lastModifiedDateTime | [dateTimeOffset](https://learn.microsoft.com/en-us/graph/api/resources/timestamp?view=graph-rest-1.0) | Date and time when the version was last modified. Read-only. Inherited from [listItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/listitemversion?view=graph-rest-1.0). |
| published | [publicationFacet](https://learn.microsoft.com/en-us/graph/api/resources/publicationfacet?view=graph-rest-1.0) | Indicates the publication status of this particular version. Read-only. Inherited from [listItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/listitemversion?view=graph-rest-1.0). |
| shouldCaptureMinorVersion | Boolean | If `true`, minor versions of items are also captured; otherwise, only major versions are captured. The default value is `false`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| fields | [fieldValueSet](https://learn.microsoft.com/en-us/graph/api/resources/fieldvalueset?view=graph-rest-1.0) | A collection of the fields and values for this version of the list item. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.documentSetVersion",
  "comment": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "id": "String (identifier)",
  "items": [
    {
      "@odata.type": "microsoft.graph.documentSetVersionItem"
    }
  ],
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "publication": {
    "@odata.type": "microsoft.graph.publicationFacet"
  },
  "shouldCaptureMinorVersion": "Boolean"
}
```
