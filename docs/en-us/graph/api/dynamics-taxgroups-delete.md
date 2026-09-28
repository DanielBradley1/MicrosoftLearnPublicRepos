<!-- Source: https://learn.microsoft.com/en-us/graph/api/dynamics-taxgroups-delete?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Delete taxGroups

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Delete a tax group object from Dynamics 365 Business Central.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Financials.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Financials.ReadWrite.All | Not available. |

## HTTP request

```
DELETE /financials/companies/{id}/taxGroups/{id}
```

## Optional query parameters

This method supports the [OData Query Parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Header | Value |
| --- | --- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| If-Match | Required. When this request header is included and the eTag provided doesn't match the current tag on the **taxGroups**, the **taxGroups** aren't updated. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns `204,No Content` response code. It doesn't return anything in the response body.

## Example

**Request**

The following example shows a request.

```http
DELETE https://graph.microsoft.com/beta/financials/companies/{id}/taxGroups/{id}
```

**Response**

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
