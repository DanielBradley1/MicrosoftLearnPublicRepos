<!-- Source: https://learn.microsoft.com/en-us/graph/api/newslinkpage-publish?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-04 -->

# newsLinkPage: publish

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Publish the latest version of a [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) resource that makes the version available to all users. If the page is checked out, check it in first and then publish it. If the page is checked out to the caller of this API, it is automatically checked in and then published. If content approval is activated in the page library, the page isn't published until the approval flow is completed.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Files.ReadWrite.All, Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Files.ReadWrite.All | Sites.ReadWrite.All |

## HTTP request

```http
POST /sites/{siteId}/pages/{pageId}/microsoft.graph.newsLinkPage/publish
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/sites/c1370818-f5e0-4a40-a99b-be4520640642/pages/637c601e-0d0e-43c0-b50f-b18513bb9de2/microsoft.graph.newsLinkPage/publish
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
