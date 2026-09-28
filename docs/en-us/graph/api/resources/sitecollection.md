<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sitecollection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# siteCollection resource type

Namespace: microsoft.graph

Provides more information about a site collection.

If a [**site**](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) resource has a non-null **siteCollection** property, then the site is a root site for a site collection.

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| **dataLocationCode** | string | The geographic region code for where this site collection resides. Only present for multi-geo tenants. Read-only. |
| **hostname** | string | The hostname for the site collection. Read-only. |
| **root** | [root](https://learn.microsoft.com/en-us/graph/api/resources/root?view=graph-rest-1.0) | If present, indicates that this is a root site collection in SharePoint. Read-only. |
| **archivalDetails** | [siteArchivalDetails](https://learn.microsoft.com/en-us/graph/api/resources/sitearchivaldetails?view=graph-rest-1.0) | Represents whether the site collection is recently archived, fully archived, or reactivating. The possible values are: `recentlyArchived`, `fullyArchived`, `reactivating`, `unknownFutureValue`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "hostname": "contoso.sharepoint.com",
  "dataLocationCode": "EUR",
  "root": { "@odata.type": "microsoft.graph.root" },
  "archivalDetails": {
    "@odata.type": "microsoft.graph.siteArchivalDetails",
    "archiveStatus": "fullyArchived"
  }
}
```
