<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointids?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# SharePointIds resource type

Namespace: microsoft.graph

The **SharePointIds** resource groups the various identifiers for an item stored in a SharePoint site or OneDrive for Business into a single structure.

**Note:** items returned from OneDrive personal will not include a **SharePointIds** facet.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "listId": "string",
    "listItemId": "string",
    "listItemUniqueId": "string",
    "siteId": "string",
    "siteUrl": "url",
    "tenantId": "string",
    "webId": "string"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| listId | string | The unique identifier \(guid\) for the item's list in SharePoint. |
| listItemId | string | An integer identifier for the item within the containing list. |
| listItemUniqueId | string | The unique identifier \(guid\) for the item within OneDrive for Business or a SharePoint site. |
| siteId | string | The unique identifier \(guid\) for the item's site collection \(SPSite\). |
| siteUrl | string \(url\) | The SharePoint URL for the site that contains the item. |
| tenantId | string | The unique identifier \(guid\) for the tenancy. |
| webId | string | The unique identifier \(guid\) for the item's site \(SPWeb\). |

## Remarks

For more information about the facets on a **driveItem**, see [**driveItem**](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
