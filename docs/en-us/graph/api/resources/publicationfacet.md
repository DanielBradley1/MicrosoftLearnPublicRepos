<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/publicationfacet?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# PublicationFacet resource type

Namespace: microsoft.graph

The **publicationFacet** resource provides details on the published status of a [driveItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/driveitemversion?view=graph-rest-1.0) or [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) resource.

## JSON representation

```json
{
  "level": "published | checkout",
  "versionId": "string",
  "checkedOutBy": { "@odata.type": "microsoft.graph.identitySet" }
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| **level** | String | The state of publication for this document. Either `published` or `checkout`. Read-only. |
| **versionId** | String | The unique identifier for the version that is visible to the current caller. Read-only. |
| **checkedOutBy** | microsoft.graph.identitySet | The user who checked out the file. |
