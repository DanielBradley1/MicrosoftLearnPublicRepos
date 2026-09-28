<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onenote-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# Use the OneNote REST API

Microsoft Graph lets your app get authorized access to a user's OneNote notebooks, sections, and pages in a personal or organization account. With the [appropriate delegated permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#notes-permissions), your app can access the OneNote data of the signed-in user or any user in a tenant.

Note

The Microsoft Graph OneNote API doesn't support app-only authentication.

## Root URL

The OneNote service root URL uses the following format for all calls to the OneNote API.

```http
https://graph.microsoft.com/{version}/{location}/onenote/ 
```

The `version` segment in the URL represents the version of Microsoft Graph that you want to use:

- `v1.0` is for stable production code.
- `beta` is to try out a feature that's in development. Features and functionality in the beta endpoint might change; we don't recommend that you use it in your production code.

The location can be user notebooks on Microsoft 365 or consumer OneDrive, group notebooks, or SharePoint site-hosted team notebooks on Microsoft 365.

![OneNote API development stack](https://cdn.graph.office.net/prod/GraphDocuments/en-us/concepts/images/onenote-dev-diagram.png)

## User notebooks

To access personal notebooks on consumer OneDrive or OneDrive for Business, use one of the following URLs:

```http
https://graph.microsoft.com/{version}/me/onenote/{notebooks | sections | sectionGroups | pages} 
https://graph.microsoft.com/{version}/users/{userPrincipalName}/onenote/{notebooks | sections | sectionGroups | pages} 
https://graph.microsoft.com/{version}/users/{id}/onenote/{notebooks | sections | sectionGroups | pages} 
```

- `me` is for OneNote content that the current user can access \(owned and shared\).
- `users/{id}` is for OneNote content that the specified user \(in the URL\) has shared with the current user. Use the [users](https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0) API.

> **Note:** You can get user IDs by making a GET request on `https://graph.microsoft.com/v1.0/users`.

## Group notebooks

To access notebooks that are owned by a group, use the following service root URL:

```http
https://graph.microsoft.com/{version}/groups/{id}/onenote/{notebooks | sections | sectionGroups | pages} 
```

## SharePoint site notebooks

To access notebooks that are owned by a SharePoint team site, use the following service root URL:

```http
https://graph.microsoft.com/{version}/sites/{id}/onenote/{notebooks | sections | sectionGroups | pages} 
```
