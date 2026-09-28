<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingstaffmember-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-05 -->

# Delete bookingStaffMember

Namespace: microsoft.graph

Delete a [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) in the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Bookings.ReadWrite.All | Bookings.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Bookings.ReadWrite.All | Bookings.Manage.All |

## HTTP request

```http
DELETE /solutions/bookingBusinesses/{id}/staffMembers/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Example

### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/staffMembers/5fae928f-6d2d-417a-ad96-4b0caeb362d6
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
