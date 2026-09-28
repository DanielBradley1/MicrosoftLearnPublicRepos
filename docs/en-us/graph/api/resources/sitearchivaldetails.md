<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sitearchivaldetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# siteArchivalDetails resource type

Represents the archival details of a [siteCollection](https://learn.microsoft.com/en-us/graph/api/resources/sitecollection?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| archiveStatus | siteArchiveStatus | Represents the current archive status of the site collection. Requires `$select` to retrieve. The possible values are: `recentlyArchived`, `fullyArchived`, `reactivating`, `unknownFutureValue`. |

## siteArchiveStatus values

| Value | Description |
| :--- | :--- |
| recentlyArchived | The site collection was recently archived. |
| fullyArchived | The site collection is fully archived. |
| reactivating | The site collection is reactivating. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "archiveStatus": "fullyArchived"
}
```
