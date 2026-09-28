<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-14 -->

# Working with SharePoint sites in Microsoft Graph

The SharePoint API in Microsoft Graph supports the following core scenarios:

- Access to SharePoint **sites**, **lists**, and **drives** \(document libraries\)
- Read-only support for **site** resources \(no ability to create new sites\)
- Read-write support for **lists**, **listItems**, and **driveItems**
- Read-write support for tenant-level **SharePointSettings**
- Address resources by SharePoint ID, URL, or relative path

The SharePoint API exposes three major resource types:

- [Site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) *\(top-level object\)*
- [List](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0)
- [ListItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0)

The following is an example of a listItem resource.

```json
{
  "fields": {
    "Title": "Access card",
    "Employee": "Ryan Gregg",
    "EmployeeId": "10",
    "CardSerial": "01235492",
    "Alias": "RGregg",
    "ID": 1,
    "ContentType": "Item",
    "Modified": "2016-09-19T23:15:25-07:00",
    "Created": "2016-09-19T23:15:25-07:00"
  },
  "createdBy": {
    "user": {
      "id": "b757fdcb-0271-4807-b243-504139e4ba04",
      "displayName": "Ryan Gregg"
    }
  },
  "createdDateTime": "2016-09-20T06:15:25Z",
  "eTag": "48e941c3-9515-4c48-9760-c07c90c79d48,1",
  "id": "4",
  "lastModifiedBy": {
    "user": {
      "id": "b757fdcb-0271-4807-b243-504139e4ba04",
      "displayName": "Ryan Gregg"
    }
  },
  "lastModifiedDateTime": "2016-09-20T06:15:25Z",
}
```

Resources expose data in three different ways:

- *Properties* \(like **id** and **name**\) expose simple values.
- *Facets* \(like **fields** and **createdBy**\) expose complex values.
- *References* \(like **items**\) point to collections of other resources.

You can expand references in your URL with the *expand* query parameter; for example, `?expand=fields`. You can request specific properties and facets with the *select* query parameter; for example, `?select=id,name`. By default, most properties and facets are returned while all references are hidden. For efficiency, we recommend that you specify *select* and *expand* to only return the data you care about.

## SharePoint API root resources

The following examples are relative to `https://graph.microsoft.com/v1.0`.

| Path | Description |
| :--- | :--- |
| /sites/root | Organization's default [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| /sites/{site-id} | Access a specific [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) by its ID. |
| /sites/{site-id}/drive | Access the default [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) \(document library\) for the given [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| /sites/{site-id}/drives | Enumerate the [drives](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) \(document libraries\) under the [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| /sites/{site-id}/sites | Enumerate the sub-sites under the [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| /sites/{site-id}/lists | Enumerate the [lists](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) under the [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| /sites/{site-id}/lists/{list-id}/items | Enumerate the [listItems](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) under the [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |
| /groups/{group-id}/sites/root | Access a group's team [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| /admin/sharepoint/settings | Access the organization's admin level [settings](https://learn.microsoft.com/en-us/graph/api/resources/sharepointsettings?view=graph-rest-1.0). |

Sites can also be addressed by path by using the SharePoint hostname, followed by a colon and the relative path to the site. You can optionally transition back to addressing the resource model by putting another colon at the end.

| Path | Description |
| :--- | :--- |
| /sites/contoso.sharepoint.com:/teams/hr | The site associated with `https://contoso.sharepoint.com/teams/hr` |
| /sites/contoso.sharepoint.com:/teams/hr:/drive | Access the default [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) for this site. |

## Note for existing SharePoint developers

The Microsoft Graph SharePoint API has a few key differences with the CSOM APIs. The [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) resource maps to `SPWeb`. The root [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) \(`SPWeb`\) in a site collection has a [siteCollection](https://learn.microsoft.com/en-us/graph/api/resources/sitecollection?view=graph-rest-1.0) facet, which contains information about the `SPSite`. Because IDs for sites are only unique within their site collection, addressing a site by ID requires providing both the site collection identifier and the site identifier.

```http
GET https://graph.microsoft.com/v1.0/sites/{hostname},{spsite-id},{spweb-id}/
```

A URL constructed with only the hostname points to the root site \(`SPWeb`\) in the default site collection.

```http
GET https://graph.microsoft.com/v1.0/sites/{hostname}
```

A URL constructed with only the hostname and siteCollection \(`SPSite`\) ID points to the root site \(`SPWeb`\) in the given site collection.

```http
GET https://graph.microsoft.com/v1.0/sites/{hostname},{spsite-id}
```

A URL constructed with only the siteCollection \(`SPSite`\) ID points to the root site \(`SPWeb`\) in the given site collection.

```http
GET https://graph.microsoft.com/v1.0/sites/{spsite-id}
```

## Mapping from SharePoint REST v1 API URLs to Microsoft Graph API URLs

The following examples help developers familiar with SharePoint REST v1 API URL patterns adapt their use cases to similar Microsoft Graph API URL patterns.

### Pattern 1

Access the site associated with the specified `SPWeb` URL.

```http
GET https://graph.microsoft.com/v1.0/sites/{hostname}:/{site-server-relative-url}
```

### Example 1

The following example returns information about the site associated with the `SPWeb` URL `https://contoso.sharepoint.com/teams/hr/benefits`. Note that `benefits` is an `SPWeb` within the site collection \(`SPSite`\) at `https://contoso.sharepoint.com/teams/hr`.

```http
GET https://graph.microsoft.com/v1.0/sites/contoso.sharepoint.com:/teams/hr/benefits
```

### Pattern 2

Access the list item associated with the following components.

| Component | Description |
| :--- | :--- |
| {hostname} | The hostname of the site. |
| {site-server-relative-url} | The server-relative URL of the site \(`SPWeb`\). |
| {list-id} | The GUID ID of the list \(`SPList`\) in the site. |
| {item-id} | The GUID or integer ID of the list item \(`SPListItem`\) in the list. |

The following example shows a request that contains the previous components.

```http
GET https://graph.microsoft.com/v1.0/sites/{hostname}:/{site-server-relative-url}:/lists/{list-id}/items/{item-id}
```

### Example 2

The following example returns information about the `SPListItem` with integer ID `42` that belongs to the list with GUID ID `5771e865-4e91-48b8-a0de-35a25d4e52fe`. This list belongs to the site associated with the `SPWeb` URL `https://contoso.sharepoint.com/teams/hr/benefits`.

```http
GET https://graph.microsoft.com/v1.0/sites/contoso.sharepoint.com:/teams/hr/benefits:/lists/5771e865-4e91-48b8-a0de-35a25d4e52fe/items/42
```
