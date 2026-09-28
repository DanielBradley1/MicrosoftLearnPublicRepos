<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# sharePointIdentity resource type

Represents the **sharePointIdentity** of an *actor*.

This resource extends from the **identity** resource to expose SharePoint-specific information; for example, **loginName** or SharePoint IDs.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The identity's display name and might not always be available or up to date. For example, if a user changes their display name, the API might show the new value in a future response, but the items associated with the user won't show up as having changed when using [delta](https://learn.microsoft.com/en-us/graph/api/driveitem-delta?view=graph-rest-1.0). |
| id | String | Unique identifier for the identity. It can be either a Microsoft Entra ID or a SharePoint ID. |
| loginName | String | The sign in name of the SharePoint identity. |
| thumbnails | [thumbnailSet](https://learn.microsoft.com/en-us/graph/api/resources/thumbnailset?view=graph-rest-1.0) collection | Collection that contains [thumbnailSet](https://learn.microsoft.com/en-us/graph/api/resources/thumbnailset?view=graph-rest-1.0) objects associated with the item. For more information, see [List thumbnails for a driveItem](https://learn.microsoft.com/en-us/graph/api/driveitem-list-thumbnails?view=graph-rest-1.0). Read-only. Nullable. |

## JSON representation

```json
{
  "loginName": "string",

  /** inherited from Identity */
  "displayName": "string",
  "id": "string",
  "thumbnails": [{ "@odata.type": "microsoft.graph.thumbnailSet" }]
}
```
