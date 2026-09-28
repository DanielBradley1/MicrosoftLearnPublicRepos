<!-- Source: https://learn.microsoft.com/en-us/graph/api/site-getbypath?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-14 -->

# Get a site resource by path

Namespace: microsoft.graph

Retrieve properties and relationships for a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) resource. A **site** resource represents a team site in SharePoint.

In addition to retrieving a [site by ID](https://learn.microsoft.com/en-us/graph/api/site-get?view=graph-rest-1.0) you can retrieve a site based on server-relative URL path.

- Site collection hostname \(contoso.sharepoint.com\)
- Site path, relative to server hostname.

There is also a reserved site identifier, `root`, which always references the root site for a given target, as follows:

- `/sites/root`: The tenant root site.
- `/groups/{group-id}/sites/root`: The group's team site.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Read.All | Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Read.All | Sites.ReadWrite.All |

## HTTP Request

```http
GET /sites/{hostname}:/{relative-path}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Example

### Request

To access the root SharePoint site with a relative path:

```http
GET https://graph.microsoft.com/v1.0/sites/{hostname}:/{relative-path}
```

### Response

This method returns a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) resource for the site referenced by the unique identifier.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "contoso.sharepoint.com,2C712604-1370-44E7-A1F5-426573FDA80A,2D2244C3-251A-49EA-93A8-39E1C3A060FE",
  "displayName": "OneDrive Team Site",
  "isPersonalSite": false,
  "name": "1drvteam",
  "createdDateTime": "2017-05-09T20:56:00Z",
  "lastModifiedDateTime": "2017-05-09T20:56:01Z",
  "webUrl": "https://contoso.sharepoint.com/teams/1drvteam"
}
```
