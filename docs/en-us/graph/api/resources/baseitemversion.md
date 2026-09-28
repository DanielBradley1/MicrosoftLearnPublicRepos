<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/baseitemversion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# BaseItemVersion resource type

Namespace: microsoft.graph

The **baseItemVersion** resource represents a previous version of an item or entity.

## JSON representation

```json
{
  "id": "string",
  "lastModifiedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "lastModifiedDateTime": "2016-01-01T15:20:01.125Z",
  "publication": { "@odata.type": "microsoft.graph.publicationFacet" }
}
```

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| **id** | string | The ID of the version. Read-only. |
| **lastModifiedBy** | [IdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user which last modified the version. Read-only. |
| **lastModifiedDateTime** | [DateTimeOffset](https://learn.microsoft.com/en-us/graph/api/resources/timestamp?view=graph-rest-1.0) | Date and time the version was last modified. Read-only. |
| **publication** | [PublicationFacet](https://learn.microsoft.com/en-us/graph/api/resources/publicationfacet?view=graph-rest-1.0) | Indicates the publication status of this particular version. Read-only. |
